Creating a Plugin
=================

Part of the power of Packages is its plugin architecture. This system allows you to hook into different areas of
Packages to enable new functionality.

> **Tip:** It is recommended that you fork the Packages repository before modification. This will allow you to continue
  to use git while keeping access to upstream changes.

The plugin system has three main components:

* A `Plugin` class which wires up services in the service container.
* One or more event subscribers (or listeners) which listen to specific events within Packages.
* Zero or more action listeners which can render widgets, allowing for configuration from the web interface.

Getting started
---------------

> **Notice:** This section is a work-in-progress.

Create a `Plugin` class that implements `Terramar\Packages\Plugin\PluginInterface`.

*  **configure(ContainerBuilder $builder)** is used to configure the given container builder. Register any services your plugin needs here.
*  **getName()** should return a displayable name for the plugin.
*  **getVersion()** should return some version, usually based on the underlying software.


### Events

Create any event subscribers, register them in your `Plugin`'s configure method.

> **Tip:** Check the [Event Reference](event-reference.md) for more details on which events you can listen to.


### Actions

Create any action handlers, register them in your `Plugin`'s configure method.

> **Tip:** Check the [Action Reference](action-reference.md) for more details on which actions you can handle.
