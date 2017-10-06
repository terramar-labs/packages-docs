Using the application
=====================

Packages is made up of two things:

* A **Remote** is a source code host: GitHub or GitLab. Packages can be used for self-hosted GitLab instances.
* Each Remote may have one or more **Package**s. A Package represents a source code repository.

When code is pushed to the source code repository, Packages will be notified via automatically installed webhooks and whatever configured tasks will run.

The original and most-used task executes a rebuild of the Composer package index. Another task generates documentation from your source code using `sami`.

More tasks can be made by creating a Plugin that responds to various events such as when code is pushed to a repository.

Getting started
---------------

Once your Packages installation is up and running, you'll want to create a Remote.

### Creating a Remote

Click the Remotes button on the sidebar, then click New Remote.

On the New Remote screen, enter a name and choose the Adapter, either GitHub or GitLab. Enter the necessary token information and then click Create Remote.

With a Remote created, you need to Sync your Packages install with the remote source code host. Click the Sync button on the Remotes listing page to create an index of available source code repositories.

> **Note:** The Remote's configured GitHub or GitLab API token determines the permissions and access rights for which projects Packages can see.

### Enable a Package

Once your Remote has been synchronized, visit the Packages page.

To enable the code-push webhook for a project, click the Enable button.

To enable and configure a specific plugin (such as the Satis plugin), click Edit.

The Edit Package screen shows which plugins are available for the package and whatever configuration options they have.

To add a Package to your Composer repository index, enable the Composer Satis plugin. 

To generate API documentation using Sami, enable the Clone Project and Sami plugins.

> **Note**: Check the [Satis Configuration section](../managing-packages/satis-configuration.md) for more information on Satis.

# Next up

Read about [customizing Packages](../managing-packages/customizing.md) or [running Packages with Docker](docker.md).

### Having trouble?

View [troubleshooting resources](../managing-packages/troubleshooting.md).