---
id: sql-export-database
title: SQL EXPORT DATABASE
slug: /commands/sql-export-database
displayed_sidebar: docs
---

<!--REF #_command_.SQL EXPORT DATABASE.Syntax-->**SQL EXPORT DATABASE** ( *folderPath* {; *numFiles* {; *fileLimitSize* {; *fieldLimitSize*}}} )<!-- END REF-->
<!--REF #_command_.SQL EXPORT DATABASE.Params-->
| Parameter | Type |  | Description |
| --- | --- | --- | --- |
| folderPath | Text | &#8594;  | Pathname of export folder or "" to display folder selection dialog box |
| numFiles | Integer | &#8594;  | Maximum number of files per folder |
| fileLimitSize | Integer | &#8594;  | Size limit value of export files (in KB) |
| fieldLimitSize | Integer | &#8594;  | Size limit (in bytes) below which the contents of a Text, BLOB or Picture field is embedded into the main file |

<!-- END REF-->

## Description 

<!--REF #_command_.SQL EXPORT DATABASE.Summary-->The SQL EXPORT DATABASE command exports in SQL format all the records of all the tables in the database.<!-- END REF--> In SQL, this global export operation is called "Dump".

**Note:** This command cannot be used with an external connection that has been opened directly or via ODBC. 

For each table, the command generates a text file containing the SQL statements necessary for importing data into another database. This file can be used directly by the [SQL EXECUTE SCRIPT](sql-execute-script.md) command in order to import data into another 4D database. 

The export files will be placed in a folder named "SQLExport" that is created in the destination folder designated by the *folderPath* parameter. Please note that if an "SQLExport" folder already exists at the location specified, the command will replace it without any warning message being displayed.   
If you pass an empty string in this parameter, 4D displays a standard dialog box which lets the user designate the destination folder. By default, the dialog box displays the current folder of the user that opened the session ("My Documents" under Windows or "Documents" under Mac OS).

For each exported table, the command carries out the following actions:

* a subfolder with the table name is created in the destination folder.
* a text file named "Export.sql" is created in the subfolder. This file is encoded in UTF-8 with a BOM (byte-order mark). It contains SQL *INSERT* orders corresponding to the exported data. The field values are separated by colons. There may be fewer values than there are fields in the table. In this case, the remaining fields will be considered NULL.
* if the table contains BLOB, picture or text fields (texts stored externally, in other words, outside of records), by default the command creates an additional subfolder named "BLOBS" next to the "Export.sql" file and creates as many subfolders named "BlobsX" as necessary. These subfolders will store as separate files the contents of all the BLOB, picture or external text fields of the table records. The BLOB files are named "BlobXXXXX.BLOB", the text files are named "TEXTXXXXX.TXT"(where XXXXX is a unique number generated by the application). The picture files are named PICTXXXXX.ZZZZ (where XXXXX is a unique number generated by the application and ZZZZ is the extension). When possible, pictures are exported in their original native format with the extension corresponding to the picture type (.jpg, .png, etc.). If the export is not possible in the native format, the pictures are exported in the internal 4D format 4D with the .4PCT extension.  
This default behavior can be adjusted according to the size of the data contained in the field using the optional *fieldLimitSize* parameter (see below).  
**Note:** This behavior differs when you execute **SQL EXPORT DATABASE** from a 4D in remote mode. In this context, the data to be stored externally are included automatically in the "Export.sql" file.

If you pass the *numFiles* parameter, the command will create as many "BlobsX" subfolders as necessary so that each one of them does not contain more than *numFiles* BLOB, picture or external text files. By default, if the *numFiles* parameter is omitted, the command limits the number of files to 200\. If you pass 0, each subfolder will contain at least one file.

The *fileLimitSize* parameter lets you set a size limit (in KB) for each "Export.sql" created on disk. Once the size of the export file being created reaches the value set in *fileLimitSize*, 4D stops writing records, closes the file and creates a new file named "ExportX.sql" (where X represents the sequence number) next to the previous one. Note that this is a theoretical limit: the actual size of the "ExportX.sql" files exceeds the value set by *fileLimitSize* because the file is only closed after the record that was being exported when the limit was reached has been completely written (the contents of the records is not divided). The minimum value accepted is 100 and the maximum value (default value) is 100,000 (100 MB).

The optional *fieldLimitSize* parameter sets a size limit below which the contents of an external BLOB, Picture or Text field will be embedded in the main "Export.sql" file rather than saved as a separate file. This purpose of this parameter is to optimize export operations by limiting the number of subfolders and files created on disk.   
This parameter must be expressed in bytes. For example, if you pass 1000, any external BLOB, Picture or Text fields that contain data with a size less than or equal to 1000 bytes are embedded into the main export file.   
Note that binary field data (BLOB and Picture) that are embedded into the export file are written in hexadecimal format, in the form of X'0f20' (standard SQL hexadecimal notation, see *literal*). This format is automatically supported by the 4D SQL engine.   
By default, if the *fieldLimitSize* parameter is omitted, external BLOB, Picture and Text fields are always exported as external files regardless of their size. 

In the export file, there may be fewer values than there are fields in the table. In this case, the empty fields will be considered as NULL. You can also pass the NULL value in a field.

If the export has been carried out correctly, the OK variable is set to 1\. Otherwise, it is set to 0\. 

### 

**Note:** This command does not support Object type fields.

## See also 

[SQL EXPORT SELECTION](sql-export-selection.md)  

## Properties

|  |  |
| --- | --- |
| Command number | 1065 |
| Thread safe | &cross; |
| Modifies variables | OK |


