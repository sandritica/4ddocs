---
id: skip
title: $skip
---

Inicia la entidad definida por este número en la colección (*por ejemplo*, `$skip=10`)

## Descrição

`$skip` define la entidad de la colección por la que se va a comenzar. Por padrão, a coleção enviada começa com a primeira entidade. Para começar com a 10.ª entidade da coleção, passe 10.

`$skip` é geralmente usado em conjunto com [`$top/$limit`]($top_$limit.md) para navegar em uma coleção de entidades.

## Exemplo

No exemplo seguinte, vamos para a 20.ª entidade do nosso conjunto de entidades:

`GET  /rest/Employee/$entityset/CB1BCC603DB0416D939B4ED379277F02?$skip=20`