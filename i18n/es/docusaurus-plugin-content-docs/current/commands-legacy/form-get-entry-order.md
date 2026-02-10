---
id: form-get-entry-order
title: FORM GET ENTRY ORDER
slug: /commands/form-get-entry-order
displayed_sidebar: docs
---

<!--REF #_command_.FORM GET ENTRY ORDER.Syntax-->**FORM GET ENTRY ORDER** ( *objectNames* : Text array {; *pageNumber* : Integer } )<br/>**FORM GET ENTRY ORDER** ( *objectNames* : Text array {; *} )<!-- END REF-->
<!--REF #_command_.FORM GET ENTRY ORDER.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| objectNames | Text array | &#8592; | Nombres de objetos ordenados por orden de entrada |
| pageNumber | Integer | &#8594;  | Número de la página para la que se obtiene el orden de entrada definido (página actual si se omite) |
| * | Operator | &#8594;  | Obtener el orden de entrada real de la página actual |

<!-- END REF-->

## Descripción

<!--REF #_command_.FORM GET ENTRY ORDER.Summary-->El comando **FORM GET ENTRY ORDER** devuelve en *objectNames* los nombres ordenados de los objetos que definen el orden de entrada del formulario.<!-- END REF--> 

* Si no pasa el parámetro *\**, **FORM GET ENTRY ORDER** devuelve el orden de entrada como se declaró anteriormente con el comando [FORM SET ENTRY ORDER](form-set-entry-order.md). Puede omitir o pasar el parámetro *pageNumber*:  
   * Si omite el parámetro *pageNumber*, el array *objectNames* devuelve el orden de entrada para la página actual,  
   * Si pasa el parámetro *pageNumber*, el array *objectNames* devuelve el orden de entrada para la página *numPag*.  
En ambos casos, si el comando [FORM SET ENTRY ORDER](form-set-entry-order.md) no fue llamado previamente para el formulario actual, el array *nomObjetos* se devuelve vacío.
* Si pasa el parámetro *\**, **FORM GET ENTRY ORDER** devuelve el orden de entrada actual de la página actual, es decir, el array *nomObjetos* sólo contiene nombres de objeto **válidos** ( (para más información sobre objetos válidos, consulte la descripción del comando [FORM SET ENTRY ORDER](form-set-entry-order.md)). El orden de entrada de formulario real puede ser:  
   * El orden de entrada de formulario predeterminado, basado en la superposición de objetos,  
   * O el orden de entrada del editor de formularios (ver *Modificar el orden de entrada de los datos*), si se ha utilizado,  
   * O el orden de entrada definido por una llamada al comando [FORM SET ENTRY ORDER](form-set-entry-order.md) en el proceso actual, si se ha utilizado.  
El orden de entrada real siempre incluye objetos de la página 0 y de los formularios heredados.

**Nota:** el orden de entrada dentro de un subformulario no se devuelve cuando se aplica este comando al formulario padre.

## Ejemplo 

Puede excluir ciertos objetos del orden de entrada:

```4d
 ARRAY TEXT($arrTabOrderObject;0)
 var $vElem : Integer
 
 FORM GET ENTRY ORDER($arrTabOrderObject;*) //obtener el orden de entrada actual
 Repeat
    $vElem:=Find in array($arrTabOrderObject;"vTax@")
    If($vElem>0) //excluye objetos cuyo nombre comienza por "vTax" del orden de entrada de datos
       DELETE FROM ARRAY($arrTabOrderObject;$vElem)
    End if
 Until($vElem<0)
 FORM SET ENTRY ORDER($arrTabOrderObject) //aplica el nuevo orden de entrada
```

## Ver también 

[FORM SET ENTRY ORDER](form-set-entry-order.md)  

## Propiedades

|  |  |
| --- | --- |
| Número de comando | 1469 |
| Hilo seguro | no |
