---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: Recurso de DSC WaitForAny
ms.openlocfilehash: 795c005c67c196ef9afb08af790fe2a1695392ec
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="6510d-103">Recurso de DSC WaitForAny</span><span class="sxs-lookup"><span data-stu-id="6510d-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="6510d-104">Aplica-se a: Windows PowerShell 5.1 e posterior</span><span class="sxs-lookup"><span data-stu-id="6510d-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="6510d-105">O recurso de DSC (Desired State Configuration) **WaitForSome** pode ser usado dentro de um bloco de nó em uma [configuração DSC](configurations.md) para especificar dependências de configurações em outros nós.</span><span class="sxs-lookup"><span data-stu-id="6510d-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="6510d-106">Esse recurso terá êxito se o recurso especificado pela propriedade **ResourceName** estiver no estado desejado em qualquer nó de destino definido na propriedade **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="6510d-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="6510d-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6510d-107">Syntax</span></span>

```
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="6510d-108">Propriedades</span><span class="sxs-lookup"><span data-stu-id="6510d-108">Properties</span></span>

|  <span data-ttu-id="6510d-109">Propriedade</span><span class="sxs-lookup"><span data-stu-id="6510d-109">Property</span></span>  |  <span data-ttu-id="6510d-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="6510d-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="6510d-111">ResourceName</span><span class="sxs-lookup"><span data-stu-id="6510d-111">ResourceName</span></span>| <span data-ttu-id="6510d-112">O nome do recurso do qual dependerá.</span><span class="sxs-lookup"><span data-stu-id="6510d-112">The resource name to depend on.</span></span>| 
| <span data-ttu-id="6510d-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="6510d-113">NodeName</span></span>| <span data-ttu-id="6510d-114">Os nós de destino do recurso do qual dependerá.</span><span class="sxs-lookup"><span data-stu-id="6510d-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="6510d-115">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="6510d-115">RetryIntervalSec</span></span>| <span data-ttu-id="6510d-116">O número de segundos antes de tentar novamente.</span><span class="sxs-lookup"><span data-stu-id="6510d-116">The number of seconds before retrying.</span></span> <span data-ttu-id="6510d-117">O mínimo é 1.</span><span class="sxs-lookup"><span data-stu-id="6510d-117">Minimum is 1.</span></span>| 
| <span data-ttu-id="6510d-118">RetryCount</span><span class="sxs-lookup"><span data-stu-id="6510d-118">RetryCount</span></span>| <span data-ttu-id="6510d-119">O número máximo de tentativas.</span><span class="sxs-lookup"><span data-stu-id="6510d-119">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="6510d-120">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="6510d-120">ThrottleLimit</span></span>| <span data-ttu-id="6510d-121">O número de máquinas para conectar-se simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="6510d-121">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="6510d-122">O padrão é new-cimsession padrão.</span><span class="sxs-lookup"><span data-stu-id="6510d-122">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="6510d-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6510d-123">DependsOn</span></span> | <span data-ttu-id="6510d-124">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="6510d-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6510d-125">Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="6510d-125">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="6510d-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6510d-126">Example</span></span>

<span data-ttu-id="6510d-127">Para obter um exemplo de como usar esse recurso, consulte [Especificando dependências de nó cruzado](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="6510d-127">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

