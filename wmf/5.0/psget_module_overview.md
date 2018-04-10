---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
ms.openlocfilehash: 82b8046d5cbb47300f090ce2ffbf3c279ed19458
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a>Descoberta, instalação e inventário do módulo PowerShell com o PowerShellGet

O PowerShellGet está incluído nesta versão do WMF:
-   Find-Module pode filtrar nos metadados do módulo com o parâmetro -Tag
-   Find-Module pode filtrar na linguagem de pesquisa específica do repositório com o parâmetro -Filter
-   Find-Module pode filtrar no conteúdo do módulo com os parâmetros -Command, -DscResource e -Includes
-   Find-DscResource permite a descoberta de recursos DSC individuais nos repositórios
-   Suporte para instalação desde compartilhamentos de arquivos e publicação neles com o NuGet

## <a name="example-commands"></a>Comandos de exemplo
```powershell
\# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

\# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

\#Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

\# Find all modules with Dsc resources
Find-Module -Includes DscResource

\# Find all modules with cmdlets
Find-Module -Includes Cmdlet

\# Find all modules with functions
Find-Module -Includes Function

\# Find all DSC resources
Find-DscResource

\# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking

\# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

\# Find modules using -Filter parameter
\# Specified filter value is searched in Name and Description properties
Find-Module -Filter Cookbook -Repository PSGallery
Find-Module -Filter RBAC -Repository PSGallery
```

## <a name="new-features-in-powershellget"></a>Novos recursos no PowerShellGet
-   Suporte à versão lado a lado no Windows PowerShell 5.0 ou mais recente
-   Suporte à instalação de dependências do módulo
-   Três novos cmdlets
    -   Get-InstalledModule
    -   Uninstall-Module
    -   Save-Module