---
id: on-sql-authentication-database-method
title: On SQL Authentication database method
slug: /commands/on-sql-authentication-database-method
displayed_sidebar: docs
---

<!--REF #_command_.On SQL Authentication database method.Syntax-->$user, $pw, $ip -> On SQL Authentication database method : Boolean<!-- END REF-->
<!--REF #_command_.On SQL Authentication database method.Params-->
| Parâmetro | Tipo |  | Descrição |
| --- | --- | --- | --- |
| $user | Texto | &#8592; | Nome de usuário |
| $pw | Texto | &#8592; | Senha |
| $ip | Texto | &#8592; | (Opcional) endereço IP de cliente na origem do pedido |
| Resultado | Boolean | &#8592; | Verdadeiro = pedido aceito, Falso = pedido recusado |

<!-- END REF-->

## 

<!--REF #_command_.On SQL Authentication database method.Summary-->O On SQL Authentication database method pode ser utilizado para filtrar os pedidos enviados ao servidor SQL integrado de 4D.<!-- END REF--> Este filtro pode estar baseado no nome e senha, assim como 7(opcional) no endereço IP do usuário. O desenvolvedor pode utilizar sua própria tabela de usuários ou a dos usuários 4D para avaliar os identificadores de conexão. Quando tiver validada a conexão, o comando [CHANGE CURRENT USER](change-current-user.md) pode ser utilizado para controlar o acesso das pedidos dentro do banco 4D.

Quando existir, o On SQL Authentication database method é chamado automaticamente por 4D ou 4D Server em cada conexão externa ao servidor SQL. Portanto o Sistema interno de gestão dos usuários de 4D não está ativado. A conexão é aceita apenas se o método de banco retorna *True* em $result e se o comando [CHANGE CURRENT USER](change-current-user.md) for executado com êxito. Se uma destas condições não for cumprida, o pedido é recusado.

**Nota**: A instrução **SQL LOGIN(SQL\_INTERNAL**;$usuário;$senha) não chama ao On SQL Authentication database method já que é uma conexão interna neste caso.

O método de banco de dados recebe até três parâmetros de tipo Texto, passados por 4D ($user, $pw e $ip) e retorna um booleano, $result\. Esta é a descrição desses parâmetros:

| **Parâmetros** | **Tipo** | **Descrição**                                              |
| -------------- | -------- | ---------------------------------------------------------- |
| $user             | Texto    | Nome de usuário                                            |
| $pw             | Texto    | Senha                                                      |
| $ip             | Texto    | (opcional) Endereço IP do cliente na origem do pedido (\*) |
| $result             | Booleano | True = pedido aceito, False = pedido recusado              |

(\*) 4D devolve os endereços IPv4 em um formato híbrido IPv6/IPv4 escrito com um prefixo de 96 bits, por exemplo ::ffff:192.168.2.34 para o endereço IPv4 192.168.2.34\. Para maior informação, consulte *Suporte de IP v6*. 

Deve declarar estes parâmetros desta forma:

```4d
  // Método de base On Web Authentication
 
 var $user;$pw;$ip;$4 : Text
  // Código para o método
```

A senha ($pw) se recebe como texto estandarte. 

Deve controlar os identificadores da conexão SQL no On SQL Authentication database method. Por exemplo, pode verificar o nome e a senha utilizando uma tabela de usuários personalizada. Se os identificadores forem válidos, passe *True* em $result para aceitar a conexão e a petição. 4D abre uma sessão SQL para o usuário. Caso contrário, passe *False* em $result; neste caso, a conexão é recusada. 

**Nota:** Se On SQL Authentication database method não existir, a conexão é avaliada utilizando o Sistema integrado de gestão de usuários de 4D (Se estiver ativado, em outras palavras, se uma senha tiver sido atribuída ao Desenhista). Se este Sistema não estiver ativado, os usuários estão conectados com os direitos de acesso do Desenhista (acesso livre).

Se passa *True* em $result, deve chamar com sucesso ao comando [CHANGE CURRENT USER](change-current-user.md) no On SQL Authentication database method para que a pedido seja aceito e para que 4D abra uma sessão SQL para o usuário.

O uso do comando [CHANGE CURRENT USER](change-current-user.md) pode ser usada para implementar um sistema de autenticação virtual que tem a dupla vantagem de permitir o controle das ações de conexão e de esconder os identificadores da conexão na sessão SQL 4D.

Quando o sistema de senhas integrado de 4D não está ativo, a execução do comando [CHANGE CURRENT USER](change-current-user.md) não tem efeito; os usuários se conectam com os direitos de acesso do Desenhador. 

Este exemplo do On SQL Authentication database method verifica que o pedido de conexão provenha da rede interna, confirma os identificadores e depois atribui os direitos de acessos "sql\_user" para a sessão SQL.

```4d
 var $user;$pw;$ip;$4 : Text
  //$user: usuário
  //$pw: senha
  //{$ip: endereço IP do cliente}
 ON ERR CALL("SQL_error")
 If(DirIPInterna($ip))
  //O método DirIPInterna verifica se o endereço IP é interna
    If($user="victor") & ($pw="hugo")
       CHANGE CURRENT USER("sql_user";"")
       If(OK=1)
          $result:=True
       Else
          $result:=False
       End if
    Else
       $result:=False
    End if
 Else
    $result:=False
 End if
```
