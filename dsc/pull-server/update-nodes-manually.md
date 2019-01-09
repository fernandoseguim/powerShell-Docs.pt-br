---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Atualizar nós de um servidor de pull
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400104"
---
# <a name="update-nodes-from-a-pull-server"></a>Atualizar nós de um servidor de pull

As seções a seguir pressupõem que você já configurou um servidor de recepção. Se você não tiver configurado seu servidor de Pull, você pode usar os guias a seguir:

- [Configurar um servidor de pull SMB de DSC](pullServerSmb.md)
- [Configurar um servidor de pull HTTP de DSC](pullServer.md)

Cada nó de destino pode ser configurado para baixar as configurações, recursos e até mesmo relatar seu status. Este artigo mostra como carregar recursos para que fiquem disponíveis para serem baixadas e configurar clientes para baixar os recursos automaticamente. Quando o nó recebe uma configuração atribuída, por meio **Pull** ou **Push** (v5), ele baixa automaticamente todos os recursos necessários para a configuração do local especificado no LCM.

## <a name="using-the-update-dscconfiguration-cmdlet"></a>Usando o cmdlet Update-DSCConfiguration

A partir do PowerShell 5.0, o [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, força um nó para atualizar sua configuração do servidor de recepção configurado no LCM.

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a>Usando Invoke-CIMMethod

No PowerShell 4.0, você pode forçar manualmente um cliente de Pull para atualizar sua configuração usando [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod). O exemplo a seguir cria uma sessão CIM com as credenciais especificadas, invoca o método apropriado de CIM e remove a sessão.

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a>Consulte Também

[PerformRequiredConfigurationChecks](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
