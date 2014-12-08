Installation
============

Packages requires:
 * PHP 5.4 or later
 * Some database platform supported by [Doctrine 2](http://doctrine-project.org)
 * Redis
 * [Composer](https://getcomposer.org)


First, clone the project and install dependencies.

```
git clone https://github.com/terramar-labs/packages
cd packages
composer install
```

Next, copy `config.yml.dist` to `config.yml`, editing any values necessary.

```
cp config.yml.dist config.yml
vi config.yml
```

Create your database if necessary, then run the schema tool to update your database schema.

```
bin/console orm:schema-tool:create
```

Next, point your webserver's webroot to your Packages installation's `web` folder.

Your installation is complete! Visit the project's web directory from your browser to configure your packages.
