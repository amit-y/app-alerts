# App Alerts

This web app creates alerts (of specific types) for applications. The app is a single page app with the following screens.

## Screens

### Applications

![Applications Screen](https://amit-y.github.io/app-alerts/docs/images/applications-screen.png)

This screen lists the applications that are available in the app.

* User clicks the `Create New` button to create an application.
* User clicks the `Delete` button to delete the application listed on that specific line.
* User can click on an application name to edit the application.

### Applications Edit

![Applications Edit Screen](https://amit-y.github.io/app-alerts/docs/images/applications-edit-screen.png)

This screen allows users to edit an application. The user is also presented with this screen when adding a new application.

* When editing an application, the application name is listed within the text input, allowing user to edit. For new application, text input is blank.
* User can select alert types from the list of alert types listed.
* User clicks on the `Save` button to save application with selected alert types.

### Alert Types

![Alert Types Screen](https://amit-y.github.io/app-alerts/docs/images/alert-types-screen.png)

This screen allows users to add/edit/delete alert types.

* Existing alert types are listed in a table.
* User clicks on the `Create New` button to add an alert type. This adds a text input in a row in the table, where user can enter a name for an alert type and hit enter to create the alert type.
* User clicks on an alert type to edit an alert type in-place. The alert type is shown in a text input, which user can edit and hit enter to save.
* User clicks the `Delete` button to delete the alert type listed on that specific line.

### Alerts

![Alerts Screen](https://amit-y.github.io/app-alerts/docs/images/alerts-screen.png)

This screen lists all alerts created within the app.

* Alerts are shown in a table with date and time, application name, and alert type listed.
* Alerts are ordered in the table as most recent first.

### Create New Alert

![Create New Alert Screen](https://amit-y.github.io/app-alerts/docs/images/create-new-alert-screen.png)

This screen allows users to create new alerts.

* User selects an application from the drop down list. The drop down will contain a list of all applications in the system.
* User then selects an alert type from the second drop down. Only alert types allowed (from the Applications Edit screen) for the application selected in the first drop down will be listed within this drop down. This drop down is initially disabled, till an application is selected from the first drop down.
* User clicks `Create Alert` button to create the alert. Alert is added to Alerts screen, on top of list.
