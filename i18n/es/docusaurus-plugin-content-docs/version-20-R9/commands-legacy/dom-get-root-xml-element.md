---
id: dom-get-root-xml-element
title: DOM Get root XML element
slug: /commands/dom-get-root-xml-element
displayed_sidebar: docs
---

<!--REF #_command_.DOM Get root XML element.Syntax-->**DOM Get root XML element** ( *elementRef* ) : Text<!-- END REF-->
<!--REF #_command_.DOM Get root XML element.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| elementRef | Text | &#8594;  | Referencia del elemento XML |
| Resultado | Text | &#8592; | Referencia del elemento raíz o "" en caso de error |

<!-- END REF-->

## Descripción 

<!--REF #_command_.DOM Get root XML element.Summary-->El comando DOM Get root XML element devuelve una referencia al elemento raíz del documento al cual pertenece el elemento XML que se pasa en el parámetro *elementRef*.<!-- END REF--> Esta referencia puede utilizarse con los otros comandos de análisis XML.

## Ver también 

[DOM Get parent XML element](dom-get-parent-xml-element.md)  

## Propiedades

|  |  |
| --- | --- |
| Número de comando | 1053 |
| Hilo seguro | &check; |
| Modifica variables | OK, error |


