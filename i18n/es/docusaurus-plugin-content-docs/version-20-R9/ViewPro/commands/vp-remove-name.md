---
id: vp-remove-name
title: VP REMOVE NAME
---

<!-- REF #_method_.VP REMOVE NAME.Syntax -->

**VP REMOVE NAME** ( *vpAreaName* : Text  ; *name*  : Text { ; *sheet* : Integer } )<!-- END REF -->

<!-- REF #_method_.VP REMOVE NAME.Params -->

| Parámetros | Tipo    |    | Descripción                                                   |                  |
| ---------- | ------- | -- | ------------------------------------------------------------- | ---------------- |
| vpAreaName | Text    | -> | Nombre de objeto formulario área 4D View Pro                  |                  |
| name       | Text    | -> | Nombre del rango nombrado o fórmula nombrada a eliminar       |                  |
| scope      | Integer | -> | Alcance objetivo (por defecto=hoja actual) | <!-- END REF --> |

## Descripción

El comando `VP REMOVE NAME` <!-- REF #_method_.VP REMOVE NAME.Summary -->elimina el rango con nombre o la fórmula con nombre pasada en el parámetro *name* en el *scope* definido<!-- END REF -->.

En *vpAreaName*, pase el nombre del área 4D View Pro. Si pasa un nombre que no existe, se devuelve un error.

Pase el rango con nombre o la fórmula con nombre que desea eliminar en *name*.

Puede definir dónde eliminar el nombre en *scope* utilizando el índice de la hoja (la numeración comienza en 0) o una de las siguientes constantes:

- `vk current sheet`
- `vk workbook`

## Ejemplo

```4d
$range:=VP Cell("ViewProArea";0;0)
VP ADD RANGE NAME("Total1";$range)
 
VP REMOVE NAME("ViewProArea";"Total1")
$formula:=VP Get formula by name("ViewProArea";"Total1")
//$formula=null
```

## Ver también

[VP Name](vp-name.md)