Installation
============

Packages requires:
 * PHP 5.6 or later
 * Some database platform supported by [Doctrine 2](http://doctrine-project.org) (sqlite works great!)
 * [Redis](https://redis.io/)
 * [Composer](https://getcomposer.org)

Download the [latest release on GitHub](https://github.com/terramar-labs/packages/releases/latest) or clone the project.

```bash
git clone https://github.com/terramar-labs/packages
cd packages
```

Install dependencies.

```bash
composer install -o --no-dev
```

Copy `config.yml.dist` to `config.yml`, editing the values appropriately.

```bash
cp config.yml.dist config.yml
vi config.yml
```

Create your database if necessary, then run the schema tool to create your database schema.

```bash
bin/console orm:schema-tool:create
```

Next, you can use the built-in PHP webserver to test your setup.

```bash
php -S localhost:8081 -t /path/to/packages/web
```

Visit `localhost:8081` in your browser and you should see your Packages application. Login with the username and password you entered in `config.yml`.

The final step is starting a background worker. Packages relies on these to perform the heavy lifting behind-the-scenes.

```bash
bin/console resque:worker:start &
```

> **Note:** For more information on the Resque workers, check [the dedication section](../managing-packages/resque.md).

Your installation is complete!


### Next up

[Using your Packages application](usage.md).
 