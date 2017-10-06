Customizing Packages
====================

Packages is easy to customize. Modify your Packages installation to suit your needs.


Modifying the landing page
--------------------------

The main landing page layout exists in `views/Default/base.html.twig`. You can modify this
file as necessary to customize Packages to suit your project or company.


Setting up for local development
--------------------------------

> **Notice:** This section is a work-in-progress.

Fork the [Packages repository](https://github.com/terramar-labs/packages) on GitHub.

Clone your fork.

Edit composer.json to add your own namespace to the autoloader, if necessary. Change the composer package name, if desired.

Add upstream remote.

```bash
git remote add upstream https://github.com/terramar-labs/packages.git
```

Follow the normal [install process](../getting-started/installation.md): modify config.yml, install dependencies, create database and schema.

> Check the [Docker documentation](../getting-started/docker.md) for details on running Packages with Docker.

Start your webserver and visit `index_dev.php` in your browser to use Packages in the `dev` environment. Caching is disabled and helpful
errors are displayed.


More info
---------

Check out the [Contributing Guide](CONTRIBUTING.md) for the recommended way to set up your development environment.

Some tips:

* Views are written using Twig and stored in `views/`.
  * Views are cached in `prod` env; use `http://localhost:8080/index_dev.php` to develop.
  * All pages inherit from `views/base.html.twig`, except for
  * Public landing page views inherit from `views/Default/base.html.twig`.
* [Composer Components](http://robloach.github.io/component-installer/) are used to manage front-end dependencies. The respective `web/images/`, `web/js/bootstrap.min.js`, and such are symlinks pointing to the real files installed by Composer in `vendor/`.
* Invoke a webhook with CURL.
  ```bash
  # Replace `123` below with an appropriate Package ID.
  curl -L http://localhost/webhook/123/receive
  ```