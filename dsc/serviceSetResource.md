---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: Recurso do ServiceSet DSC
ms.openlocfilehash: 92fa4a442eb42e89195162b7831f1a96d40b84f5
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="10aac-103">Recurso do ServiceSet DSC</span><span class="sxs-lookup"><span data-stu-id="10aac-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="10aac-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="10aac-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="10aac-105">O recurso **ServiceSet** na DSC (Configuração de Estado Desejado) do Windows PowerShell oferece um mecanismo para gerenciar serviços no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="10aac-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="10aac-106">Esse recurso é um [recurso composto](authoringResourceComposite.md) que chama o [Recurso de serviço](serviceResource.md) para cada serviço especificado na propriedade `Name`.</span><span class="sxs-lookup"><span data-stu-id="10aac-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the `Name` property.</span></span>

<span data-ttu-id="10aac-107">Use esse recurso quando desejar configurar vários serviços para o mesmo estado.</span><span class="sxs-lookup"><span data-stu-id="10aac-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="10aac-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="10aac-108">Syntax</span></span>

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a><span data-ttu-id="10aac-109">Propriedades</span><span class="sxs-lookup"><span data-stu-id="10aac-109">Properties</span></span>

|  <span data-ttu-id="10aac-110">Propriedade</span><span class="sxs-lookup"><span data-stu-id="10aac-110">Property</span></span>  |  <span data-ttu-id="10aac-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="10aac-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="10aac-112">Nome</span><span class="sxs-lookup"><span data-stu-id="10aac-112">Name</span></span>| <span data-ttu-id="10aac-113">Indica os nomes do serviço.</span><span class="sxs-lookup"><span data-stu-id="10aac-113">Indicates the service names.</span></span> <span data-ttu-id="10aac-114">Observe que, às vezes, isso é diferente dos nomes de exibição.</span><span class="sxs-lookup"><span data-stu-id="10aac-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="10aac-115">É possível obter uma lista dos serviços e seus estados atuais com o cmdlet [Get-Service](https://technet.microsoft.com/en-us/library/hh849804.aspx).</span><span class="sxs-lookup"><span data-stu-id="10aac-115">You can get a list of the services and their current state with the [Get-Service](https://technet.microsoft.com/en-us/library/hh849804.aspx) cmdlet.</span></span>|
| <span data-ttu-id="10aac-116">StartupType</span><span class="sxs-lookup"><span data-stu-id="10aac-116">StartupType</span></span>| <span data-ttu-id="10aac-117">Indica o tipo de inicialização para o serviço.</span><span class="sxs-lookup"><span data-stu-id="10aac-117">Indicates the startup type for the service.</span></span> <span data-ttu-id="10aac-118">Os valores permitidos para essa propriedade são: **Automatic**, **Disabled** e **Manual**</span><span class="sxs-lookup"><span data-stu-id="10aac-118">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|  
| <span data-ttu-id="10aac-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="10aac-119">BuiltInAccount</span></span>| <span data-ttu-id="10aac-120">Indica a conta de credenciais a ser usada para os serviços.</span><span class="sxs-lookup"><span data-stu-id="10aac-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="10aac-121">Os valores permitidos para essa propriedade são: **LocalService**, **LocalSystem** e **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="10aac-121">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>| 
| <span data-ttu-id="10aac-122">Estado</span><span class="sxs-lookup"><span data-stu-id="10aac-122">State</span></span>| <span data-ttu-id="10aac-123">Indica o estado que você deseja garantir para os serviços: **Parado** ou **Em execução**.</span><span class="sxs-lookup"><span data-stu-id="10aac-123">Indicates the state you want to ensure for the services: **Stopped** or **Running**.</span></span>| 
| <span data-ttu-id="10aac-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="10aac-124">Ensure</span></span>| <span data-ttu-id="10aac-125">Indica se os serviços existem no sistema.</span><span class="sxs-lookup"><span data-stu-id="10aac-125">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="10aac-126">Defina essa propriedade como **Ausente** para garantir que os serviços não existam.</span><span class="sxs-lookup"><span data-stu-id="10aac-126">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="10aac-127">Configurá-la como **Present** (o valor padrão) garantirá que os serviços de destino existam.</span><span class="sxs-lookup"><span data-stu-id="10aac-127">Setting it to **Present** (the default value) ensures that target services exist.</span></span>|
| <span data-ttu-id="10aac-128">Credential</span><span class="sxs-lookup"><span data-stu-id="10aac-128">Credential</span></span>| <span data-ttu-id="10aac-129">Indica as credenciais para a conta sob a qual o serviço será executado.</span><span class="sxs-lookup"><span data-stu-id="10aac-129">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="10aac-130">Essa propriedade e a propriedade **BuiltinAccount** não podem ser usadas juntas.</span><span class="sxs-lookup"><span data-stu-id="10aac-130">This property and the **BuiltinAccount** property cannot be used together.</span></span>| 
| <span data-ttu-id="10aac-131">DependsOn</span><span class="sxs-lookup"><span data-stu-id="10aac-131">DependsOn</span></span>| <span data-ttu-id="10aac-132">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="10aac-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="10aac-133">Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for *ResourceName* e seu tipo for *ResourceType*, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="10aac-133">For example, if the ID of the resource configuration script block that you want to run first is *ResourceName* and its type is *ResourceType*, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 



## <a name="example"></a><span data-ttu-id="10aac-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="10aac-134">Example</span></span>

<span data-ttu-id="10aac-135">A configuração a seguir inicia os serviços "Áudio do Windows" e "Serviços de Área de Trabalho Remota".</span><span class="sxs-lookup"><span data-stu-id="10aac-135">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        } 
    }
}
```

