---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Especificando dependências de nó cruzado
ms.openlocfilehash: c1802d6baa1f2b3449603e0374a83e213abf598e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218613"
---
# <a name="specifying-cross-node-dependencies"></a>Especificando dependências de nó cruzado

> Aplica-se a: Windows PowerShell 5.0

O DSC fornece recursos especiais, **WaitForAll**, **WaitForAny**, e **WaitForSome** que podem ser usados em configurações para especificar dependências em configurações em outros nós. O comportamento desses recursos é o seguinte:

* **WaitForAll**: terá êxito se o recurso especificado estiver no estado desejado em todos os nós de destino definidos na propriedade **NodeName**.
* **WaitForAny**: terá êxito se o recurso especificado estiver no estado desejado em pelo menos um dos nós de destino definidos na propriedade **NodeName**.
* **WaitForSome**: especifica uma propriedade **NodeCount** além de uma propriedade **NodeName**. O recurso terá êxito se estiver no estado desejado em um número mínimo de nós (especificado por **NodeCount**) definido pela propriedade **NodeName**.

## <a name="using-waitforxxxx-resources"></a>Usando os recursos WaitForXXXX

Para usar os recursos **WaitForXXXX**, você cria um bloco de recursos desse tipo de recurso que especifica o recurso DSC e os nós a serem esperados. Em seguida, use a propriedade **DependsOn** em quaisquer outros blocos de recursos em sua configuração para aguardar que as condições especificadas no nó **WaitForXXXX** sejam bem-sucedidas.

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

>**Observação:** por padrão, os recursos WaitForXXX tentam uma vez e, em seguida, falham. Embora não seja obrigatório, você geralmente deve especificar um intervalo de repetição e uma contagem.

## <a name="see-also"></a>Consulte Também
* [Configurações DSC](configurations.md)
* [Recursos de DSC](resources.md)
* [Configurando o Gerenciador de Configurações Local](metaConfig.md)