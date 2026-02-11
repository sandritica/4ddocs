---
id: get-relation-properties
title: GET RELATION PROPERTIES
slug: /commands/get-relation-properties
displayed_sidebar: docs
---

<!--REF #_command_.GET RELATION PROPERTIES.Syntax-->**GET RELATION PROPERTIES** ( *fieldPtr* : Pointer ; *oneTable* : Integer ; *oneField* : Integer {; *choiceField* : Integer {; *autoOne* : Boolean {; *autoMany* : Boolean}}} )<br/>**GET RELATION PROPERTIES** ( *tableNum* : Integer ; *fieldNum* : Integer ; *oneTable* : Integer ; *oneField* : Integer {; *choiceField* : Integer {; *autoOne* : Boolean {; *autoMany* : Boolean}}} )<!-- END REF-->
<!--REF #_command_.GET RELATION PROPERTIES.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| fieldPtr | Pointer | &#8594;  | Puntero de campo |
| tableNum | Integer | &#8594;  | Número de tabla |
| fieldNum | Integer | &#8594;  | Número de campo si se pasa un número de tabla  como primer parámetro |
| oneTable | Integer | &#8592; | Número de la tabla Uno ó 0 si no se define  ninguna relación desde el campo |
| oneField | Integer | &#8592; | Número de campo Uno ó 0 si no se define  ninguna relación desde el campo |
| choiceField | Integer | &#8592; | Número de campo discriminante o 0 si ningún campo discriminante |
| autoOne | Boolean | &#8592; |  True = Relación uno automática,  False = Relación uno manual |
| autoMany | Boolean | &#8592; |  True = Relación uno automática,  False = Relación uno manual |

<!-- END REF-->

## Descripción 

<!--REF #_command_.GET RELATION PROPERTIES.Summary-->El comando GET RELATION PROPERTIES devuelve las propiedades de la relación (si la hay) que comienza del campo fuente definido por *numTabla* y *numCamp* o por *ptrCamp*.<!-- END REF--> 

Puede pasar:

* Números de tabla y de campo en *tableNum* y *fieldNum*,
* O un puntero al campo en *fieldPtr*.

Una se haya ejecutado el comando:

* Los parámetros *oneTable* y *oneField* contienen respectivamente el número de la tabla y del campo hacia los cuales apunta la relación (del campo fuente). Si ninguna relación comienza en el campo, este parámetro devuelve 0.
* El parámetro *discriminante* contiene el número del campo discriminante (de la tabla objetivo) definido dentro de esta relación. Si no se ha definido un campo discriminante en esta relación, o si ninguna relación parte del campo fuente, este parámetro devuelve 0.
* Los parámetro *autoOne* y *autoMuchos* devuelven [True](true.md "True") si, respectivamente, las opciones “Relación uno a muchos automática” y “Relación muchos a uno automática” se han seleccionado para esta relación; de lo contrario, devuelven [False](false.md "False").

**Nota:** los parámetros *autoUno* y *autoMany* también devolverán [True](true.md "True") si ninguna relación parte del campo fuente (en este caso devuelven valores no significativos.). El valor de los parámetros *oneTable* y *oneField* permiten asegurarse de que una relación existe. 

## Ver también 

[GET FIELD ENTRY PROPERTIES](get-field-entry-properties.md)  
[GET FIELD PROPERTIES](get-field-properties.md)  
[GET TABLE PROPERTIES](get-table-properties.md)  
[SET AUTOMATIC RELATIONS](set-automatic-relations.md)  
[SET FIELD RELATION](set-field-relation.md)  

## Propiedades

|  |  |
| --- | --- |
| Número de comando | 686 |
| Hilo seguro | yes |
