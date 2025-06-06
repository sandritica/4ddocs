---
id: onBeforeDataEntry
title: On Before Data Entry
---

| コード | 呼び出し元                                                                                             | 定義                          |
| --- | ------------------------------------------------------------------------------------------------- | --------------------------- |
| 41  | [リストボックス](FormObjects/listbox_overview.md) - [リストボックス列](FormObjects/listbox_overview.md#リストボックス列) | リストボックスセルが編集モードに変更されようとしている |

## 説明

このイベントは、リストボックス中のセルが編集される直前に生成されます (入力カーソルが表示される前)。 このイベントを使用して、たとえば表示中と編集中で異なるテキストを表示させることができます。

カーソルがセルに入ると、そのリストボックスまたは列のメソッドで `On Before Data Entry` イベントが生成されます。

- このイベントのコンテキストにおいて、$0 に -1 を設定すると、そのセルは入力不可として扱われます。 **Tab** や **Shift+Tab** が押された後にイベントが生成された場合には、フォーカスはそれぞれ次あるいは前のセルに移動します。
- $0 が -1 でなければ (デフォルトは 0)、列は入力可であり編集モードに移行します。

[入力の管理](FormObjects/listbox_overview.md#入力の管理) の章を参照ください。