---
id: change-licenses
title: CHANGE LICENSES
slug: /commands/change-licenses
displayed_sidebar: docs
---

<!--REF #_command_.CHANGE LICENSES.Syntax-->**CHANGE LICENSES**<!-- END REF-->
<!--REF #_command_.CHANGE LICENSES.Params-->
| このコマンドは引数を必要としません |  |
| --- | --- |

<!-- END REF-->

## 説明 

<!--REF #_command_.CHANGE LICENSES.Summary-->CHANGE LICENSES コマンドは、4Dライセンス管理ダイアログボックスを表示します。<!-- END REF-->

こ のコマンドは、4Dシングルユーザー向けアプリケーションでのみ使用することができ、コンポーネントから呼び出すことはできません。パスワードが有効化さ れている場合、このコマンドはデザイナーまたは管理者によってのみ実行可能です。適切な権限がないユーザーから呼び出された場合、このコマンドは何もしま せん。

ライセンス管理ダイアログボックスを使用することによって、ユーザーは実行されたマシン上でプラグインやWebサーバーを有効化することができます。4Dでは、このダイアログボックスは**ヘルプ**メニュー内の**ライセンス管理...** を選択することによって表示できます。

CHANGE LICENSES は、顧客に配付されたコンパイル済みのシングルユーザー向け4Dアプリケーションに対してライセンスを有効化し、Expansion 番号を追加するための便利な方法です。4DデベロッパまたはISマネージャからすると、このコマンドを使用することによって、その都度アプリケーションの アップデートを送ることなく、ユーザーに各々のライセンス番号を入力させるだけで4Dアプリケーションを配布することが可能になります。

このダイアログボックスに関する詳細は、4Dインストールガイドの*インストールとアクティベーション* のセクションを参照してください。

## 例題 

カスタム設定または環境設定ダイアログボックス内に、以下のメソッドを持つボタンを設定します:

```4d
  // bLicense button のオブジェクトメソッド
 CHANGE LICENSES
```

この方法であれば、ユーアーはデータベースに手を加えることなくライセンスを有効化することができます。

## 参照 

[License info](../commands/license-info.md)  
[Is license available](is-license-available.md)  

## プロパティ

|  |  |
| --- | --- |
| コマンド番号 | 637 |
| スレッドセーフである | &cross; |
| サーバー上での使用は不可 ||


