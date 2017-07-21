---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método EnableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 7220c972b3f43b4697cf71df54d2d43881938367
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d09bd-103">Método EnableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="d09bd-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d09bd-104">Habilita a depuração do recurso DSC.</span><span class="sxs-lookup"><span data-stu-id="d09bd-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="d09bd-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d09bd-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="d09bd-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d09bd-106">Parameters</span></span>
----------

<span data-ttu-id="d09bd-107">*BreakAll* \[in\]</span><span class="sxs-lookup"><span data-stu-id="d09bd-107">*BreakAll* \[in\]</span></span>  
<span data-ttu-id="d09bd-108">Define um ponto de interrupção em cada linha do script de recurso.</span><span class="sxs-lookup"><span data-stu-id="d09bd-108">Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="d09bd-109">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="d09bd-109">Return value</span></span>
------------

<span data-ttu-id="d09bd-110">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="d09bd-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d09bd-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="d09bd-111">Remarks</span></span>

<span data-ttu-id="d09bd-112">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="d09bd-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d09bd-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d09bd-113">Requirements</span></span>
------------
><span data-ttu-id="d09bd-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d09bd-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="d09bd-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d09bd-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="d09bd-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d09bd-116">See also</span></span>


[<span data-ttu-id="d09bd-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d09bd-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



