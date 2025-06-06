---
id: new-shared-collection
title: New shared collection
displayed_sidebar: docs
---

<!-- REF #_command_.New shared collection.Syntax -->**New shared collection** {( *...value* : any )} : Collection<!-- END REF -->

<!--REF #_command_.New shared collection.Params-->

| Parâmetro | Tipo                                                  |                             | Descrição                        |
| --------- | ----------------------------------------------------- | --------------------------- | -------------------------------- |
| value     | Number, Text, Date, Time, Boolean, Object, Collection | &#8594; | Valores da collection compartida |
| Resultado | Collection                                            | &#8592; | New shared collection            |

<!-- END REF-->

## Descrição

O comando `New shared collection` <!-- REF #_command_.New shared collection.Summary --> cria uma nova coleção compartilhada vazia ou pré-preenchida<!-- END REF --> e retorna sua referência. Coleções podem ser tratadas usando propriedades e funções da [API da classe da coleção](../API/CollectionClass.md).

A adição de um elemento a esta coleção utilizando o operador de atribuição deve ser rodeada pela estrutura [`Use...End use`](../Concepts/shared.md#useend-use), caso contrário é gerado um erro (isto não é necessário ao adicionar elementos utilizando funções como [`push()`](../API/CollectionClass.md#push) ou [`map()`](../API/CollectionClass.md#map) porque estes ativam automaticamente uma estrutura interna *Use...End use*). A leitura de um elemento sem um *Use... End use* estrutura é, no entanto, possível.

:::info

Para obter mais informações sobre coleções compartilhadas, consulte a página [Objetos e coleções compartilhadas](../Concepts/shared.md).

:::

Se não quiser passar parâmetros, `New shared collection` cria uma coleção vazia partilhada e retorna sua referência.

Precisa atribuir a referência devolvida à uma variável 4D de tipo Collection.

> Keep in mind that `var : Collection` statement declares a variable of the `Collection` type but does not create any collection.

Opcionalmente pode preencher automaticamente a nova coleção partilhada passando um ou vários *value* como parâmetros. Também pode adicionar ou modificar elementos através de atribuição de notação de objetos (ver exemplo).

Se o novo índice elemento for além do último elemento existente da coleção partilhada, a coleção é automaticamente redimensionada e todos os novos elementos intermediários são atribuídos um valor **null**.

Pode passar qualquer número de valores dos tipos compatíveis abaixo:

- número (real, longint....). Valores numéricos são sempre armazenados como reais.
- text
- boolean
- date
- hora (armazenada como número de milissegundos - real)
- null
- objeto compartido
- coleção compartilhada

:::note

Diferente de coleções padrão (não partilhadas), coleções partilhadas não são compatíveis com imagens, ponteiros e objetos ou coleção que não forem partilhadas.

:::

## Exemplo

```4d
 $mySharedCol:=New shared collection("alpha";"omega")
 Use($mySharedCol)
    $mySharedCol[1]:="beta"
 End use
```

## Veja também

[New collection](new-collection.md)\
[New shared object](../commands-legacy/new-shared-object.md)\
*Shared objects and shared collections*

## Propriedades

|                   |                             |
| ----------------- | --------------------------- |
| Número de comando | 1527                        |
| Thread safe       | &check; |


