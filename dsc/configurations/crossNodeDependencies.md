---
ms.date: 12/12/2018
keywords: DSC,powershell,configuração,instalação
title: Especificando dependências de nó cruzado
ms.openlocfilehash: 1bdfbd9f8a94809d6bf410eff525e1c877fb6aad
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400116"
---
# <a name="specifying-cross-node-dependencies"></a>Especificando dependências de nó cruzado

> Aplica-se a: Windows PowerShell 5.0

O DSC fornece recursos especiais, **WaitForAll**, **WaitForAny**, e **WaitForSome** que podem ser usados em configurações para especificar dependências em configurações em outros nós. O comportamento desses recursos é o seguinte:

- **WaitForAll**: Terá êxito se o recurso especificado está no estado desejado em todos os nós de destino definido na **NodeName** propriedade.
- **WaitForAny**: Terá êxito se o recurso especificado está no estado desejado em pelo menos um de nós de destino definidos na **NodeName** propriedade.
- **WaitForSome**: Especifica um **NodeCount** propriedade além uma **NodeName** propriedade. O recurso terá êxito se estiver no estado desejado em um número mínimo de nós (especificado por **NodeCount**) definido pela propriedade **NodeName**.

## <a name="syntax"></a>Sintaxe

O **WaitForAll** e **WaitForAny** recursos compartilham a mesma sintaxe. Substitua \<ResourceType\> no exemplo a seguir com um **WaitForAny** ou **WaitForAll**.
Como o **DependsOn** palavra-chave, será necessário formatar o nome como "[ResourceType] ResourceName". Se o recurso pertence a um separado [Configuration](configurations.md), incluem o **ConfigurationName** na cadeia de caracteres formatada "[ResourceType] ResourceName:: [ConfigurationName]:: [ConfigurationName]". O **NodeName** é o computador ou o nó, na qual o recurso atual deve aguardar.

```
<ResourceType> [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential]]
    [ RetryCount = [Uint32] ]
    [ RetryIntervalSec = [Uint64] ]
    [ ThrottleLimit = [Uint32]]
}
```

O **WaitForSome** recurso tem uma sintaxe semelhante ao exemplo acima, mas adiciona o **NodeCount** chave. O **NodeCount** indica quantos nós deve aguardar o recurso atual.

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

Todos os **WaitForXXXX** compartilhar as chaves de sintaxe a seguir.

|  Propriedade |  Descrição | | RetryIntervalSec | O número de segundos antes de tentar novamente. Mínimo é 1. | | RetryCount | O número máximo de tentativas. | | ThrottleLimit | Número de máquinas para se conectar simultaneamente. O padrão é `New-CimSession` padrão. | | DependsOn | Indica que a configuração de outro recurso deve ser executada antes dele ser configurado. Para obter mais informações, consulte [DependsOn](resource-depends-on.md)| | PsDscRunAsCredential | Consulte [usando DSC com credenciais de usuário](./runAsUser.md) |


## <a name="using-waitforxxxx-resources"></a>Usando os recursos WaitForXXXX

Cada **WaitForXXXX** recurso aguarda para que os recursos especificados ser concluída no nó especificado. Outros recursos na mesma configuração podem, em seguida, *dependem* as **WaitForXXXX** recursos usando o **DependsOn** chave.

Por exemplo, na configuração a seguir, o nó de destino aguarda que o recurso **xADDomain** seja concluído no nó **MyDC** com um número máximo de 30 novas tentativas, em intervalos de 15 segundos, antes que o nó de destino possa se unir ao domínio.

```powershell
Configuration JoinDomain
{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain NewDomain
        {
            DomainName = 'Contoso.com'
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }
    }

    Node myDomainJoinedServer
    {
        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

Quando você compila a configuração, são gerados dois arquivos ". MOF". Se aplicam a ambos os arquivos ". MOF" a nós de destino usando o [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet

>**Observação:** Por padrão o WaitForXXX recursos tentam uma vez e, em seguida, falham. Embora não seja necessário, você geralmente deseja especificar uma **RetryCount** e **RetryIntervalSec**.

## <a name="see-also"></a>Consulte Também

- [Configurações DSC](configurations.md)
- [Usar dependências de recursos](resource-depends-on.md)
- [Recursos de DSC](../resources/resources.md)
- [Configurando o Gerenciador de Configurações Local](../managing-nodes/metaConfig.md)
