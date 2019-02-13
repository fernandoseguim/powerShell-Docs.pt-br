---
ms.date: 1/17/2019
keywords: DSC,powershell,configuração,instalação
title: Reiniciar um nó
ms.openlocfilehash: 33ecd98aa62c3dc94a8ff2213fd3e68bf0c05cb7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675787"
---
# <a name="reboot-a-node"></a>Reiniciar um nó

> [!NOTE]
> Este tópico fala sobre como reiniciar um nó. Para que a reinicialização seja executada com êxito a **ActionAfterReboot** e **RebootNodeIfNeeded** as configurações de LCM precisam ser configurados corretamente.
> Para ler sobre as configurações do Gerenciador de configurações Local, consulte [configurar o Gerenciador de configurações Local](../managing-nodes/metaConfig.md), ou [configurar o Gerenciador de configurações Local (v4)](../managing-nodes/metaConfig4.md).

Nós podem ser reinicializados de dentro de um recurso, usando o `$global:DSCMachineStatus` sinalizador. Defina esse sinalizador como `1` no `Set-TargetResource` função força o LCM para reinicializar o nó diretamente após o **definir** método do recurso atual. Usar este sinalizador, o **xPendingReboot** recurso detecta se uma reinicialização fica pendente fora do DSC.

Sua [configurações](configurations.md) pode seguir as etapas que exigem o nó a reinicialização. Isso pode incluir as coisas, como:

- Windows: Atualizações
- Instalação de software
- Arquivo renomeia
- Renomeação do computador

O **xPendingReboot** recurso verifica os locais de computador específico para determinar se uma reinicialização está pendente. Se o nó requer uma reinicialização fora do DSC, o **xPendingReboot** conjuntos de recursos a `$global:DSCMachineStatus` sinalizador como `1` forçar uma reinicialização e resolução da condição pendente.

> [!NOTE]
> Qualquer recurso de DSC pode instruir o LCM para reinicializar o nó ao definir esse sinalizador `Set-TargetResource` função. Para obter mais informações, consulte [escrevendo um recurso personalizado de DSC com MOF](../resources/authoringResourceMOF.md).

## <a name="syntax"></a>Sintaxe

```
xPendingReboot [String] #ResourceName
{
    Name = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [SkipCcmClientSDK = [bool]]
    [SkipComponentBasedServicing = [bool]]
    [SkipPendingComputerRename = [bool]]
    [SkipPendingFileRename = [bool]]
    [SkipWindowsUpdate = [bool]]
}
```

## <a name="properties"></a>Propriedades

| Propriedade | Descrição |
| --- | --- |
| Nome| Parâmetro obrigatório que deve ser exclusivo por instância do recurso dentro de uma configuração.|
| SkipComponentBasedServicing | Reinicializações de ignorar disparadas pelo componente de serviço baseado em componente. |
| SkipWindowsUpdate | Reinicializações de ignorar disparadas pelo Windows Update.|
| SkipPendingFileRename | Ignore as reinicializações de renomeação de arquivo pendente. |
| SkipCcmClientSDK | Reinicializações de ignorar disparadas pelo cliente do ConfigMgr. |
| SkipComputerRename | Ignorar reinicializações disparada por renomeações de computador. |
| PSDSCRunAsCredential | Suporte para v5. Executa o recurso como o usuário especificado. |
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`. Para obter mais informações, consulte [usando DependsOn](resource-depends-on.md)|

## <a name="example"></a>Exemplo

O exemplo a seguir instala o Microsoft Exchange usando o [xExchange](https://github.com/PowerShell/xExchange) recursos.
Durante a instalação, o **xPendingReboot** recurso é usado para reinicializar o nó.

> [!NOTE]
> Esse exemplo requer a credencial de uma conta que tenha direitos para adicionar um servidor do Exchange na floresta. Para obter mais informações sobre como usar as credenciais na DSC, consulte [tratamento de credenciais na DSC](../configurations/configDataCredentials.md)

```powershell
$ConfigurationData = @{
    AllNodes = @(
        @{
            NodeName                    = '*'
            PSDSCAllowPlainTextPassword = $true
        },
        @{
            NodeName = 'DSCPULL-1'
        }
    )
}

Configuration Example
{
    param
    (
        [Parameter(Mandatory = $true)]
        [System.Management.Automation.PSCredential]
        $ExchangeAdminCredential
    )

    Import-DscResource -Module xExchange
    Import-DscResource -Module xPendingReboot

    Node $AllNodes.NodeName
    {
        # Copy the Exchange setup files locally
        File ExchangeBinaries
        {
            Ensure          = 'Present'
            Type            = 'Directory'
            Recurse         = $true
            SourcePath      = '\\rras-1\Binaries\E15CU6'
            DestinationPath = 'C:\Binaries\E15CU6'
        }

        # Check if a reboot is needed before installing Exchange
        xPendingReboot BeforeExchangeInstall
        {
            Name       = 'BeforeExchangeInstall'
            DependsOn  = '[File]ExchangeBinaries'
        }

        # Do the Exchange install
        xExchInstall InstallExchange
        {
            Path       = 'C:\Binaries\E15CU6\Setup.exe'
            Arguments  = '/mode:Install /role:Mailbox /Iacceptexchangeserverlicenseterms'
            Credential = $ExchangeAdminCredential
            DependsOn  = '[xPendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        xPendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> Este exemplo pressupõe que você tenha configurado o Gerenciador de configurações Local para permitir reinicializações e continuar a configuração após uma reinicialização.

## <a name="where-to-download"></a>Onde fazer Download

Você pode baixar os recursos usados neste tópico, nos seguintes locais, ou usando a Galeria do PowerShell.

- [xPendingReboot](https://github.com/PowerShell/xPendingReboot)
- [xExchange](https://github.com/PowerShell/xExchange)
