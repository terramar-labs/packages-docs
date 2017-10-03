Upgrading Packages
==================

Since Packages 3.0, backwards compatibility breaks have been carefully avoided. However, upgrading along the 3.x line does require some effort.


## 3.0.x to 3.1.0

Packages 3.1.0 introduces the Sami and Clone Project plugins.

First, update your Packages installation using git.

```bash
git fetch
git checkout 3.1.0
```

Next, install updated dependencies.

```bash
composer install -o --no-dev
```

Clear the application cache.

```bash
rm -rf cache/*
```

Finally, run the version's database migration.

```bash
bin/console migrations:migrate
```


## 3.0.0 to 3.0.1

> **Notice:** Packages 3.0.1 updated its dependency on nice/doctrine-orm which caused the format of `config.yml` to change.

The `doctrine:mapping:` section was extended to allow multiple entity managers. Update your `config.yml`,
using `config.yml.dist` as a guide.

```yml
doctrine:
  mapping:
-    paths: [ '%app.root_dir%/src/Terramar/Packages/Entity', '%app.root_dir%/src/Terramar/Packages/Plugin' ]
+    default:
+      paths: [ '%app.root_dir%/src/Entity', '%app.root_dir%/src/Plugin' ]
+      namespace: Terramar
  database:
    # ...
```

