---
id: listbox-get-number-of-columns
title: LISTBOX Get number of columns
slug: /commands/listbox-get-number-of-columns
displayed_sidebar: docs
---

<!--REF #_command_.LISTBOX Get number of columns.Syntax-->**LISTBOX Get number of columns** ( * ; *object* : Text ) : Integer<br/>**LISTBOX Get number of columns** ( *object* : Variable ) : Integer<!-- END REF-->
<!--REF #_command_.LISTBOX Get number of columns.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| * | Operator | &#8594; | Si se especifica, objeto es un nombre de objeto (cadena) Si se omite, objeto es una variable |
| object | Text, Variable | &#8594; | Nombre de objeto (si se especifica *) o Variable (si se omite *) |
| Resultado | Integer | &#8592; | Número de columnas |

<!-- END REF-->

## Descripción 

<!--REF #_command_.LISTBOX Get number of columns.Summary-->El comando **LISTBOX Get number of columns** devuelve el número total de columnas (visibles o invisibles) presentes en el list box designado por los parámetros *object* y *\**.<!-- END REF-->

Si pasa el parámetro opcional *\**, indica que el parámetro *object* es un nombre de objeto (cadena). Si omite este parámetro, indica que el parámetro *object* es una variable. En ese caso, no pasa una cadena, sino una referencia de variable. Para mayor información sobre nombres de objetos, consulte la sección *Propiedades de los objetos*. 

## Ver también 

[LISTBOX DELETE COLUMN](listbox-delete-column.md)  

## Propiedades

|  |  |
| --- | --- |
| Número de comando | 831 |
| Hilo seguro | no |
