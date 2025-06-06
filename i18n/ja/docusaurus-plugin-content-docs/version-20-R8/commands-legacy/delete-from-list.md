---
id: delete-from-list
title: DELETE FROM LIST
slug: /commands/delete-from-list
displayed_sidebar: docs
---

<!--REF #_command_.DELETE FROM LIST.Syntax-->**DELETE FROM LIST** ( {* ;} *list* ; itemRef | * {; *} )<!-- END REF-->
<!--REF #_command_.DELETE FROM LIST.Params-->
| 引数 | 型 |  | 説明 |
| --- | --- | --- | --- |
| * | 演算子 | &#8594;  | 指定した場合, listはオブジェクト名 (文字列) 省略した場合, listはリスト参照番号 |
| list | Integer, Text | &#8594;  | リスト参照番号 (* が省略された場合), または リストタイプオブジェクト名 (* を渡した場合) |
| itemRef &#124; * | 倍長整数, 演算子 | &#8594;  | 項目参照番号, または 0 はリストに最後に追加された項目 または * 現在選択されているリスト項目 |
| * | Operator |  &#8594;  | 指定した場合, サブリストがあればそれもメモリから消去 省略した場合, サブリストがあってもそれを消去しない |

<!-- END REF-->

## 説明 

<!--REF #_command_.DELETE FROM LIST.Summary-->DELETE FROM LIST コマンドは、*list*に指定した参照番号またはオブジェクト名を持つリストから、*itemRef*引数で指定した項目を削除します。<!-- END REF-->

1番目のオプション引数 *\** を渡すと、*list* 引数はフォーム中のリストオブジェクトのオブジェクト名 (文字列) です。この引数を渡さない場合、*list* 引数には階層リスト参照 ([ListRef](# "階層リストへの参照")) を渡します。階層リストのフォームオブジェクトを1つしか使用しない場合や、2番目の *\** を省略して階層リスト構造にアクセスする場合は、両方のシンタックスを使用できます。他方、1つの階層リストを複数のフォームオブジェクトで使用する場合や、2番目の *\** を渡してカレントの項目を処理対象とする場合は、それぞれのオブジェクトが個別にカレント項目を持つため、オブジェクト名に基づくシンタックスを使用しなければなりません。

*itemRef*に *\** を渡すと、現在選択されている項目をリストから削除します。この引数に0を渡すとリストに最後に追加された項目が削除されます。

また削除する項目の項目参照番号を指定することができます。指定された項目参照番号を持つ項目が見つからなければ、コマンドは何も行いません。

項目参照番号を指定する場合、それぞれの項目にユニークな参照番号を持つリストをビルドします。そうでなければ項目を識別できません。詳細は*階層リストの管理*の説明を参照してください。

どの項目を削除するかに関わらず、オプションの *\** 引数を渡して、4Dがサブリストも削除するように指示すべきです。*\** 引数を渡さない場合、サブリストのリスト参照番号を事前に取得します。後で[CLEAR LIST](clear-list.md "CLEAR LIST") コマンドを使用してこのリストを削除できます。

## 例題 

以下のコードは現在選択されている項目を*hList*リストから削除します。項目にサブリストが添付されていれば、そのサブリストおよびさらにそのサブリストも削除されます:

```4d
 DELETE FROM LIST(hList;*;*)
```

## 参照 

[CLEAR LIST](clear-list.md)  
[GET LIST ITEM](get-list-item.md)  

## プロパティ

|  |  |
| --- | --- |
| コマンド番号 | 624 |
| スレッドセーフである | &cross; |


