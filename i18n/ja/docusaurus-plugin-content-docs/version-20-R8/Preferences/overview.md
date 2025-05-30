---
id: overview
title: 環境設定
---

環境設定は、作業環境に影響する様々なオプションを指定します (例: デフォルトオプション、表示テーマ、コードエディター機能、ショートカット)。 これらの設定は、4D や 4D Server アプリケーションで開くすべてのプロジェクトに適用されます。

**4D Server**: 複数のユーザーが同時に環境設定を更新しようとすると、オブジェクトのロックが発生します。 一度に一人のユーザーのみが環境設定ダイアログボックスを使用できます。

> 4D は開かれているプロジェクト固有の設定をおこなうための **ストラクチャー設定** ダイアログも提供しています (**デザイン** メニューから利用可能です)。 詳細はデータベース設定の章を参照ください。

## アクセス

環境設定ダイアログボックスにアクセスするには **編集** (Windows) または **4D** アプリケーションメニュー (macOS) から **環境設定...** を選択します:

![](../assets/en/Preferences/overviewAccess.png)

このメニューコマンドは、プロジェクトが開かれていない場合でも利用できます。

`OPEN SETTINGS WINDOW` コマンドや、"環境設定" 標準アクションを (ボタンやメニューに割り当てて) 使用することで、アプリケーションモードでも環境設定ダイアログボックスを表示できます。

## ストレージ

Settings made in the Preferences dialog box are saved in an XML format preferences file named **4D Preferences vXX.4DPreferences** that is stored in the active 4D folder of the current user, as returned by the [`Get 4D folder`](../commands-legacy/get-4d-folder.md) command:

- Windows: `\{disk\}\Users\\{username\}\AppData\Roaming\4D`
- macOS: `\{disk\}:Users:\{username\}:Library:Application Support:4D`

## パラメーターのカスタマイズと初期設定

設定ダイアログボックスでは、変更された設定内容は太字で表示されます:

![](../assets/en/Preferences/overviewUser.png)

環境設定においては、ダイアログボックスで直接変更されたか、変換されたデータベースの場合以前のバージョンで変更された設定が、カスタマイズ箇所として扱われます。

パラメーターは手作業でデフォルト値に置き換えられたときにも太字で表示されます。 このように、カスタマイズされたパラメーターはすべて目視で識別することができます。

パラメーターをデフォルト値に戻し、カスタマイズされたことを示す太字スタイルを取り除くためには、**初期設定にリセット** ボタンをクリックします:

![](../assets/en/Preferences/overviewSettings.png)

このボタンをクリックすると、現在表示されているページの全パラメーターがリセットされます。 現在のページで最低でも一つのパラメーターが変更されると、このボタンはアクティブになります。

