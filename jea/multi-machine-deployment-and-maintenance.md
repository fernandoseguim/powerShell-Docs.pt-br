---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "manutenção e implantação de vários computadores"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 784806197a64eb30af1ecea4af55575434ce7b87

---

# Manutenção e implantação de vários computador
Neste ponto, você já implantou o JEA para sistemas locais várias vezes.
Como seu ambiente de produção provavelmente consiste em mais de um computador, é importante seguir as etapas essenciais no processo de implantação que deve ser repetido em cada computador.

## Etapas de alto nível:
1.  Copie seus módulos (com Capacidades de Função) para cada nó.
2.  Copie os arquivos de configuração de sessão para cada nó.
3.  Execute `Register-PSSessionConfiguration` com sua sessão de configuração.
4.  Mantenha uma cópia da sua configuração de sessão e kits de ferramentas em um local seguro.
Ao fazer modificações, é recomendável ter uma "única fonte verdadeira".

## Script de Exemplo
Veja este exemplo de script de implantação.
Para usá-lo em seu ambiente, você terá que usar os nomes ou caminhos de compartilhamentos de arquivo reais e módulos.
```PowerShell
# First, copy the session configuration and modules (containing role capability files) onto a file share you have access to.
Copy-Item -Path 'C:\Demo\Demo.pssc' -Destination '\\FileShare\JEA\Demo.pssc'
Copy-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\SomeModule\' -Recurse -Destination '\\FileShare\JEA\SomeModule'

# Next, author a setup script (C:\JEA\Deploy.ps1) to run on each individual node
    # Contents of C:\JEA\Deploy.ps1
    New-Item -ItemType Directory -Path C:\JEADeploy
    Copy-Item -Path '\\FileShare\JEA\Demo.pssc' -Destination 'C:\JEADeploy\'
    Copy-Item -Path '\\FileShare\JEA\SomeModule' -Recurse -Destination 'C:\Program Files\WindowsPowerShell\Modules' # Remember, Role Capability Files are found in modules
    if (Get-PSSessionConfiguration -Name JEADemo -ErrorAction SilentlyContinue)
    {
        Unregister-PSSessionConfiguration -Name JEADemo -ErrorAction Stop
    }

    Register-PSSessionConfiguration -Name JEADemo -Path 'C:\JEADeploy\Demo.pssc'
    Remove-Item -Path 'C:\JEADeploy' # Don't forget to clean up!

# Now, invoke the script on all of the target machines.
# Note: this requires PowerShell Remoting be enabled on each machine. Enabling PowerShell remoting is a requirement to use JEA as well.
# You may need to provide the "-Credential" parameter if your current user account does not have admin permissions on these machines.
Invoke-Command –ComputerName 'Node1', 'Node2', 'Node3', 'NodeN' -FilePath 'C:\JEA\Deploy.ps1'

# Finally, delete the session configuration and role capability files from the file share.
Remove-Item -Path '\\FileShare\JEA\Demo.pssc'
Remove-Item -Path '\\FileShare\JEA\SomeModule' -Recurse
```
## Modificar Capacidades
Ao lidar com vários computadores, é importante que as modificações sejam distribuídas de maneira consistente.
Uma vez que JEA tem um recurso de DSC, isso ajuda a garantir que seu ambiente esteja sincronizado.
Até lá, é altamente recomendável manter uma cópia mestra de suas configurações de sessão e implantar novamente cada vez que fizer uma alteração.

## Remover Capacidades
Para remover a configuração de JEA de seus sistemas, use o seguinte comando em cada computador:
```PowerShell
Unregister-PSSessionConfiguration -Name JEADemo
```




<!--HONumber=Jul16_HO1-->


