---
title: Recurso PackageManagementSource da DSC
ms.date: 
keywords: powershell,DSC
description: 
ms.topic: article
author: brywang-msft
manager: kriscv
ms.prod: powershell
ms.openlocfilehash: 22e61490e7b3f98335334a2703ec9639cbdaa87e
ms.sourcegitcommit: 89e7ae30faff5f96641fc72764bdc76e0e257bc2
translationtype: HT
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

Este exemplo registra a origem do pacote de http://nuget.org usando o recurso de DSC **PackageManagementSource**.

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
