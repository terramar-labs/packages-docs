Satis Configuration
===================

Enable the Satis plugin on each Package you want to expose via Satis. A webhook will be installed in GitHub or
GitLab to enable the automatic update of your Satis repository information.

> **Note:** You must also ensure a Resque worker is running for automatic webhook updating to work. See the
  [section on Resque management](resque.md) for more information.

Packages uses the information retrieved from GitHub and GitLab to generate a `satis.json` configuration. Satis consumes this file, and generates a `packages.json` file that Composer can use to resolve private dependencies.

> **Notice:** `packages.json` is publicly accessible, exposing information about the available repositories
and their branches, tags, etc.

Manually updating Satis
-----------------------

Sometimes you need to manually build or generate the exposed Satis information. You can do this by using the Packages command-line interface.


```
bin/console satis:build
```

Alternatively, running the `satis:update` command while passing `--build` will both
update `satis.json` and build `packages.json`.

```
bin/console satis:update --build
```

Using your Satis repository
---------------------------

In your project's `composer.json`, add the section `repositories` if it doesn't already exist. Then add a new `composer` repository with your Packages URL as the `url`.

```json
{
  /* ... */
  "require": { /* ... */ },
  "repositories": [
    {
      "type": "composer",
      "url":  "https://packages.example.com/"
    }
  ],
  /* ... */
}
```