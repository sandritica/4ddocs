---
id: vp-insert-rows
title: VP INSERT ROWS
---

<!-- REF #_method_.VP INSERT ROWS.Syntax -->

**VP INSERT ROWS** ( *rangeObj* : Object ) <!-- END REF -->

<!-- REF #_method_.VP INSERT ROWS.Params -->

| Parâmetro | Tipo   |    | Descrição        |                  |
| --------- | ------ | -- | ---------------- | ---------------- |
| rangeObj  | Object | -> | Objeto intervalo | <!-- END REF --> |

## Descrição

O comando `VP INSERT ROWS` <!-- REF #_method_.VP INSERT ROWS.Summary --> insere linhas definidas pelo *rangeObj*<!-- END REF -->.

In *rangeObj*, pass an object containing a range of the starting row (the row which designates where the new row will be inserted) and the number of rows to insert. Se o número de linhas a inserir for omitido (não definido), uma única linha é inserida.

Novas linhas são inseridas imediatamente antes da primeira linha do *rangeObj*.

## Exemplo

Para inserir 3 linhas antes da primeira linha:

```4d
VP INSERT ROWS(VP Row("ViewProArea";0;3))
```

O resultado é:

![](../../assets/en/ViewPro/cmd_vpInsertRows.PNG)

## Veja também

[VP DELETE COLUMNS](vp-delete-columns.md)<br/>
[VP DELETE ROWS](vp-delete-rows.md)<br/>
[VP INSERT COLUMNS](vp-insert-columns.md)