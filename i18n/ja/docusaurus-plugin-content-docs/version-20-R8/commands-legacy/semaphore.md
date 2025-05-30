---
id: semaphore
title: Semaphore
slug: /commands/semaphore
displayed_sidebar: docs
---

<!--REF #_command_.Semaphore.Syntax-->**Semaphore** ( *semaphore* {; *tickCount*} ) : Boolean<!-- END REF-->
<!--REF #_command_.Semaphore.Params-->
| 引数 | 型 |  | 説明 |
| --- | --- | --- | --- |
| semaphore | Text | &#8594;  | テストと設定を行うセマフォ |
| tickCount | Integer | &#8594;  | 最大待ち時間 |
| 戻り値 | Boolean | &#8592; | FALSE: セマフォの設定に成功した TRUE: 既にセマフォが存在する |

<!-- END REF-->

## 説明 

<!--REF #_command_.Semaphore.Summary-->セマフォは、ワークステーション間、または同一ワークステーション上のプロセス間で共有されるフラグです。<!-- END REF-->セマフォは、単に存在したり存在しなかったりするだけです。各ユーザが実行して いるメソッドでセマフォの存在を調べることができます。セマフォは、クライアントのワークステーション、あるいはそれを作成したプロセスからのみ削除する事ができます。セマフォを作成する、またはその存在の有無を調べることにより、ワークステーション間でのメソッドの通信が可能になります。セマフォはレコードのアクセスの保護目的には使用しません。これは4Dと4D Serverが自動的に行います。セマフォは、複数のユーザが同じ処理を同時に実行するのを防ぐために用います。

**Semaphore** 関数はすでにセマフォが存在する場合TRUEを返し、何も行いません。セマフォが存在しない場合、**Semaphore** はセマフォを作成しFALSEを返します。同時に1人のユーザしかセマフォを作成することはできません。**Semaphore**がFALSEを返すということは、セマフォが存在しなかったことを意味すると同時に、コマンド呼び出したプロセスに対して新たにセマフォ設定されたことを意味します。

**Semaphore**は、セマフォが設定されていなければFALSEを返します。またコマンドを呼び出したプロセスが既にそのセマフォを設定している場合もFALSEを返します。

セマフォは先頭の$を含めて255文字以内に制限されています。これより長い文字列を指定すると、切り捨てられた文字列を使ってセマフォがテストされます。4Dではセマフォ名は大文字/小文字を区別するという事に注意して下さい(例えば、プログラムは"MySemaphore" と "mysemaphore"は異なるものであると認識します)。

オプションの引数*tickCount* は、*semaphore* が既にセットされている時の待ち時間 (tick) を設定します。  
この場合、関数はセマフォが解放されるか、またはTRUEを返す前に待ち時間が終了まで待ちます。

4Dには2種類のセマフォ、ローカルセマフォとグローバルセマフォがあります。

* ローカルセマフォは、同じワークステーショ ン上のすべてのプロセスからアクセスすることができます (同一ワークステーション上に限られます) 。ローカルセマフォは、セマフォ名の先頭にドル記号 ($) を付けて作成します。ローカルセマフォは、同一ワークステーション上で実行しているプロセス間で処理を監視する際に使用します。例えばローカルセマフォを 使用して、シングルユーザデータベースやワークステーション上のすべてのプロセスで共用するインタープロセス配列へのアクセスを監視します。
* グローバルセマフォは、すべてのユーザとそのプロセスからアクセスすることができます。グローバルセマフォはマルチユーザデータベースのユーザ間で処理を監視するために用います。

グローバルセマフォとローカルセマフォは理論的には同じものです。違いはその有効範囲にあります。

クライアント/サーバーモードでは、グローバルセマフォはすべてのクライアントおよびサーバーで実行しているすべてのプロセス間で共用されます。ローカルセマフォは、それが作成されたマシン上で実行しているプロセス間でのみ共用されます。

スタンドアロンモードの4Dでは、ユーザは一人だけなため、グローバルセマフォもローカルセマフォもその有効範囲は同じです。ただし、シングルとマルチの両方の形でデータベースを使用する場合は、用途によってグローバルセマフォとローカルセマフォを使い分けてください。

**注:** インターフェースやインタープロセス変数など、クライアントアプリケーションのローカルな状態を管理するためにセマフォを使用する場合、ローカルセマフォ を利用することをお勧めします。このようなケースでグローバルセマフォを使用すると、不必要なネットーワークアクセスが行われるだけでなく、不必要に他の クライアントに影響を与えてしまいます。ローカルセマフォを使用すればこのような望ましくない副作用を避けることができます。

## 例題 1 

セマフォを使用した典型的なコードを考えてみます:

```4d
 While(Semaphore("MySemaphore";300))
    IDLE
 End while
  // セマフォで保護されたコードをここに記載
 CLEAR SEMAPHORE("MySemaphore")
```

## 例題 2 

以下の例では、2人のユーザがProducts テーブルの価格を更新するのを防ぎます。以下のメソッドではセマフォを用いて、これを実現しています:

```4d
 If(Semaphore("UpdatePrices")) // セマフォの作成を試行
    ALERT("Another user is already updating prices. Retry later.")
 Else
    DoUpdatePrices // 料金の更新
    CLEAR SEMAPHORE("UpdatePrices")) // セマフォをクリア
 End if
```

## 例題 3 

以下の例はローカルセマフォを使用します。複数のプロセスを持つデータベースで、To Doリストを管理する必要があるとします。このリストはテーブルではなく、インタープロセス配列で管理します。セマフォを使って同時にアクセスされるのを防ぎます。このような場合に、To Doリストは自分だけのものなため、ローカルセマフォで十分です。

インタープロセス配列はOn Startup データベースメソッドで初期化します:

```4d
 ARRAY TEXT(<>ToDoList;0) // The To Do list is initially empty
```

To Doリストに項目を追加するメソッドを次に示します:

```4d
  // ADD TO DO LIST project method
  // ADD TO DO LIST ( Text )
  // ADD TO DO LIST ( To do list item )
 #DECLARE($item : Text)
 If(Not(Semaphore("$AccessToDoList";300)))
  // Wait 5 seconds if the semaphore already exists
    $vlElem:=Size of array(<>ToDoList)+1
    INSERT IN ARAY(<>ToDoList;$vlElem)
    <>ToDoList{$vlElem}:=$item
    CLEAR SEMAPHORE("$AccessToDoList") // Clear the semaphore
 End if
```

どのプロセスからも上記メソッドを呼び出せます。

## 例題 4 

以下のメソッドは、セマフォーが存在する場合コードを実行せず、呼び出し元メソッドにエラーコードとテキストメッセージを返します。

シンタックス:   

```4d
 $L_Error:=Semaphore_proof(->$T_Text_error)
```

```4d
  // セマフォーを使用した保護構造
 #DECLARE($errorPtr : Pointer) -> $result : Integer
 var $L_MyError : Integer
  // エラーメッセージ


var $T_Sema_local;$T_Message : Text
 
  // メソッド開始
 $L_MyError:=0
 $T_Sema_local:="$tictac"
 
 If(Semaphore($T_Sema_local;300))
  // 300 tickの待ち時間の間に、同じセマフォを作成したプロセスがWe expected 300 ticks but the semaphore
  // そのセマフォを解放しなかった場合、ここで停止する
    $L_MyError:=-1
 
 Else
 
  // このメソッドは同時に複数プロセスで実行されることがない
 
  // このプロセスでセマフォーを設定したので、
  // このプロセスで必ずセマフォーを解放しなければならない
 
  // 処理を行う
    ...
  // セマフォーを解放する
    CLEAR SEMAPHORE($T_Sema_local)
 End if
 
 If($L_MyError=-1)
    $T_Message:="セマフォー "+$T_Sema_local+" が既に設定されていたためコードは実行されませんでした。"
 Else
    $T_Message:="OK"
 End if
 
 $result:=$L_MyError
 $errorPtr->:=$T_Message  // 呼び出し元メソッドはエラーコードとメッセージテキストを受け取る


```

## 参照 

[CLEAR SEMAPHORE](clear-semaphore.md)  
[Test semaphore](test-semaphore.md)  
*セマフォーとシグナル*  

## プロパティ

|  |  |
| --- | --- |
| コマンド番号 | 143 |
| スレッドセーフである | &check; |


