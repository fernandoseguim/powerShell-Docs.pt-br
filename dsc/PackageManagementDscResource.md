---
ms.date: 06/20/2018
keywords: DSC,powershell,configuração,instalação
title: Recurso PackageManagement de DSC
ms.openlocfilehash: 281aee13eb005f00b23c97870eaefaa332d9c232
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892494"
---
# <a name="dsc-packagemanagement-resource"></a>Recurso PackageManagement de DSC

Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1

O recurso **PackageManagement** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para instalar ou desinstalar pacotes de Gerenciamento de Pacotes em um nó de destino. Este recurso requer o módulo **PackageManagement**, disponível em [http://PowerShellGallery.com](http://PowerShellGallery.com).

> [!IMPORTANT]
> O módulo **PackageManagement** deve ser pelo menos a versão 1.1.7.0 para as informações de propriedade a seguir estarem corretas.

## <a name="syntax"></a>Sintaxe

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [AdditionalParameters = [HashTable]]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [MaximumVersion = [string]]
    [MinimumVersion = [string]]
    [ProviderName = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [RequiredVersion = [string]]
    [Source = [string]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   |
|---|---|
| Nome| Especifica o nome do Pacote a ser instalado ou desinstalado.|
| AdditionalParameters| Tabela de hash específica do provedor dos parâmetros que seria passado para o `Get-Package -AdditionalArguments`. Por exemplo, para o provedor do NuGet, você pode transmitir parâmetros adicionais, como DestinationPath.|
| Ensure| Determina se o pacote deve ser instalado ou desinstalado.|
| MaximumVersion|Especifica a versão máxima permitida do pacote que você deseja encontrar. Se você não adicionar esse parâmetro, o recurso localizará a versão mais recente disponível do pacote.|
| MinimumVersion|Especifica a versão mínima permitida do pacote que você deseja encontrar. Se você não adicionar esse parâmetro, esse recurso encontrará a versão disponível mais recente do pacote que também atende a qualquer versão máxima especificada pelo parâmetro _MaximumVersion_.|
| ProviderName| Especifica um nome de provedor de pacote para o qual definir o escopo de sua pesquisa de pacote. Você pode obter os nomes de provedor de pacotes executando o cmdlet `Get-PackageProvider`.|
| RequiredVersion| Especifica a versão exata do pacote que você deseja instalar. Se você não especificar esse parâmetro, esse recurso DSC instalará a versão disponível mais recente do pacote que também atende a qualquer versão máxima especificada pelo parâmetro _MaximumVersion_.|
| Origem| Especifica o nome da origem do pacote onde é possível encontrar o pacote. Isso pode ser um URI ou uma fonte registrada com o recurso de DSC `Register-PackageSource` ou PackageManagementSource.|
| SourceCredential | Especifica uma conta de usuário que tenha direitos para instalar um pacote para um provedor de pacote ou origem específicos.|

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
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2/"
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