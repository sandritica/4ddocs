---
id: is-field-number-valid
title: Is field number valid
slug: /commands/is-field-number-valid
displayed_sidebar: docs
---

<!--REF #_command_.Is field number valid.Syntax-->**Is field number valid** ( *tablePtr* : Pointer ; *fieldNum* : Integer ) : Boolean<br/>**Is field number valid** ( *tableNum* : Integer ; *fieldNum* : Integer ) : Boolean<!-- END REF-->
<!--REF #_command_.Is field number valid.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| tableNum | Integer | &#8594;  | Número de tabla |
| tablePtr | Pointer | &#8594;  | Puntero a una tabla |
| fieldNum | Integer | &#8594;  | Número de campo |
| Resultado | Boolean | &#8592; | True = el campo existe en la tabla False = el campo no existe en la tabla |
</div>
<!-- END REF-->

## Descripción 

<!--REF #_command_.Is field number valid.Summary-->El comando **Is field number** valid devuelve True si el campo cuyo número se pasa en el parámetro *fieldNum* existe en la tabla cuyo número o puntero se pasa en el parámetro *tableNum* o *tablePtr*.<!-- END REF--> Si el campo no existe, el comando devuelve False. Recuerde que el comando devuelve False si la tabla que contiene el campo se encuentra en la Papelera del Explorador. 

Este comando permite detectar las eventuales eliminaciones de campos, que crean rupturas en la secuencia de números de los campos.

## Ver también 

[Last table number](last-table-number.md)  
[Is table number valid](is-table-number-valid.md)  

## Propiedades

|  |  |
| --- | --- |
| Número de comando | 1000 |
| Hilo seguro | yes |
