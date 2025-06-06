---
id: text
title: テキスト
---


テキストオブジェクトを使って、指示・タイトル・ラベルなどの静的 (スタティック) なテキストをフォーム上に表示することができます。 これらのテキストは、参照を含むことで動的にもなります。 詳細については [スタティックテキスト中で参照を使用する](https://doc.4d.com/4Dv18/4D/18/Using-references-in-static-text.300-4575714.ja.html) を参照ください。

#### JSON 例:

```4d
    "myText": {
                "type": "text",
                "text": "Hello World!",
                "textAlign": "center",
                "left": 60,         
                "top": 160, 
                "width": 100,
                "height": 20,
                "stroke": "#ff0000"     // テキストカラー   
                "fontWeight": "bold"
                }
```


## 回転

4D では、フォーム内のテキストエリアを [回転](properties_Text.md#方向) させることができます。

![](../assets/en/FormObjects/staticText.png)

> このプロパティは `OBJECT SET TEXT ORIENTATION` ランゲージコマンドによっても設定することができます。

テキストが回転された後でも、サイズや位置などすべてのプロパティを変更することが可能です。 テキストエリアの高さと幅は、回転の方向に依らないという点に注意してください:

![](../assets/en/FormObjects/staticText2.png)

- オブジェクトが A 方向にリサイズされるとき、変更されるのは [幅](properties_CoordinatesAndSizing.md#幅) です。
- オブジェクトが C 方向にリサイズされるとき、変更されるのは [高さ](properties_CoordinatesAndSizing.md#高さ) です。
- オブジェクトが B 方向にリサイズされるとき、[幅](properties_CoordinatesAndSizing.md#幅) と [高さ](properties_CoordinatesAndSizing.md#高さ) の両方が同時に変更されます。


## プロパティ一覧

<details><summary>履歴</summary>

| リリース  | 内容        |
| ----- | --------- |
| 19 R7 | 角の半径をサポート |

</details>


[太字](properties_Text.md#太字) - [境界線スタイル](properties_BackgroundAndBorder.md#境界線スタイル) - [下](properties_CoordinatesAndSizing.md#下) - [cssクラス](properties_Object.md#cssクラス) - [角の半径](properties_CoordinatesAndSizing.md#角の半径) - [背景色/塗りカラー](properties_BackgroundAndBorder.md#背景色塗りカラー) - [フォント](properties_Text.md#フォント) - [フォントカラー](properties_Text.md#フォントカラー) - [フォントサイズ](properties_Text.md#フォントサイズ) - [高さ](properties_CoordinatesAndSizing.md#高さ) - [横揃え](properties_Text.md#横揃え) - [横方向サイズ変更](properties_ResizingOptions.md#横方向サイズ変更) - [イタリック](properties_Text.md#イタリック) - [左](properties_CoordinatesAndSizing.md#左) - [オブジェクト名](properties_Object.md#オブジェクト名) - [方向](properties_Text.md#方向) - [右](properties_CoordinatesAndSizing.md#右) - [タイトル](properties_Object.md#タイトル) - [上](properties_CoordinatesAndSizing.md#上) - [型](properties_Object.md#型) - [下線](properties_Text.md#下線) - [縦方向サイズ変更](properties_ResizingOptions.md#縦方向サイズ変更) - [表示状態](properties_Display.md#表示状態) - [幅](properties_CoordinatesAndSizing.md#width) 
