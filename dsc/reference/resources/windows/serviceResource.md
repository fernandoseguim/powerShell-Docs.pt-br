---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recurso Service de DSC
ms.openlocfilehash: 09571bd0eaa428e7d0bb7a533d6ad1c0c936e2cf
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046995"
---
# <a name="dsc-service-resource"></a><span data-ttu-id="70c70-103">Recurso Service de DSC</span><span class="sxs-lookup"><span data-stu-id="70c70-103">DSC Service Resource</span></span>

> <span data-ttu-id="70c70-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="70c70-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="70c70-105">O recurso **Service** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para gerenciar serviços no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="70c70-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="70c70-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="70c70-106">Syntax</span></span>

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Path = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="70c70-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="70c70-107">Properties</span></span>

|  <span data-ttu-id="70c70-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="70c70-108">Property</span></span>  |  <span data-ttu-id="70c70-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="70c70-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="70c70-110">Nome</span><span class="sxs-lookup"><span data-stu-id="70c70-110">Name</span></span>| <span data-ttu-id="70c70-111">Indica o nome do serviço.</span><span class="sxs-lookup"><span data-stu-id="70c70-111">Indicates the service name.</span></span> <span data-ttu-id="70c70-112">Observe que, às vezes, é diferente do nome de exibição.</span><span class="sxs-lookup"><span data-stu-id="70c70-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="70c70-113">É possível obter uma lista dos serviços e seus estados atuais com o cmdlet Get-Service.</span><span class="sxs-lookup"><span data-stu-id="70c70-113">You can get a list of the services and their current state with the Get-Service cmdlet.</span></span>|
| <span data-ttu-id="70c70-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="70c70-114">BuiltInAccount</span></span>| <span data-ttu-id="70c70-115">Indica a conta de entrada que deve ser usada para o serviço.</span><span class="sxs-lookup"><span data-stu-id="70c70-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="70c70-116">Os valores permitidos para essa propriedade são: **LocalService**, **LocalSystem**, e **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="70c70-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>|
| <span data-ttu-id="70c70-117">Credential</span><span class="sxs-lookup"><span data-stu-id="70c70-117">Credential</span></span>| <span data-ttu-id="70c70-118">Indica as credenciais para a conta em que o serviço será executado.</span><span class="sxs-lookup"><span data-stu-id="70c70-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="70c70-119">Essa propriedade e a propriedade __BuiltinAccount__ não podem ser usadas juntas.</span><span class="sxs-lookup"><span data-stu-id="70c70-119">This property and the __BuiltinAccount__ property cannot be used together.</span></span>|
| <span data-ttu-id="70c70-120">DependsOn</span><span class="sxs-lookup"><span data-stu-id="70c70-120">DependsOn</span></span>| <span data-ttu-id="70c70-121">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="70c70-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="70c70-122">Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="70c70-122">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="70c70-123">StartupType</span><span class="sxs-lookup"><span data-stu-id="70c70-123">StartupType</span></span>| <span data-ttu-id="70c70-124">Indica o tipo de inicialização para o serviço.</span><span class="sxs-lookup"><span data-stu-id="70c70-124">Indicates the startup type for the service.</span></span> <span data-ttu-id="70c70-125">Os valores permitidos para essa propriedade são: **Automática**, **desabilitado**, e **Manual**</span><span class="sxs-lookup"><span data-stu-id="70c70-125">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|
| <span data-ttu-id="70c70-126">Estado</span><span class="sxs-lookup"><span data-stu-id="70c70-126">State</span></span>| <span data-ttu-id="70c70-127">Indica o estado que você deseja garantir para o serviço.</span><span class="sxs-lookup"><span data-stu-id="70c70-127">Indicates the state you want to ensure for the service.</span></span>|
| <span data-ttu-id="70c70-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="70c70-128">Description</span></span> | <span data-ttu-id="70c70-129">Indica a descrição do serviço de destino.</span><span class="sxs-lookup"><span data-stu-id="70c70-129">Indicates the description of the target service.</span></span>|
| <span data-ttu-id="70c70-130">DisplayName</span><span class="sxs-lookup"><span data-stu-id="70c70-130">DisplayName</span></span> | <span data-ttu-id="70c70-131">Indica o nome de exibição do serviço de destino.</span><span class="sxs-lookup"><span data-stu-id="70c70-131">Indicates the display name of the target service.</span></span>|
| <span data-ttu-id="70c70-132">Ensure</span><span class="sxs-lookup"><span data-stu-id="70c70-132">Ensure</span></span> | <span data-ttu-id="70c70-133">Indica se o serviço de destino existe no sistema.</span><span class="sxs-lookup"><span data-stu-id="70c70-133">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="70c70-134">Defina essa propriedade como **Ausente** para garantir que o serviço de destino não exista.</span><span class="sxs-lookup"><span data-stu-id="70c70-134">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="70c70-135">Configurá-la como **Present** (o valor padrão) garante que o grupo exista.</span><span class="sxs-lookup"><span data-stu-id="70c70-135">Setting it to **Present** (the default value) ensures that target service exists.</span></span>|
| <span data-ttu-id="70c70-136">Caminho</span><span class="sxs-lookup"><span data-stu-id="70c70-136">Path</span></span> | <span data-ttu-id="70c70-137">Indica o caminho para o arquivo binário para um novo serviço.</span><span class="sxs-lookup"><span data-stu-id="70c70-137">Indicates the path to the binary file for a new service.</span></span>|

## <a name="example"></a><span data-ttu-id="70c70-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="70c70-138">Example</span></span>

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```