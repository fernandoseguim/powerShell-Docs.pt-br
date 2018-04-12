---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC,powershell,configuração,instalação
title: Recurso PackageManagementSource da DSC
ms.openlocfilehash: 8c0cb5a3b0a019ddb5ed995406f499298103b07c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="36107-103">Recurso PackageManagementSource da DSC</span><span class="sxs-lookup"><span data-stu-id="36107-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="36107-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="36107-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="36107-105">O recurso **PackageManagementSource** na Configuração do Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para registrar ou cancelar o registro de fontes de Gerenciamento de Pacote em um nó de destino.</span><span class="sxs-lookup"><span data-stu-id="36107-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="36107-106">**Fontes de Gerenciamento de Pacote registradas dessa forma são registradas no contexto do Sistema, podem ser usadas pela conta do Sistema ou pelo mecanismo de DSC.**</span><span class="sxs-lookup"><span data-stu-id="36107-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="36107-107">Este recurso requer o módulo **PackageManagement**, disponível em http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="36107-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="36107-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="36107-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="36107-109">Propriedades</span><span class="sxs-lookup"><span data-stu-id="36107-109">Properties</span></span>
|  <span data-ttu-id="36107-110">Propriedade</span><span class="sxs-lookup"><span data-stu-id="36107-110">Property</span></span>  |  <span data-ttu-id="36107-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="36107-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="36107-112">Nome</span><span class="sxs-lookup"><span data-stu-id="36107-112">Name</span></span>| <span data-ttu-id="36107-113">Especifica o nome da origem do pacote a ser registrado ou cancelado no seu sistema.</span><span class="sxs-lookup"><span data-stu-id="36107-113">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="36107-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="36107-114">Ensure</span></span>| <span data-ttu-id="36107-115">Determina se a origem do pacote deve ser registrada ou cancelada.</span><span class="sxs-lookup"><span data-stu-id="36107-115">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="36107-116">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="36107-116">InstallationPolicy</span></span>| <span data-ttu-id="36107-117">Determina se você confia na origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="36107-117">Determines whether you trust the package source.</span></span> <span data-ttu-id="36107-118">Um destes: "Não confiável", "Confiável".</span><span class="sxs-lookup"><span data-stu-id="36107-118">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="36107-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="36107-119">ProviderName</span></span>| <span data-ttu-id="36107-120">Especifica o nome do provedor OneGet por meio do qual você pode fornecer interoperabilidade com a origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="36107-120">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="36107-121">SourceUri</span><span class="sxs-lookup"><span data-stu-id="36107-121">SourceUri</span></span>| <span data-ttu-id="36107-122">Especifica o URI de origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="36107-122">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="36107-123">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="36107-123">SourceCredential</span></span>| <span data-ttu-id="36107-124">Fornece acesso ao pacote em uma fonte remota.</span><span class="sxs-lookup"><span data-stu-id="36107-124">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="36107-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="36107-125">Example</span></span>

<span data-ttu-id="36107-126">Este exemplo registra a origem do pacote de http://nuget.org usando o recurso DSC **PackageManagementSource**.</span><span class="sxs-lookup"><span data-stu-id="36107-126">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

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