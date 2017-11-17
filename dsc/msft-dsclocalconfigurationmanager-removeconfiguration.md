---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: faa113c442b80eea3ac474220b098b7d80ec50a8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="59ce9-103">Método RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="59ce9-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="59ce9-104">Remove os arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="59ce9-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="59ce9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="59ce9-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="59ce9-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="59ce9-106">Parameters</span></span>
----------

<span data-ttu-id="59ce9-107">*Stage* \[in\]</span><span class="sxs-lookup"><span data-stu-id="59ce9-107">*Stage* \[in\]</span></span>  
<span data-ttu-id="59ce9-108">Especifica qual documento de configuração remover.</span><span class="sxs-lookup"><span data-stu-id="59ce9-108">Specifies which configuration document to remove.</span></span> <span data-ttu-id="59ce9-109">Os seguintes valores são válidos:</span><span class="sxs-lookup"><span data-stu-id="59ce9-109">The following values are valid:</span></span>

|<span data-ttu-id="59ce9-110">Valor</span><span class="sxs-lookup"><span data-stu-id="59ce9-110">Value</span></span> |<span data-ttu-id="59ce9-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="59ce9-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="59ce9-112">**1**</span><span class="sxs-lookup"><span data-stu-id="59ce9-112">**1**</span></span> | <span data-ttu-id="59ce9-113">O documento de configuração **atual** (current.mof).</span><span class="sxs-lookup"><span data-stu-id="59ce9-113">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="59ce9-114">**2**</span><span class="sxs-lookup"><span data-stu-id="59ce9-114">**2**</span></span> | <span data-ttu-id="59ce9-115">O documento de configuração **Pendente** (current.mof).</span><span class="sxs-lookup"><span data-stu-id="59ce9-115">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="59ce9-116">**4**</span><span class="sxs-lookup"><span data-stu-id="59ce9-116">**4**</span></span> | <span data-ttu-id="59ce9-117">O documento de configuração **Anterior** (current.mof).</span><span class="sxs-lookup"><span data-stu-id="59ce9-117">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="59ce9-118">*Force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="59ce9-118">*Force* \[in\]</span></span>  
<span data-ttu-id="59ce9-119">**true** para forçar a remoção da configuração.</span><span class="sxs-lookup"><span data-stu-id="59ce9-119">**true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="59ce9-120">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="59ce9-120">Return value</span></span>
------------

<span data-ttu-id="59ce9-121">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="59ce9-121">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="59ce9-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="59ce9-122">Remarks</span></span>

<span data-ttu-id="59ce9-123">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="59ce9-123">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="59ce9-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="59ce9-124">Requirements</span></span>
------------
><span data-ttu-id="59ce9-125">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="59ce9-125">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="59ce9-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="59ce9-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="59ce9-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59ce9-127">See also</span></span>


[<span data-ttu-id="59ce9-128">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="59ce9-128">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



