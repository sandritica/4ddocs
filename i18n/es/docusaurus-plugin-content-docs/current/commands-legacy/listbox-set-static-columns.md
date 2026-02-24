---
id: listbox-set-static-columns
title: LISTBOX SET STATIC COLUMNS
slug: /commands/listbox-set-static-columns
displayed_sidebar: docs
---

<!--REF #_command_.LISTBOX SET STATIC COLUMNS.Syntax-->**LISTBOX SET STATIC COLUMNS** ( * ; *object* : Text ; *numColumn* : Integer )<br/>**LISTBOX SET STATIC COLUMNS** ( *object* : Variable ; *numColumn* : Integer )<!-- END REF-->
<!--REF #_command_.LISTBOX SET STATIC COLUMNS.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| * | Operator | &#8594; | Si se especifica, objeto es un nombre de objeto (cadena)Si se omite, objeto es una variable |
| object | Text, Variable | &#8594; | Nombre de objeto formulario (si se especifica *) o Variable (si se omite *) |
| numColumn | Integer | &#8594; | Número de columnas a convertir estáticas |

<!-- END REF-->

## Descripción 

<!--REF #_command_.LISTBOX SET STATIC COLUMNS.Summary-->El comando **LISTBOX SET STATIC COLUMNS** define las primeras *numColumns* columnas (empezando por la izquierda) en el list box designado por los parámetros *object* y *\**.<!-- END REF-->

Las columnas estáticas no pueden moverse en el list box.

**Nota:** las columnas estáticas y las columnas bloqueadas son dos funcionalidades independientes. Para mayor información, consulte el manual de *Diseño*.

## Ver también 

[LISTBOX Get static columns](listbox-get-static-columns.md)  
[LISTBOX SET LOCKED COLUMNS](listbox-set-locked-columns.md)  

## Propiedades

|  |  |
| --- | --- |
| Número de comando | 1153 |
| Hilo seguro | no |
