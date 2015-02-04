packages
========

Packages extends [Satis](https://github.com/composer/satis), adding useful management functionality.

Packages automatically registers GitLab and GitHub project web hooks to keep Satis up to date. Packages also
features a web management interface that allows for easy management of exposed packages and configured source 
control repositories.

Packages version 3 works on a plugin based system based around source code repositories. Packages
can trigger, with each code push, many automated tasks like documentation generation or code 
analysis. The simple event-based architecture allows easy creation of new automation tasks.

Currently implemented plugins:

* **GitLab integration plugin**
  Provides project sync support and automatic webhook registration within GitLab.

* **GitHub integration plugin**
  Provides project sync support and automatic webhook registration within GitHub.

* **Satis plugin**
  Updates Satis when source code is updated.

* **Clone Project plugin**
  Clones the source code repository to allow for further analysis locally.

* **Sami plugin**
  Automatically generates documentation when code is pushed. Depends on Clone Project.
