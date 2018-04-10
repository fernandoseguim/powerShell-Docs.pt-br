---
ms.date: 08/25/2017
keywords: powershell, cmdlet
title: O objeto ObjectModelRoot
ms.openlocfilehash: 2670321ebac1eac4ecc8457afb796f9f260da471
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="the-objectmodelroot-object"></a><span data-ttu-id="d488b-103">O objeto ObjectModelRoot</span><span class="sxs-lookup"><span data-stu-id="d488b-103">The ObjectModelRoot Object</span></span>

<span data-ttu-id="d488b-104">O objeto **$psISE**, que é o objeto raiz da entidade de segurança no ISE (Ambiente de Script Integrado) do Windows PowerShell®, é uma instância da classe Microsoft.PowerShell.Host.ISE.ObjectModelRoot.</span><span class="sxs-lookup"><span data-stu-id="d488b-104">The **$psISE** object, which is the principal root object in Windows PowerShell® Integrated Scripting Environment (ISE) is an instance of the Microsoft.PowerShell.Host.ISE.ObjectModelRoot class.</span></span>
<span data-ttu-id="d488b-105">Este tópico descreve as propriedades do objeto **ObjectModelRoot**.</span><span class="sxs-lookup"><span data-stu-id="d488b-105">This topic describes the properties of the **ObjectModelRoot** object.</span></span>

## <a name="properties"></a><span data-ttu-id="d488b-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="d488b-106">Properties</span></span>

### <a name="currentfile"></a><span data-ttu-id="d488b-107">CurrentFile</span><span class="sxs-lookup"><span data-stu-id="d488b-107">CurrentFile</span></span>

> <span data-ttu-id="d488b-108">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="d488b-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d488b-109">A propriedade somente leitura que obtém o arquivo, que é associada ao objeto host que atualmente tem o foco.</span><span class="sxs-lookup"><span data-stu-id="d488b-109">The read-only property that gets the file, which is associated with this host object that currently has the focus.</span></span>

### <a name="currentpowershelltab"></a><span data-ttu-id="d488b-110">CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="d488b-110">CurrentPowerShellTab</span></span>

> <span data-ttu-id="d488b-111">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="d488b-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d488b-112">A propriedade somente leitura que obtém a guia do PowerShell que tem o foco.</span><span class="sxs-lookup"><span data-stu-id="d488b-112">The read-only property that gets the PowerShell tab that has the focus.</span></span>

### <a name="currentvisiblehorizontaltool"></a><span data-ttu-id="d488b-113">CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="d488b-113">CurrentVisibleHorizontalTool</span></span>

> <span data-ttu-id="d488b-114">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="d488b-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d488b-115">A propriedade somente leitura que obtém a ferramenta complementar do ISE do Windows PowerShell visível no momento que está localizada no painel de ferramentas horizontal na parte inferior do editor.</span><span class="sxs-lookup"><span data-stu-id="d488b-115">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the horizontal tool pane at the bottom of the editor.</span></span>

### <a name="currentvisibleverticaltool"></a><span data-ttu-id="d488b-116">CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="d488b-116">CurrentVisibleVerticalTool</span></span>

> <span data-ttu-id="d488b-117">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="d488b-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d488b-118">A propriedade somente leitura que obtém a ferramenta complementar do ISE do Windows PowerShell visível no momento que está localizada no painel de ferramentas vertical no lado direito do editor.</span><span class="sxs-lookup"><span data-stu-id="d488b-118">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the vertical tool pane on the right side of the editor.</span></span>

### <a name="options"></a><span data-ttu-id="d488b-119">Opções</span><span class="sxs-lookup"><span data-stu-id="d488b-119">Options</span></span>

> <span data-ttu-id="d488b-120">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="d488b-120">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d488b-121">A propriedade somente leitura que obtém as várias opções que podem alterar as configurações no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d488b-121">The read-only property that gets the various options that can change settings in Windows PowerShell ISE.</span></span>

### <a name="powershelltabs"></a><span data-ttu-id="d488b-122">PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="d488b-122">PowerShellTabs</span></span>

> <span data-ttu-id="d488b-123">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="d488b-123">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d488b-124">A propriedade somente leitura que obtém a coleção de guias do PowerShell, que está aberta no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d488b-124">The read-only property that gets the collection of the PowerShell tabs, which are open in Windows PowerShell ISE.</span></span> <span data-ttu-id="d488b-125">Por padrão, esse objeto contém uma guia do PowerShell. No entanto, é possível adicionar mais guias do PowerShell a esse objeto usando scripts ou usando os menus no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d488b-125">By default, this object contains one PowerShell tab. However, you can add more PowerShell tabs to this object by using scripts or by using the menus in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="d488b-126">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="d488b-126">See Also</span></span>

- [<span data-ttu-id="d488b-127">Objetivo do modelo de objeto de script do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d488b-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="d488b-128">A hierarquia de modelo de objeto do ISE</span><span class="sxs-lookup"><span data-stu-id="d488b-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)