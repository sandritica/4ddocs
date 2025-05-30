---
id: on-system-event-database-method
title: On System Event database method
slug: /commands/on-system-event-database-method
displayed_sidebar: docs
---

<!--REF #_command_.On System Event database method.Syntax-->On System Event($event : Integer)<!-- END REF-->
<!--REF #_command_.On System Event database method.Params-->
| Parameter | Type |  | Description |
| --- | --- | --- | --- |
| $event | Integer | &#8592; | Event code |

<!-- END REF-->

## Description 

<!--REF #_command_.On System Event database method.Summary-->The **On System Event database method** is called each time a system event occurs.<!-- END REF--> This concerns all 4D environments: 4D (all modes) and 4D Server, as well as 4D applications that are compiled and merged with 4D Volume Desktop.

To process an event, you must test the value of the $event parameter within the method and compare it to one of the following constants, found in the *Database Events* theme:

| Constant                       | Type    | Value | Comment                                    |
| ------------------------------ | ------- | ----- | ------------------------------------------ |
| On application background move | Integer | 1     | The 4D application moves to the background |
| On application foreground move | Integer | 2     | The 4D application moves to the foreground |

These events are generated when a 4D application changes level, irrespective of the user action initiating this change. For example: 

* Clicking the window of the application or of another application,
* selecting it using the **Alt+Tab** (Windows) or **Command+Tab** (macOS) keyboard shortcut,
* Selecting the **Hide** command in the dock (macOS),
* Clicking the application icon in the dock or task bar,
* Clicking the minimize button of the main window (Windows).

It is absolutely necessary to declare the $event parameter (longint) in the database method. The structure of the database method code is therefore:

```4d
  // On System Event database method
 
 #DECLARE($event : Integer)
 Case of
    :($event=On application background move)
  //Do something
    :($event=On application foreground move)
  //Do something else
 End case
```
