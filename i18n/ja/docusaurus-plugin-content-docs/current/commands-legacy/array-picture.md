---
id: array-picture
title: ARRAY PICTURE
slug: /commands/array-picture
displayed_sidebar: docs
---

<!--REF #_command_.ARRAY PICTURE.Syntax-->**ARRAY PICTURE** ( *arrayName* ; *size* {; *size2*} )<!-- END REF-->
<!--REF #_command_.ARRAY PICTURE.Params-->
| 引数 | 型 |  | 説明 |
| --- | --- | --- | --- |
| arrayName | Array | &#8594;  | 配列名 |
| size | Integer | &#8594;  | 配列の要素数、またはsize2を指定した場合は配列の行数 |
| size2 | Integer | &#8594;  | 2次元配列の列数 |

<!-- END REF-->

## 説明 

<!--REF #_command_.ARRAY PICTURE.Summary-->ARRAY PICTURE コマンドは、メモリ上にピクチャ要素の配列を作成またはリサイズします。<!-- END REF-->  
  
*arrayName*引数は作成する配列の名前です。  
  
*size*引数は配列の要素数です。  
  
*size2*引数はオプションです。*size2*が渡されている場合、コマンドは2次元配列を作成します。この場合、*size*に配列の行数を、*size2*にはそれぞれの配列の列数を指定します。2次元配列の各行は要素および配列として扱えます。これは配列の一番目の次元を扱う時、2次元配列中の配列全体を挿入あるいは削除するために、他の配列コマンドを使用できることを意味します。  
  
ARRAY PICTURE を既存の配列に適用する場合、  
  
* 配列サイズを増やす場合、既存の値は保持され、新しい要素は空のピクチャで初期化されます。この新しい要素に[Picture size](picture-size.md) を適用した場合、0が返されます。
* 配列サイズを減らす場合、後ろの要素は配列から削除され、失われます。

## 例題 1 

この例は、100要素のピクチャプロセス配列を作成します:  

```4d
 ARRAY PICTURE(agValues;100)
```

## 例題 2 

この例は、100行50列要素のピクチャローカル配列を作成します:  

```4d
 ARRAY PICTURE($agValues;100;50)
```

## 例題 3 

この例題ではインタープロセスピクチャ配列を作成し、ピクチャをそれぞれの要素にロードします。配列の要素数は'*PICT*' リソース数と同じです。配列のリソース名は"*User Intf/*"から始まります。:   

```4d
 RESOURCE LIST("PICT";$aiResIDs;$asResNames)
 ARRAY PICTURE(<>agValues;Size of array($aiResIDs))
 $vlPictElem:=0
 For($vlElem;1;Size of array(<>agValues))
    If($asResNames{$vlElem}="User Intf/@")
       $vlPictElem:=$vlPictElem+1
       GET PICTURE RESOURCE("PICT";$aiResIDs{$vlElem};$vgPicture)
       <>agValues{$vlPictElem}:=$vgPicture
    End if
 End for
 ARRAY PICTURE(<>agValues;$vlPictElem)
```


## プロパティ

|  |  |
| --- | --- |
| コマンド番号 | 279 |
| スレッドセーフである | &check; |


