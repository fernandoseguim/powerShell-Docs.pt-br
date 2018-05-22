---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recurso PackageManagementSource da DSC
ms.openlocfilehash: 3e67cec9058ecb0e43f882f98f5ec8b92e261a09
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-packagemanagementsource-resource"></a>Recurso PackageManagementSource da DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O recurso **PackageManagementSource** na Configuração do Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para registrar ou cancelar o registro de fontes de Gerenciamento de Pacote em um nó de destino. **Fontes de Gerenciamento de Pacote registradas dessa forma são registradas no contexto do Sistema, podem ser usadas pela conta do Sistema ou pelo mecanismo de DSC.** Este recurso requer o módulo **PackageManagement**, disponível em http://PowerShellGallery.com.

## <a name="syntax"></a>Sintaxe

```
PSModule [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ InstallationPolicy = [string] ]
    [ ProviderName = [string] ]
    [ SourceUri = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propriedades
|  Propriedade  |  Descrição   |
|---|---|
| Nome| Especifica o nome da origem do pacote a ser registrado ou cancelado no seu sistema.|
| Ensure| Determina se a origem do pacote deve ser registrada ou cancelada.|
| InstallationPolicy| Determina se você confia na origem do pacote. Um destes: "Não confiável", "Confiável".|
| ProviderName| Especifica o nome do provedor OneGet por meio do qual você pode fornecer interoperabilidade com a origem do pacote.|
| SourceUri| Especifica o URI de origem do pacote.|
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
        SourceUri   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```