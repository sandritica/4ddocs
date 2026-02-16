---
id: listbox-get-table-source
title: LISTBOX GET TABLE SOURCE
slug: /commands/listbox-get-table-source
displayed_sidebar: docs
---

<!--REF #_command_.LISTBOX GET TABLE SOURCE.Syntax-->**LISTBOX GET TABLE SOURCE** ( * ; *object* : Text ; *tableNum* : Integer {; *name* : Text {; *highlightName* : Text}} )<br/>**LISTBOX GET TABLE SOURCE** ( *object* : Variable ; *tableNum* : Integer {; *name* : Text {; *highlightName* : Text}} )<!-- END REF-->
<!--REF #_command_.LISTBOX GET TABLE SOURCE.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| * | Operator | &#8594; | Si se especifica, objeto es un nombre de objeto (cadena) Si se omite, objeto es una variable |
| object | Text, Variable | &#8594; | Nombre del objeto formulario (si se especifica *) o Variable (si se omite *) |
| tableNum | Integer | &#8592; | Número de la tabla de la selección |
| name | Text | &#8592; | Nombre de la selección temporal o "" para la selección actual |
| nomSel | Text | &#8592; | Nombre del conjunto seleccionado |

<!-- END REF-->

## Descripción 

<!--REF #_command_.LISTBOX GET TABLE SOURCE.Summary-->El comando LISTBOX GET TABLE SOURCE permite conocer la fuente actual de datos mostrados en el list box designado por los parámetros *\** y *object*.<!-- END REF-->

Si pasa el parámetro opcional *\**, indica que el parámetro *object* es un nombre de objeto (cadena). Si no pasa este parámetro, indica que el parámetro *object* es una variable. En este caso, no pase una cadena sino una referencia de variable. Para mayor información sobre nombres de objeto, por favor consulte la sección *Propiedades de los objetos*.

El comando devuelve en el parámetro *tableNum* el número de la tabla principal asociada al list box y en el parámetro opcional *name* el nombre de la selección temporal eventualmente utilizada.

Si las líneas del list box están vinculadas con la selección actual de la tabla, el parámetro *name*, si se pasa, devuelve una cadena vacía. Si las líneas del list box están vinculadas con una selección temporal, el parámetro *name* devuelve el nombre de esta selección temporal.

Si el list box está asociado con arrays, *numTabla* devuelve -1 y *tempo*, si se pasa, devuelve una cadena vacía.

## Ver también 

[LISTBOX SET TABLE SOURCE](listbox-set-table-source.md)  

## Propiedades

|  |  |
| --- | --- |
| Número de comando | 1014 |
| Hilo seguro | no |
