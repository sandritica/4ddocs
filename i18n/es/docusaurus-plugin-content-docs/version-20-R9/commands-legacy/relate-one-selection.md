---
id: relate-one-selection
title: RELATE ONE SELECTION
slug: /commands/relate-one-selection
displayed_sidebar: docs
---

<!--REF #_command_.RELATE ONE SELECTION.Syntax-->**RELATE ONE SELECTION** ( *tablaN* ; *tabla1* )<!-- END REF-->
<!--REF #_command_.RELATE ONE SELECTION.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| tablaN | Table | &#8594;  | Nombre de la tabla Muchos (donde inicia la relación) |
| tabla1 | Table | &#8594;  | Nombre de la tabla Uno (donde termina la relación) |

<!-- END REF-->

## Descripción 

<!--REF #_command_.RELATE ONE SELECTION.Summary-->El comando **RELATE ONE SELECTION** crea una nueva selección de registros en *tabla1* a partir de la selección de registros de la *tablaN* relacionada y carga el primer registro de la nueva selección como el registro actual.<!-- END REF--> 

Este comando sólo puede utilizarse si hay una relación de  la *tablaN* a la *tabla1*. **RELATE ONE SELECTION** puede funcionar a través de varios niveles de relaciones. Puede haber varias tablas relacionadas entre la *tablaN* y la *tabla1*. 

Las relaciones pueden ser manuales o automáticas. Cuando existen relaciones automáticas, **RELATE ONE SELECTION** siempre las utiliza en primer lugar. Cuando hay varios caminos posibles desde la tabla de inicio a la tabla de destino, **RELATE ONE SELECTION** toma el más corto, utilizando las relaciones automáticas (si las hay). Si existen rutas del mismo tamaño y desea controlar la ruta utilizada, o si desea «forzar» el uso de relaciones manuales, deberá utilizar el comando [`SET FIELD RELATION`](set-field-relation.md).

## Ejemplo 

El siguiente ejemplo busca los clientes cuyas facturas se vencen hoy. 

Esta es una manera de crear una selección en la tabla *\[Clientes\]*, a partir de una selección de registros de la tabla *\[Facturas\]*:

```4d
 CREATE EMPTY SET([Clientes];"Fecha de vencimiento del pago")
 QUERY([Facturas];[Facturas]FechaVence=Current date)
 While(Not(End selection([Facturas])))
    RELATE ONE([Facturas]CustID)
    ADD TO SET([Clientes];"Fecha de vencimiento del pago")
    NEXT RECORD([Invoices])
 End while
```

La siguiente técnica utiliza **RELATE ONE SELECTION** para obtener el mismo resultado:

```4d
 QUERY([Facturas];[Facturas]FechaVence=Current date)
 RELATE ONE SELECTION([Facturas];[Clientes])
```

**Note:** a partir de la versión 11, este código puede escribirse de esta manera sin perdida de rendimiento:  

```4d
 QUERY([Clientes];[Facturas]FechaVence=Current date)
```

## Ver también 

*Conjuntos*  
[QUERY](query.md)  
[RELATE MANY SELECTION](relate-many-selection.md)  
[RELATE ONE](relate-one.md)  

## Propiedades

|  |  |
| --- | --- |
| Número de comando | 349 |
| Hilo seguro | &check; |
| Modifica el registro actual ||
| Modifica la selección actual ||


