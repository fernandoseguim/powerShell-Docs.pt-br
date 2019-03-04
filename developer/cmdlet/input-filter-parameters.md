---
title: Parâmetros de filtro de entrada | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854462"
---
# <a name="input-filter-parameters"></a><span data-ttu-id="da9f8-102">Parâmetros de filtro de entrada</span><span class="sxs-lookup"><span data-stu-id="da9f8-102">Input Filter Parameters</span></span>

<span data-ttu-id="da9f8-103">Um cmdlet pode definir `Filter`, `Include`, e `Exclude` parâmetros que filtram o conjunto de objetos de entrada que afeta o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="da9f8-103">A cmdlet can define `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

<span data-ttu-id="da9f8-104">Normalmente, o conjunto de objetos de entrada é especificado por um `InputObject`, `Path`, ou `Name` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="da9f8-104">Typically, the set of input objects is specified by an `InputObject`, `Path`, or `Name` parameter.</span></span> <span data-ttu-id="da9f8-105">Por exemplo, um cmdlet pode ter um `Path` parâmetro que aceita vários caminhos usando caracteres curinga e cada caminho aponta para um objeto de entrada.</span><span class="sxs-lookup"><span data-stu-id="da9f8-105">For example, a cmdlet can have a `Path` parameter that accepts multiple paths by using wildcard characters, and each path points to an input object.</span></span> <span data-ttu-id="da9f8-106">Usados juntos, o `Filter`, `Include`, e `Exclude` ainda mais parâmetros qualificam os caminhos que o cmdlet funciona em cada vez que ele é invocado.</span><span class="sxs-lookup"><span data-stu-id="da9f8-106">Used together, the `Filter`, `Include`, and `Exclude` parameters further qualify the paths the cmdlet works on each time it is invoked.</span></span>

## <a name="include-and-exclude-parameters"></a><span data-ttu-id="da9f8-107">Incluir e excluir parâmetros</span><span class="sxs-lookup"><span data-stu-id="da9f8-107">Include and Exclude Parameters</span></span>

<span data-ttu-id="da9f8-108">O `Include` e `Exclude` parâmetros identificam os objetos que são incluídos ou excluídos do conjunto de objetos de entrada passados para o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="da9f8-108">The `Include` and `Exclude` parameters identify the objects that are included or excluded from the set of input objects passed to the cmdlet.</span></span> <span data-ttu-id="da9f8-109">Use esses parâmetros quando o filtro pode ser expresso na linguagem de padrão curinga.</span><span class="sxs-lookup"><span data-stu-id="da9f8-109">Use these parameters when the filter can be expressed in the standard wildcard language.</span></span> <span data-ttu-id="da9f8-110">(Para obter mais informações sobre os caracteres curinga, consulte [que dão suporte a curingas nos parâmetros de Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).) O `Include` parâmetro inclui todos os objetos cujos nomes correspondem ao filtro de inclusão.</span><span class="sxs-lookup"><span data-stu-id="da9f8-110">(For more information about wildcard characters, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) The `Include` parameter includes all the objects whose names match the inclusion filter.</span></span> <span data-ttu-id="da9f8-111">O `Exclude` parâmetro exclui todos os objetos cujos nomes correspondem ao filtro.</span><span class="sxs-lookup"><span data-stu-id="da9f8-111">The `Exclude` parameter excludes all the objects whose names match the filter.</span></span>

## <a name="filter-parameter"></a><span data-ttu-id="da9f8-112">Parâmetro de filtro</span><span class="sxs-lookup"><span data-stu-id="da9f8-112">Filter Parameter</span></span>

<span data-ttu-id="da9f8-113">O `Filter` parâmetro especifica um filtro que não é expressado na linguagem padrão de curinga.</span><span class="sxs-lookup"><span data-stu-id="da9f8-113">The `Filter` parameter specifies a filter that is not expressed in the standard wildcard language.</span></span> <span data-ttu-id="da9f8-114">Por exemplo, filtros de Active Directory Service Interfaces (ADSI) ou SQL podem ser passados para o cmdlet por meio de seu `Filter` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="da9f8-114">For example, Active Directory Service Interfaces (ADSI) or SQL filters might be passed to the cmdlet through its `Filter` parameter.</span></span> <span data-ttu-id="da9f8-115">Os cmdlets fornecidos pelo Windows PowerShell, esses filtros são especificados pelos provedores do Windows PowerShell que usa o cmdlet para acessar um armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="da9f8-115">In the cmdlets provided by Windows PowerShell, these filters are specified by the Windows PowerShell providers that use the cmdlet to access a data store.</span></span> <span data-ttu-id="da9f8-116">Normalmente, cada provedor define seu próprio filtro.</span><span class="sxs-lookup"><span data-stu-id="da9f8-116">Each provider typically defines its own filter.</span></span>

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a><span data-ttu-id="da9f8-117">Se nenhum conjunto de objetos de entrada for especificado de filtragem</span><span class="sxs-lookup"><span data-stu-id="da9f8-117">Filtering If No Set of Input Objects Is Specified</span></span>

<span data-ttu-id="da9f8-118">Se nenhum conjunto de objetos de entrada for especificado, isso normalmente significa filtrar em relação a todos os objetos.</span><span class="sxs-lookup"><span data-stu-id="da9f8-118">If no set of input objects is specified, this typically means to filter against all objects.</span></span> <span data-ttu-id="da9f8-119">Para obter mais informações, consulte[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span><span class="sxs-lookup"><span data-stu-id="da9f8-119">For more information, see[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span></span>

## <a name="see-also"></a><span data-ttu-id="da9f8-120">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="da9f8-120">See Also</span></span>

<span data-ttu-id="da9f8-121">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="da9f8-121">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>