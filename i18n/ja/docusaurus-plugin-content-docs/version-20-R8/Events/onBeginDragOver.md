---
id: onBeginDragOver
title: On Begin Drag Over
---

| コード | 呼び出し元                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | 定義               |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- |
| 17  | [4D Write Pro エリア](FormObjects/writeProArea_overview.md) - [ボタン](FormObjects/button_overview.md) - [ボタングリッド](FormObjects/buttonGrid_overview.md) - [チェックボックス](FormObjects/checkbox_overview.md) - [ドロップダウンリスト](FormObjects/dropdownList_Overview.md) - Form - [階層リスト](FormObjects/list_overview.md) - [入力](FormObjects/input_overview.md) - [リストボックス](FormObjects/listbox_overview.md) - [リストボックス列](FormObjects/listbox_overview.md#リストボックス列) - [ピクチャーボタン](FormObjects/pictureButton_overview.md) - [ピクチャーポップアップメニュー](FormObjects/picturePopupMenu_overview.md) - [プラグインエリア](FormObjects/pluginArea_overview.md) - [進捗インジケーター](FormObjects/progressIndicator.md) - [ラジオボタン](FormObjects/radio_overview.md) - [ルーラー](FormObjects/ruler.md) - [スピナー](FormObjects/spinner.md) - [スプリッター](FormObjects/splitters.md) - [ステッパー](FormObjects/stepper.md) - [タブコントロール](FormObjects/tabControl.md) | オブジェクトがドラッグされている |

## 説明

`On Begin Drag Over` フォームイベントは、ドラッグ可能なすべてのフォームオブジェクト で選択できます。 このイベントは、オブジェクトが [ドラッグ有効](FormObjects/properties_Action.md#ドラッグ有効) プロパティを持っているすべてのケースで生成されます。 このイベントは、ソースオブジェクトのメソッドまたはソースオブジェクトのフォームメソッドから呼び出すことができます。

> [`On Drag Over`](onDragOver.md) フォームイベントとは異なり、`On Begin Drag Over` イベントはドラッグアクションの **ソースオブジェクト** のコンテキスト内で呼び出されます。

`On Begin Drag Over` イベントは、ドラッグアクションの準備に役立ちます。 このイベントは以下のように使用できます: このイベントは以下のように使用できます: このイベントは以下のように使用できます: このイベントは以下のように使用できます:

- `APPEND DATA TO PASTEBOARD` コマンドを使って、ペーストボードにデータや署名を追加する。
- `SET DRAG ICON` コマンドを使って、ドラッグアクション中にカスタムアイコンを表示する。
- ドラッグされたオブジェクトのメソッドの戻り値を使用して、ドラッグを許可/拒否する。
    - ドラッグアクションを受け入れるには、ソースオブジェクトのメソッドは 0 (ゼロ) を返さなければなりません。
    - ドラッグアクションを拒否するには、ソースオブジェクトのメソッドは -1 (マイナス1) を返さなければなりません。
    - 結果が返されない場合は、ドラッグアクションが受け入れられたと 4D は判断します。

4D のデータは、イベントが呼び出される前に、ペーストボードに置かれます。 たとえば、**自動ドラッグ** アクションなしでドラッグした場合、ドラッグされたテキストは、イベントが呼び出される時にはペーストボードにあります。
