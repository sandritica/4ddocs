---
id: object-get-font
title: OBJECT Get font
slug: /commands/object-get-font
displayed_sidebar: docs
---

<!--REF #_command_.OBJECT Get font.Syntax-->**OBJECT Get font** ( * ; *object* : Text ) : Text<br/>**OBJECT Get font** ( *object* : Variable, Field ) : Text<!-- END REF-->
<!--REF #_command_.OBJECT Get font.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| * | Operator | &#8594; | Si se especifica, objeto es un nombre de objeto (cadena). Si se omite, objeto es una variable o un campo |
| object | Text, Variable, Field | &#8594; | Nombre de objeto (si se especifica *), o Campo o variable (si se omite *) |
| Resultado | Text | &#8592; | Nombre de la fuente |

<!-- END REF-->

## Descripción 

<!--REF #_command_.OBJECT Get font.Summary-->El comando **OBJECT Get font** devuelve el nombre de la fuente utilizada por el objeto de formulario designado por *object*.<!-- END REF-->

Si pasa el parámetro opcional *\**, indica que el parámetro objeto es un nombre de objeto (cadena). Si no pasa este parámetro, indica que el parámetro *object* es un campo o una variable. En este caso, se pasa una referencia de campo o variable (campo o variable objeto únicamente) en lugar de una cadena. 

## Ver también 

[OBJECT SET FONT](object-set-font.md)  

## Propiedades

|  |  |
| --- | --- |
| Número de comando | 1069 |
| Hilo seguro | no |
