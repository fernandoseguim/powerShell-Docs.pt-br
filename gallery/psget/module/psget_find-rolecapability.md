---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: Find-RoleCapability
ms.openlocfilehash: 89aacd604d54f6a5e9752790be65cc3bcc77c8e1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="find-rolecapability"></a>Find-RoleCapability

Localiza capacidades de função em módulos.

## <a name="description"></a>Descrição
O cmdlet Find-RoleCapability localiza capacidades de função do PowerShell em módulos. Find-RoleCapability faz pesquisas em módulos em repositórios registrados.
Para cada capacidade de função localizada, esse cmdlet retorna um objeto PSGetRoleCapabilityInfo. Você pode passar um objeto PSGetRoleCapabilityInfo para o cmdlet Install-Module para instalar o módulo que contém a capacidade de função.
As capacidades de função do PowerShell definem quais comandos, aplicativos e assim por diante ficam disponíveis para um usuário em um ponto de extremidade do tipo JEA ("Administração Suficiente"). As capacidades de função são definidas por arquivos com uma extensão .psrc.

- Find-RoleCapability pode filtrar segundo os parâmetros de versão: MinimumVersion, RequiredVersion, AllVersions.
  - Esses parâmetros são mutuamente exclusivos.
  - Esses parâmetros de versão são permitidos apenas com o nome exclusivo do módulo, sem curingas.
  - Se o parâmetro RequiredVersion não for especificado, Find-RoleCapability retorna a versão mais recente do módulo que for igual ou maior que a versão mínima especificada ou a versão mais recente do módulo se nenhuma versão mínima tiver sido especificada.
  - Se o parâmetro RequiredVersion for especificado, Find-RoleCapability retornará apenas a versão do módulo que corresponde exatamente à versão especificada.
- Find-RoleCapability pode filtrar nos metadados do módulo com o parâmetro -Tag
- Find-RoleCapability pode filtrar na linguagem de pesquisa específica do repositório com o parâmetro -Filter.
- Find-RoleCapability pode filtrar módulos de todos ou de alguns dos repositórios registrados.

## <a name="cmdlet-syntax"></a>Sintaxe do cmdlet
```powershell
Get-Command -Name Find-RoleCapability -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Referência da ajuda online sobre cmdlets

[Find-RoleCapability](http://go.microsoft.com/fwlink/?LinkId=718029)

## <a name="example-commands"></a>Comandos de exemplo
```powershell

# Find a specific role capability
Find-RoleCapability -Name Maintenance

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Maintenance                         1.5.0      RoleCapModule                       PrivatePSGallery

# Find multiple role capabilities
Find-RoleCapability -Name MyJeaRole, Maintenance

# Find all available role capabilities from all registered repositories
Find-RoleCapability

# Find available role capabilities from few registered repositories
Find-RoleCapability -Repository PSGallery,PrivatePSGallery

# Find all role capabilities in a specified repository
Find-RoleCapability -Repository PSGallery

# Find a role capability defined in a specific module
Find-RoleCapability -Name Maintenance -ModuleName RoleCapModule

# Find role capabilities from all versions of a module
Find-RoleCapability -ModuleName RoleCapModule -AllVersions

# Find role capabilities with module name and MinimumVersion.
Find-RoleCapability -ModuleName RoleCapModule -MinimumVersion 1.1

# Find role capabilities with module name and exact version
Find-RoleCapability -ModuleName RoleCapModule -RequiredVersion 1.4.0

# Find role capabilities defined modules with -Filter based search. -Filter searches in description and module names
Find-RoleCapability -Filter Cookbook
Find-RoleCapability -Filter RBAC

# Find all role capabilities with tags Azure or DSC in module metadata
Find-RoleCapability -Tag Azure, DSC

```