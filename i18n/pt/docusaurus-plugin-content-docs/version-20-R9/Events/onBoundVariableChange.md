---
id: onBoundVariableChange
title: On Bound Variable Change
---

| Code | Pode ser chamado por | Definição                                         |
| ---- | -------------------- | ------------------------------------------------- |
| 54   | Formulário           | A variável ligada a um subformulário é modificada |

## Descrição

Este evento é gerado no contexto do método formulário de um [subformulário](FormObjects/subform_overview.md) assim que um valor é atribuído à variável vinculada com o subformulário no formulário pai (mesmo que o mesmo valor seja reatribuído) e se o subformulário pertence à página atual do formulário ou à página 0.

Para obter mais informações, consulte a seção [Gerenciar a variável vinculada](FormObjects/subform_overview.md#using-the-bound-variable-or-expression).