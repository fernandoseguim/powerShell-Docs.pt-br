---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet, galeria
ms.date: 2016-10-14
contributor: manikb
title: "módulo psget_update"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: c7eb34252ad912c83168bc763425e0dc76e27813

---

# Update-Module

Baixa e instala a versão mais recente dos módulos especificados de uma galeria online para o computador local.

## Descrição

O cmdlet Update-Module instala uma versão mais recente de um módulo do Windows PowerShell que foi instalado da galeria online executando Install-Module no computador local.

Por padrão, a versão mais recente do módulo especificado disponível na galeria online é instalada, a menos que você especifique uma versão obrigatória. Você pode atualizar um módulo existente instalado especificando o nome do módulo. Update-Module procura pelo $env:PSModulePath do módulo que você deseja atualizar.

Executar Update-Module sem o parâmetro de nome atualiza todos os módulos que podem ser atualizados no computador local.

### Observações

- Esse cmdlet é executado no Windows PowerShell 3.0 ou em versões posteriores do Windows PowerShell, no Windows 7 ou no Windows 2008 R2 e em versões posteriores do Windows.
- Se o módulo especificado com o parâmetro de nome não tiver sido instalado usando Install-Module, ocorrerá um erro. Você só pode executar Update-Module em módulos que foram instalados da galeria online executando Install-Module.
- Se Update-Module tentar atualizar binários que estão em uso, ele retornará um erro que identifica os processos com problema e instruirá o usuário a repetir Update-Module depois de interromper os processos.
- No PowerShell 5.0 ou em versões mais recentes, quando Update-Module atualiza um módulo, ele adiciona a versão mais recente (ou especificada) do módulo, portanto, as versões mais antigas e mais recentes ficam lado a lado no mesmo diretório. Seria útil dizer isso e mostrar um exemplo da saída desses comandos.


## Sintaxe do cmdlet
```powershell
Get-Command -Name Update-Module -Module PowerShellGet -Syntax
```

## Referência da ajuda online sobre cmdlets

[Update-Module](http://go.microsoft.com/fwlink/?LinkID=398576)


## Comandos de exemplo

```powershell
PS C:\\windows\\system32> Update-Module -Name ContosoServer -RequiredVersion 1.5
PS C:\\windows\\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.0
PS C:\\windows\\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
PS C:\\windows\\system32> Update-Module -Name ContosoServer
PS C:\\windows\\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.8.1
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.8.1
Name : ContosoServer
Version : 2.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.0
PS C:\\windows\\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
```


###  Atualize o módulo TestDepWithNestedRequiredModules1 com dependências.
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -AllVersions

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module

Update-Module -Name TestDepWithNestedRequiredModules1 -RequiredVersion 2.0
Get-InstalledModule

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
2.5        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
1.0        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        RequiredModule3                     LocalRepo   RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
```




<!--HONumber=Oct16_HO2-->


