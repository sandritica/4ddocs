---
id: listbox-get-hierarchy
title: LISTBOX GET HIERARCHY
slug: /commands/listbox-get-hierarchy
displayed_sidebar: docs
---

<!--REF #_command_.LISTBOX GET HIERARCHY.Syntax-->**LISTBOX GET HIERARCHY** ( * ; *object* : Text ; *hierarchical* : Boolean {; *hierarchy* : Pointer array} )<br/>**LISTBOX GET HIERARCHY** ( *object* : Variable ; *hierarchical* : Boolean {; *hierarchy* : Pointer array} )<!-- END REF-->
<!--REF #_command_.LISTBOX GET HIERARCHY.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| * | Operator | &#8594; | Si se especifica, objeto es un nombre de objeto (cadena). Si se omite, objeto es una variable |
| object | Text, Variable | &#8594; | Nombre del objeto (si se especifica *) o variables (si * se omite) |
| hierarchical  | Boolean | &#8592; | True = list box jerárquico, False = list box no jerárquico |
| hierarchy  | Pointer array | &#8592; | Array de punteros |

<!-- END REF-->

## Descripción 

<!--REF #_command_.LISTBOX GET HIERARCHY.Summary-->El comando **LISTBOX GET HIERARCHY** permite buscar las propiedades jerárquicas del objeto list box designado por los parámetros *object* y *\** .<!-- END REF-->  
  
Si pasa el parámetro opcional *\**, indica que el parámetro *object* es un nombre de objeto (cadena). Si no pasa este parámetro, indica que el parámetro *object* es una variable. En este caso, se pasa una referencia de variable en lugar de una cadena.   
  
El parámetro booleano *jerarquico* indica si el listbox está o no en modo jerárquico:

* Si el parámetro devuelve True, el list box está en modo jerárquico,
* Si el parámetro devuelve False, el list box se muestra en modo no jerárquico (modo de array estándar).

Si el list box está en modo jerárquico, el comando llena el array *hierarchy* con los punteros a los arrays del list box utilizado para definir la jerarquía.

**Nota**: si el list box está en modo no jerárquico, el comando devuelve, en el primer elemento del array *hierarchy*, un puntero al array de la primera columna del listbox.

## Ver también 

[LISTBOX SET HIERARCHY](listbox-set-hierarchy.md)  

## Propiedades

|  |  |
| --- | --- |
| Número de comando | 1099 |
| Hilo seguro | no |
