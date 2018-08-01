---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recurso nxService de DSC para Linux
ms.openlocfilehash: fe8043995205649378725f2ab0a78e19313739c9
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39267772"
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="8e21c-103">Recurso nxService de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="8e21c-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="8e21c-104">O recurso **nxService** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para gerenciar serviços em um nó do Linux.</span><span class="sxs-lookup"><span data-stu-id="8e21c-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="8e21c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e21c-105">Syntax</span></span>

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="8e21c-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="8e21c-106">Properties</span></span>

| <span data-ttu-id="8e21c-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="8e21c-107">Property</span></span> | <span data-ttu-id="8e21c-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e21c-108">Description</span></span> |
|---|---|
| <span data-ttu-id="8e21c-109">Nome</span><span class="sxs-lookup"><span data-stu-id="8e21c-109">Name</span></span>| <span data-ttu-id="8e21c-110">O nome do serviço/daemon que será configurado.</span><span class="sxs-lookup"><span data-stu-id="8e21c-110">The name of the service/daemon to configure.</span></span>|
| <span data-ttu-id="8e21c-111">Controlador</span><span class="sxs-lookup"><span data-stu-id="8e21c-111">Controller</span></span>| <span data-ttu-id="8e21c-112">O tipo de controlador de serviço que deve ser usado ao configurar o serviço.</span><span class="sxs-lookup"><span data-stu-id="8e21c-112">The type of service controller to use when configuring the service.</span></span>|
| <span data-ttu-id="8e21c-113">Habilitada</span><span class="sxs-lookup"><span data-stu-id="8e21c-113">Enabled</span></span>| <span data-ttu-id="8e21c-114">Indica se o serviço começa na inicialização.</span><span class="sxs-lookup"><span data-stu-id="8e21c-114">Indicates whether the service starts on boot.</span></span>|
| <span data-ttu-id="8e21c-115">Estado</span><span class="sxs-lookup"><span data-stu-id="8e21c-115">State</span></span>| <span data-ttu-id="8e21c-116">Indica se o serviço está em execução.</span><span class="sxs-lookup"><span data-stu-id="8e21c-116">Indicates whether the service is running.</span></span> <span data-ttu-id="8e21c-117">Defina essa propriedade como "Stopped" para garantir que o serviço não esteja em execução.</span><span class="sxs-lookup"><span data-stu-id="8e21c-117">Set this property to "Stopped" to ensure that the service is not running.</span></span> <span data-ttu-id="8e21c-118">Defina-a como "Running" para garantir que o serviço esteja em execução.</span><span class="sxs-lookup"><span data-stu-id="8e21c-118">Set it to "Running" to ensure that the service is not running.</span></span>|
| <span data-ttu-id="8e21c-119">DependsOn</span><span class="sxs-lookup"><span data-stu-id="8e21c-119">DependsOn</span></span> | <span data-ttu-id="8e21c-120">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="8e21c-120">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8e21c-121">Por exemplo, se a **ID** do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="8e21c-121">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="8e21c-122">Informações adicionais</span><span class="sxs-lookup"><span data-stu-id="8e21c-122">Additional Information</span></span>

<span data-ttu-id="8e21c-123">O recurso **nxService** não criará uma definição de serviço ou um script para o serviço se não existir.</span><span class="sxs-lookup"><span data-stu-id="8e21c-123">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="8e21c-124">É possível usar o recurso **nxFile** de Configuração de Estado Desejado do PowerShell para gerenciar a existência ou o conteúdo do arquivo ou script de definição de serviço.</span><span class="sxs-lookup"><span data-stu-id="8e21c-124">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="8e21c-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8e21c-125">Example</span></span>

<span data-ttu-id="8e21c-126">O exemplo a seguir mostra a configuração do serviço 'httpd' (para o Apache HTTP Server), registrado com o controlador de serviço **SystemD**.</span><span class="sxs-lookup"><span data-stu-id="8e21c-126">The following example shows configuration of the 'httpd' service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node {
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```