# Packages

> Source code repository management made simple.

Packages extends [Satis](https://github.com/composer/satis), adding useful management functionality.

[Download the latest release](https://github.com/terramar-labs/packages/releases/latest).

Packages automatically registers GitLab and GitHub project web hooks to keep Satis up to date. Packages also
features a web management interface that allows for easy management of exposed packages and configured source 
control repositories.

The application is made up of three things: Remotes and Packages and Plugins. A Remote is somewhere that one or more projects, 
known as Packages, are hosted, for example GitHub or GitLab. Plugins integrate new source code hosts, or generate your Composer repository index, or generate documentation, or run unit tests, etc, when you push code to your repositories.

Packages automatically registers GitLab and GitHub project webhooks to keep Satis up to date every time you push code. Packages also features a web management interface that allows for easy management of exposed packages and configured source control repositories.

Packages version 3 works on a plugin based system based around source code repositories. Packages can trigger, with each code push, many automated tasks like documentation generation or code  analysis. The simple event-based architecture allows easy creation of new automation tasks.

Currently implemented plugins:

* **GitLab integration plugin**
  Provides project sync support and automatic webhook registration within GitLab.

* **GitHub integration plugin**
  Provides project sync support and automatic webhook registration within GitHub.

* **Satis plugin**
  Updates Satis when source code is updated. [View documentation](managing-packages/satis-configuration.md).

* **Clone Project plugin**
  Clones the source code repository to allow for further analysis locally.

* **Sami plugin**
  Automatically generates documentation when code is pushed. Depends on Clone Project.
