---
id: highlight-text
title: HIGHLIGHT TEXT
slug: /commands/highlight-text
displayed_sidebar: docs
---

<!--REF #_command_.HIGHLIGHT TEXT.Syntax-->**HIGHLIGHT TEXT** ( {* ;} *object* : Variable, Field, any ; *startSel* : Integer ; *endSel* : Integer )<!-- END REF-->
<!--REF #_command_.HIGHLIGHT TEXT.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| * | Operator | &#8594; | Si se especifica, objeto es un nombre de objeto (cadena)Si se omite, objeto es un campo o una variable |
| object | Field, Variable, any | &#8594; | Nombre del objeto (si se especifica *) o Campo o variable (si se omite *) |
| startSel | Integer | &#8594; | Nueva posición de inicio de selección de texto |
| endSel | Integer | &#8594; | Nueva posición de fin de selección de texto |

<!-- END REF-->

<details><summary>History</summary>
|Lanzamiento|Cambios|
|---|---|
|21|Soporte en subformularios|

</details>

## Descripción 

<!--REF #_command_.HIGHLIGHT TEXT.Summary-->El comando `HIGHLIGHT TEXT` selecciona una parte de texto en *object*.<!-- END REF-->  
  
Si pasa el parámetro opcional *\**, indica que el parámetro *object* es un nombre de un objeto (una cadena) Si no pasa el parámetro \*, indica que el parámetro *object* es un campo o una variable. En este caso, pase la referencia del campo o de la variable (campos o variables de formulario únicamente) en lugar de una cadena.  

Si *object* no es el objeto que está siendo modificado, esta área recupera el foco.

El comando `HIGHLIGHT TEXT` puede utilizarse en el contexto de un subformulario. Cuando se llama desde un subformulario, primero busca el objeto en el subformulario y, si no encuentra nada allí, amplía la búsqueda a los objetos del formulario principal. 
  
El parámetro *startSel* representa la posición del primer carácter a seleccionar, y el parámetro *endSel* representa la posición del último carácter a seleccionar más uno. Si *startSel* y *endSel* son iguales, el punto de inserción está ubicado antes del carácter especificado por *startSel*, y ningún carácter está seleccionado.

Si *endSel* es superior al número de caracteres en *object*, todos los caracteres entre *startSel* y el final del texto son seleccionados.

## Ejemplo 1 

El siguiente ejemplo selecciona todos los caracteres en el campo editable *\[Productos\]Notas*: 

```4d
 HIGHLIGHT TEXT([Productos]Notas;1;Length([Productos]Notas)+1)
```

## Ejemplo 2 

El siguiente ejemplo mueve el punto de inserción al principio del campo editable *\[Productos\]Notas*: 

```4d
 HIGHLIGHT TEXT([Productos]Notas;1;1)
```

## Ejemplo 3 

El siguiente ejemplo mueve el punto de inserción al final del campo editable *\[Productos\]Notas*: 

```4d
 $vLen:=Length([Productos]Notas)+1HIGHLIGHT TEXT([Productos]Notas;$vLen;$vLen)
```


## Ejemplo 4 

Ver el ejemplo del comando [FILTER KEYSTROKE](filter-keystroke.md "FILTER KEYSTROKE").

## Ver también 

[GET HIGHLIGHT](get-highlight.md)  

## Propiedades

|  |  |
| --- | --- |
| Número de comando | 210 |
| Hilo seguro | no |
