---
id: object-get-filter
title: OBJECT Get filter
slug: /commands/object-get-filter
displayed_sidebar: docs
---

<!--REF #_command_.OBJECT Get filter.Syntax-->**OBJECT Get filter** ( * ; *object* : Text ) : Text<br/>**OBJECT Get filter** ( *object* : Variable, Field ) : Text<!-- END REF-->
<!--REF #_command_.OBJECT Get filter.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| * | Operator | &#8594; | Si se especifica, objeto es un nombre de objeto (cadena). Si se omite, objeto es una variable o un campo |
| object | Text, Variable, Field | &#8594; | Nombre del objeto (si se especifica *) o variable o campo (si se omite) |
| Resultado | Text | &#8592; | Nombre del filtro |

<!-- END REF-->

## Descripción 

<!--REF #_command_.OBJECT Get filter.Summary-->El comando **OBJECT Get filter** devuelve el nombre de todo filtro asociado con el objeto o grupo de objetos designado por *object*.<!-- END REF-->  
  
Si pasa el parámetro opcional *\**, indica que el parámetro objeto es un nombre de objeto (cadena). Si no pasa este parámetro, indica que el parámetro *object* es un campo o una variable. En este caso, se pasa una referencia de campo o variable (campo o variable objeto únicamente) en lugar de una cadena.

## Ver también 

[OBJECT SET FILTER](object-set-filter.md)  

## Propiedades

|  |  |
| --- | --- |
| Número de comando | 1073 |
| Hilo seguro | no |
