# Docker

Packages comes with an example `docker-compose.yml` that sets up the necessary web and Redis server, along with the option to create a self-hosted GitLab with a Highly-Available Redis configuration.

## Getting started

Follow the steps outlined on the [Installation](installation.md) page, including the database schema creation. The Docker container is set up to use the files on your system, so changes made are visible on the container very quickly. But, this means you need to have all the dependencies and configuration set up prior to using Docker.

To run the default setup, Packages and a single Redis server, just use `docker-compose up`.

```bash
docker-compose up
```

Docker will download the necessary images and start the containers. Once the containers are started, visit `http://localhost` in your browser, and you will be greeted with the Packages landing page.

> Visit Packages in your browser at `http://localhost`.

Note that in the default configuration, Docker will setup Nginx to direct all requests to `index_dev.php`, which will cause an error since your browser is not local to the Packages application. **Comment out the local checks in `index_dev.php` to use Docker**.

```php
<?php

/* .. */

// Borrowed from Symfony
//if (isset($_SERVER['HTTP_CLIENT_IP'])
//    || isset($_SERVER['HTTP_X_FORWARDED_FOR'])
//    || !in_array(@$_SERVER['REMOTE_ADDR'], array('127.0.0.1', '::1', 'fe80::1'))
//) {
//    header('HTTP/1.0 403 Forbidden');
//    exit('You are not allowed to access this file. Check ' . basename(__FILE__) . ' for more information.');
//}

```

### Running Resque workers

Resque workers are not started automatically. Start one after the `web` container is running using `docker exec`.

```bash
# In a different terminal from where you ran `docker-compose up`
docker exec -t packages_web_1 /bin/bash -c \
    'cd /app && bin/console resque:worker:start'
```

> **Find the name of a specific container** by using `docker ps`.
  ```bash
  docker ps
  ```

> **Start a bash session on the `web` container** with `docker exec`.
  ```bash
  # Hint: replace `packages_web_1` with another container's name to 
  # start a shell for that container.
  docker exec -it packages_web_1 /bin/bash
  ```

## Self-hosted GitLab container

Open up `docker-compose.yml` in your favorite editor and uncomment the line about GitLab.

```yaml
# docker-compose.yml
version: '2'
services:
  web:
    image: webdevops/php-nginx:7.1
    volumes:
      - .:/app
      - ./docker/nginx/vhost.common.d/vhost.common.conf:/opt/docker/etc/nginx/vhost.common.d/10-location-root.conf
    links:
      - redis-master
#      - redis-slave      # Uncomment to start a slave Redis container
      - gitlab           # Uncommented, start a GitLab CE container (starts mailhog, too)
# ...
```

Bring up the Docker-composition, but ensure you destroy the old Docker-compose setup with `docker-compose down`. 

```bash
docker-compose down
# Then start it back up
docker-compose up
```

GitLab takes a while to get going, but once you see happy log messages in the Docker monitor, visit `http://127.0.0.1:8082`. You should be greeted with a first-time password set (the default username is `root`) and then you're set. Add some repositories, create a Remote in Packages using your GitLab user's Private Auth Token and the URL `http://127.0.0.1:8082` and Synchronize!

> Access GitLab in your browser at `http://127.0.0.1:8082`.

### MailHog

GitLab sends emails, so this Docker-composition includes a [MailHog](https://github.com/mailhog/MailHog) container. View any emails sent by GitLab by visiting `http://127.0.0.1:8025` in your browser.

> Access MailHog's UI in your browser at `http://127.0.0.1:8025`.

## Highly-available Redis setup

The Redis server Docker configuration comes with Redis Sentinel built-in. Sentinel can be used to switch masters automatically when the current master fails.

> Packages doesn't yet support Sentinel's fail-overs, but GitLab does.

The first Redis server container started is called `redis-master`. This server already has Sentinel running on port 26379 (along with Redis on 6379).

Additional "slave" servers can be started using `docker-compose scale`.

```bash
# Start two (2) Redis slaves.
docker-compose scale redis-slaves=2
```