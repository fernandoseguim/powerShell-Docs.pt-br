---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: Find-DscResource
ms.openlocfilehash: 37ba7925d6f73c453126f25e0818b3f8839d3b3b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
<a id="find-dscresource" class="xliff"></a>
# Find-DscResource

Localiza Recursos de DSC nos módulos.

<a id="description" class="xliff"></a>
## Descrição

O cmdlet Find-DscResource localiza recursos de [DSC (Configuração de Estado Desejado)](https://msdn.microsoft.com/en-us/PowerShell/dsc/overview) contidos em módulos que correspondam aos critérios especificados dos repositórios registrados.
Para cada módulo que localiza, o cmdlet Find-DscResource retorna um objeto PSGetDscResourceInfo que você pode redirecionar para Install-Module para instalar os módulos que contêm os recursos que esse cmdlet retorna.

A DSC é uma nova plataforma de gerenciamento do Windows PowerShell que permite implantar e gerenciar dados de configuração para serviços de software e gerenciar o ambiente no qual esses serviços são executados.

Os Recursos de Configuração de Estado Desejado (DSC) fornecem os blocos de construção para uma configuração DSC. Um recurso expõe propriedades que podem ser configuradas (esquema) e contém as funções de script do PowerShell que o Gerenciador de Configurações Local (LCM) chama de "realizar".

Um recurso pode modelar algo tão genérico quanto um arquivo ou tão específico quanto uma configuração de servidor do IIS. Grupos de recursos semelhantes são combinados em um Módulo de DSC, que organiza todos os arquivos necessários em uma estrutura que é portátil e inclui metadados para identificar como os recursos devem ser usados.

- Find-DscResource pode filtrar segundo os parâmetros de versão: MinimumVersion, RequiredVersion, AllVersions.
  - Esses parâmetros são mutuamente exclusivos.
  - Esses parâmetros de versão são permitidos apenas com o nome exclusivo do módulo, sem curingas.
  - Se o parâmetro RequiredVersion não for especificado, Find-DscResource retorna a versão mais recente do módulo que for igual ou maior que a versão mínima especificada ou a versão mais recente do módulo se nenhuma versão mínima tiver sido especificada.
  - Se o parâmetro RequiredVersion for especificado, Find-DscResource retornará apenas a versão do módulo que corresponde exatamente à versão especificada.
- Find-DscResource pode filtrar nos metadados do módulo com o parâmetro -Tag
- Find-DscResource pode filtrar na linguagem de pesquisa específica do repositório com o parâmetro -Filter.
- Find-DscResource pode filtrar módulos de todos ou de alguns dos repositórios registrados.

<a id="cmdlet-syntax" class="xliff"></a>
## Sintaxe do cmdlet
```powershell
Get-Command -Name Find-DscResource -Module PowerShellGet -Syntax
```

<a id="cmdlet-online-help-reference" class="xliff"></a>
## Referência da ajuda online sobre cmdlets

[Find-DscResource](http://go.microsoft.com/fwlink/?LinkId=517196)

<a id="example-commands" class="xliff"></a>
## Comandos de exemplo
```powershell

# Find a specific DSC Resource
Find-DscResource -Name xIisFeatureDelegation

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
xIisFeatureDelegation               1.10.0.0   xWebAdministration                  PSGallery

# Find all available DSC Resources from all registered repositories
Find-DscResource

# Find a DSC resource by name
Find-DscResource -Name xWebsite

# Find multiple DSC Resources
Find-DscResource -Name xIisHandler, xFirewall

# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking
Find-DscResource -ModuleName xWebAdministration

# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

# Find available DSC Resources from few registered repositories
Find-DscResource -Repository PSGallery,PrivatePSGallery

# Find all DSC Resources in a specified repository
Find-DscResource -Repository PSGallery

# Find DSC Resources from all versions of a module
Find-DscResource -ModuleName xNetworking -AllVersions

# Find DSC Resources with module name and MinimumVersion.
Find-DscResource -ModuleName xNetworking -MinimumVersion 1.1

# Find DSC Resources with module name and exact version
Find-DscResource -ModuleName xNetworking -RequiredVersion 2.1.1

# Find DSC Resources defined modules with -Filter based search. -Filter searches in description and module names
Find-DscResource -Filter Domain

# Find all DSC Resources with tags Azure or DSC in module metadata
Find-DscResource -Tag Azure, DSC

```

