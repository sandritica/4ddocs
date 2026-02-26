---
id: object-get-auto-spellcheck
title: OBJECT Get auto spellcheck
slug: /commands/object-get-auto-spellcheck
displayed_sidebar: docs
---

<!--REF #_command_.OBJECT Get auto spellcheck.Syntax-->**OBJECT Get auto spellcheck** ( * ; *object* : Text ) : Boolean<br/>**OBJECT Get auto spellcheck** ( *object* : Variable, Field ) : Boolean<!-- END REF-->
<!--REF #_command_.OBJECT Get auto spellcheck.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| * | Operator | &#8594; | Si se especifica, objeto es un nombre de objeto (cadena)Si se omite, objeto es una variable o campo |
| object | Text, Variable, Field | &#8594; | Nombre del objeto (si se especifica *) o Variable o campo (si se omite *) |
| Resultado | Boolean | &#8592; | True = corrección automática, False = no corrección automática |

<!-- END REF-->

## Descripción 

<!--REF #_command_.OBJECT Get auto spellcheck.Summary-->El comando **OBJECT Get auto spellcheck** devuelve el estado de la opción Corrección ortográfica automática del o de los objeto(s) designado(s) por los parámetros *object* y *\** para el proceso actual .<!-- END REF--> 

Este comando admite objetos de tipo:

- [input](../FormObjects/input_overview.md) de tipo texto solamente,
- 4D Write Pro area](../FormObjects/writeProArea_overview.md).

Si pasa el parámetro opcional *\**, indica que el parámetro *object* es un nombre de objeto (una cadena). Si no pasa este parámetro, indica que *object* es una variable o un campo. En este caso, pase una referencia en lugar de un nombre.  
  
El comando devuelve **True** cuando la corrección ortográfica automática está activada para el *object* y **False** si no.

## Ver también 

[OBJECT SET AUTO SPELLCHECK](object-set-auto-spellcheck.md)  

## Propiedades

|  |  |
| --- | --- |
| Número de comando | 1174 |
| Hilo seguro | no |
