---
id: get-list-item-properties
title: GET LIST ITEM PROPERTIES
slug: /commands/get-list-item-properties
displayed_sidebar: docs
---

<!--REF #_command_.GET LIST ITEM PROPERTIES.Syntax-->**GET LIST ITEM PROPERTIES** ( {* ;} *list* : Integer, Text ; *itemRef* : Integer, Operator ; *enterable* : Boolean {; *styles* : Integer {; *icon* : Text, Integer {; *color* : Integer}}} )<!-- END REF-->
<!--REF #_command_.GET LIST ITEM PROPERTIES.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| * | Operador | &#8594; | Si se especifica, lista es un nombre de objeto (cadena) Si se omite, lista es una referencia de lista |
| list | Integer, Text | &#8594; | Número de referencia de lista (si se omite *) o Nombre del objeto de tipo lista (si se pasa *) |
| itemRef | Operator, Integer | &#8594; | Número de referencia del elemento, o 0 para el último elemento añadido a la lista, o * para el elemento actual de la lista |
| enterable  | Boolean | &#8592; | TRUE = Editable, FALSE = No editable |
| styles  | Integer | &#8592; | Estilo de fuente del elemento |
| icon | Text, Integer | &#8592; | Número o nombre de imagen |
| color | Integer | &#8592; | Valor de color RGB |
</div>
<!-- END REF-->

## Descripción 

<!--REF #_command_.GET LIST ITEM PROPERTIES.Summary-->El comando **GET LIST ITEM PROPERTIES** devuelve las propiedades del elemento designado por el parámetro *itemRef* de la lista cuyo número de referencia o nombre de objeto se pasa en *list*.<!-- END REF-->

Si pasa el primer parámetro opcional \*, indica que el parámetro *lista* es un nombre de objeto (cadena) correspondiente a una representación de lista en el formulario. Si no pasa este parámetro, indica que el parámetro *list* es una referencia de lista jerárquica (RefLista). Si utiliza sólo una representación de lista, puede utilizar indiferentemente una u otra sintaxis. Por el contrario, si utiliza varias representaciones de una misma lista y trabaja con el elemento actual (el segundo \* se pasa), la sintaxis basada en el nombre del objeto es necesaria ya que cada representación puede tener su propio elemento actual.

**Nota**: si utiliza el carácter @ en el nombre de la lista y el formulario contiene varias listas que responden a este nombre, el comando **GET LIST ITEM PROPERTIES** se aplicará al primer objeto cuyo nombre corresponde.

En *itemRef*, puede pasar un número de referencia, o el valor 0 con el fin de designar el último elemento añadido a la lista, o \* para designar el elemento actual de la lista. Si se seleccionan varios elementos, el elemento actual es el último en ser seleccionado.

Si pasa \* y ningún elemento es seleccionado o si el número de referencia del elemento no corresponde a ningún elemento de la lista, el comando deja los parámetros sin cambios.

Si trabaja con números de referencia de los elementos, asegúrese de utilizar, construya una lista en la cual los elemento tengan números de referencia únicos, de lo contrario no podrá diferenciar los elementos. Para mayor información, consulte la descripción del comando [APPEND TO LIST](append-to-list.md).

Después de la llamada:

* *enterable* devuelve TRUE si el elemento es editable.
* *styles* devuelve el estilo de fuente del elemento.
* *icon* devuelve la imagen asignada al elemento, si lo hay.  
   * Si el ícono se ha especificado utilizando un archivo de imagen, el comando devuelve en el *icon* la ruta de acceso utilizando **path:<filesystem path>**.  
   * Si el icono se ha especificado utilizando una imagen de la librería (solo bases de datos binarias), el comando devuelve el número o el nombre de la imagen, según el tipo de variable que se pase en este parámetro. El siguiente patrón se utiliza para un nombre: **pictlib:<name>**. Si no atribuye un tipo específico a la variable *icono*, de forma predeterminada, se devuelve el nombre de la imagen (texto). Si no hay ningún icono asociado con el elemento, el comando devuelve un valor en blanco.  
         
   **Nota:** puede recuperar, en una variable imagen, el icono asociado con un elemento utilizando el comando [GET LIST ITEM ICON](get-list-item-icon.md)*.*
* *color* devuelve el color del texto del elemento especificado.

Para mayor información sobre estas propiedades, consulte la descripción del comando [SET LIST ITEM PROPERTIES](set-list-item-properties.md).

## Ver también 

[GET LIST ITEM](get-list-item.md)  
[GET LIST ITEM ICON](get-list-item-icon.md)  
[SET LIST ITEM](set-list-item.md)  
[SET LIST ITEM PROPERTIES](set-list-item-properties.md)  

## Propiedades

|  |  |
| --- | --- |
| Número de comando | 631 |
| Hilo seguro | no |
