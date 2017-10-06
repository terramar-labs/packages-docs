Installation
============

Pre-requisites:
 * PHP 5.6 or later
 * [Composer](https://getcomposer.org)
 * Some database platform supported by [Doctrine 2](http://doctrine-project.org) (sqlite works great!)
 * [Redis](https://redis.io/) 

Download the [latest release](https://github.com/terramar-labs/packages/releases/latest), or clone the repository.

```bash
git clone git@github.com:terramar-labs/packages.git
```

### Install dependencies

Switch to the project root directory and run `composer install`.

```bash
cd packages
composer install
```

### Edit configuration

Copy `config.yml.dist` to `config.yml` and edit as appropriate.

```bash
cp config.yml.dist config.yml
vi config.yml
```

### Generate the database schema

Packages uses Doctrine ORM to auto-generate the database schema for your configured platform.

```bash
bin/console orm:schema-tool:create
```

> Check the [Docker page](../getting-started/docker.md) for details on running Packages with Docker.

Running the application
-----------------------

Start PHP's built-in webserver to run the Packages web application with minimal effort.

```bash
# Visit http://localhost:8080 to see the landing page.
php -S localhost:8080 -t web
```

### Start a Resque worker

For fully-automatic integration with GitHub, GitLab, and your Satis repository, you must always have at least one Resque worker running. 

```bash
bin/console resque:worker:start
```

> For more information on Resque workers, check [the dedicated section](../managing-packages/resque.md).


### Development/debug mode

Visit `index_dev.php` in your browser to view the site with the `dev` environment configuration. In this env, views and the service container are not cached, so changes made are immediately visible.

Your installation is complete!


### Next up

[Using your Packages application](usage.md).
 