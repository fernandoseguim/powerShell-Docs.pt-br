---
ms.date: 06/20/2018
keywords: DSC,powershell,configuração,instalação
title: Recurso PackageManagementSource da DSC
ms.openlocfilehash: e51b5318288bef458567dd4b58d17caaea3ed69b
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046993"
---
# <a name="dsc-packagemanagementsource-resource"></a>Recurso PackageManagementSource da DSC

> Aplica-se a: Windows PowerShell 4.0, o Windows PowerShell 5.0, o Windows PowerShell 5.1

O recurso **PackageManagementSource** na Configuração do Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para registrar ou cancelar o registro de fontes de Gerenciamento de Pacote em um nó de destino. **Fontes de Gerenciamento de Pacote registradas dessa forma são registradas no contexto do Sistema, podem ser usadas pela conta do Sistema ou pelo mecanismo de DSC.** Este recurso requer o módulo **PackageManagement**, disponível em http://PowerShellGallery.com.

> [!IMPORTANT]
> O módulo **PackageManagement** deve ser pelo menos a versão 1.1.7.0 para as informações de propriedade a seguir estarem corretas.

## <a name="syntax"></a>Sintaxe

```
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [InstallationPolicy = [string]{ Trusted | Untrusted }]
    [PsDscRunAsCredential = [PSCredential]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   |
|---|---|
| Nome| Especifica o nome da origem do pacote a ser registrado ou cancelado no seu sistema.|
| ProviderName| Especifica o nome do provedor OneGet por meio do qual você pode fornecer interoperabilidade com a origem do pacote.|
| SourceLocation| Especifica o URI de origem do pacote.|
| Ensure| Determina se a origem do pacote deve ser registrada ou cancelada.|
| InstallationPolicy| Usada por provedores como o Nuget interno. Determina se você confia na origem do pacote. Um de: , . "Não confiável", "confiável".|
| SourceCredential| Fornece acesso ao pacote em uma fonte remota.|

## <a name="example"></a>Exemplo

Este exemplo registra a origem do pacote de http://nuget.org usando o recurso DSC **PackageManagementSource**.

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```