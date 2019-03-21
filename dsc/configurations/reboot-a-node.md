---
ms.date: 1/17/2019
keywords: DSC,powershell,configuração,instalação
title: Reiniciar um nó
ms.openlocfilehash: 015b82a32caefc420973651c72e272fd85baf880
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58054723"
---
# <a name="reboot-a-node"></a>Reiniciar um nó

> [!NOTE]
> Este tópico aborda a reinicialização de um nó. Para que a reinicialização seja bem-sucedida, as configurações do LCM **ActionAfterReboot** e **RebootNodeIfNeeded** precisam ser definidas corretamente.
> Para ler sobre as configurações do Gerenciador de Configurações Local, confira [Configurar o Gerenciador de Configurações Local](../managing-nodes/metaConfig.md) ou [Configurar o Gerenciador de Configurações Local (v4)](../managing-nodes/metaConfig4.md).

É possível reinicializar nós de dentro de um recurso usando o sinalizador `$global:DSCMachineStatus`. Definir esse sinalizador como `1` na função `Set-TargetResource` força o LCM a reinicializar o nó diretamente após o método **Set** do recurso atual. Usando este sinalizador, o recurso **xPendingReboot** detecta se uma reinicialização está pendente fora do DSC.

Suas [configurações](configurations.md) podem executar etapas que exigem a reinicialização do nó. Essas etapas poderiam incluir:

- Atualizações do Windows
- Instalações de software
- Renomeações de arquivo
- Renomeações de computador

O recurso **xPendingReboot** verifica locais específicos do computador para determinar se uma reinicialização está pendente. Se o nó exigir uma reinicialização fora do DSC, o recurso **xPendingReboot** definirá o sinalizador `$global:DSCMachineStatus` como `1`, forçando uma reinicialização e resolvendo a condição pendente.

> [!NOTE]
> Qualquer recurso de DSC pode instruir o LCM a reinicializar o nó definindo esse sinalizador na função `Set-TargetResource`. Para obter mais informações, confira [Escrevendo um recurso personalizado de DSC com MOF](../resources/authoringResourceMOF.md).

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
| SkipComponentBasedServicing | Ignorar reinicializações disparadas pelo componente de Serviço Baseado em Componente. |
| SkipWindowsUpdate | Ignorar reinicializações disparadas pelo Windows Update.|
| SkipPendingFileRename | Ignorar reinicializações com renomeação de arquivo pendente. |
| SkipCcmClientSDK | Ignorar reinicializações disparadas pelo cliente do ConfigMgr. |
| SkipComputerRename | Ignorar reinicializações disparadas por renomeações de computador. |
| PSDSCRunAsCredential | Com suporte na v5. Executa o recurso como o usuário especificado. |
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`. Para obter mais informações, confira [Usando DependsOn](resource-depends-on.md)|

## <a name="example"></a>Exemplo

O exemplo a seguir instala o Microsoft Exchange usando o recurso [xExchange](https://github.com/PowerShell/xExchange).
Durante a instalação, o recurso **xPendingReboot** é usado para reinicializar o nó.

> [!NOTE]
> Esse exemplo requer a credencial de uma conta com direitos para adicionar um servidor do Exchange à floresta. Para obter mais informações sobre como usar credenciais na DSC, confira [Lidando com Credenciais na DSC](../configurations/configDataCredentials.md)

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
> Este exemplo pressupõe que você tenha configurado o Gerenciador de Configurações Local para permitir reinicializações e continuar a configuração após uma reinicialização.

## <a name="where-to-download"></a>Onde baixar

Você pode baixar os recursos usados neste tópico nos seguintes locais ou usando a Galeria do PowerShell.

- [xPendingReboot](https://github.com/PowerShell/xPendingReboot)
- [xExchange](https://github.com/PowerShell/xExchange)
