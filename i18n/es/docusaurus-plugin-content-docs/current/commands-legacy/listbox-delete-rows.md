---
id: listbox-delete-rows
title: LISTBOX DELETE ROWS
slug: /commands/listbox-delete-rows
displayed_sidebar: docs
---

<!--REF #_command_.LISTBOX DELETE ROWS.Syntax-->**LISTBOX DELETE ROWS** ( * ; *object* : Text ; *rowPosition* : Integer {; *numRows* : Integer} )<br/>**LISTBOX DELETE ROWS** ( *object* : Variable ; *rowPosition* : Integer {; *numRows* : Integer} )<!-- END REF-->
<!--REF #_command_.LISTBOX DELETE ROWS.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| * | Operador | &#8594; | Si se especifica, objeto es un nombre de objeto (cadena) Si se omite, objeto es una variable |
| object | Text, Variable | &#8594; | Nombre de objeto (si se especifica *) o Variable (si se omite *) |
| rowPosition | Integer | &#8594; | Posición de la fila a eliminar |
| numRows | Integer | &#8594; | Número de líneas a borrar |

<!-- END REF-->

## Descripción 

<!--REF #_command_.LISTBOX DELETE ROWS.Summary-->El comando **LISTBOX DELETE ROWS** borra una o varias líneas a partir de *rowPosition* (visible o no) del list box definido por los parámetros *object* y \*.<!-- END REF-->

**Nota**: este comando funciona únicamente con los list box basados en arrays. Cuando este comando se utiliza con un list box basado en una selección, no hace nada y la variable sistema OK devuelve 0

Si pasa el parámetro opcional *\**, indica que el parámetro *object* es un nombre de objeto (cadena). Si omite este parámetro, indica que el parámetro *object* es una variable. En ese caso, no pasa una cadena, sino una referencia de variable. Para mayor información sobre nombres de objetos, consulte la sección *Propiedades de los objetos*. 

Recuerde que después de la ejecución del comando, no habrá ningún elemento seleccionado en el list box.

La fila *rowPosition* se elimina automáticamente de todos los arrays utilizados por las columnas del list box.   

Si el parámetro *rowPosition* es superior al número de líneas del array del list box o si es inferior a 1, el comando no hace nada. 

**Nota**: este comando no tiene en cuenta los posibles estados ocultos/visibles de las líneas del list box.

## Ver también 

[LISTBOX Get number of rows](listbox-get-number-of-rows.md)  
[LISTBOX INSERT ROWS](listbox-insert-rows.md)  

## Propiedades

|  |  |
| --- | --- |
| Número de comando | 914 |
| Hilo seguro | no |
| Modifica variables | OK |
