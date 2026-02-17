---
id: listbox-moved-column-number
title: LISTBOX MOVED COLUMN NUMBER
slug: /commands/listbox-moved-column-number
displayed_sidebar: docs
---

<!--REF #_command_.LISTBOX MOVED COLUMN NUMBER.Syntax-->**LISTBOX MOVED COLUMN NUMBER** ( * ; *object* : Text ; *oldPosition* : Integer ; *newPosition* : Integer )<br/>**LISTBOX MOVED COLUMN NUMBER** ( *object* : Variable ; *oldPosition* : Integer ; *newPosition* : Integer )<!-- END REF-->
<!--REF #_command_.LISTBOX MOVED COLUMN NUMBER.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| * | Operator | &#8594; | Si se especifica, objeto es un nombre de objeto (cadena) Si se omite, objeto es una variable |
| object | Text, Variable | &#8594; | Nombre de objeto (si se especifica *) o Variable (si se omite *) |
| oldPosition | Integer | &#8592; | Posición anterior de la columna movida |
| newPosition | Integer | &#8592; | Nueva posición de la columna movida |

<!-- END REF-->

## Descripción 

<!--REF #_command_.LISTBOX MOVED COLUMN NUMBER.Summary-->El comando **LISTBOX MOVED COLUMN NUMBER** devuelve dos números en *oldPosition* y *newPosition* indicando respectivamente la posición anterior y la nueva posición de la columna movida en el list box designado por los parámetros *object* y *\**.<!-- END REF-->

Si pasa el parámetro opcional \*, indica que el parámetro *object* es un nombre de objeto (cadena). Si omite este parámetro, indica que el parámetro *object* es una variable. En ese caso, no pasa una cadena, sino una referencia de variable. Para mayor información sobre nombres de objetos, consulte la sección . 

Este comando debe utilizarse con el evento de formulario On column moved (ver el comando [Form event](../commands/form-event.md "Form event")). 

**Nota:** este comando tiene en cuenta las columnas invisibles.

## Ver también 

[Form event code](../commands/form-event-code.md)  
[LISTBOX MOVED ROW NUMBER](listbox-moved-row-number.md)  

## Propiedades

|  |  |
| --- | --- |
| Número de comando | 844 |
| Hilo seguro | no |
