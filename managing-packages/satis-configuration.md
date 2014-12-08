Satis Configuration
===================

Enable the Satis plugin on each Package you want to expose via Satis. A webhook will be installed in GitHub or
GitLab to enable the automatic update of your Satis repository information.


Manually updating Satis
-----------------------

Sometimes you need to manually build or generate the exposed Satis information. You can do this by using the
Packages command-line interface.


### Updating satis.json

`satis.json` is the Satis configuration file. This file tells Satis which repositories to look at.

```
bin/console satis:update
```

This command generates an updated satis.json with all enabled packages.


### Updating the exposed packages.json

`packages.json` is publicly accessible, exposing information about the available repositories
and their branches, tags, etc. Once `satis.json` is updated, run the build command to update `packages.json`.

```
bin/console satis:build
```

Alternatively, running the `satis:update` command while passing `--build` will both
update `satis.json` and build `packages.json`.

```
bin/console satis:update --build
```

