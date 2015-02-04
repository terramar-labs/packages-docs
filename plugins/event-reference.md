Event reference
===============

Packages dispatches different events when something occurs within the application. Your custom listeners can
listen for these events and act accordingly.


Event Name | Description
---------- | -----------
package.create | Fired when a new package is created. This occurs when Syncing a Remote.
package.update | Fired when a package's source code is updated. This happens when GitLab or GitHub notify Packages via webhook that code has been pushed.
package.enable | Fired when a package is enabled. This is when the GitLab and GitHub plugins register webhooks.
package.disable | Fired when a package is disabled. Webhooks are also disabled when this event fires.
remote.enable | Fired when a remote is enabled.
remote.disable | Fired when a remote is disabled. A listener for this event removes all webhooks from GitHub and GitLab for packages associated with the given remote.
