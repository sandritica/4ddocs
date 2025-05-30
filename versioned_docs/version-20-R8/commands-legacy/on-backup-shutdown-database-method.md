---
id: on-backup-shutdown-database-method
title: On Backup Shutdown database method
slug: /commands/on-backup-shutdown-database-method
displayed_sidebar: docs
---

<!--REF #_command_.On Backup Shutdown database method.Syntax-->On Backup Shutdown ($status)<!-- END REF-->
<!--REF #_command_.On Backup Shutdown database method.Params-->
| Parameter | Type |  | Description |
| --- | --- | --- | --- |
| $status | Integer | &#8592; | 0 = backup executed correctly; other value = error, interrupted by user or code returned by On Backup Startup |

<!-- END REF-->

## 

<!--REF #_command_.On Backup Shutdown database method.Summary-->The On Backup Shutdown database method is called every time a database backup ends.<!-- END REF--> The reasons for the stoppage of a backup can be the end of the copy, user interruption or an error.  
This concerns all 4D environments: 4D (all modes), 4D Server as well as 4D applications compiled and merged with 4D Volume Desktop. 

The On Backup Shutdown database method allows verifying that the backup was executed correctly. It receives, in the *$status* parameter, a value representing the status of the backup once completed:

* If the backup was executed correctly, *$status* equals 0.
* If the backup was interrupted by the user or following an error, *$status* is different from 0\.  
   * If the backup was stopped by the [On Backup Startup Database Method](on-backup-startup-database-method.md), *$status* gets the value actually returned in the *$result* parameter. This allows you to implement a customized error management system.  
   * If the backup was stopped due to an error, the error code is returned in *$status*.  
In any case, you can get information about the error using the [BACKUP INFO](backup-info.md) command.

**Note**: You must declare the *$status* parameter (longint) in the database method:

```4d
 #DECLARE( $status : Integer)
```

It is important to note that in the case of an error during backup (disk full, support unavailable, etc.), the information related to the error is only displayed in the 4D Server monitor or in the MSC, and copied into the backup log. No alert dialog box appears and the *error* variable is not modified. If you want to be able to notify the administrator that an error has occurred, particularly in the context of an application running in client/server mode, you will need to use the **On Backup Shutdown database method**.
