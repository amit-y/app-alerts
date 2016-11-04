# App Alerts

This web app creates alerts (of specific types) for applications.

## Screens

The app is a single page app with the following screens.

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

## Rest API

All requests return an `200` HTTP code when successful. Errors return a `500` HTTP code and the error message is specified within the body of the response in a JSON object.

- [ ] TODO Return specific error codes and not 500.
- [ ] TODO Implement paging so large responses can be handled efficiently.

### Applications
#### Show All Applications
Returns all applications in the system.

URL: `/applications`  
Method: `GET`
```
GET /applications
```
Returns: JSON object with all applications in an array
```
{
  applications: [
    {
      id: "135D23B3-D4EA-4057-816F-06E86227644B",
      name: "App 1",
      alertTypes: [
        {
          id: "4C629231-FBAB-4A76-BFA7-4A55F34A8D44",
          name: "Alert Type 1"
        }
      ]
    }
  ]
}
```

#### Fetch an Application
Returns a specific application, whose `id` is specified in the URL. If application does not exist, throws an error.

URL: `/applications/:id`  
Method: `GET`
```
GET /applications/135D23B3-D4EA-4057-816F-06E86227644B
```
Returns: JSON object with application object
```
{
  id: "135D23B3-D4EA-4057-816F-06E86227644B",
  name: "App 1",
  alertTypes: [
    {
      id: "4C629231-FBAB-4A76-BFA7-4A55F34A8D44",
      name: "Alert Type 1"
    }
  ]
}
```

#### Create Application
Saves new application.

URL: `/applications`  
Method: `POST`  
Input: Accepts JSON object with following params:
```
name: STRING  // Name of Application
alertTypes: [STRING] // Array of AlertType Ids
```
```
POST /applications  
{
  name: "App 2",
  alertTypes: [
    "4C629231-FBAB-4A76-BFA7-4A55F34A8D44"
  ]
}
```
Returns: JSON object with `id` of saved application
```
{
  id: "0883E13E-92A0-45BD-8FF9-3BBCCB01455D"
}
```

#### Update Application
Updates an existing application whose `id` is specified in the URL. If application does not exist, throws an error.

URL: `/applications/:id`  
Method: PUT  
Input: Accepts JSON object with following params:
```
name: STRING  // Name of Application
alertTypes: [STRING] // Array of AlertType Ids
```
```
PUT /applications/0883E13E-92A0-45BD-8FF9-3BBCCB01455D  
{
  name: "App 2",
  alertTypes: [
    "4C629231-FBAB-4A76-BFA7-4A55F34A8D44",
    "B6DD7F46-EB62-40E6-9BB6-D378B7A55274"
  ]
}
```
Returns: None

#### Delete an Application
Deletes an application, whose `id` is specified in the URL. If application does not exist, throws an error.

URL: `/applications/:id`  
Method: `DELETE`
```
DELETE /applications/0883E13E-92A0-45BD-8FF9-3BBCCB01455D 
```
Returns: None

### Alert Types
#### Show All Alert Types
Returns all alert types in the system.

URL: `/alerttypes`  
Method: `GET`
```
GET /alerttypes
```
Returns: JSON object with all alert types in an array
```
{
  alertTypes: [
    {
      id: "4C629231-FBAB-4A76-BFA7-4A55F34A8D44",
      name: "Alert Type 1"
    }
  ]
}
```

#### Fetch an Alert Type
Returns a specific alert type, whose `id` is specified in the URL. If alert type does not exist, throws an error.

URL: `/alerttypes/:id`  
Method: `GET`
```
GET /alerttypes/4C629231-FBAB-4A76-BFA7-4A55F34A8D44
```
Returns: JSON object with alert type object
```
{
  id: "4C629231-FBAB-4A76-BFA7-4A55F34A8D44",
  name: "Alert Type 1"
}
```

#### Create Alert Type
Saves new alert type.

URL: `/alerttypes`  
Method: `POST`  
Input: Accepts JSON object with following params:
```
name: STRING  // Name of Alert Type
```
```
POST /alerttypes  
{
  name: "Alert Type 2",
}
```
Returns: JSON object with `id` of saved alert type
```
{
  id: "B6DD7F46-EB62-40E6-9BB6-D378B7A55274"
}
```

#### Update Alert Type
Updates an existing alert type whose `id` is specified in the URL. If alert type does not exist, throws an error.

URL: `/alerttypes/:id`  
Method: PUT  
Input: Accepts JSON object with following params:
```
name: STRING  // Name of Alert Type
```
```
PUT /alerttypes/B6DD7F46-EB62-40E6-9BB6-D378B7A55274  
{
  name: "Alert Type 3"
}
```
Returns: None

#### Delete an Alert Type
Deletes an alert type, whose `id` is specified in the URL. If alert type does not exist, throws an error.

URL: `/alerttypes/:id`  
Method: `DELETE`
```
DELETE /alerttypes/B6DD7F46-EB62-40E6-9BB6-D378B7A55274
```
Returns: None

### Alerts
#### Show All Alerts
Returns all alerts in the system.

URL: `/alerts`  
Method: `GET`
```
GET /alerts
```
Returns: JSON object with all alerts in an array
```
{
  alerts: [
    {
      id: "143FF94D-F2E7-4AFE-B2BE-5AD777500487",
      timestamp: 1478241211255,
      application: {
        id: "135D23B3-D4EA-4057-816F-06E86227644B",
        name: "App 1"
      },
      alertType: {
          id: "4C629231-FBAB-4A76-BFA7-4A55F34A8D44",
          name: "Alert Type 1"
      }
    }
  ]
}
```

#### Create Alert
Saves new alert.

> Timestamp is generated by server in this implementation. However, it could just as easily have been generated on the client and sent to server as an input param.

URL: `/alerts`  
Method: `POST`  
Input: Accepts JSON object with following params:
```
application: STRING  // Application Id
alertType: STRING // AlertType Id
```
```
POST /alerts  
{
  application: "135D23B3-D4EA-4057-816F-06E86227644B",
  alertType: "4C629231-FBAB-4A76-BFA7-4A55F34A8D44"
}
```
Returns: JSON object with `id` and timestamp of alert
```
{
  id: "143FF94D-F2E7-4AFE-B2BE-5AD777500487",
  timestamp: 1478241211255
}
```
