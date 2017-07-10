---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Especificando dependências de nó cruzado"
ms.openlocfilehash: dcdf9f8ef4b74d23bd083767db2cc4aafc0ee83b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
<a id="specifying-cross-node-dependencies" class="xliff"></a>
# Especificando dependências de nó cruzado

> Aplica-se a: Windows PowerShell 5.0

O DSC fornece recursos especiais, **WaitForAll**, **WaitForAny**, e **WaitForSome** que podem ser usados em configurações para especificar dependências em configurações em outros nós. O comportamento desses recursos é o seguinte:

* **WaitForAll**: terá êxito se o recurso especificado estiver no estado desejado em todos os nós de destino definidos na propriedade **NodeName**.
* **WaitForAny**: terá êxito se o recurso especificado estiver no estado desejado em pelo menos um dos nós de destino definidos na propriedade **NodeName**.
* **WaitForSome**: especifica uma propriedade **NodeCount** além de uma propriedade **NodeName**. O recurso terá êxito se estiver no estado desejado em um número mínimo de nós (especificado por **NodeCount**) definido pela propriedade **NodeName**. 

<a id="using-waitforxxxx-resources" class="xliff"></a>
## Usando os recursos WaitForXXXX

Para usar os recursos **WaitForXXXX**, você cria um bloco de recursos desse tipo de recurso que especifica o recurso DSC e os nós a serem esperados. Em seguida, use a propriedade **DependsOn** em quaisquer outros blocos de recursos em sua configuração para aguardar que as condições especificadas no nó **WaitForXXXX** sejam bem-sucedidas.

Por exemplo, na configuração a seguir, o nó de destino aguarda que o recurso **xADDomain** seja concluído no nó **MyDC** com um número máximo de 30 novas tentativas, em intervalos de 15 segundos, antes que o nó de destino possa se unir ao domínio.

```powershell
Configuration JoinDomain

{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myPC
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

<a id="see-also" class="xliff"></a>
## Consulte Também
* [Configurações DSC](configurations.md)
* [Recursos de DSC](resources.md)
* [Configurando o Gerenciador de Configurações Local](metaConfig.md)

