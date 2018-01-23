---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: fed45836293adedbce18f01cfe53cdfa1a474975
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7a058-103">Método RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="7a058-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7a058-104">Remove os arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="7a058-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="7a058-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7a058-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="7a058-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7a058-106">Parameters</span></span>
----------

<span data-ttu-id="7a058-107">*Stage* \[in\]</span><span class="sxs-lookup"><span data-stu-id="7a058-107">*Stage* \[in\]</span></span>  
<span data-ttu-id="7a058-108">Especifica qual documento de configuração remover.</span><span class="sxs-lookup"><span data-stu-id="7a058-108">Specifies which configuration document to remove.</span></span> <span data-ttu-id="7a058-109">Os seguintes valores são válidos:</span><span class="sxs-lookup"><span data-stu-id="7a058-109">The following values are valid:</span></span>

|<span data-ttu-id="7a058-110">Valor</span><span class="sxs-lookup"><span data-stu-id="7a058-110">Value</span></span> |<span data-ttu-id="7a058-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="7a058-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="7a058-112">**1**</span><span class="sxs-lookup"><span data-stu-id="7a058-112">**1**</span></span> | <span data-ttu-id="7a058-113">O documento de configuração **atual** (current.mof).</span><span class="sxs-lookup"><span data-stu-id="7a058-113">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="7a058-114">**2**</span><span class="sxs-lookup"><span data-stu-id="7a058-114">**2**</span></span> | <span data-ttu-id="7a058-115">O documento de configuração **Pendente** (current.mof).</span><span class="sxs-lookup"><span data-stu-id="7a058-115">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="7a058-116">**4**</span><span class="sxs-lookup"><span data-stu-id="7a058-116">**4**</span></span> | <span data-ttu-id="7a058-117">O documento de configuração **Anterior** (current.mof).</span><span class="sxs-lookup"><span data-stu-id="7a058-117">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="7a058-118">*Force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="7a058-118">*Force* \[in\]</span></span>  
<span data-ttu-id="7a058-119">**true** para forçar a remoção da configuração.</span><span class="sxs-lookup"><span data-stu-id="7a058-119">**true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="7a058-120">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="7a058-120">Return value</span></span>
------------

<span data-ttu-id="7a058-121">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="7a058-121">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7a058-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="7a058-122">Remarks</span></span>

<span data-ttu-id="7a058-123">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="7a058-123">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7a058-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7a058-124">Requirements</span></span>
------------
><span data-ttu-id="7a058-125">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7a058-125">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="7a058-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7a058-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="7a058-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7a058-127">See also</span></span>


[<span data-ttu-id="7a058-128">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7a058-128">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



