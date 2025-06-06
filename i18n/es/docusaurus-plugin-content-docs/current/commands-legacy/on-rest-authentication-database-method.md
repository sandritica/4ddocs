---
id: on-rest-authentication-database-method
title: On REST Authentication database method
slug: /commands/on-rest-authentication-database-method
displayed_sidebar: docs
---

<!--REF #_command_.On REST Authentication database method.Syntax-->$1, $2, $3, $4 -> On REST Authentication database method -> $0<!-- END REF-->
<!--REF #_command_.On REST Authentication database method.Params-->
| Parameter | Type |  | Description |
| --- | --- | --- | --- |
| $1 | Text | &#8592; | User name |
| $2 | Text | &#8592; | Password |
| $3 | Boolean | &#8592; | True = Digest mode, False = Basic mode |
| $4 | Text | &#8592; | Ip address of the caller |
| $0 | Boolean | &#8592; | True = session opening accepted, False = session opening rejected |

<!-- END REF-->

## Description 

<!--REF #_command_.On REST Authentication database method.Summary-->The **On REST Authentication database method** is deprecated in projects as of 4D 20 R6.<!-- END REF-->

The [Force login authentication](../REST/authUsers.md) is now highly recommended. In converted projects, you can upgrade your configuration by clicking on the [**Activate REST authentication through ds.authentify() function**](../settings/web.md#access) settings button. See also [this blog post](https://blog.4d.com/force-login-becomes-default-for-all-rest-auth/) to know how to migrate your code if necessary.


## Properties

|  |  |
| --- | --- |
| Command number | 3367 |
| Thread safe | &cross; |


