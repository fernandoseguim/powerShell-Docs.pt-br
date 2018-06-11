---
ms.date: 06/20/2018
keywords: DSC,powershell,configuração,instalação
title: Recurso PackageManagementSource da DSC
ms.openlocfilehash: 5d049b05c387cafe27edb202d569852b10852dce
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753763"
---
# <a name="dsc-packagemanagementsource-resource"></a>Recurso PackageManagementSource da DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1

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
| InstallationPolicy| Usada por provedores como o Nuget interno. Determina se você confia na origem do pacote. Um destes: "Não confiável", "Confiável".|
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