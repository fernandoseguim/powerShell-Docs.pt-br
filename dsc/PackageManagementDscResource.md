---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC,powershell,configuração,instalação
title: Recurso PackageManagement de DSC
ms.openlocfilehash: e6eea9f0bae42e131976dacb9813da759ff31239
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-packagemanagement-resource"></a>Recurso PackageManagement de DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O recurso **PackageManagement** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para instalar ou desinstalar pacotes de Gerenciamento de Pacotes em um nó de destino. Este recurso requer o módulo **PackageManagement**, disponível em http://PowerShellGallery.com.

## <a name="syntax"></a>Sintaxe

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ Source = [string] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ RequiredVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ MaximumVersion = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ ProviderName = [string] ]
    [ AdditionalParameters = [Microsoft.Management.Infrastructure.CimInstance[]] ]
}
```

## <a name="properties"></a>Propriedades
|  Propriedade  |  Descrição   |
|---|---|
| Nome| Especifica o nome do Pacote a ser instalado ou desinstalado.|
| Origem| Especifica o nome da origem do pacote onde é possível encontrar o pacote. Isso pode ser um URI ou uma fonte registrada com o recurso de DSC Register-PackageSource ou PackageManagementSource. O recurso de DSC MSFT_PackageManagementSource também pode registrar uma origem de pacote.|
| Ensure| Determina se o pacote deve ser instalado ou desinstalado.|
| RequiredVersion| Especifica a versão exata do pacote que você deseja instalar. Se você não especificar esse parâmetro, esse recurso DSC instalará a versão disponível mais recente do pacote que também atende a qualquer versão máxima especificada pelo parâmetro MaximumVersion.|
| MinimumVersion| Especifica a versão mínima permitida do pacote que você deseja instalar. Se você não adicionar esse parâmetro, esse recurso de DSC instalará a versão disponível mais recente do pacote que também atende a qualquer versão máxima especificada pelo parâmetro MaximumVersion.|
| MaximumVersion| Especifica a versão máxima permitida do pacote que você deseja instalar. Se você não especificar esse parâmetro, esse recurso de DSC instalará a versão com maior numeração disponível do pacote.|
| SourceCredential | Especifica uma conta de usuário que tenha direitos para instalar um pacote para um provedor de pacote ou origem específicos.|
| ProviderName| Especifica um nome de provedor de pacote para o qual definir o escopo de sua pesquisa de pacote. Você pode obter os nomes de provedores de pacote executando o cmdlet Get-PackageProvider.|
| AdditionalParameters| Parâmetros específicos do provedor que são transmitidos como uma tabela de hash. Por exemplo, para o provedor do NuGet, você pode transmitir parâmetros adicionais, como DestinationPath.|

## <a name="additional-parameters"></a>Parâmetros Adicionais
A tabela a seguir lista as opções para a propriedade AdditionalParameters.
|  Parâmetro  | Descrição   |
|---|---|
| DestinationPath| Usada por provedores como o Nuget interno. Especifica o local de um arquivo onde você deseja que o pacote seja instalado.|
| InstallationPolicy| Usada por provedores como o Nuget interno. Determina se você confia na origem do pacote. Um destes: "Não confiável", "Confiável".|

## <a name="example"></a>Exemplo

Este exemplo instala o pacote do NuGet **JQuery** e o módulo do PowerShell **GistProvider** usando o recurso de DSC **PackageManagement**. Este exemplo primeiro garante que as origens dos pacotes necessários estejam disponíveis e, em seguida, define o estado esperado dos pacotes **JQuery** e **GistProvider** (NuGet e PowerShell, respectivamente).

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceUri   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceUri   = "https://www.powershellgallery.com/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagement NugetPackage
    {
        Ensure               = "Present"
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1"
        DependsOn            = "[PackageManagementSource]SourceRepository"
    }

    PackageManagement PSModule
    {
        Ensure               = "Present"
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery"
    }
}
```