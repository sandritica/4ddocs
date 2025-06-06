---
id: web-server-list
title: WEB Server list
displayed_sidebar: docs
---

<!--REF #_command_.WEB Server list.Syntax-->**WEB Server list** : Collection<!-- END REF-->

<!--REF #_command_.WEB Server list.Params-->

| Parâmetro | Tipo       |                             | Descrição                                      |
| --------- | ---------- | --------------------------- | ---------------------------------------------- |
| Resultado | Collection | &#8592; | Collection of the available Web Server objects |

<!-- END REF-->

<details><summary>História</summary>

| Release | Mudanças   |
| ------- | ---------- |
| 18 R3   | Adicionado |

</details>

## Descrição

O comando `WEB Server list` <!-- REF #_command_.WEB Server list.Summary -->retorna uma coleção de todos os objetos do servidor Web disponíveis na aplicação 4D<!-- END REF -->.

Uma aplicação 4D pode conter em qualquer lugar de um a vários servidores Web:

- um servidor Web para o banco de dados host (servidor Web padrão)
- um servidor web para cada componente.

All available Web servers are returned by the `WEB Server list` command, whether they are actually running or not.

> O objeto do servidor Web padrão é carregado automaticamente pelo 4D na inicialização. Por outro lado, cada servidor Web de componentes que você deseja usar precisa ser instanciado usando o comando [`WEB Server`](web-server.md).

You can use the [.name](../API/WebServerClass.md#name) property of the Web server object to identify the project or component to which each Web server object in the list is attached.

## Exemplo

Queremos saber quantos servidores rodando estão disponíveis:

```4d
 var $wSList : Collection
 var $vRun : Integer

 $wSList:=WEB Server list
 $vRun:=$wSList.countValues(True;"isRunning")
 ALERT(String($vRun)+" web server(s) running on "+String($wSList.length)+" available.")
```

## Veja também

[WEB Server](web-server.md)\
[webServer.stop()](../API/WebServerClass.md#stop)

## Propriedades

|                   |                             |
| ----------------- | --------------------------- |
| Número de comando | 1716                        |
| Thread safe       | &check; |


