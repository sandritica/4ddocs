---
id: get-list-item-icon
title: GET LIST ITEM ICON
slug: /commands/get-list-item-icon
displayed_sidebar: docs
---

<!--REF #_command_.GET LIST ITEM ICON.Syntax-->**GET LIST ITEM ICON** ( {* ;} *list* ; *itemRef* ; *icon* )<br/>**GET LIST ITEM ICON** ( * ; *list* ; * ; *icon* <!-- END REF-->
<!--REF #_command_.GET LIST ITEM ICON.Params-->
| 引数 | 型 |  | 説明 |
| --- | --- | --- | --- |
| * | 演算子 | &#8594;  | 指定時, listはオブジェクト名 (文字列) 省略時, listはリスト参照番号 |
| list | Integer, Text | &#8594;  | リスト参照番号 (* 省略時) または リストオブジェクト名 (* 指定時) |
| itemRef &#124; * | 演算子, 倍長整数 | &#8594;  | 項目参照番号 または 0: リストに最後に追加された項目 または *: リストのカレントの項目 |
| icon | Picture | &#8592; | 項目に関連付けられたアイコン |

<!-- END REF-->

## 説明 

<!--REF #_command_.GET LIST ITEM ICON.Summary-->GET LIST ITEM ICON コマンドは、*list*に参照番号またはオブジェクト名を渡したリスト内の、*itemRef*項目参照の項目に割り当てられたアイコンを*icon*に返します。<!-- END REF-->  
  
オプションの第一引数 *\** を渡すと、*list* 引数はフォーム上のリストオブジェクトに対応するオブジェクト名 (文字列) です。この引数を渡さない場合、*list* 引数は階層リスト参照 ([ListRef](# "階層リストへの参照")) です。リストオブジェクトを一つしか使わない場合や、2番目の *\** を使用しない場合は、両方のシンタックスを使用できます。他方フォーム上に同じ階層リストを参照する複数のオブジェクトがある場合で、2番目の *\** を渡して現在選択されている項目を参照する場合、それぞれのオブジェクトが個別に選択された項目をもつので、オブジェクト名に基づくシンタックスを使用しなければなりません。

**Note:** オブジェクト名に @ 文字を使用することで、名前に対応するオブジェクトが複数検索された場合、GET LIST ITEM ICON コマンドは最初に見つけたオブジェクトを処理の対象とします。

*itemRef*に項目参照番号を渡すことができます。対応する項目がない場合、コマンドは何も行いません。0を渡した場合、リストに最後に追加された項目が処理の対象となります。*\** を渡した場合、コマンドは現在選択されている項目を処理の対象とします。複数の項目が選択されている場合、カレントの項目は最後に選択された項目です。項目が選択されていない場合、コマンドは何も行いません。

iconにはピクチャ変数を渡します。コマンド実行後、(スタティックピクチャ、リソース、ピクチャ式になどの) ソースに関わらず、引数には項目に割り当てられたアイコンが返されます。

項目にアイコンが割り当てられていない場合、*icon*変数は空となります。

**Note:** 項目に割り当てられたアイコンがスタティックな参照 (リソース参照またはピクチャライブラリのピクチャ) で定義されている場合、その番号は[GET LIST ITEM PROPERTIES](get-list-item-properties.md "GET LIST ITEM PROPERTIES") コマンドで取得できます。

## 参照 

[GET LIST ITEM PROPERTIES](get-list-item-properties.md)  
[SET LIST ITEM ICON](set-list-item-icon.md)  

## プロパティ

|  |  |
| --- | --- |
| コマンド番号 | 951 |
| スレッドセーフである | &cross; |


