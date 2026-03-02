---
id: object-get-focus-rectangle-invisible
title: OBJECT Get focus rectangle invisible
slug: /commands/object-get-focus-rectangle-invisible
displayed_sidebar: docs
---

<details><summary>History</summary>

|Lanzamiento|Cambios|
|---|---|
|21 R2|Soportado con Fluent UI en Windows|

</details>


<!--REF #_command_.OBJECT Get focus rectangle invisible.Syntax-->**OBJECT Get focus rectangle invisible** ( * ; *object* : Text ) : Boolean**<br/>**OBJECT Get focus rectangle invisible** ( *object* : Variable, Field ) : Boolean**<!-- END REF-->
<!--REF #_command_.OBJECT Get focus rectangle invisible.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| * | Operator | &#8594; | Si se especifica, objeto es un nombre de objeto (cadena)Si se omite, objeto es una variable o un campo |
| object | Text, Variable, Field | &#8594; | Nombre de objeto (si se especifica *) o Variable o campo (si se omite *) |
| Resultado | Boolean | &#8592; | True = rectángulo de foco oculto, False = rectángulo de foco visible |

<!-- END REF-->

## Descripción 

<!--REF #_command_.OBJECT Get focus rectangle invisible.Summary-->El comando **OBJECT Get focus rectangle invisible** devuelve el estado de la opción de invisibilidad del rectángulo de foco del objeto o de los objetos designados por los parámetros *object* y *\** para el proceso actual.<!-- END REF--> Esta configuración corresponde a la opción **Ocultar rectángulo de foco** disponible para los objetos editables en la Lista de propiedades en modo Diseño. Este comando devuelve el estado actual de la opción, como se definió en modo Diseño o utilizando el comando [OBJECT SET FOCUS RECTANGLE INVISIBLE](object-set-focus-rectangle-invisible.md).

**Nota:** puede utilizar esta opción únicamente en Mac OS. No tiene efecto en Windows. 

Si pasa el parámetro opcional *\**, indica que el parámetro *object* es un nombre de objeto (una cadena). Si no pasa este parámetro, indica que el parámetro *object* es una variable o un campo. En este caso, se pasa una referencia de variable en lugar de una cadena.

El comando devuelve **True** si el rectángulo de foco está oculto y **False** cuando es visible.

## Ver también 

[OBJECT SET FOCUS RECTANGLE INVISIBLE](object-set-focus-rectangle-invisible.md)  

## Propiedades

|  |  |
| --- | --- |
| Número de comando | 1178 |
| Hilo seguro | no |
