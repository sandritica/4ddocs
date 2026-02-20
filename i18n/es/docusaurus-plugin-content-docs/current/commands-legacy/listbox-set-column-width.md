---
id: listbox-set-column-width
title: LISTBOX SET COLUMN WIDTH
slug: /commands/listbox-set-column-width
displayed_sidebar: docs
---

<!--REF #_command_.LISTBOX SET COLUMN WIDTH.Syntax-->**LISTBOX SET COLUMN WIDTH** ( * ; *object* : Text ; *width* : Integer {; *minWidth* : Integer {; *maxWidth* : Integer}} )<br/>**LISTBOX SET COLUMN WIDTH** ( *object* : Variable ; *width* : Integer {; *minWidth* : Integer {; *maxWidth* : Integer}} )<!-- END REF-->
<!--REF #_command_.LISTBOX SET COLUMN WIDTH.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| * | Operator | &#8594; | Si se especifica, objeto es un nombre de objeto (cadena) Si se omite, objeto es una variable |
| object | Text, Variable | &#8594; | Nombre de objeto (si se especifica *) o Variable (si se omite *) |
| width | Integer | &#8594; | Ancho de la columna (en píxeles) |
| minWidth | Integer | &#8594; | Ancho mínimo de columna (en píxeles) |
| maxWidth  | Integer | &#8594; | Ancho máximo de columna (en píxeles) |

<!-- END REF-->

## Descripción 

<!--REF #_command_.LISTBOX SET COLUMN WIDTH.Summary-->El comando **LISTBOX SET COLUMN WIDTH** le permite modificar por programación el ancho de una o todas las columnas del objeto (list box, columna o título) designado utilizando los parámetros *object* y *\**.<!-- END REF-->

Si pasa el parámetro opcional \*, indica que el parámetro *object* es un nombre de objeto (cadena). Si omite este parámetro, indica que el parámetro *object* es una variable. En ese caso, no pasa una cadena, sino una referencia de variable. Para mayor información sobre nombres de objetos, consulte la sección . 

Pase en el parámetro *width* el nuevo ancho (en píxeles) del objeto. 

• Si *object* designa el objeto list box, todas las columnas del list box son redimensionadas.  

• Si *object* designa una columna o un título de columna, sólo la columna designada es redimensionada. 

Los parámetros opcionales *minWidth* y *maxWidth* permiten definir los límites para el redimensionamiento manual de la columna. Puede pasar en anchoMin y anchoMax respectivamente los valores del ancho mínimo y máximo, expresado en píxeles. Si quiere que el usuario no pueda redimensionar la columna, debe pasar el mismo valor en *width*, *minWidth* y *maxWidth*. 

## Ver también 

[LISTBOX Get column width](listbox-get-column-width.md)  

## Propiedades

|  |  |
| --- | --- |
| Número de comando | 833 |
| Hilo seguro | no |

