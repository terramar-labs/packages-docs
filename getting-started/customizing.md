Customizing Packages
====================

Packages is easy to customize. Modify your Packages installation to suit your needs.


Modifying the landing page
--------------------------

The main landing page layout exists in `views/Default/base.html.twig`. You can modify this
file as necessary to customize Packages to suit your project or company.


Setting up Packages for development
-----------------------------------

> **Notice:** This section is a work-in-progress.

Fork the [Packages repository](https://github.com/terramar-labs/packages) on GitHub.

Clone your fork.

Edit composer.json to add your own namespace to the autoloader, if necessary.

Add upstream remote.

```bash
git remote add upstream https://github.com/terramar-labs/packages.git
```

Follow the normal install process: modify config.yml, install dependencies, create database and schema.

Now visit `web/index_dev.php` to start Packages in the `dev` environment. Caching is disabled and helpful
errors are displayed.
