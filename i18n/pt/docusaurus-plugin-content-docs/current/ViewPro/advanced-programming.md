---
id: advanced-programming
title: Programação avançada com Javascript
---

Un Área 4D View Pro es un [objeto de formulario de Área Web](../FormObjects/webArea_overview.md) que utiliza el [motor de renderizado web integrado](../FormObjects/properties_WebArea.md#use-embedded-web-rendering-engine). Como tal, ele se comporta como qualquer outra área da Web, e você pode fazer com que execute o código Javascript chamando o comando [`WA Evaluate Javascript`](../commands-legacy/wa-evaluate-javascript.md) 4D.

Dado que 4D View Pro es alimentado por la [solución de hoja de cálculo SpreadJS](https://developer.mescius.com/spreadjs), también puede llamar a los métodos Javascript de SpreadJS en las áreas 4D View Pro.

## Exemplo prático: Esconder a faixa de opções

Uma vez que 4D View Pro é uma área web, você pode selecionar um elemento da página da Web e modificar seu comportamento usando Javascript. El siguiente ejemplo oculta la [cinta](./configuring.md#ribbon) spreadJS:

```4d
//Método objeto do botão

var $js; $answer : Text

$js:="document.getElementsByClassName('ribbon')[0].setAttribute('style','display: none');"

$js+="window.dispatchEvent(new Event('resize'));"

$answer:=WA Evaluate JavaScript(*; "ViewProArea"; $js)
```

## Chamar métodos Transcriptase do SpreadJS

Você pode tocar na biblioteca SpreadJS de métodos Javascript e chamá-los diretamente para controlar suas planilhas.

4D has a built-in `Utils.spread` property that gives access to the spreadsheet document (also called workbook) inside the 4D View Pro area, making it simpler to call the SpreadJS [Workbook methods](https://developer.mescius.com/spreadjs/api/classes/GC.Spread.Sheets.Workbook).

#### Exemplo

O código seguinte anula a última ação na folha de cálculo:

```4d
WA Evaluate JavaScript(*; "ViewProArea"; "Utils.spread.undoManager().undo()")
```

## Repositório 4D View Pro Tips

[4D-View-Pro-Tips](https://github.com/4d-depot/4D-View-Pro-Tips) es un repositorio GitHub que contiene un proyecto lleno de funciones útiles, que permiten gestionar imágenes flotantes, ordenar columnas o líneas, crear una cultura personalizada, ¡y mucho m Sinta-se à vontade para o clonar e experimentar com o projeto. Sinta-se à vontade para o clonar e experimentar com o projeto.
