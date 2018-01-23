---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: Recurso nxService de DSC para Linux
ms.openlocfilehash: 4273ad59f15eedd08b07888ebb6ee51d039b72b3
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="df642-103">Recurso nxService de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="df642-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="df642-104">O recurso **nxService** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para gerenciar serviços em um nó do Linux.</span><span class="sxs-lookup"><span data-stu-id="df642-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="df642-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df642-105">Syntax</span></span>

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd }  ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="df642-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="df642-106">Properties</span></span>
|  <span data-ttu-id="df642-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="df642-107">Property</span></span> |  <span data-ttu-id="df642-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="df642-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="df642-109">Nome</span><span class="sxs-lookup"><span data-stu-id="df642-109">Name</span></span>| <span data-ttu-id="df642-110">O nome do serviço/daemon que será configurado.</span><span class="sxs-lookup"><span data-stu-id="df642-110">The name of the service/daemon to configure.</span></span>| 
| <span data-ttu-id="df642-111">Controlador</span><span class="sxs-lookup"><span data-stu-id="df642-111">Controller</span></span>| <span data-ttu-id="df642-112">O tipo de controlador de serviço que deve ser usado ao configurar o serviço.</span><span class="sxs-lookup"><span data-stu-id="df642-112">The type of service controller to use when configuring the service.</span></span>| 
| <span data-ttu-id="df642-113">Habilitada</span><span class="sxs-lookup"><span data-stu-id="df642-113">Enabled</span></span>| <span data-ttu-id="df642-114">Indica se o serviço começa na inicialização.</span><span class="sxs-lookup"><span data-stu-id="df642-114">Indicates whether the service starts on boot.</span></span>| 
| <span data-ttu-id="df642-115">Estado</span><span class="sxs-lookup"><span data-stu-id="df642-115">State</span></span>| <span data-ttu-id="df642-116">Indica se o serviço está em execução.</span><span class="sxs-lookup"><span data-stu-id="df642-116">Indicates whether the service is running.</span></span> <span data-ttu-id="df642-117">Defina essa propriedade como "Stopped" para garantir que o serviço não esteja em execução.</span><span class="sxs-lookup"><span data-stu-id="df642-117">Set this property to "Stopped" to ensure that the service is not running.</span></span> <span data-ttu-id="df642-118">Defina-a como "Running" para garantir que o serviço esteja em execução.</span><span class="sxs-lookup"><span data-stu-id="df642-118">Set it to "Running" to ensure that the service is not running.</span></span>| 
| <span data-ttu-id="df642-119">DependsOn</span><span class="sxs-lookup"><span data-stu-id="df642-119">DependsOn</span></span> | <span data-ttu-id="df642-120">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="df642-120">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="df642-121">Por exemplo, se a **ID** do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="df642-121">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 


## <a name="additional-information"></a><span data-ttu-id="df642-122">Informações adicionais</span><span class="sxs-lookup"><span data-stu-id="df642-122">Additional Information</span></span>

<span data-ttu-id="df642-123">O recurso **nxService** não criará uma definição de serviço ou um script para o serviço se não existir.</span><span class="sxs-lookup"><span data-stu-id="df642-123">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="df642-124">É possível usar o recurso **nxFile** de Configuração de Estado Desejado do PowerShell para gerenciar a existência ou o conteúdo do arquivo ou script de definição de serviço.</span><span class="sxs-lookup"><span data-stu-id="df642-124">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="df642-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df642-125">Example</span></span>

<span data-ttu-id="df642-126">O exemplo a seguir mostra a configuração do serviço “httpd” (para o Apache HTTP Server), registrado com o controlador de serviço **SystemD**.</span><span class="sxs-lookup"><span data-stu-id="df642-126">The following example shows configuration of the “httpd” service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

```
Import-DSCResource -Module nx 

Node $node {
#Apache Service
nxService ApacheService 
{
Name = "httpd"
State = "running"
Enabled = $true
Controller = "systemd"
}
}
```

