---
id: jsonReference
title: JSON プロパティリスト
---

この一覧は、すべてのフォームプロパティを JSON名順に並べてまとめたものです。 プロパティ名をクリックすると、詳細説明に移動します。
> "フォームプロパティ" の章では、プロパティリストにおけるテーマと名称で各プロパティを紹介しています。

[b](#b) - [c](#c) - [d](#d) - [e](#e) - [f](#f) - [h](#h) - [i](#i) - [m](#m) - [p](#p) - [r](#r) - [s](#s) - [w](#w)

| プロパティ                                                                       | 説明                                                        | とりうる値                                                                                 |
| --------------------------------------------------------------------------- | --------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| <a name="b">**b**</a>                                                   |                                                           |                                                                                       |
| [`bottomMargin`](properties_FormSize.md#垂直-マージン)                            | 垂直マージン値 (ピクセル単位)                                          | 最小値: 0<a name="d"></a>                                                       |
| <a name="c">**c**</a>                                                   |                                                           |                                                                                       |
| [`colorScheme`](properties_FormProperties.md#カラースキーム)                       | フォームのカラースキーム                                              | "dark", "light"                                                                       |
| [`css`](properties_FormProperties.md#css)                                   | フォームが使用する CSSファイル                                         | 文字列、文字列のコレクション、または "path" と "media" プロパティを持つオブジェクトのコレクションとして提供される CSSファイルパス。          |
| <a name="d">**d**</a>                                                   |                                                           |                                                                                       |
| [`destination`](properties_FormProperties.md#フォームタイプ)                       | フォームタイプ                                                   | "detailScreen", "listScreen", "detailPrinter", "listPrinter"                          |
| <a name="e">**e**</a>                                                   |                                                           |                                                                                       |
| [`entryOrder`](formEditor.md#データの入力順)                                       | 入力フォームで **Tab**キーや **改行**キーが使用されたときに、アクティブオブジェクトが選択される順番。 | 4Dフォームオブジェクト名のコレクション                                                                  |
| [`events`](Events/overview.md)                                              | オブジェクトまたはフォームについて選択されているイベントのリスト                          | イベント名のコレクション。例: ["onClick","onDataChange"...].                                        |
| <a name="f">**f**</a>                                                   |                                                           |                                                                                       |
| [`formSizeAnchor`](./properties_FormSize.md#size-based-on)                  | フォームサイズを定義するために使用するオブジェクトの名前 (最小長さ: 1) (最小長さ: 1)          | 4Dオブジェクトの名前                                                                           |
| <a name="h">**h**</a>                                                   |                                                           |                                                                                       |
| [`height`](properties_FormSize.md#高さ)                                       | フォームの高さ                                                   | 最小値: 0                                                                                |
| <a name="i">**i**</a>                                                   |                                                           |                                                                                       |
| [`inheritedForm`](properties_FormProperties.md#継承されたフォーム名)                  | 継承フォームを指定します                                              | テーブルまたはプロジェクトフォームの名前 (文字列), フォームを定義する .json ファイルへの POSIX パス (文字列), またはフォームを定義するオブジェクト |
| [`inheritedFormTable`](properties_FormProperties.md#継承されたフォームテーブル)          | 継承フォームがテーブルに属していれば、そのテーブル                                 | テーブル名またはテーブル番号                                                                        |
| <a name="m">**m**</a>                                                   |                                                           |                                                                                       |
| [`markerBody`](properties_Markers.md#フォーム詳細)                                | 詳細マーカーの位置                                                 | 最小値: 0                                                                                |
| [`markerBreak`](properties_Markers.md#フォームブレーク)                             | ブレークマーカーの位置                                               | 最小値: 0                                                                                |
| [`markerFooter`](properties_Markers.md#フォームフッター)                            | フッターマーカーの位置                                               | 最小値: 0                                                                                |
| [`markerHeader`](properties_Markers.md#form-header)                         | ヘッダーマーカーの位置                                               | 最小値 (整数): 0; 最小値 (整数配列): 0                                                            |
| [`memorizeGeometry`](properties_FormProperties.md#save-geometry)            | フォームウィンドウが閉じられた時に、フォームパラメーターを記憶                           | true, false                                                                           |
| [`menuBar`](properties_Menu.md#連結メニューバー)                                    | フォームと関連づけるメニューバー                                          | 有効なメニューバーの名称                                                                          |
| [`method`](properties_Action.md#メソッド)                                       | プロジェクトメソッド名                                               | 存在するプロジェクトメソッドの名前                                                                     |
| <a name="p">**p**</a>                                                   |                                                           |                                                                                       |
| [`pages`](properties_FormProperties.md#pages)                               | ページのコレクション (各ページはオブジェクトです)                                | ページオブジェクト                                                                             |
| [`pageFormat`](properties_Print.md#設定)                                      | object                                                    | 利用可能な印刷プロパティ                                                                          |
| <a name="r">**r**</a>                                                  |                                                           |                                                                                       |
| [`rightMargin`](properties_FormSize.md#水平-マージン)                             | 水平マージン値 (ピクセル単位)                                          | 最小値: 0                                                                                |
| <a name="s">**s**</a>                                                  |                                                           |                                                                                       |
| [`shared`](properties_FormProperties.md#サブフォームとして公開)                        | フォームがサブフォームとして利用可能かを指定します                                 | true, false                                                                           |
| <a name="w">**w**</a>                                                  |                                                           |                                                                                       |
| [`width`](properties_FormSize.md#幅)                                         | フォームの幅                                                    | 最小値: 0                                                                                |
| [`windowMaxHeight`](properties_WindowSize.md#maximum-height-minimum-height) | フォームウィンドウの最大高さ                                            | 最小値: 0                                                                                |
| [`windowMaxWidth`](properties_WindowSize.md#maximum-width-minimum-width)    | フォームウィンドウの最大幅                                             | 最小値: 0                                                                                |
| [`windowMinHeight`](properties_WindowSize.md#maximum-height-minimum-height) | フォームウィンドウの最小高さ                                            | 最小値: 0                                                                                |
| [`windowMinWidth`](properties_WindowSize.md#maximum-width-minimum-width)    | フォームウィンドウの最小幅                                             | 最小値: 0                                                                                |
| [`windowSizingX`](properties_FormSize.md#固定幅)                               | フォームウィンドウの高さ固定                                            | "fixed", "variable"                                                                   |
| [`windowSizingY`](properties_WindowSize.md#固定高さ)                            | フォームウィンドウの幅固定                                             | "fixed", "variable"                                                                   |
| [`windowTitle`](properties_FormProperties.md#ウィンドウタイトル)                     | フォームウィンドウのタイトルを指定します                                      | フォームウィンドウの名前。                                                                         |