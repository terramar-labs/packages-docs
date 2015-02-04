Upgrading Packages
==================

Since Packages 3.0, backwards compatibility breaks have been carefully avoided. However, upgrading along the 3.x line
does require some effort.


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


