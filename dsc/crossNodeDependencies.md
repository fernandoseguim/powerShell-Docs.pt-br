---
title: "Especificando dependências de nó cruzado"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 04aa6292dee991060669e1ac770cf98cbba41bfc
ms.openlocfilehash: f4c64d3603fd01f29a63f8b180057714bf3d1197

---

# Especificando dependências de nó cruzado

> Aplica-se a: Windows PowerShell 5.0

O DSC fornece recursos especiais, **WaitForAll**, **WaitForAny**, e **WaitForSome** que podem ser usados em configurações para especificar dependências em configurações em outros nós. O comportamento desses recursos é o seguinte:

* **WaitForAll**: terá êxito se o recurso especificado estiver no estado desejado em todos os nós de destino definidos na propriedade **NodeName**.
* **WaitForAny**: terá êxito se o recurso especificado estiver no estado desejado em pelo menos um dos nós de destino definidos na propriedade **NodeName**.
* **WaitForSome**: especifica uma propriedade **NodeCount** além de uma propriedade **NodeName**. O recurso terá êxito se estiver no estado desejado em um número mínimo de nós (especificado por **NodeCount**) definido pela propriedade **NodeName**. 

## Usando os recursos WaitForXXXX

Para usar os recursos **WaitForXXXX**, você cria um bloco de recursos desse tipo de recurso que especifica o recurso DSC e os nós a serem esperados. Em seguida, use a propriedade **DependsOn** em quaisquer outros blocos de recursos em sua configuração para aguardar que as condições especificadas no nó **WaitForXXXX** sejam bem-sucedidas.

Por exemplo, na configuração a seguir, o nó de destino aguarda que o recurso **xADDomain** seja concluído no nó **MyDC** com um número máximo de 30 novas tentativas, em intervalos de 15 segundos, antes que o nó de destino possa se unir ao domínio.

```PowerShell
Configuration JoinDomain

{
    Import-DscResource -Module xComputerManagement

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
            Name             = 'MyPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

>**Observação:** por padrão, os recursos WaitForXXX tentam uma vez e, em seguida, falham. Embora não seja obrigatório, você geralmente deve especificar um intervalo de repetição e uma contagem.

## Consulte Também
* [Configurações DSC](configurations.md)
* [Recursos de DSC](resources.md)
* [Configurando o Gerenciador de Configurações Local](metaConfig.md)




<!--HONumber=Jun16_HO4-->


