---
id: listbox-set-locked-columns
title: LISTBOX SET LOCKED COLUMNS
slug: /commands/listbox-set-locked-columns
displayed_sidebar: docs
---

<!--REF #_command_.LISTBOX SET LOCKED COLUMNS.Syntax-->**LISTBOX SET LOCKED COLUMNS** ( * ; *object* : Text ; *numColumns* : Integer )<br/>**LISTBOX SET LOCKED COLUMNS** ( *object* : Variable ; *numColumns* : Integer )<!-- END REF-->
<!--REF #_command_.LISTBOX SET LOCKED COLUMNS.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| * | Operator | &#8594; | Si se especifica, objeto es un nombre de objeto (cadena)Si se omite, objeto es una variable |
| object | Text, Variable | &#8594; | Nombre del objeto formula (si se especifica *) o Variable (si se omite *) |
| numColumns | Integer | &#8594; | Número de columnas a bloquear |

<!-- END REF-->

## Descripción 

<!--REF #_command_.LISTBOX SET LOCKED COLUMNS.Summary-->El comando **LISTBOX SET LOCKED COLUMNS** bloquea las primeras *numColumns* columnas izquierdas del list box designado por los parámetros *object* y *\**.<!-- END REF-->  
  
Las columnas bloqueadas se muestran en la parte izquierda del list box y no se desplazan con el resto de las columnas del list box. Para mayor información, consulte el Manual de *Diseño*.  
  
Si pasa el parámetro opcional *\**, indica que el parámetro *objeto* es un nombre de objeto (una cadena). Si no pasa este parámetro, esto indica que el parámetro *object* es una variable. En este caso, se pasa una referencia de variable en lugar de una cadena.  
  
En *numColumns*, puede pasar cualquier valor entre 1 y el número total de columnas del list box -1\. Para un list box con X columnas, si pasa un valor > X-1 en *numColumns*, se reducirá automáticamente al valor X-1.

Para eliminar el bloqueo de columnas, pase 0 o un valor negativo en *numColumns*.

## Ver también 

[LISTBOX Get locked columns](listbox-get-locked-columns.md)  
[LISTBOX SET STATIC COLUMNS](listbox-set-static-columns.md)  

## Propiedades

|  |  |
| --- | --- |
| Número de comando | 1151 |
| Hilo seguro | no |
