---
id: listbox-insert-rows
title: LISTBOX INSERT ROWS
slug: /commands/listbox-insert-rows
displayed_sidebar: docs
---

<!--REF #_command_.LISTBOX INSERT ROWS.Syntax-->**LISTBOX INSERT ROWS** ( * ; *object* : Text ; *rowPosition* : Integer {; *numRows* : Integer} )<br/>**LISTBOX INSERT ROWS** ( *object* : Variable ; *rowPosition* : Integer {; *numRows* : Integer} )<!-- END REF-->
<!--REF #_command_.LISTBOX INSERT ROWS.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| * | Operator | &#8594; | Si se especifica, objeto es un nombre de objeto (cadena) Si se omite, objeto es una variable |
| object | Text, Variable | &#8594; | Nombre de objeto (si se especifica *) o Variable (si se omite *) |
| rowPosition  | Integer | &#8594; | Posición de la fila a insertar |
| numRows  | Integer | &#8594; | Número de líneas a insertar |

<!-- END REF-->

## Descripción 

<!--REF #_command_.LISTBOX INSERT ROWS.Summary-->El comando **LISTBOX INSERT ROWS** inserta una o varias nuevas líneas en el list box designado por los parámetros *object* y *\**.<!-- END REF-->

**Nota**: este comando funciona únicamente con los list box basados en arrays. Cuando este comando se utiliza con un list box basado en una selección, no hace nada y la variable sistema OK toma el valor 0.

Si pasa el parámetro opcional *\**, indica que el parámetro *object* es un nombre de objeto (cadena). Si omite este parámetro, indica que el parámetro *object* es una variable. En ese caso, no pasa una cadena, sino una referencia de variable. Para mayor información sobre nombres de objetos, consulte la sección *Propiedades de los objetos*. 

Por defecto, si se omite el parámetro *numRows*, sólo se inserta una línea. De lo contrario, el comando inserta el número de líneas definido en este parámetro.

La fila se inserta en la posición definida por el parámetro *rowPosition*. Una nueva fila se añade automáticamente en esta posición en todos los arrays utilizados por las columnas del list box, cualquiera que sea su tipo y visibilidad.

Si el valor de *rowPosition* es mayor que el número total de filas en el list box, la fila se añade al final de cada array. Si es igual a 0, la fila se añade al principio de cada array. Si contiene un valor negativo, el comando no hace nada.

## Ver también 

[LISTBOX DELETE ROWS](listbox-delete-rows.md)  

## Propiedades

|  |  |
| --- | --- |
| Número de comando | 913 |
| Hilo seguro | no |
| Modifica variables | OK |
