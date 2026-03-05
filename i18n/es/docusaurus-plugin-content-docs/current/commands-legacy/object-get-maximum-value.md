---
id: object-get-maximum-value
title: OBJECT GET MAXIMUM VALUE
slug: /commands/object-get-maximum-value
displayed_sidebar: docs
---

<!--REF #_command_.OBJECT GET MAXIMUM VALUE.Syntax-->**OBJECT GET MAXIMUM VALUE** ( * ; *object* : Text ; *maxValue* : Date, Time, Real )<br/>**OBJECT GET MAXIMUM VALUE** ( *object* : Variable, Field ; *maxValue* : Date, Time, Real )<!-- END REF-->
<!--REF #_command_.OBJECT GET MAXIMUM VALUE.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| * | Operator | &#8594; | Si se especifica, objeto es un nombre de objeto (cadena) Si se omite, objeto es un campo o una variable |
| object | Text, Variable, Field | &#8594; | Nombre de objeto (si se especifica *) o  Campo o variable (si se omite *) |
| maxValue | Date, Time, Real | &#8592; | Valor máximo actual para objeto |

<!-- END REF-->

## Descripción 

<!--REF #_command_.OBJECT GET MAXIMUM VALUE.Summary-->El comando **OBJECT GET MAXIMUM VALUE** devuelve, en la variable valorMax, el valor máximo actual del objeto o de los objetos designados por los parámetros *object* y *\** .<!-- END REF--> 

Puede establecer la propiedad "Valor máximo" con la lista de propiedades en modo Diseño o utilizando el comando [OBJECT SET MAXIMUM VALUE](object-set-maximum-value.md).

Si pasa el parámetro opcional *\** indica que el parámetro *object* es un nombre de objeto (cadena). Si no se pasa este parámetro, indica que el parámetro *object* es un campo o una variable. En este caso, se pasa una referencia de campo o variable en lugar de una cadena (campo o variable objeto únicamente).

## Ver también 

[OBJECT GET MINIMUM VALUE](object-get-minimum-value.md)  
[OBJECT SET MAXIMUM VALUE](object-set-maximum-value.md)  

## Propiedades

|  |  |
| --- | --- |
| Número de comando | 1245 |
| Hilo seguro | no |
