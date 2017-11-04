# Docker

Get started instantly with the example `docker-compose.yml` that sets up nginx and Redis containers with Packages installed and configured, ready to try out.

> **Tip**: Check out [special-happiness](https://github.com/veonik/special-happiness) for an example of highly-available GitLab and Redis configurations.

## Getting started

Follow the steps outlined on the [Installation](installation.md) page, including the database schema creation. The Docker container is set up to use the files on your system, so changes made are visible on the container very quickly. But, this means you need to have all the dependencies and configuration set up prior to using Docker.

To run the setup, just use `docker-compose up`.

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
