---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: usando jea
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 3bac5932c3ed57713bdb08e3a9ed435b228518bc

---

# Usando JEA
Esta seção enfoca a compreensão da experiência do usuário final do *use do JEA*.
Na seção de pré-requisitos, você criou um ponto de extremidade JEA de demonstração.
Usaremos esta demonstração para mostrar o JEA em ação.
Nas próximas seções, o guia abordará ao contrário, apresentando as ações e os arquivos que tornaram a experiência do usuário final possível.

## Usando o JEA como não administrador
Para mostrar JEA em ação, você precisará usar a comunicação remota do PowerShell como se você fosse um usuário não administrador.
Execute o seguinte comando em uma nova janela do PowerShell:   

```PowerShell
$NonAdminCred = Get-Credential
```

Insira as credenciais para a conta não administradora quando solicitado.
Se você acompanhou a seção [Configurar usuários e grupos](creating-a-domain-controller.md#set-up-users-and-groups), eles serão:
-   Nome do usuário = "OperatorUser"
-   Senha = "pa$$w0rd"

Em seguida, execute o comando a seguir para conectar-se ao ponto de extremidade de demonstração usando as credenciais fornecidas:

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred
```

Agora você entrou em uma sessão comunicação remota interativa do PowerShell no computador local.
Usando o parâmetro "Credential", você se conectou *como se fosse* o OperatorUser (ou a conta usada).
A alteração no prompt para `[localhost]: PS>` indica que você está operando em uma sessão remota.  

Execute o seguinte no prompt de comando remoto para mostrar os comandos disponíveis a você:

```PowerShell
Get-Command
```

Como você pode ver, este é um subconjunto muito limitado de comandos disponíveis em uma janela normal do PowerShell (que geralmente pode incluir milhares de comandos).
Especificamente, ela mostra apenas os sete cmdlets JEA padrão (Clear-Host, Exit-PSSession, Get-Command, Get-FormatData, Get-Help, Measure-Object, Out-Default e Select-Object) e os dois comandos explicitamente incluídos no arquivo de Capacidade de Função de manutenção.

Em seguida, abordaremos o contexto do usuário no qual esta sessão está operando invocando a função personalizada incluída no arquivo de Capacidade de Função de manutenção:

```PowerShell
Get-UserInfo
```

A saída dessa função mostra "ConnectedUser" e "RunAsUser".
O usuário conectado é a conta conectada à sessão remota (por exemplo, sua conta).
O usuário conectado não precisa ter privilégios de administrador.
A conta "Executar como" é a conta que realmente executa as ações privilegiadas.
Ao conectar-se como um usuário e administrar como um usuário privilegiado, permitimos que usuários não privilegiados executem tarefas administrativas específicas sem lhes conceder direitos administrativos.

Para demonstrar isso em ação, execute o seguinte comando:

```PowerShell
Restart-Service -Name Spooler -Verbose
```

Normalmente, Restart-Service requer privilégios de administrador para ser executado.
Com a conta virtual JEA, no entanto, podemos executá-lo usando credenciais sem privilégios.

Dessa forma, o JEA permite fazer seu trabalho usando os comandos que você já usa.
Mas e quanto aos comandos que *não devem* poder ser usados?
Tente executar um comando diferente na sessão JEA, como `Restart-Computer`, e observe como o JEA impede que esses comandos sejam executados.

```PowerShell
[localhost]: PS> Restart-Computer
The term 'Restart-Computer' is not recognized as the name of a cmdlet, function, script file, or
operable program. Check the spelling of the name, or if a path was included, verify that the path
is correct and try again.
    + CategoryInfo          : ObjectNotFound: (Restart-Computer:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

Por fim, para deixar o ponto de extremidade JEA restrito, execute o seguinte comando:

```PowerShell
Exit-PSSession
```

Isso se desconecta da sessão de comunicação remota do PowerShell.




<!--HONumber=Jun16_HO4-->


