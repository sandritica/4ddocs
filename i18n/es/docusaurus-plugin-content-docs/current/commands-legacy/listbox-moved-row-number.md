---
id: listbox-moved-row-number
title: LISTBOX MOVED ROW NUMBER
slug: /commands/listbox-moved-row-number
displayed_sidebar: docs
---

<!--REF #_command_.LISTBOX MOVED ROW NUMBER.Syntax-->**LISTBOX MOVED ROW NUMBER** ( * ; *object* : Text ; *oldPosition* : Integer ; *newPosition* : Integer )<br/>**LISTBOX MOVED ROW NUMBER** ( *object* : Variable ; *oldPosition* : Integer ; *newPosition* : Integer )<!-- END REF-->
<!--REF #_command_.LISTBOX MOVED ROW NUMBER.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| * | Operator | &#8594; | Si se especifica, objeto es un nombre de objeto (cadena) Si se omite, objeto es una variable |
| object | Text, Variable | &#8594; | Nombre de objeto formulario (si se especifica *) o Variable (si se omite *) |
| oldPosition | Integer | &#8592; | Posición anterior de la fila movida |
| newPosition | Integer | &#8592; | Nueva posición de la fila movida |

<!-- END REF-->

## Descripción 

<!--REF #_command_.LISTBOX MOVED ROW NUMBER.Summary-->El comando **LISTBOX MOVED ROW NUMBER** devuelve dos números en *oldPosition* y *newPosition* indicando respectivamente la posición anterior y la nueva posición de la fila movida en el list box, especificadas por los parámetros *object* y *\**.<!-- END REF-->

**Nota:** sólo puede mover las líneas en los list box de tipo array.

Si pasa el parámetro opcional *\**, indica que el parámetro *object* es un nombre de objeto (cadena). Si omite este parámetro, indica que el parámetro *object* es una variable. En ese caso, no pasa una cadena, sino una referencia de variable. Para mayor información sobre nombres de objetos, consulte la sección *Propiedades de los objetos*. 

Este comando debe utilizarse con el evento de formulario On row moved (ver el comando [Form event code](../commands/form-event-code.md)). 

**Nota:** este comando no tiene en cuenta el estado oculto/mostrado de las líneas del list box. 

## Ver también 

[Form event code](../commands/form-event-code.md)  
[LISTBOX MOVED COLUMN NUMBER](listbox-moved-column-number.md)  

## Propiedades

|  |  |
| --- | --- |
| Número de comando | 837 |
| Hilo seguro | no |
