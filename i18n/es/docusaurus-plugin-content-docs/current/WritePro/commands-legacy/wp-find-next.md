---
id: wp-find-next
title: WP Find next
slug: /WritePro/commands/wp-find-next
displayed_sidebar: docs
---

<!--REF #_command_.WP Find next.Syntax-->**WP Find next** ( *objTarget* ; *buscarDespues* ; *buscarValor* ; *condicionBusq* {; *valorReempl*} ) -> Resultado<!-- END REF-->
<!--REF #_command_.WP Find next.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| objTarget | Object | &#8594;  | Rango o elemento o documento 4D Write Pro |
| buscarDespues | Object | &#8594;  | Rango después del cual comenzar a buscar |
| buscarValor | Text | &#8594;  | Valor a buscar |
| condicionBusq | Integer | &#8594;  | Regla(s) de búsqueda |
| valorReempl | Text | &#8594;  | Cadena a reemplazar |
| Resultado | Object | &#8592; | Rango del valor encontrado/reemplazado |

<!-- END REF-->

## Descripción 

<!--REF #_command_.WP Find next.Summary-->El comando **WP Find next** busca en *objTarget*, después del rango *buscarDespues*, el *buscarValor* basado en la *condicionBusq*.<!-- END REF--> Se puede utilizar un parámetro opcional para reemplazar los resultados encontrados.

**Nota**: **WP Find next** no busca ni reemplaza texto en fórmulas. Utilice el comando [WP Get formulas](wp-get-formulas.md) en este caso. 

En el parámetro *objTarget*, pase un objeto que contenga:

* un rango, o
* un elemento (tabla / fila / celda(s) / párrafo / cuerpo / encabezado / pie de página / sección / subsección / caja de texto), o
* un documento de 4D Write Pro.

Pase un rango en el parámetro *buscarDespues*. La búsqueda comenzará inmediatamente después del rango definido o pase NULL para encontrar el primer valor de *objTarget*.

**Nota**: si *objTarget* es el documento 4D Write Pro y *buscarDespues* está en una caja de texto, el comando busca primero en la caja de texto padre y luego en la(las) caja(s) de texto siguiente(s) en orden ascendente -- según el orden descrito a continuación. 

El parámetro *buscarValor* permite pasar el texto a buscar dentro del *objTarget*. 

Puede especificar cómo se realiza la búsqueda con el parámetro *condicionBusq*. Puede utilizar una (o una combinación) de las siguientes constantes:

| Constante                | Comentario                                                                                                                                                                                                                                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| wk case insensitive      | Las cadenas se comparan sin tener en cuenta las diferencias de mayúsculas y minúsculas. Tenga en cuenta que se tienen en cuenta los signos diacríticos. Por ejemplo, "A" se considera igual que "a", pero "a" no se considera igual que "à".                                                                  |
| wk diacritic insensitive | Las cadenas se comparan, pero la marca diacrítica (por ejemplo, el acento o el símbolo) de las letras se ignora. Por ejemplo, "a" se considera igual que "à".                                                                                                                                                 |
| wk find reverse          | La búsqueda se realiza en orden inverso.                                                                                                                                                                                                                                                                      |
| wk kana insensitive      | Para el idioma japonés. Las cadenas se comparan según el significado (no el estilo de escritura). Por ejemplo, "あ" se considera igual que "ア". <br/><br/> Cuando se define esta opción, wk width insensitive  está implícito (se considera definido), sin embargo, lo contrario no es cierto. |
| wk keep character style  | Al reemplazar el texto, se mantiene el estilo de caracteres existente (si es posible).                                                                                                                                                                                                                        |
| wk override protected    | La protección de lectura/escritura se ignora y las cadenas en áreas protegidas pueden ser reemplazadas.                                                                                                                                                                                                       |
| wk use keyboard language | Para la comparación de cadenas, utilice la propiedad de idioma del teclado del objeto formulario que se está editando en lugar del idioma de los datos actuales (por defecto). **Nota**: se ignora si el documento está fuera de la pantalla.                                                                 |
| wk whole word            | Sólo se consideran las cadenas que son palabras completas. No se tienen en cuenta las cadenas que coinciden con otras cadenas. Por ejemplo, "where" no se considera cuando se encuentra dentro de "somewhere".                                                                                                |
| wk width insensitive     | Para el idioma japonés. Las cadenas se comparan por la anchura de los caracteres. Por ejemplo, "ｱ" se considera igual que "ア".                                                                                                                                                                                |

**Nota**: las cadenas se comparan con el lenguaje de datos actual a menos que se utilice wk use keyboard language.

En el parámetro opcional *valorReempl*, puede pasar un texto para que tome el lugar de toda instancia de texto en *buscarValor* que se encuentre en el *objTarget*.

  
**Rango devuelto**

La función devuelve un rango del valor encontrado o sustituido:

* operaciones de búsqueda - los rangos coinciden con las posiciones de las cadenas encontradas
* operaciones de reemplazo - los rangos coinciden con las posiciones de las cadenas reemplazadas

Si *objTarget* es un rango o elemento, los valores encontrados se devuelven en el orden en que se encuentran. Si *objTarget* es un documento 4D Write Pro, los valores encontrados se devuelven en el siguiente orden:

1. cuerpo
2. encabezado de la primera página de la sección 1 (si la hay)
3. pie de página de la sección 1 (si lo hay)
4. encabezado de la página izquierda de la sección 1 (si lo hay)
5. pie de página izquierdo de la sección 1 (si lo hay)
6. encabezado de la página derecha para la sección (si la hay)
7. pie de página derecho para la sección 1 (si lo hay)
8. encabezado principal de la sección 1 (si lo hay)
9. pie de página principal para la sección 1 (si la hay)
10. repetir con la sección 2, la sección 3, y así sucesivamente.
11. cajas de texto.

Se devuelve un rango vacío si no se encuentran resultados.

## Ejemplo 

```4d
 var $userSel ;$target ;$alphaRanges ;$nextRange : object
 var $options : Integer
 
  // definir opciones de búsqueda
 $options:=wk case insensitive+wk diacritic insensitive
 
  // obtener la posición actual del usuario
 $userSel:=WP Selection range(*;"WParea")
 
  // definir el objetivo
 $target:=WP Get body(WParea) // buscar sólo dentro del cuerpo
 
  // lanzar la BÚSQUEDA de la SIGUIENTE ocurrencia de la cadena "alpha" (basada en la selección actual)
 $nextRange:=WP Find next($target;$userSel;"alpha";$options)
```

## Ver también 

[WP Find all](wp-find-all.md)  
[WP Find previous ](wp-find-previous.md)  