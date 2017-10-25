---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Especificando dependências de nó cruzado"
ms.openlocfilehash: 885c130fb050629aac4c072e18a147d77b9deb8f
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/27/2017
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="1c3dc-103">Especificando dependências de nó cruzado</span><span class="sxs-lookup"><span data-stu-id="1c3dc-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="1c3dc-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1c3dc-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="1c3dc-105">O DSC fornece recursos especiais, **WaitForAll**, **WaitForAny**, e **WaitForSome** que podem ser usados em configurações para especificar dependências em configurações em outros nós.</span><span class="sxs-lookup"><span data-stu-id="1c3dc-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="1c3dc-106">O comportamento desses recursos é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1c3dc-106">The behavior of these resources is as follows:</span></span>

* <span data-ttu-id="1c3dc-107">**WaitForAll**: terá êxito se o recurso especificado estiver no estado desejado em todos os nós de destino definidos na propriedade **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="1c3dc-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="1c3dc-108">**WaitForAny**: terá êxito se o recurso especificado estiver no estado desejado em pelo menos um dos nós de destino definidos na propriedade **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="1c3dc-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="1c3dc-109">**WaitForSome**: especifica uma propriedade **NodeCount** além de uma propriedade **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="1c3dc-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="1c3dc-110">O recurso terá êxito se estiver no estado desejado em um número mínimo de nós (especificado por **NodeCount**) definido pela propriedade **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="1c3dc-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="1c3dc-111">Usando os recursos WaitForXXXX</span><span class="sxs-lookup"><span data-stu-id="1c3dc-111">Using WaitForXXXX resources</span></span>

<span data-ttu-id="1c3dc-112">Para usar os recursos **WaitForXXXX**, você cria um bloco de recursos desse tipo de recurso que especifica o recurso DSC e os nós a serem esperados.</span><span class="sxs-lookup"><span data-stu-id="1c3dc-112">To use the **WaitForXXXX** resources, you create a resource block of that resource type that specifies the DSC resource and node(s) to wait for.</span></span> <span data-ttu-id="1c3dc-113">Em seguida, use a propriedade **DependsOn** em quaisquer outros blocos de recursos em sua configuração para aguardar que as condições especificadas no nó **WaitForXXXX** sejam bem-sucedidas.</span><span class="sxs-lookup"><span data-stu-id="1c3dc-113">You then use the **DependsOn** property in any other resource blocks in your configuration to wait for the conditions specified in the **WaitForXXXX** node to succeed.</span></span>

<span data-ttu-id="1c3dc-114">Por exemplo, na configuração a seguir, o nó de destino aguarda que o recurso **xADDomain** seja concluído no nó **MyDC** com um número máximo de 30 novas tentativas, em intervalos de 15 segundos, antes que o nó de destino possa se unir ao domínio.</span><span class="sxs-lookup"><span data-stu-id="1c3dc-114">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

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

><span data-ttu-id="1c3dc-115">**Observação:** por padrão, os recursos WaitForXXX tentam uma vez e, em seguida, falham.</span><span class="sxs-lookup"><span data-stu-id="1c3dc-115">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="1c3dc-116">Embora não seja obrigatório, você geralmente deve especificar um intervalo de repetição e uma contagem.</span><span class="sxs-lookup"><span data-stu-id="1c3dc-116">Although it is not required, you will typically want to specify a retry interval and count.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c3dc-117">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="1c3dc-117">See Also</span></span>
* [<span data-ttu-id="1c3dc-118">Configurações DSC</span><span class="sxs-lookup"><span data-stu-id="1c3dc-118">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="1c3dc-119">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="1c3dc-119">DSC Resources</span></span>](resources.md)
* [<span data-ttu-id="1c3dc-120">Configurando o Gerenciador de Configurações Local</span><span class="sxs-lookup"><span data-stu-id="1c3dc-120">Configuring The Local Configuration Manager</span></span>](metaConfig.md)

