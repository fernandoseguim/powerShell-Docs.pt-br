---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: Recurso de DSC WaitForSome
ms.openlocfilehash: 5d67a9111f6358240590b651e627ffb96abc0896
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="5c64c-103">Recurso de DSC WaitForSome</span><span class="sxs-lookup"><span data-stu-id="5c64c-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="5c64c-104">Aplica-se a: Windows PowerShell 5.0 e posterior</span><span class="sxs-lookup"><span data-stu-id="5c64c-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="5c64c-105">O recurso de DSC (Desired State Configuration) **WaitForAny** pode ser usado dentro de um bloco de nó em uma [configuração DSC](configurations.md) para especificar dependências de configurações em outros nós.</span><span class="sxs-lookup"><span data-stu-id="5c64c-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="5c64c-106">O recurso terá êxito se o recurso especificado pela propriedade **ResourceName** estiver no estado desejado em um número mínimo de nós (especificado por **NodeCount**) definidos pela propriedade **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="5c64c-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 


## <a name="syntax"></a><span data-ttu-id="5c64c-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5c64c-107">Syntax</span></span>

```
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    NodeCount = [Uint32]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="5c64c-108">Propriedades</span><span class="sxs-lookup"><span data-stu-id="5c64c-108">Properties</span></span>

|  <span data-ttu-id="5c64c-109">Propriedade</span><span class="sxs-lookup"><span data-stu-id="5c64c-109">Property</span></span>  |  <span data-ttu-id="5c64c-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c64c-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="5c64c-111">ResourceName</span><span class="sxs-lookup"><span data-stu-id="5c64c-111">ResourceName</span></span>| <span data-ttu-id="5c64c-112">O nome do recurso do qual dependerá.</span><span class="sxs-lookup"><span data-stu-id="5c64c-112">The resource name to depend on.</span></span>| 
| <span data-ttu-id="5c64c-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="5c64c-113">NodeName</span></span>| <span data-ttu-id="5c64c-114">Os nós de destino do recurso do qual dependerá.</span><span class="sxs-lookup"><span data-stu-id="5c64c-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="5c64c-115">NodeCount</span><span class="sxs-lookup"><span data-stu-id="5c64c-115">NodeCount</span></span>| <span data-ttu-id="5c64c-116">O número mínimo de nós que devem estar no estado desejado para que esse recurso tenha êxito.</span><span class="sxs-lookup"><span data-stu-id="5c64c-116">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="5c64c-117">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="5c64c-117">RetryIntervalSec</span></span>| <span data-ttu-id="5c64c-118">O número de segundos antes de tentar novamente.</span><span class="sxs-lookup"><span data-stu-id="5c64c-118">The number of seconds before retrying.</span></span> <span data-ttu-id="5c64c-119">O mínimo é 1.</span><span class="sxs-lookup"><span data-stu-id="5c64c-119">Minimum is 1.</span></span>| 
| <span data-ttu-id="5c64c-120">RetryCount</span><span class="sxs-lookup"><span data-stu-id="5c64c-120">RetryCount</span></span>| <span data-ttu-id="5c64c-121">O número máximo de tentativas.</span><span class="sxs-lookup"><span data-stu-id="5c64c-121">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="5c64c-122">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="5c64c-122">ThrottleLimit</span></span>| <span data-ttu-id="5c64c-123">O número de máquinas para conectar-se simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="5c64c-123">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="5c64c-124">O padrão é new-cimsession padrão.</span><span class="sxs-lookup"><span data-stu-id="5c64c-124">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="5c64c-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="5c64c-125">DependsOn</span></span> | <span data-ttu-id="5c64c-126">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="5c64c-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5c64c-127">Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="5c64c-127">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="5c64c-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5c64c-128">Example</span></span>

<span data-ttu-id="5c64c-129">Para obter um exemplo de como usar esse recurso, consulte [Especificando dependências de nó cruzado](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="5c64c-129">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

