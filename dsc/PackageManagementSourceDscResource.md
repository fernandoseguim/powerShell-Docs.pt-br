---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: Recurso PackageManagementSource da DSC
ms.openlocfilehash: 1c904c70369a75802484c3c0520df63602760361
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="d50a8-103">Recurso PackageManagementSource da DSC</span><span class="sxs-lookup"><span data-stu-id="d50a8-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="d50a8-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d50a8-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="d50a8-105">O recurso **PackageManagementSource** na Configuração do Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para registrar ou cancelar o registro de fontes de Gerenciamento de Pacote em um nó de destino.</span><span class="sxs-lookup"><span data-stu-id="d50a8-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="d50a8-106">**Fontes de Gerenciamento de Pacote registradas dessa forma são registradas no contexto do Sistema, podem ser usadas pela conta do Sistema ou pelo mecanismo de DSC.**</span><span class="sxs-lookup"><span data-stu-id="d50a8-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="d50a8-107">Este recurso requer o módulo **PackageManagement**, disponível em http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="d50a8-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="d50a8-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d50a8-108">Syntax</span></span>

```
PSModule [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ InstallationPolicy = [string] ]
    [ ProviderName = [string] ]
    [ SourceUri = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="d50a8-109">Propriedades</span><span class="sxs-lookup"><span data-stu-id="d50a8-109">Properties</span></span>
|  <span data-ttu-id="d50a8-110">Propriedade</span><span class="sxs-lookup"><span data-stu-id="d50a8-110">Property</span></span>  |  <span data-ttu-id="d50a8-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="d50a8-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="d50a8-112">Nome</span><span class="sxs-lookup"><span data-stu-id="d50a8-112">Name</span></span>| <span data-ttu-id="d50a8-113">Especifica o nome da origem do pacote a ser registrado ou cancelado no seu sistema.</span><span class="sxs-lookup"><span data-stu-id="d50a8-113">Specifies the name of the package source to be registered or unregistered on your system.</span></span>| 
| <span data-ttu-id="d50a8-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="d50a8-114">Ensure</span></span>| <span data-ttu-id="d50a8-115">Determina se a origem do pacote deve ser registrada ou cancelada.</span><span class="sxs-lookup"><span data-stu-id="d50a8-115">Determines whether the package source is to be registered or unregistered.</span></span>| 
| <span data-ttu-id="d50a8-116">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="d50a8-116">InstallationPolicy</span></span>| <span data-ttu-id="d50a8-117">Determina se você confia na origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="d50a8-117">Determines whether you trust the package source.</span></span> <span data-ttu-id="d50a8-118">Um destes: "Não confiável", "Confiável".</span><span class="sxs-lookup"><span data-stu-id="d50a8-118">One of: "Untrusted", "Trusted".</span></span>| 
| <span data-ttu-id="d50a8-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="d50a8-119">ProviderName</span></span>| <span data-ttu-id="d50a8-120">Especifica o nome do provedor OneGet por meio do qual você pode fornecer interoperabilidade com a origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="d50a8-120">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>| 
| <span data-ttu-id="d50a8-121">SourceUri</span><span class="sxs-lookup"><span data-stu-id="d50a8-121">SourceUri</span></span>| <span data-ttu-id="d50a8-122">Especifica o URI de origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="d50a8-122">Specifies the URI of the package source.</span></span>| 
| <span data-ttu-id="d50a8-123">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="d50a8-123">SourceCredential</span></span>| <span data-ttu-id="d50a8-124">Fornece acesso ao pacote em uma fonte remota.</span><span class="sxs-lookup"><span data-stu-id="d50a8-124">Provides access to the package on a remote source.</span></span>| 

## <a name="example"></a><span data-ttu-id="d50a8-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d50a8-125">Example</span></span>

<span data-ttu-id="d50a8-126">Este exemplo registra a origem do pacote de http://nuget.org usando o recurso de DSC **PackageManagementSource**.</span><span class="sxs-lookup"><span data-stu-id="d50a8-126">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{    
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present" 
        Name        = "MyNuget" 
        ProviderName= "Nuget" 
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }
}
```

