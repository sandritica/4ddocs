---
id: branching
title: Estruturas condicionais
---

Uma estrutura de branching permite que os métodos provem uma condição e tomem caminhos alternativos, dependendo do resultado.


## If... Else... End if

A sintaxe formal da estrutura de fluxo de controle `If...Else...End if` é:

```4d
 If(Boolean_Expression)
    statement(s)
 Else
    statement(s)
 End if
```

Note que a parte `Else` é opcional; pode escrever:
```4d
 If(Boolean_Expression)
    statement(s)
 End if
```

A estrutura `If...Else...End if` permite que o seu método escolha entre duas ações, dependendo se um teste (uma expressão booleana) é TRUE ou FALSO. Quando a expressão Booleana for TRUE, são executadas as declarações que seguem imediatamente ao teste. Se a expressão Booleana for FALSE, são executadas as declarações que seguem a linha Else. A declaração `Else` é opcional; se omitir Else, a execução continua com a primeira instrução (se houver) que seguir `End if`.

Note que a expressão booleana é sempre avaliada completamente. Considere particularmente o teste abaixo:

```4d
 If(MethodA & MethodB)
    ...
 End if
```

A expressão é TRUE apenas se ambos os métodos forem TRUE. Entretanto, mesmo se _MethodA_ devolver  FALSE, 4D ainda iria avaliar _MethodB_, o que seria uma perda de tempo. Nesse caso, é mais interessante usar uma estrutra como:

```4d
 If(MethodA)
    If(MethodB)
       ...
    End if
 End if
```

O resultado é parecido mas o _MethodB_ é avaliado somente se necessário.

### Exemplo

```4d
  // Ask the user to enter a name
 $Find:=Request(Type a name)
 If(OK=1)
    QUERY([People];[People]LastName=$Find)
 Else
    ALERT("You did not enter a name.")
 End if
 End if
 End if 
```

**Dica:** a ramificação pode ser realizada sem que as instruções sejam executadas em um caso ou no outro. Quando desenvolver um algoritmo ou uma aplicação especializada, nada impede que escreva:

```4d
 If(Boolean_Expression)
 Else
    statement(s)
 End if
```
ou :

```4d
 If(Boolean_Expression)
    statement(s)
 Else
 End if
```

## Case of... Else... End case

A sintaxe formal da estrutura de fluxo de controle `Case of...Else...End case` é:
```4d
 Case of
    :(Boolean_Expression)
       statement(s)
    :(Boolean_Expression)
       statement(s)
       .
       .
       .

    :(Boolean_Expression)
       statement(s)
    Else
       statement(s)
 End case
```

Note que a parte `Else` é opcional; pode escrever:
```4d
 Case of
    :(Boolean_Expression)
       statement(s)
    :(Boolean_Expression)
       statement(s)
       .
       .
       .

    :(Boolean_Expression)
       statement(s)
 End case
```
Como na estrutura `If...Else...End if`, a estrutura `Case of...Else...End case` também permite que seu método escolha entre ações alternativas. Ao contrário da estrutura `If...Else...End`, a estrutura `Case of...Else...End case` pode testar um número ilimitado e razoável de expressões booleanas e tomar medidas, dependendo do qual uma seja TRUE.

Cada expressão booleana é precedida de dois pontos (`:`). A combinação dos dois pontos e da expressão booleana é chamada de um caso. Por exemplo, a linha abaixo é um caso:

```4d
:(bValidate=1)
```

Só são executadas as instruções que seguem o primeiro caso TRUE (até o próximo caso). Se nenhum dos casos for TRUE, nenhuma das instruções será executada (se nenhuma parte `Else` for incluida).

Pode incluir uma instrução Else depois do último caso. Se todos os casos forem FALSE, as instruções que seguem `Else` serão executadas.

### Exemplo

Esse exemplo testa uma variável numérica e exibe uma caixa de alerta com uma apalavra:

```4d
 Case of
    :(vResult=1) //Teste se o número é 1
       ALERT("One.") //Se for 1, mostrar um alerta
    :(vResult=2) //Testar se o número é 2
       ALERT("Two.") //Se for 2, exibe um alerta
    :(vResult=3) //Testa se o número é 3
       ALERT("Three.") //Se for 3, exibe um alerta
    Else //Se não for 1, 2, ou 3, exibe um alerta
       ALERT("It was not one, two, or three.")
 //statement(s)
 End case //Se for 2, mostrar um alerta
    :(vResult=3) //Testar se o número é 3
       ALERT("Three.") //Se for 3, exiba um alerta
    Else //Se não for 1, 2 ou 3, exibir um alerta
       ALERT("Não foram um, dois ou três.")
 //statement(s)
 End case
```

Para comparação, aqui está a versão `If...Else...End if` do mesmo método:

```4d
 If(vResult=1) //Teste se o número é 1
    ALERT("One.") If(vResult=1) //Test if the number is 1
    ALERT("One.") //If it is 1, display an alert
 Else
    If(vResult=2) //Test if the number is 2
       ALERT("Two.") //If it is 2, display an alert
    Else
       If(vResult=3) //Test if the number is 3
          ALERT("Three.") //If it is 3, display an alert
       Else //If it is not 1, 2, or 3, display an alert
          ALERT("It was not one, two, or three.")
       End if
    End if
 End if //Se for 2, exibir um alerta
    Else
       If(vResult=3) //Testa se o número é 3
          ALERT("Três.") //Se for 3, exiba um alerta
    Else //Se não for 1, 2 ou 3, exibir um alerta
       ALERT("Não foram um, dois ou três.")
       End if
    End if
 End if
```

Lembre-se que com uma estrutura `Case of...Else...End case`, apenas o primeiro caso TRUE é executado. Mesmo se dois ou mais casos forem TRUE, só as instruções que seguirem o primeiro caso TRUE serão executadas.

Dessa maneira, quando quiser implementar testes hierárquicos, deve garantir que as declarações de condição que estejam mais abaixo no esquema hierárquico apareçam primeiro na sequência de testes. Por exemplo, o teste para a presença da condition1 cobre o teste para a presença de condition1&condition2 e, portanto deveria estar localizada por último na sequência de testes. Por exemplo, o código abaixo nunca terá sua última condição detectada:

```4d
 Case of
    :((vResult=1) & (vCondition#2)) //this case will be detected first
       ... //statement(s)
    :(vResult=1)
       ...
```

No código anterior, a presença da segunda condição não é detectada, já que o teste "vResult=1" ramifica o código antes de qualquer outro teste. Para que o código funcione corretamente, pode escrevê-lo assim:

```4d
 Case of
    :(vResult=1) //Test if the number is 1
       ALERT("One.") //If it is 1, display an alert
    :(vResult=2) //Test if the number is 2
       ALERT("Two.") //If it is 2, display an alert
    :(vResult=3) //Test if the number is 3
       ALERT("Three.") //If it is 3, display an alert
    Else //If it is not 1, 2, or 3, display an alert
       ALERT("It was not one, two, or three.")
 End case
```

Além disso, se quiser implementar teste hierárquico, pode considerar usar um código hierárquico.

**Dica:** a ramificação pode ser feita sem que as instruções sejam executados em um caso ou outro. Quando desenvolver um algoritmo ou uma aplicação especializada, nada impede que escreva:
```4d
 Case of
    :(Boolean_Expression)
    :(Boolean_Expression)
      ...

    :(Boolean_Expression)
       statement(s)
    Else
       statement(s)
 End case
```

ou :
```4d
 Case of
    :(Boolean_Expression)
       statement(s)
    :(Boolean_Expression)
       statement(s)
       ...

    :(Boolean_Expression)
       statement(s)
    Else
 End case
```

ou :
```4d
 Case of
    Else
       statement(s)
 End case
```
