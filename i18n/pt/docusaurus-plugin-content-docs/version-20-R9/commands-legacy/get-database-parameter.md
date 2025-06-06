---
id: get-database-parameter
title: Get database parameter
slug: /commands/get-database-parameter
displayed_sidebar: docs
---

<!--REF #_command_.Get database parameter.Syntax-->**Get database parameter** ( {*tabela* ;} *seletor* {; *valorAlfa*} ) : Real<!-- END REF-->
<!--REF #_command_.Get database parameter.Params-->
| Parâmetro | Tipo |  | Descrição |
| --- | --- | --- | --- |
| tabela | Table | &#8594;  | Tabela do parâmetro ou tabela padrão se este parâmetro for omitido |
| seletor | Integer | &#8594;  | Código do parâmetro do banco |
| valorAlfa | Text | &#8592; | Valor alfa do parâmetro |
| Resultado | Real | &#8592; | Valor atual do parâmetro |

<!-- END REF-->

## Descrição 

<!--REF #_command_.Get database parameter.Summary-->O comando **Get database parameter** permite obter o valor atual de um parâmetro do banco 4D.<!-- END REF--> Quando o valor do parâmetro é uma cadeia de caracteres, é retornado o o parâmetro *valorAlfa*.

O parâmetro *seletor* designa o parâmetero a ser obtido. 4D oferece as seguintes constantes pré-definidas, que se encontram no tema“*Parâmetros de Banco*”:

### 4D Server timeout (13)

**Descrição**: valor do tempo de espera antes de desconexão (timeout) de 4D Server. Por padrão, O valor do timeout de 4D Server se define na página "Cliente-Servidor/Configuração" da caixa de diálogo Preferências na máquina servidor.

O seletor 4D Server Timeout lhe permite atribuir no parâmetro valor um novo timeout, expresso em minutos. Esta funcionalidade é particularmente útil para aumentar o valor do timeout antes da execução na máquina cliente de uma operação de longa duração no cliente, tal como a impressão de um grande número de páginas, a qual pode causar um timeout inesperado.



Há duas opções:



 \* Se passar um valor positivo no parâmetro valor, realiza uma modificação global e permanente: o novo valor se aplica a todos os processos e se armazena nas preferências da aplicação 4D (equivalente a uma mudança nas Preferências).

 \* Se passar um valor negativo no parâmetro valor, define um timeout local e temporário: o novo valor apenas se aplica ao processo que o invoca (os outros processos conservam os valores por padrão) e retoma o valor por padrão logo que o servidor receber um sinal de atividade do cliente, por exemplo, quando a operação termina. Esta opção é muito útil para administrar operações longas iniciadas por plug-ins 4D .



Para definir uma conexão "Sem timeout", passe 0 em valor. Ver o exemplo 1.





### 4D Remote mode timeout (14)

**Alcance**: aplicação 4D se *valor* positivo

 Se conserva entre duas **sessões** **:** sim se *valor* positivo

 **Descrição**: valor do timeout outorgado pela máquina 4D remota à máquina 4D Server. Por padrão, este valor é definido na página "Cliente-Servidor/Configuração" da caixa de diálogo de Preferências na máquina remota.

Para maior informação sobre este seletor, consulte a descrição do seletor 4D Server Timeout (13). O seletor 4D Remote Mode Timeout pode ser utilizado em vários casos específicos.





### Port ID (15)

**Alcance**: 4D local, 4D Server

**Se conserva entre duas sessões**: não

**Descrição**: Número de porta TCP utilizado pelo servidor web 4D com 4D em modo local e 4D Server. O valor por padrão, é 80.

O número de porta TCP está definida na página "Web/Configuração" da caixa de diálogo das Propriedades do banco de dados. Pode utilizar as constantes do tema *Números de porta TCP* para o parâmetro *valor*.

O seletor Port ID é útil no marco de servidores web 4D compilados e fusionados com 4D Desktop (nos quais não há acesso ao ambiente Desenho). Para maior informação sobre o número de porta TCP, consulte a seção *Web Server Settings*.



### Character set (17)

**Alcance**: 4D local, 4D Server

**Se conserva entre duas sessões**: sim**

Descrição:** Constante obsoleto (mantido apenas para compatibilidade). Agora nós recomendamos usar os comandos [WEB SET OPTION](web-set-option.md) e [WEB GET OPTION](web-get-option.md) para a configuração do servidor HTTP.





### Max concurrent Web processes (18)

**Alcance:**  4D local, 4D Server

**Se conserva entre duas sessões**: sim **Valores**: todo valor entre 10 e 32 000\. O valor por padrão é 100.

**Descrição**:Constante obsoleta (se conserva por compatibilidade unicamente). Se recomenda utilizar os comandos [WEB SET OPTION](web-set-option.md) e [WEB GET OPTION](web-get-option.md) para a configuração do servidor HTTP.



### Client port ID (22)

**Alcance**: todas as máquinas 4D remotos

**Se conserva entre duas sessões**: sim

**Valores possíveis**: ver seletor 15

**Descrição**: permite especificar este parâmetro para todas as máquinas 4D remotas utilizadas como servidores web. Os valores definidos utilizando estes seletores se aplicam a todas as máquinas remotas utilizadas como servidores web. Se desejar definir valores apenas para certas máquinas remotas, utilize a caixa de diálogo de Preferências de 4D em modo remoto.



### Client character set (24)

**Alcance**: todas as máquinas 4D remotos

**Se conserva entre duas sessões**: sim

**Valores possíveis**: ver seletor 17

**Descrição**: permite especificar este parâmetro para todas as máquinas 4D remotos utilizadas como servidores web. Os valores definidos utilizando estes seletores se aplicam a todas as máquinas remotas utilizadas como servidores web. Se desejar definir os valores apenas para alguns remotos, utilize a caixa de diálogo de Preferências de 4D em modo remoto.



### Client max concurrent Web proc (25)

**Alcance**: todas as máquinas 4D remotas

**Se conserva entre duas sessões**: sim

**Valores possíveis**: ver seletor 18

**Descrição**: permite especificar este parâmetro para as máquinas 4D remotas utilizadas como servidores web. Os valores definidos utilizando estos seletores se aplicam a todas as máquinas remotas utilizadas como servidores web. Se desejar definir este valor apenas para certas máquinas remotas, utilize a caixa de diálogo de Preferências de 4D em modo remoto.





### Maximum Web requests size (27)

**Alcance**: 4D local, 4D Server

**Se conserva entre duas sessões**: sim

**Valores possíveis**: 500 000 a 2 147 483 648.

**Descrição**: Constante obsoleta (se conserva por compatibilidade unicamente). Se recomenda utilizar os comandos [WEB SET OPTION](web-set-option.md) e [WEB GET OPTION](web-get-option.md) para a configuração do servidor HTTP.



### 4D Server log recording (28)

**Thread-safe** : Yes

**Alcance**: 4D Server, 4D remoto*

* Se conserva entre duas **sessões**: não

 **Valores** **possíveis**: 0 ou de 1 a X (0 = não grava, 1 a X = número sequêncial, adicionado ao nome do arquivo).

**Descrição**: inicia ou para a gravação das petições padrão recebidas por 4D Server (excluindo as petições web). Por padrão, o valor é 0 (não são gravadas as petições).

4D Server lhe permite gravar cada petição recebida pela máquina servidora em um arquivo de histórico. Quando este mecanismo estiver ativo, o arquivo de histórico for criado junto ao arquivo de estrutura do banco. Seu nome é "4DRequestsLog\_X," onde X é o número sequêncial do histórico. Quando o arquivo alcançar um tamanho de 10 MB, ele se fecha e é gerado um novo arquivo, com um número sequêncial incrementado. Se existir um arquivo com o mesmo nome, ele é substituído diretamente. Pode definir o número de início da sequência utilizando o parâmetro *valor*.

Este arquivo texto armazena em formato tabulado simples diferente informações sobre cada petição: hora, número de processo, usuário, tamanho da petição, duração do processo, etc. Esta informação pode ser útil particularmente durante a fase de afinamento da aplicação ou com fins estatísticos. Por exemplo pode ser importado, em um software de folha de cálculo para ser processado.



### Client Web log recording (30)

**Alcance**: todas as máquinas 4D remotos

**Se conserva entre duas sessões**: sim

**Valores possíveis**: 0 = Não gravar (por padrão), 1 = Registrar em formato CLF, 2 = Registrar em formato DLF, 3 = Registrar em formato ELF, 4 = Registrar em formato WLF.

**Descrição**: inicia ou para a gravação das petições web recibidas pelos servidores web de todas as máquinas cliente. Por padrão, o valor é 0 (não se gravam as petições).

O funcionamento deste seletor é idêntico ao do seletor 29; entretanto, aplica a todas as máquinas 4D remotas utilizados como servidores web. O arquivo "logweb.txt", neste caso, automaticamente que fica na subpasta Logs do banco 4D remoto (pasta de cache). Se desejar definir os valores unicamente para certas máquinas cliente, utilize a caixa de diálogo de Preferências de 4D em modo remoto.



### Table sequence number (31)

**Alcance**: aplicação 4D**Se conserva entre duas sessões**: sim**Valores possíveis**: todo valor de tipo inteiro longo.**Descrição**: este seletor se utiliza para modificar ou modificar ou obter o número único atual dos registros da tabela passada em parâmetro. "Número atual" significa "último número utilizado": se modificar este valor utilizando [SET DATABASE PARAMETER](set-database-parameter.md "SET DATABASE PARAMETER"), o registro abaixo será o valor passado + 1\. Este novo número é o número devolvido pelo comando Sequence number assim como em todo campo da tabela a qual se atribui a propriedade "Autoincrementar" no editor de estrutura ou através de SQL.Por padrão, este número único é definido por 4D e corresponde à ordem de criação dos registros. Para informação adicional, por favor consulte a documentação do comando [Sequence number](sequence-number.md "Sequence number").



### Debug log recording (34)

**Thread-safe** : Yes

**Alcance**: Aplicação 4D

**Conservar entre duas sessões**: Não

**Descrição**: Inicia ou detém a gravação sequencial dos eventos a nível de programação de 4D no arquivo DDebugLog\[\_n\].txt ou 4DDebugLogServer\[\_n\].txt (onde \_n é o número de segmento do arquivo e Server é adicionado ao nome do arquivo quando for gerado no servidor). 

Dois modos estão disponíveis:

- Modo Standard oferece uma visão básica de eventos e o arquivo é colocado automaticamente na subpasta Logs do banco de dados, do lado do arquivo estrutura. Tempos de execução são expressos em milissegundos com o valor "< ms" exibido quando uma operação durar menos que um milissegundo. 

- Modo tabbed fornece informação adicional e usa um formato mais compacto no arquivo. Tempos de execução são expressos em microssegundos **Valores possíveis**: Inteiro longo contém um campo de bits: valor = bit1(1)+bit2(2)+bit3(4)+bit4(8)+…). \- Bit 0 (valor 1) permite ativar o arquivo (note que qualquer outro valor não nulo também o ativará)

- Bit 1 (valor 2) permite solicitar os parâmetros de chamada aos métodos e comandos.

- Bit 2 (valor 4) permite ativar o novo formato tabulado.

- Bit 3 (valor 8) permite desativar a escritura imediata de cada operação no disco (ativado por padrão). A escritura imediata é mais rápida e mais eficaz por exemplo para buscar as causas de uma falha. Se desativa este modo, o conteúdo do arquivo será mais compacto e será gerado de forma mais rápida.

- Bit 4 (valor 16) desativa o registro de chamadas de plug-ins (ativado por padrão).

- Bit 5 (valor 32) desativa a função de logging dos membros. Exemplos:

SET DATABASE PARAMETER (34;1) // ativa o arquivo modo v13 sem os parâmetros, com as durações

SET DATABASE PARAMETER (34;2) // ativa o arquivo modo v13 com os parâmetros e as durações

SET DATABASE PARAMETER (34;2+4) // ativa o arquivo ao formato v14 com os parâmetros e as durações

SET DATABASE PARAMETER (34;0) // desativa o arquivo

Para evitar que o arquivo registre muita informação, pode restringir os comandos 4D a examinar com o seletor 80, Log Command list.

Para todo tipo de aplicação 4D interpretada ou compilada (4D todos os modos, 4D Server, 4D Volume Desktop), pode evitar criar um arquivo de regisotro com muita informação com:

-restrição de comandos 4D que são examinados usando Log command list (selector 80), ou

-restrição do processo atual com Current process debug log recording (selector 111). Isso vai adicionar a letra "p" e o número de processo ao nome de arquivo: 4DDebugLog\[\_pn\_n\].txt ou 4DDebugLogServer\[\_pn\_n\].txt Para saber mais sobre esse formato e o uso do arquivo 4DDebugLog, veja a seção *Descrição de arquivos de log* **Nota**: Esta opção se oferece unicamente com fins de depuração e deve ser utilizada com cuidado já que pode afetar o rendimento da aplicação.



### Client Server port ID (35)

**Alcance**: banco de dados

**Se conserva entre duas sessões**: sim

**Valores possíveis**: 0 a 65535

**Descrição**: número de porta TCP onde o servidor 4D publica o banco de dados (para conexão remota 4D). Por padrão, o valor é 19813.

A personalização deste valor permite utilizar várias aplicações 4D cliente-servidor na mesma máquina com o protocolo TCP; neste caso, deve indicar um número de porta diferente para cada aplicação.

O valor se guarda no arquivo de estrutura do banco. Pode definir-se com 4D em modo local mas apenas se leva em consideração na configuração cliente servidor.

Quando modifica este valor, é necessário reiniciar a máquina servidor para que o novo valor seja levado em consideração.



### HTTPS Port ID (39)

**Alcance**: 4D local, 4D Server

**Se conserva entre duas sessões**: sim

**Descrição**: Constante obsoleta (se conserva por compatibilidade unicamente). Se recomenda utilizar os comandos [WEB SET OPTION](web-set-option.md) e [WEB GET OPTION](web-get-option.md) para a configuração do servidor HTTP.



### Client HTTPS port ID (40)

**Alcance**: todas as máquinas 4D remotos**Se conserva entre duas sessões**: sim**Valores possíveis**: 0 ate 65535**Descrição**: numero da porta TCP usada pelos servidores web das máquinas clientes para conexões seguras via SSL (protocolo HTTPS). Por padrão, o valor é 443 (valor estândar).Este seletor pode ser usado para modificar por programação a porta TCP usada pelos servidores web das máquinas clientes para as conexões seguras via SSL (protocolo HTTPS). Por padrão, o valor é 443 (valor estândar).Este seletor funciona exatamente igual que o seletor 39; contudo, aplica para todas as máquinas 4D remotas usadas como servidores web. Se somente quiser modificar o valor de certas máquinas clientes, use a caixa de diálogo de preferências de 4D remoto.





### SQL Autocommit (43)

**Alcance**: banco de dados

**Se conserva entre duas sessões**: sim

**Possíveis valores**: 0 (desativação) ou 1 (ativação)

**Descrição**: ativação ou desativação do modo SQL auto-commit. Por padrão, o valor é 0 (modo desativado)

O modo auto-commit permite reforçar a integridade referencial do banco. Quando este modo estiver ativo, as petições SELET, INSERT, UPDATE e DELETE (SIUD) são incluídas automaticamente nas transações quando não tiver sido executado dentro de uma transação. Este modo igualmente pode ser definido nas Preferências do banco.



### SQL Engine case sensitivity (44)

**Alcance**: banco de dados

**Se conserva entre duas sessões**: sim

**Valores possívei**s: 0 (não se leva em consideração as maiúsculas e minúsculas) ou 1 (sensível às maiúsculas e minúsculas)

**Descrição**: ativação ou desativação da sensibilidade a maiúsculas e minúsculas para comparações de strings efetuadas pelo motor SQL.

Por padrão, o valor é 1 (sensível às maiúsculas e minúsculas): o motor SQL diferencia entre maiúsculas e minúsculas ao comparar strings (ordenações e pesquisas). Por exemplo “ABC”= “ABC” mas “ABC” # “Abc.” Em alguns casos, por exemplo para alinhar o funcionamento do motor SQL com o do motor 4D, poderia querer que as comparações de strings não levem em consideração as maiúsculas e minúsculas (“ABC”=“Abc”).

Esta opção também pode ser definida na página SQL/Configuração das Preferências da aplicação.





### Client log recording (45)

**Alcance**: máquina 4D remoto

**Se conserva entre duas sessões**: não

**Valores possíveis**: 0 ou de 1 a X (0 = não gravar, 1 a X = número sequêncial, associado ao nome do arquivo).

**Descrição**: inicia ou para a gravação de petições padrão efetuadas pela máquina cliente 4D que executou o comando (excluindo as petições web). Por padrão, o valor é 0 (não são gravadas as petições).

4D lhe permite registrar o histórico de petições realizadas pela máquina cliente. Quando este mecanismo for ativado, são criados dois arquivos na máquina cliente, na subpasta Logs da pasta local do banco. São chamados 4DRequestsLog\_X e 4DRequestsLog\_ProcessInfo\_X, onde X é o número sequêncial do histórico. Quando tiver o arquivo 4DRequestsLog alcança um tamanho de 10 MB, é fechada e se gera um novo, com um número sequêncial incrementado. Se já existir um arquivo com o mesmo nome, se substitue diretamente. Pode definir o número de início para a sequência utilizando o parâmetro valor.

Estes arquivos texto armazenam em formato tabulado simples diferente informação relacionada com cada petição: hora, número de processo, tamanho da petição, duração do processo, etc. Esta informação é particularmente útil durante a fase de desenvolvimento da aplicação ou com fins estatísticos.





### Query by formula on server (46)

**Alcance**: tabela e processos atuais

**Se conserva entre duas sessões**: não

**Valores possíveis**: 0 (utilizar a configuração da banco), 1 (executar em cliente) ou 2 (executar em servidor)

**Descrição**: localização da execução dos comandos QUERY BY FORMULA e QUERY SELETION BY FORMULA para a tabela passada em parâmetro.

Quando utilizar um banco em modo cliente-servidor, os comandos de pesquisa "por fórmula" podem ser executados no servidor ou na máquina cliente:

em bancos criados com 4D v11 SQL, estes comandos são executados no servidor.em bancos convertidos, estes comandos são executados na máquina cliente, como nas versões anteriores de 4D.nos bancos convertidos, uma preferência específica permite modificar globalmente a localização de execução de estes comandos.Esta diferença em localização de execução influi não apenas no rendimento da aplicação (a execução no servidor é geralmente mais rápida) mas também na programação. Na verdade, o valor dos componentes da fórmula (em particular as variáveis chamadas através de um método) varía de acordo ao contexto de execução. Pode utilizar este seletor para adaptar pontualmente o funcionamento de sua aplicação.

Se passar 0 no parâmetro valor, a localização de execução dos comandos de pesquisa "por fórmula" dependerá da configuração do banco: em bancos criados com 4D v11 SQL, estes comandos serão executados no servidor. Em bancos convertidos, serão executados na máquina cliente ou no servidor em função das preferências do banco. Passe 1 ou 2 em valor para "forçar" a execução destes comandos respectivamente na máquina cliente ou no servidor. Consulte o exemplo 2.



**Nota**: se desejar ativar as uniões "tipo SQL" (consulte o seletor QUERY BY FORMULA Joins seletor), sempre deve executar as fórmulas no servidor de maneira que tenham acesso aos registros. Atenção, neste contexto, a fórmula não deve conter chamadas a um método, do contrário passará automaticamente a máquina remoto



### Order by formula on server (47)

**Alcance**: tabela e processos atuais

**Se conserva entre duas sessões**: não

**Valores possíveis**: 0 (utilizar a configuração da banco), 1 (executar no cliente) ou 2 (executar no servidor)

**Descrição**: localização da execução do comando ORDER BY FORMULA para a tabela passada em parâmetro.

Ao utilizar um banco em modo cliente-servidor, o comando ORDER BY FORMULA pode ser executado seja na máquina servidor ou no cliente. Este seletor pode ser utilizado para especificar a localização da execução deste comando (servidor ou cliente). Este modo também pode ser definido nas preferências do banco. Para maior informação, consulte a descrição do seletor 46, Query By Formula On Server.



**Nota**: se desejar ativar as uniões "tipo SQL" (consulte o seletor QUERY BY FORMULA Joins seletor), sempre deve executar as fórmulas no servidor de maneira que tenhan acesso aos registros. Atenção, neste contexto, a fórmula não deve conter chamadas a um método, do contrário passará automaticamente a máquina remota.



### Auto synchro resources folder (48)

**Alcance**: máquina 4D remota

**Se conserva entre duas sessões**: não

**Valores possíveis**: 0 (sem sincronização), 1 (auto sincronização) ou 2 (perguntar).

**Descrição**: modo de sincronização dinâmico da pasta Resources do máquina cliente 4D que executa o comando com o servidor.

Quando o conteúdo da pasta Resources no servidor tiver sido modificado ou um usuário ha solicitado a sincronização (por exemplo através o explorador de recursos ou seguindo a execução do comando NOTIFY RESOURCES FOLDER MODIFICATION), o servidor notifica a os máquinas cliente conetados.

Três modos de sincronização são possíveis do lado do cliente. O seletor Auto Synchro Resources Folder é utilizado para especificar o modo a utilizar pela máquina cliente para a sessão atual:

0 (valor por padrão): sem sincronização dinâmica (a petição de sincronização é ignorada)1: sincronização dinâmica automática 2: visualização de uma caixa de diálogo nos máquinas clientes, com a possibilidade de realizar ou recusar a sincronização.O modo de sincronização também pode definirse globalmente nas Preferências da aplicação.





### Query by formula joins (49)

**Alcance**: Processo atual

**Se conserva entre duas sessões**: não

**Valores possíveis**: 0 (utilizar configuração da banco), 1 (sempre utilizar relações automáticas) ou 2 (utilizar as uniões SQL se for possível).

**Descrição**: modo de funcionamento dos comandos QUERY BY FORMULA e QUERY SELETION BY FORMULA relativos ao uso de "uniões SQL."

Nos bancos de dados criados a partir da versão 11.2 de 4D v11 SQL, estes comandos realizam uniões baseadas no modelo de uniões SQL. Este mecanismo permite modificar a seleção de uma tabela em função de uma pesquisa efetuada em outra tabela sem que as tabelas estejam conectadas por uma relação automática (condição necessária nas versões anteriores de 4D).

O seletor QUERY BY FORMULA Joins permite definir o modo de funcionamento dos comandos de pesquisa por fórmula para o processo atual:



0: Utilizar os parâmetros atuais do banco (valor por padrão). Em bancos criados a partir da versão 11.2 de 4D v11 SQL, as "uniões SQL" sempre se ativam para as pesquisas por fórmula. Em bancos de dados convertidos, este mecanismo não se ativa por padrão por razões de compatibilidade mas pode ser implementado através de uma preferência.1: Sempre utilizar relações automáticas (= funcionamento de versões anteriores de 4D). Neste modo, uma relação é necessária para definir a seleção de uma tabela em função de pesquisas efetuadas em outra tabela. 4D não realiza mais "uniões SQL."2: Utilizar as uniões SQL se for possível (= funcionamento ou padrão dos bancos criados em versão 11.2 e superiores de 4D v11 SQL). Neste modo, 4D estábelece "uniões SQL" para as pesquisas por fórmula quando a fórmula se ajustar para isso (com duas exceções, ver a descrição do comando QUERY BY FORMULA ou QUERY SELETION BY FORMULA).**Nota**: se desejar ativar as uniões "tipo SQL" (consulte o seletor QUERY BY FORMULA Joins seletor), sempre deve executar as fórmulas no servidor de maniera que tenham acesso aos registros. Atenção, neste contexto, a fórmula não deve conter chamadas a um método, do contrário passará automaticamente a máquina remoto



### HTTP compression level (50)

**Alcance**: aplicação 4D

**Se conserva entre duas sessões**: não

**Valores possíveis**: 1 a 9 (1 = mais rápido, 9 = mais comprimido) ou -1 = o mejor compromiso.

**Descrição**: nível de compressão para todos os intercambios HTTP comprimidos efetuados para os serviços web (petições cliente ou respostas servidor). Os intercâmbios comprimidos são uma otimização que pode implementar quando tiver duas aplicações 4D que se comunicam através serviços web (ver o comando *SET WEB SERVICE OPTION*). Este seletor lhe permite otimizar os intercâmbios n seja privilegiando a velocidade de execução (menor compressão) ou a quantidade de compressão (menor velocidade). A escolha de um valor depende do tamanho e da natureza dos dados intercambiados. Passe de 1 a 9 no parâmetro valor onde 1 é a compressão mais rápida e 9 a mais alta. Também pode passar -1 para obter um compromisso entre velocidade e taxa de compressão. Por padrão, o nível de compressão é 1 (compressão rápida).

 







### HTTP compression threshold (51)

**Alcance**: aplicação 4D

**Se conserva entre duas sessões**: não

**Valores possíveis**: todo valor de tipo inteiro longo

**Descrição**: Constante obsoleta (se conserva por compatibilidade unicamente). Se recomenda utilizar os comandos [WEB SET OPTION](web-set-option.md) e [WEB GET OPTION](web-get-option.md) para a configuração do servidor HTTP.



### Server base process stack size (53)

**Alcance**: 4D Server

**Se conserva entre duas sessões**: não

**Valores possíveis**: inteiro longo positivo.

**Descrição**: tamanho da pilha atribuída a cada processo do sistema preferente no servidor, expresso em bytes. O tamanho por padrão é determinado pelo sistema.

Os processos sistema preferente (processos de tipo Processo banco 4D client) são carregados para controlar os processos cliente 4D principais. O tamanho atribuído por padrão à pilha de cada processo preferente da facilidade de execução mas pode resultar consequente quando for criada um grande número de processos (várias centenas).

Por razões de otimização, este tamanho pode ser reduzido consideravelmente se as operações efetuadas pelo banco o permitirem (por exemplo se o banco não realizar ordenações de grandes quantidades de registros). São possíveis valores de 512 ou mesmo 256 KB. Seja cuidadoso, subdimensionar a pilha é critico e pode afetar a operação de 4D Server. A definição deste parâmetro deve ser feita com precaução e levar em consideração as condições de uso do banco (número de registros, tipo de operações, etc.).

Para que seja levado em consideração, este parâmetro deve ser executado na máquina servidor (por exemplo no método de banco On Server Startup).





### Idle connections timeout (54)

**Alcance**: aplicação 4D a menos que valor seja negativo

**Se conserva entre duas sessões**: não

**Valores possíveis**: valor inteiro que expressa uma duração em segundos. O valor pode ser positivo (novas conexões) ou negativo (conexões existentes). Por padrão, o valor é 0 (não timeout) com 4D v11 SQL e 20 com 4D v12.

**Descrição**: do lado do servidor, máximo periodo de inatividade (timeout) para conexões ao motor de banco de dados 4D e ao motor SQL. Quando uma conexão inativa alcançar este limite, se coloca em espera automaticamente, o que congela a sessão cliente/servidor e fecha o socket de red. Este funcionamento é totalmente transparente para o usuário: logo que houver uma nova atividade na conexão que está em espera, o socket se reabre automaticamente e a sessão cliente/servidor se restaura.

Este parâmetro permite, por um lado, economizar os recursos no servidor: as conexões em espera fechan o socket e liberam um processo no servidor. Por outro lado, isso lhe permite evitar perda de conexões pelo fechamento de sockets por parte do firewall. Por esta razão, o valor do timeout para conexões inativas deve ser menor que a da firewall neste caso.

Se passar um valor positivo em valor, se aplicará a todas as novas conexões em todos os processos. Se passar um valor negativo, se aplicará as conexões que se abrem no processo atual. Se passar 0, as conexões inativas não serão submetidas a um timeout.

Este parâmetro pode ser definido do lado do cliente. Geralmente, não necessita modificar este valor.



### PHP interpreter IP address (55)

**Alcance**: Aplicação 4D

**Se conserva entre duas sessões**: Não

**Valores**: string formateada do tipo "nnn.nnn.nnn.nnn" (por exemplo "127.0.0.1").

**Descrição**: endereço IP utilizado localmente por 4D para se comunicar com o intérprete PHP através FastCGI. Por padrão, o valor é "127.0.0.1". Esta endereço deve corresponder à máquina onde se encontra 4D. Este parâmetro também pode ser definido globalmente para todas as máquinas através das Propriedades do banco.

Para maior informação sobre o intérprete PHP, por favor consulte o manual de Desenho.



### PHP interpreter port (56)

**Alcance**: Aplicação 4D

**Conservado entre duas sessões**: No

**Valores**: valor de tipo inteiro longo positivo. Por padrão, o valor é 8002.

**Descrição**: número de porta TCP utilizado ou pelo intérprete PHP de 4D. Este parâmetro também pode ser modificado globalmente para todas as máquinas através das Propriedades do banco. Para maior informação sobre o intérprete PHP, consulte o manual de Desenho





### SSL cipher list (64)

**Alcance**: Aplicação 4D

**Se conserva entre duas sessõe**s: Não

**Valores possíveis**: sequência de strings separadas por dois pontos.

**Descrição**: lista de cifrado (cipher list) utilizada por 4D para o protocolo seguro. Esta lista modifica a prioridade dos algoritmos de cifrado implementados por 4D. Por exemplo, pode passar a seguinte cadeia no parâmetro valor:

"HIGH:!aNULL:!MD5:!3DES:!CAMELLIA:!AES128:!RSA:!DH:!RC4". Para uma descrição completa da sintaxe para a lista cifrada, consulte a página de cifrado do site *OpenSSL*.

Este parâmetro se aplica ao servidor Web principal (excluindo objetos servidor Web), o servidor SQL, conexões cliente/servidor, e também ao cliente HTTP e a todas as funções 4D que usam o protocolo seguro. Étemporário (não se conserva entre sessões).

Quando a lista de cifrado tiver sido modificada, deve reiniciar o servidor correspondente para que os novos parâmetros sejam levados em consideração.

Para reinicializar a lista de cifrado a seu valor por padrão (guardado permanentemente no arquivo SLI), chame o comando [SET DATABASE PARAMETER](set-database-parameter.md) e passe uma string vazia ("") no parâmetro valor.



**Nota**: com o comando [Get database parameter](get-database-parameter.md), a lista de cifrado é retornada no parâmetro opcional valorAlfa e o parâmetro de retorno é sempre 0.



### Cache unload minimum size (66)

**Alcance**: Aplicação 4D

**Se conserva entre duas sessões**: Não

**Valores possíveis**: Inteiro longo positivo > 1.

**Descrição**: tamanho mínimo de memória a liberar do cache da banco de dados quando o motor necesita criar espaço para botar um objeto (valor em bytes).

O propósito deste seletor é reduzir o número de liberações de dados da cache com o objetivo de obter um melhor rendimento. Pode fazer variar este parâmetro em função do tamanho da cache e dos blocos de dados manipulados em seu banco.

Por padrão, se este seletor não for utilizado, 4D descarrega mínimo 10% da cache em caso de que necessite espaço.



### Direct2D status (69)

**Alcance**: aplicação 4D

**Se conserva entre duas sessões**: Não

**Descrição**: modo de ativação de Direct2D em Windows.

**Valores possíveis**: uma das constantes abaixo (modo 3 padrão):

Direct2D Disabled (0): o modo Direct2D não está habilitado e o banco de dados funciona no modo anterior (GDI/GDIPlus).

Direct2D Hardware (1): utilize Direct2D como contexto de hardware de gráficos para toda a aplicação 4D. Se este contexto não estiver disponíveis, use o contexto do software de gráficos Direct2D.

Direct2D Software (3) (modo pré-determinado): a partir de Windows 7, utilize o contexto de software de gráficos Direct2D para toda a aplicação 4D.

***Advertência* : este seletor se proporciona só para fins de depuração. Dado que várias funções 4D se baseiam em Direct2D, não deve ser desativado nas aplicações implementadas. Só o modo pré-determinado (Direct2D Software)* **está aprovado para as aplicações lançadas.*



### Direct2D get active status (74)

**Nota**: somente pode usar este seletor com o comando GET DATABASE PARAMETER e o seu valor não pode ser definido.**Descrição**: retorna a implementação ativa do Direct2D sob Windows.**Valores possíveis**: 0, 1, 2, 3, 4 ou 5 (ver os valores do seletor 69). o valor retornado depende da disponibilidad de direct2D, do hardware e da qualidade Direct2D suportado pelo sistema operativo.por exemplo, se executar: SET DATABASE PARAMETER(Direct2D status;Direct2D Hardware)$mode:=Get database parameter(Direct2D get active status)\- No Windows 7 e superiores, mode vale 1 quando o sistema detecta um hardware compatível com Direct2D; do contrário, $mode terá o valor 3 (contexto software).\- No Windows Vista, $mode terá o valor 1 se o sistema detecta um hardware compatível com Direct2D; do contrário, $mode terá o valor 0 (desativando Direct2D).\- No Windows XP, $mode sempre terá valor 0 (não compatível com Direct2D).844217



### Diagnostic log recording (79)

**Thread-safe** : Yes

**Alcance**: Aplicação 4D

**Se conserva entre duas sessões**: Não

**Valores possíveis**: 0 ó 1 (0 = sem salvar,1 = salvar)

**Descrição:** iniciar ou parar gravação de arquivos de diagnóstico do 4D. O valor padrão é 0 (sem registro).

4D permite gravar continuamente em um arquivo de diagnóstico de um conjunto de eventos relacionados com o funcionamento interno da aplicação. As informações contidas neste arquivo é destinado para o desenvolvimento de aplicações 4D e podem ser analisados com a ajuda de serviços técnicos 4D. Quando você coloca 1 em este seletor, o arquivo de diagnóstico chamado *NomBase.txt*, é criado automaticamente (ou aberto) na pasta **Logs** do banco de dados. Depois que o arquivo atinge um tamanho de 10 MB, ele é fechado e um novo arquivo é gerado *NomBase\_N.txt* com um número de sequência incrementado N.

Note que é possível incluir informações personalizadas no arquivo usando o comando[LOG EVENT](log-event.md "LOG EVENT").







### Log command list (80)

**Alcance**: Aplicação 4D

 **Se conserva entre duas sessões**: Não

 **Valores possíveis**: uma string contendo a lista de números de comandos 4D a gravar (separados por ponto e vírgula), "todos" para salvar todos os comandos ou "" (string vazia) para no gravar não comando.

 **Descrição:** Lista de comandos 4D para salvar no arquivo de depuração (ver seletor de 34, Debug Log Recording). Por padrão, todos os comandos 4D são registrados.

Este seletor permite que você restrinja a quantidade de informação armazenada no arquivo de depuração, limitando os comandos 4D que você deseja salvar o desempenho.

 





### Spellchecker (81)

**Alcance:** Aplicação 4D**

 Conservar entre duas sessões**: Não

 **Valores possíveis**: 0 (por padrão) = corretor macOS nativo (Hunspell desativado), 1 = corretor Hunspell ativo. 

**Descrição**: Permite ativar o corretor ortográfico Hunspell sob macOS. Por padrão, nesta plataforma o corretor nativo está ativo. Pode preferir utilizar o corretor Hunspell, por exemplo, para unificar a interface de suas aplicações multiplataformas (sob Windows, só o corretor Hunspell está disponível). Para maior informação, consulte *Correção ortográfica*.



### Dates inside objects (85)

**Alcance**: Processo atual

 **Conservar entre duas sessões:** Não**

 Valores possíveis**: String type without time zone (0), String type with time zone (1), Date type (2) (default)



**Descrição**: Define a maneira como as datas são armazenadas dentro de objetos, assim a maneira como elas serão importadas/exportadas em JSON. Quando o valor do seletor for Date type (valor padrão para bancos de dados criados com 4D v17 e superior) datas 4D são armazenadas com o tipo data dentro de objetos, com respeito às configurações de data locais. Quando converter para formato JSON, atributos de data são convertidos a strings que não incluem uma hora. (Nota: essa configuração pode ser estabelecida através da opção "Use data type instead of ISO date format in objects" encontrada em *Página Compatibilidade* das Configurações de Banco de Dados).



Passar String type with time zone nesse seltor converte datas 4D em strings ISO e leva em conta a zona horária local. Por exemplo, a conversão da data 23/08/2013 dá "2013-08-22T22:00:00Z" em formato JSON quando a operação se realiza na França durante o horário de verão (GMT +2). Este princípio se ajusta a operação padrão de JavaScript.

Este funcionamento pode ser uma fonte de erros se deseja enviar valores de data em JSON a uma pessoa que se encontra em uma zona horária diferente. Este é o caso, por exemplo, ao exportar uma tabela usando [Selection to JSON](selection-to-json.md) em França que está destinado a ser importada para os E.U.A com [JSON TO SELECTION](json-to-selection.md). Por padrão, as datas retornam a ser interpretadas em cada fuso horário, os valores armazenados na base serão diferentes. Neste caso, pode modificar o modo de conversão de datas para que não se leve em conta o fuso horário ao passar 0 no seletor. A conversão da data 23/08/2013 logo lhe dará "2013-08-23T00:00:00Z" em todos os casos.



### Diagnostic log level (86)

**Thread-safe** : Yes

**Alcance**: Aplicação 4D

**Se conserva entre duas sessões**: Não

**Descrição**: nivel das mensagens que serão incluiídas no registro de diagnóstico quando esteja habilitado (ver seletor Diagnostic log recording). Cada nivel designa uma categoria de mensagens de diagnóstico e inclui automaticamente as categorias mais importantes. Para uma descrição das categorias, consulte a seção *Niveis de registro de diagnóstico* em *developer.4d.com*. 

**Valores possíveis**: uma das seguintes constantes (Log info por padrão): Log trace: ativa ERROR, WARN, INFO, DEBUG, TRACE (nivel mais detalhado) Log debug: ativa ERROR, WARN, INFO, DEBUG Log info: ativa ERROR, WARN, INFO (por padrão) Log warn: ativa ERROR, WARN Log error: ativa ERROR (nivel menos detalhado)



### Use legacy network layer (87)

**Alcance:** 4D em modo local, 4D Server**

Se conserva entre duas sessões:** sim**

** **Descrição:** fixa ou obtém o estado atual da capa de rede antiga para as conexões cliente/servidor. 

A capa de rede antiga é obsoleta a partir de 4D v14 R5 e deve ser substituída progressivamente em suas aplicações pela capa de rede   *ServerNet*. *ServerNet* será requerida em próximas versões 4D com o propósito de se beneficiar das futuras evoluções da rede. Por razões de compatibilidade, a capa de rede antiga ainda é suportada para permitir uma transição sem problemas para as aplicações existentes; (se usar por padrão em aplicações convertidas de uma versão anterior a v14 R5). Passe 1 neste parâmetro para utilizar a capa de rede antiga (e desativar *ServerNet*) para as conexões cliente/servidor, e passe 0 para desabilitar a rede antiga (e utilizar *ServerNet*).

Esta propriedade também pode ser definida mediante a opção "Usar capa de rede antiga " que se encontram em *Página Compatibilidade* das Propriedades da base (ver *Preferências de configuração*). Nesta seção, também pode encontrar uma discussão sobre a estratégia de migração. Lhe recomendamos que ative *ServerNet* o mais rápido possível.

Deverá reiniciar a aplicação para que este parâmetro seja levado em conta. Não está disponível em 4D Server v14 R5 64-bit versão para macOS, que só suporta o *ServetNet*; (sempre devolve 0).

**Valores possíveis**: 0 ou 1 (0 = não utilizam capa de rede antiga, 1 = uso capa de rede antiga)

**Valor por padrão:** 0 em bases de dados criadas com 4D v14 R5 ou superior, 1 em bases de dados convertidas de 4D v14 R4 ou anteriores.



### SQL Server Port ID (88)

**Alcance**: 4D modo local e 4D Server.

: Sim

**Descrição**: permite ler ou definir o número da porta TCP utilizada pelo servidor SQL integrado de 4D em modo local ou 4D Server. Por padrão, o valor é 19812\. Quando se define este seletor, a configuração da base se atualiza. Também pode definir o número da porta TCP na página "SQL" da caixa de diálogo de Propriedades da base.

**Valores possíveis:** 0 a 65535.

**Valor por padrão:** 19812



### Circular log limitation (90)

**Thread-safe** : Yes

**Alcance**: 4D local, 4D Server.

**É conservado entre duas sessões**: não

**Valores possíveis**: qualquer valor inteiro, 0 = conservar todos os registros

**Descrição**: número máximo de arquivos a conservar em rotação para cada tipo de registro. Como padrão, todos os arquivos são conservados. Se passar um valor X, só os X arquivos mais recentes são conservados, o mais antigo é apagado automaticamente quando se cria um novo. Este ajuste é aplicado a a cada um dos seguintes arquivos de registro: registros de petições (seletores 28 e 45), registro de depuração (seletor 34), registro de eventos (seletor 79), assim como o histórico de petições web e o histórico de depuração Web (seletores 29 e 84 do comando [WEB SET OPTION](web-set-option.md)).



### Number of formulas in cache (92)

**Alcance**: aplicação 4D

**Se conserva entre duas sessões:** não

**Valores possíveis**: inteiros longos positivos

**Valor padrão**: 0 (sem cache) 

**Descrição**: estabelece ou obtém o número máximo de fórmulas a conservar na memória cache de fórmulas, que é utilizado pelo comando [EXECUTE FORMULA](execute-formula.md). Este limite é aplicado a todos os processos, mas cada processo tem sua própria cache de fórmulas. Localizar as fórmulas na cache acelera a execução do comando [EXECUTE FORMULA](execute-formula.md) em modo compilado, já que cada fórmula em cache se tokeniza só uma vez neste caso.Quando se modifica o valor da memória cache, o conteúdo existente se restabelece mesmo se o novo tamanho for maior que o anterior. Quando for alcançado o número máximo de fórmulas na memória cache, uma nova fórmula executada apagará a mais antiga da memória cache (modo FIFO). Este parâmetro só é levado em consideração nos bancos de dados ou componentes compilados.



### OpenSSL version (94)

**Escopo**: todas as máquinas 4D*

* **Mantido entre sessões**: Não

**Descriçãop**: Retorna o número de versão da biblioteca OpenSSL em uso na máquina. (Apenas leitura)



### Cache flush periodicity (95)

**Thread-safe** : Yes


**Alcance**: 4D local, 4D Server

**Mantido entre duas sessões**: Não

**Valores possíveis**: longint > 1 (segundos)

**Descrição**: Obtém ou estabelece a peridiocidade de esvaziamento da cache atual, expressa em segundos. Modificar este valor sobrepuja a opção **Flush Cache every X Seconds** em [XML DECODE](xml-decode.md) das configurações de Bancos de Dados para a sessão (não é armazenada nas configurações do Banco de Dados).



### Remote connection sleep timeout (98)

**Escopo**: Aplicação 4D Server

**Mantido entre duas sessões**: Não

**Valores possíveis**: LongInt Positivo

**Descrição**: Tempo de timeout de conexão remota em segundos. O padrão desse valor é 172800 (48 horas). 

O tempo para dormir é aplicado depois que a máquina rodando a aplicação 4D remote mudou para o modo de hibernação. Nesse caso, a sessão é mantido pelo Servidor 4D (vera descrição em ). O Servidor 4D verifica a cada 5 minutos se excedeu o timetout. Assim, o período maximo de hibernação permitido é *current sleep timeout + 300*. Em alguns casos, pode querer modificar o sleep timeout, por exemplo para destrancar registors/licençadas presos mais rapidamente.



### Tips enabled (101)

**Escopo**: aplicação 4D

**Se conserva entre duas sessões**: Não

**Valores possíveis**: 0 = conselhos desativados, 1 = conselhos ativados (predeterminado)

**Descrição**: define ou obtém o estado de visualização atual dos conselhos para a aplicação 4D. De forma predeterminada, as sugestões estão ativadas.

Lembre que este parâmetro define todos os conselhos 4D, ou seja, as mensages de ajuda de formulário e as sugestões de editor de modo Desenho.



### Tips delay (102)

**Alcance**: aplicação 4D

**Se conserva entre duas sessões**: Não

**Valores possíveis**: inteiro longo >= 0 (tics)

**Descrição**: atraso antes de que se mostrem as sugestões quando o cursor do mouse tenha sido detido em objetos com mensagens de ajuda adjuntos. O valor se expressa em tics (1/60 de segundo). O valor pre-determinado é 45 tics (0.75 segundos).



### Tips duration (103)

**Alcance**: aplicação 4D

**Se conserva entre duas sessões**: Não

**Valores possíveis**: inteiro longo \>= 60 (tics)

**Descrição**: duração máxima de visualização de uma sugestão. O valor se expressa em tics (1/60 de segundo). O valor predeterminado é 720 tics (12 segundos).



### Min TLS version (105)

**Escopo**: 4D Server, 4D Web Server e 4D SQL Server

**Mantido entre sessões**: Não

**Descrição**: Usado para especificar o nível de Transport Layer Security (TLS) , o que oferece criptografia e autenticação de dados entre aplicações e servidores. Os valores definidos são aplicados globalmente a capa de rede. Quando for modificado o servidor deve ser reiniciado para usar o novo valor. O protocolo mínimo padrão é TLSv1\_2.

**Valores possíveis**:

TLSv1\_0 \- TLS 1.0, introduzido em 1999 como uma atualização de SSL v3.0\. TLS 1.0 e SSL 3.0 não interoperamTLSv1\_1 \- TLS 1.1, introduzido em 2006 como uma atualização de TLS 1.0\. Melhorias incluem melhor segurança e manejo de erros.TLSv1\_2 \- TLS 1.2, introduzido em 2008 como uma atualização de TLS 1.1\. Melhorias incluem flexibilidade, compatibilidade adicional para criptografia autenticada, etc.**NOTA**: O plugin 4D Internet Commands usa uma capa de rede diferente, portanto esse seletor terá nenhum impacto na versão TLS.



### User param value (108)

**Escopo:** 4D local, 4D Server

**Mantido entre duas sessões:** Não

**Valores possíveis**: Qualquer string personalizada

**Descrição:** String personalizada passada de uma sessão para a próxima quando a aplicação 4D for reiniciada. Esse seletor é útil no contexto de testes de unidade automáticos que exigem que a aplicação reinicie com parâmetros diferentes. 

Quando usados com [SET DATABASE PARAMETER](set-database-parameter.md), define um novo valor que estará disponível dentro do novo banco de dados aberto depois que 4D for reiniciado manualmente ou usando os comandos [OPEN DATABASE](open-database.md)(\*), [OPEN DATA FILE](open-data-file.md), ou [RESTART 4D](restart-4d.md). Quando usados com [Get database parameter](get-database-parameter.md), obtém o valor do parâmetro de usuário disponível definido usando a linha de comando (ver *Interface da linha de comando*), o arquivo .4DLink (ver *Usar um arquivo 4DLink*), ou uma chamada a [SET DATABASE PARAMETER](set-database-parameter.md) durante a sessão anterior. (\*) se [SET DATABASE PARAMETER](set-database-parameter.md) estabelecer User param value antes da chamada a [OPEN DATABASE](open-database.md) com o arquivo .4DLink que também contém um atributo usuário param xml. 4D leva em consideração apenas o parâmetro fornecido por [SET DATABASE PARAMETER](set-database-parameter.md).



### Times inside objects (109)

Escopo: 4D local, 4D Server (todos os processos)

 Mantido entre sessões: Não

 **Valores possíveis**: Times in seconds (0) (padrão), Times in milliseconds (1) 

**Descrição**: Defina a maneira que os valores de tempo são convertidos e armazenados dentro das propriedades de objeto e elementos de coleção, e também como serão importados e exportados em JSON e áreas Web. Como padrão, a partir de 4D v17, valores de tempo são convertidos e armazenados como números de segundos em objetos.

Em versões anteriores, valores de tempo eram convertidos e armazenados como número de milissegundos nesses contextos. Usar este seletor pode ajudar a migrar suas aplicações ao reverter às configurações anteriores se necessário.

**Nota**: métodos ORDA e motores SQL ignoram esta configuração. Eles sempre assumem os valores de tempo como sendo em segundos



### SMTP Log (110)

**Thread-safe** : Yes

**Escopo**: 4D local, 4D Server*

* **Mantido entre sessões**: Não

 **Valores possíveis**: 0 ou de 1 a X (0 = não registra, 1 a X = número sequencial, adicionado ao nome de arquivo). Normalmente, o valor será 0 (trocas SMTP não registradas).

**Descrição**: Inicia ou para o registro de trocas entre 4D e o servidor SMTP, quando um objeto *transporter* for processado *transporter.send( )* ou *SMTP\_transporter.checkConnection( )*. Normalmente o valor é 0 (trocas não registradas). Quando este mecanismo for ativado, um arquivo de log é criado na pasta Logs no banco de dados. É nomeado 4DSMTPLog\_X.txt, onde *X* é o número sequencial do log. Uma vez que o arquivo 4DSMTPLog alcance um tamanho de 10 MB, ele é fechado e um outro é gerado, com um número sequencial incrementado. Se um arquivo de mesmo nome já existir, será substituido diretamente. Pode estabelecer o número inicial da sequência usando o parâmetro *value*. Normalmente todos os arquivos são mantidos, mas pode controlar o número de arquivos a manter usando o parâmetro Circular log limitation.

Para saber mais sobre arquivos 4DSMTPLog\_X.txt, veja *Descrição de arquivos de log*.



### Current process debug log recording (111)

**Escopo:** aplicação 4D 

**Mantido entre sessões:** Não

**Descrição**: Inicia ou para a gravação sequencial de eventos programáticos para **o processo atual** em um arquivo separado de histórico. Este histórico é similar a Debug log recording (selector 34) mas foca no processo atual apenas. O nome do arquivo de histórico inclui a letra "p" e o número de processo: 4DDebugLog\[\_p*N*_*n*].txt, onde N é a ID única de processo. 

Para saber mais sobre este formato e o uso de arquivo *4DDebugLog*, veja *Descrição de arquivos de log* na Referência de Design. 

**Notas:** Este seletor é fornecido apenas para o propósito de debugar e deve ser usado com cuidado. Em particular, não deve ser colocado na produção já que pdoe ter um impacto na performance da aplicação. Pode usar ambos os seletores Debug log recording e Current process debug log recording simultaneamente, e neste caso as ações do processo atual não serão logados no arquivo de histórico principal



### Is current database a project (112)

**Nota:** Só se pode usar este seletor com o comando [Get database parameter](get-database-parameter.md) e seu valor não pode ser estabelecido.

**Escopo**: aplicação 4D

**Descrição**: Retorna 1 se a arquitetura de banco de dados atual for um projeto, e 0 se não for. Para saber mais veja a seção *Bancos de dados Projeto vs Binários*.



### Is host database a project (113)

**Nota:** só se pode usar este seletor com o comando [Get database parameter](get-database-parameter.md) e seu valor não pode ser estabelecido.

**Escopo**: aplicação 4D

**Descrição**: Retorna 1 se a arqutetura de banco de dados for um projeto, 0 se não for. Para saber mais veja *Bancos de dados Projeto vs Binários*.



### Libldap version (114)

**Alcance**: máquina 4D atual 

**Se conserva entre duas sessões**: não

**Descrição**: devolve o número de versão da biblioteca LDAP na aplicação 4D na máquina atual. (Só leitura)



### Libsasl version (115)

**Alcance**: máquina 4D atual 

**Se conserva entre duas sessões**: não

**Descrição**: devolve o número de versão da biblioteca SASL na aplicação 4D na máquina atual. (Só leitura) 







### POP3 Log (116)

**Thread-safe** : Yes

**Alcance:** 4D local, 4D Server

**Se conserva entre duas sessões**: não

**Valores possíveis:** 0 ou de 1 a X (0 = não registrar, 1 a X = número sequencial, agregado ao nome de arquivo). Por padrão, o valor é 0 (intercambios POP3 não registrados).

: iInicia ou para a gravação de intercambios entre 4D e o servidor POP3, quando um objeto transportador se processa através de *POP3\_transporter.getMail( )* ou *POP3\_transporter.checkConnection( )*. Por padrão, o valor é 0 (intercambios não registrados). Quando este mecanismo estiver habilitado, se cria um arquivo de registro na pasta Logs do banco de dados. Se chama 4DPOP3Log\_X.txt, onde X é o número sequencial de registro. Quando o arquivo 4DPOP3Log tiver alcançado um tamanho de 10 MB, se fecha e se gera um novo, com um número sequencial incrementado. Se já existir um arquivo com o mesmo nome, se substitui diretamente. Pode estabelecer o número inicial da sequencia utilizando o parâmetro valor. De maneira predeterminada, todos os arquivos se mantém, mas pode controlar a quantidade de arquivos que se devem seguir utilizando o parãmetro Circular log limitation. 

Para mais informação sobre os arquivos 4DPOP3Log\_X.txt, consulte a seção *Descrição de arquivos de log*.



### Is host database writable (117)

**Nota:** só pode usar este seletor com o comando [Get database parameter](get-database-parameter.md) e seu valor não pode ser estabelecido.

**Escopo**: aplicação 4D

**Descrição**: Retorna 1 se o arquivo projeto/arquivo estrutura anfitirão for editável, e 0 se for apenas leitura



### IMAP Log (119)

**Thread-safe** : Yes

**Alcance**: 4D local, 4D Server

**Mantido entre sessões**: Não

**Valores possíveis**: 0 ou de1 a X (0 = não registrar, 1 a X = número sequencial, adicionado ao nome de arquivos). Como padrão, o valor é 0 (IMAP exchanges não registradas).

**Descrição**: Inicia ou para o registro de trocas entre 4D e o servidor IMAP, quando um objeto transportador for processado através de *IMAP\_transporter.getMail( )* ou *IMAP\_transporter.checkConnection( )*. Como padrão, o valor é 0 (trocas não registradas). Quando esse mecanismo estiver ativado, um arquivo de histórico é criado na pasta Logs do banco de dados. É chamada de 4DIMAPLog\_X.txt, onde X é o número sequencial do histórico. Quando o arquivo 4DIMAPLog alcançar um tamanho de 10MB, ele é fechado e outro arquivo é gerado, com um número incrementado sequencialmente. Se um arquivo do mesmo nome já existir, é substituido diretamente. Pode estabelecer o número inicial da sequência usando o parâmetro valor. Como padrão, todos os arquivos são mantidos, mas pode controlar o número de arquivos para manter usando o parâmetro Circular log limitation. Para saber mais informações sobre 4DIMAPLog\_X.txt, veja a seção *Descrição de arquivos de log*.



### Libzip version (120)

**Alcance**: máquina 4D atual

**Se conserva entre duas sessões**: n/a

**Descrição**: devolve o número de versão da biblioteca libzip na aplicação 4D na máquina atual. (Só leitura)



### Pause logging (121)

**Thread-safe** : Yes

**Escopo**: aplicação 4D

**Mantido entre duas sessões**: Não

**Valores possíveis**: 0 (continua históricos), 1 (pausa históricos)

Esse seletor permite suspender/retomar todas as operações de histórico iniciadas na aplicação (exceto históricos ORDA). Essa funcionalidade pode ser útil para aliviar temporariamente a aplicação 4D ou agendar operações de histórico.





## seletores Thread-seguro 

O comando **Get database parameter** pode ser usado em processos preemptivos ao chamar os seletores abaixo:

* [4D Server log recording](#4d-server-log-recording-28)
* [Debug log recording](#debug-log-recording-34)
* [Diagnostic log recording](#diagnostic-log-recording-79)
* [Diagnostic log level](#diagnostic-log-level-86)
* [Circular log limitation](#circular-log-limitation-90)
* [Cache flush periodicity](#cache-flush-periodicity-95)
* [SMTP Log](#smtp-log-110)
* [POP3 Log](#pop3-log-116)
* [IMAP Log](#imap-log-119)
* [Pause logging](#pause-logging-121)


## Exemplo 

Imagine que queira que sua aplicação reinicie após a primeira execução. A aplicação é lançada, com, por exemplo, uma linha de comando em Windows:

```RAW
%HOMEPATH%\Desktop\4D\4D.exe %HOMEPATH%\Documents\myDB.4dbase\myDB.4db --user-param "First launch"
```

Em [Método banco de dados On Startup](metodo-banco-de-dados-on-startup.md), pode escrever:

```4d
 var $realVal : Real
 var $welcome : Text
 $realVal:=Get database parameter(Valor de parâmetro do usuário;$welcome)
 If($welcome#"")
    ALERT($welcome)
    If($welcome="First launch") //é o primeiro lançamento
  //... faz algumas operações
       SET DATABASE PARAMETER(User param value;"Database has restarted!") //para o próximo lançamento
       RESTART 4D
    End if
 End if
```

## Ver também 

[DISTINCT VALUES](distinct-values.md)  
[Application info](application-info.md)  
[QUERY SELECTION](query-selection.md)  
[SET DATABASE PARAMETER](set-database-parameter.md)  

## Propriedades

|  |  |
| --- | --- |
| Número do comando | 643 |
| Thread-seguro | &cross; |


