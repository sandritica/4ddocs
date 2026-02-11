---
id: get-table-properties
title: GET TABLE PROPERTIES
slug: /commands/get-table-properties
displayed_sidebar: docs
---

<!--REF #_command_.GET TABLE PROPERTIES.Syntax-->**GET TABLE PROPERTIES** ( *tablePtr* : Pointer ; *invisible* : Boolean {; *trigSaveNew* : Boolean {; *trigSaveRec* : Boolean {; *trigDelRec* : Boolean {; *trigLoadRec* : Boolean}}}} )<br/>**GET TABLE PROPERTIES** ( *tableNum* : Integer ; *invisible* : Boolean {; *trigSaveNew* : Boolean {; *trigSaveRec* : Boolean {; *trigDelRec* : Boolean {; *trigLoadRec* : Boolean}}}} )<!-- END REF-->
<!--REF #_command_.GET TABLE PROPERTIES.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| tablePtr | Pointer | &#8594; | Puntero de tabla |
| tableNum | Integer | &#8594;  | Número de tabla |
| invisible | Boolean | &#8592; | True = Invisible, False = Visible |
| trigSaveNew | Boolean | &#8592; | True = Trigger “On saving new record” activado; de lo contrario, False |
| trigSaveRec | Boolean | &#8592; | True = Trigger “On saving an existing record” activado; de lo contrario, False |
| trigDelRec | Boolean | &#8592; | True = Trigger “On deleting a record” activado; de lo contrario, False |
| trigLoadRec | Boolean | &#8592; | *** No usado (obsoleto) *** |

<!-- END REF-->

## Descripción 

<!--REF #_command_.GET TABLE PROPERTIES.Summary-->El comando GET TABLE PROPERTIES devuelve las propiedades de la tabla pasada por *ptrTabla* o *numTabl* *a*.<!-- END REF--> Puede pasar en el primer parámetro el número de tabla o puntero de la tabla. 

Una vez ejecutado el comando:

* El parámetro *invisible* devuelve True si el atributo “Invisible” ha sido definido para la tabla, de lo contrario False. El atributo invisible permite ocultar la tabla en los editores estándar de 4D (etiquetas, gráficos...).
* El parámetro *trigSaveNew* devuelve True si el trigger “Al guardar un registro nuevo” se ha activado para la tabla, de lo contrario False.
* El parámetro *trigSaveRec* devuelve True si el trigger “Al guardar un registro existente” se ha activado para la tabla, de lo contrario False.
* El parámetro *trigDelRec* devuelve True si el trigger “Al borrar un registro” se ha activado para esta tabla, de lo contrario False.

## Ver también 

[GET FIELD ENTRY PROPERTIES](get-field-entry-properties.md)  
[GET FIELD PROPERTIES](get-field-properties.md)  
[GET RELATION PROPERTIES](get-relation-properties.md)  

## Propiedades

|  |  |
| --- | --- |
| Número de comando | 687 |
| Hilo seguro | yes |
