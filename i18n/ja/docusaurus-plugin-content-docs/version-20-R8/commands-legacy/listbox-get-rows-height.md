---
id: listbox-get-rows-height
title: LISTBOX Get rows height
slug: /commands/listbox-get-rows-height
displayed_sidebar: docs
---

<!--REF #_command_.LISTBOX Get rows height.Syntax-->**LISTBOX Get rows height** ( {* ;} *object* {; *unit*} ) : Integer<!-- END REF-->
<!--REF #_command_.LISTBOX Get rows height.Params-->
| 引数 | 型 |  | 説明 |
| --- | --- | --- | --- |
| * | 演算子 | &#8594;  | 指定時, objectはオブジェクト名 (文字列) 省略時, objectは変数 |
| object | any | &#8594;  | オブジェクト名 (* 指定時) または 変数 (* 省略時) |
| unit | Integer | &#8594;  | 高さを表す単位: 0または省略時はピクセル、1の場合行単位 |
| 戻り値 | Integer | &#8592; | 行の高さ |

<!-- END REF-->

## 説明 

<!--REF #_command_.LISTBOX Get rows height.Summary-->**LISTBOX Get rows height**コマンドは、*object*引数および *\** で指定されたリストボックスの現在の行の高さを返します。<!-- END REF-->

オプションの引数 *\** を渡すことにより、*object*引数がオブジェクト名（文字列）であることを示します。この引数を渡さない場合、*object*引数が変数であることを示します。この場合、文字列ではなく変数参照を指定します。オブジェクト名についての詳細は*オブジェクトプロパティ*を参照してください。

*unit* 引数を省略するとデフォルトで、行の高さはピクセル単位で行われます。他の単位を使用する場合は *unit* 引数に*List Box*テーマの以下の定数を渡します:

| 定数        | 型    | 値 | コメント                            |
| --------- | ---- | - | ------------------------------- |
| lk lines  | 倍長整数 | 1 | 高さを行数で指定。4Dはフォント設定に応じて高さを計算します。 |
| lk pixels | 倍長整数 | 0 | 高さをピクセルで指定 (デフォルト)。             |

**注:** 行の高さの計算に関する情報はデザインリファレンスマニュアルを参照してください。

## 参照 

[LISTBOX Get auto row height](listbox-get-auto-row-height.md)  
[LISTBOX Get row height](listbox-get-row-height.md)  
[LISTBOX SET ROWS HEIGHT](listbox-set-rows-height.md)  

## プロパティ

|  |  |
| --- | --- |
| コマンド番号 | 836 |
| スレッドセーフである | &cross; |


