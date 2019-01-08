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
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="d3492-103">Especificando dependências de nó cruzado</span><span class="sxs-lookup"><span data-stu-id="d3492-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="d3492-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d3492-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="d3492-105">O DSC fornece recursos especiais, **WaitForAll**, **WaitForAny**, e **WaitForSome** que podem ser usados em configurações para especificar dependências em configurações em outros nós.</span><span class="sxs-lookup"><span data-stu-id="d3492-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="d3492-106">O comportamento desses recursos é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d3492-106">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="d3492-107">**WaitForAll**: Terá êxito se o recurso especificado está no estado desejado em todos os nós de destino definido na **NodeName** propriedade.</span><span class="sxs-lookup"><span data-stu-id="d3492-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="d3492-108">**WaitForAny**: Terá êxito se o recurso especificado está no estado desejado em pelo menos um de nós de destino definidos na **NodeName** propriedade.</span><span class="sxs-lookup"><span data-stu-id="d3492-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="d3492-109">**WaitForSome**: Especifica um **NodeCount** propriedade além uma **NodeName** propriedade.</span><span class="sxs-lookup"><span data-stu-id="d3492-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="d3492-110">O recurso terá êxito se estiver no estado desejado em um número mínimo de nós (especificado por **NodeCount**) definido pela propriedade **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="d3492-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="d3492-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d3492-111">Syntax</span></span>

<span data-ttu-id="d3492-112">O **WaitForAll** e **WaitForAny** recursos compartilham a mesma sintaxe.</span><span class="sxs-lookup"><span data-stu-id="d3492-112">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="d3492-113">Substitua \<ResourceType\> no exemplo a seguir com um **WaitForAny** ou **WaitForAll**.</span><span class="sxs-lookup"><span data-stu-id="d3492-113">Replace \<ResourceType\> in the example below with either **WaitForAny** or **WaitForAll**.</span></span>
<span data-ttu-id="d3492-114">Como o **DependsOn** palavra-chave, será necessário formatar o nome como "[ResourceType] ResourceName".</span><span class="sxs-lookup"><span data-stu-id="d3492-114">Like the **DependsOn** keyword, you will need to format the name as "[ResourceType]ResourceName".</span></span> <span data-ttu-id="d3492-115">Se o recurso pertence a um separado [Configuration](configurations.md), incluem o **ConfigurationName** na cadeia de caracteres formatada "[ResourceType] ResourceName:: [ConfigurationName]:: [ConfigurationName]".</span><span class="sxs-lookup"><span data-stu-id="d3492-115">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span></span> <span data-ttu-id="d3492-116">O **NodeName** é o computador ou o nó, na qual o recurso atual deve aguardar.</span><span class="sxs-lookup"><span data-stu-id="d3492-116">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

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

<span data-ttu-id="d3492-117">O **WaitForSome** recurso tem uma sintaxe semelhante ao exemplo acima, mas adiciona o **NodeCount** chave.</span><span class="sxs-lookup"><span data-stu-id="d3492-117">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="d3492-118">O **NodeCount** indica quantos nós deve aguardar o recurso atual.</span><span class="sxs-lookup"><span data-stu-id="d3492-118">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

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

<span data-ttu-id="d3492-119">Todos os **WaitForXXXX** compartilhar as chaves de sintaxe a seguir.</span><span class="sxs-lookup"><span data-stu-id="d3492-119">All **WaitForXXXX** share the following syntax keys.</span></span>

<span data-ttu-id="d3492-120">|  Propriedade |  Descrição | | RetryIntervalSec | O número de segundos antes de tentar novamente.</span><span class="sxs-lookup"><span data-stu-id="d3492-120">|  Property  |  Description   | | RetryIntervalSec| The number of seconds before retrying.</span></span> <span data-ttu-id="d3492-121">Mínimo é 1. | | RetryCount | O número máximo de tentativas. | | ThrottleLimit | Número de máquinas para se conectar simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="d3492-121">Minimum is 1.| | RetryCount| The maximum number of times to retry.| | ThrottleLimit| Number of machines to connect simultaneously.</span></span> <span data-ttu-id="d3492-122">O padrão é `New-CimSession` padrão. | | DependsOn | Indica que a configuração de outro recurso deve ser executada antes dele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="d3492-122">Default is `New-CimSession` default.| | DependsOn | Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d3492-123">Para obter mais informações, consulte [DependsOn](resource-depends-on.md)| | PsDscRunAsCredential | Consulte [usando DSC com credenciais de usuário](./runAsUser.md) |</span><span class="sxs-lookup"><span data-stu-id="d3492-123">For more information, see [DependsOn](resource-depends-on.md)| | PsDscRunAsCredential | See [Using DSC with User Credentials](./runAsUser.md) |</span></span>


## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="d3492-124">Usando os recursos WaitForXXXX</span><span class="sxs-lookup"><span data-stu-id="d3492-124">Using WaitForXXXX resources</span></span>

<span data-ttu-id="d3492-125">Cada **WaitForXXXX** recurso aguarda para que os recursos especificados ser concluída no nó especificado.</span><span class="sxs-lookup"><span data-stu-id="d3492-125">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span> <span data-ttu-id="d3492-126">Outros recursos na mesma configuração podem, em seguida, *dependem* as **WaitForXXXX** recursos usando o **DependsOn** chave.</span><span class="sxs-lookup"><span data-stu-id="d3492-126">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="d3492-127">Por exemplo, na configuração a seguir, o nó de destino aguarda que o recurso **xADDomain** seja concluído no nó **MyDC** com um número máximo de 30 novas tentativas, em intervalos de 15 segundos, antes que o nó de destino possa se unir ao domínio.</span><span class="sxs-lookup"><span data-stu-id="d3492-127">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

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

<span data-ttu-id="d3492-128">Quando você compila a configuração, são gerados dois arquivos ". MOF".</span><span class="sxs-lookup"><span data-stu-id="d3492-128">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="d3492-129">Se aplicam a ambos os arquivos ". MOF" a nós de destino usando o [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span><span class="sxs-lookup"><span data-stu-id="d3492-129">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

><span data-ttu-id="d3492-130">**Observação:** Por padrão o WaitForXXX recursos tentam uma vez e, em seguida, falham.</span><span class="sxs-lookup"><span data-stu-id="d3492-130">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="d3492-131">Embora não seja necessário, você geralmente deseja especificar uma **RetryCount** e **RetryIntervalSec**.</span><span class="sxs-lookup"><span data-stu-id="d3492-131">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

## <a name="see-also"></a><span data-ttu-id="d3492-132">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="d3492-132">See Also</span></span>

- [<span data-ttu-id="d3492-133">Configurações DSC</span><span class="sxs-lookup"><span data-stu-id="d3492-133">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="d3492-134">Usar dependências de recursos</span><span class="sxs-lookup"><span data-stu-id="d3492-134">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="d3492-135">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="d3492-135">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="d3492-136">Configurando o Gerenciador de Configurações Local</span><span class="sxs-lookup"><span data-stu-id="d3492-136">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
