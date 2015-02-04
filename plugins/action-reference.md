Action reference
================

Actions are the key to adding functionality to the web management portal.

Actions function much like events except that certain actions require a Response, while the others
might handle submitted form data. For example, plugin actions render widgets when you visit a package's
edit page. When you submit that edit form, plugin actions are called to handle the form data.


Types:
  **render** type actions *must* return a Response.
  **submit** type actions handle form submissions and are paired with **render** actions.

Action name | Type | Description
----------- | ---- | -----------
dashboard.index | render | This action should render a single dashboard widget
remote.new | render | This action should render a form to configure a new remote
remote.create | submit | This action is dispatched when a remote's creation form is submitted
remote.edit | render | This action should render a form to configure a existing remote
remote.update | submit | This action is dispatched when a remote's edit form is submitted
package.edit | render | This action should render a form to configure a existing package
package.update | submit | This action is dispatched when a package's edit form is submitted



