---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC,powershell,configuração,instalação
title: Método EnableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 9fe41fa806a6abff1d36dadd0c041a5cf0e78caf
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="34bc4-103">Método EnableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="34bc4-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="34bc4-104">Habilita a depuração do recurso DSC.</span><span class="sxs-lookup"><span data-stu-id="34bc4-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="34bc4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34bc4-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="34bc4-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34bc4-106">Parameters</span></span>
----------

<span data-ttu-id="34bc4-107">*BreakAll* \[in\] Define um ponto de interrupção em cada linha do script de recurso.</span><span class="sxs-lookup"><span data-stu-id="34bc4-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="34bc4-108">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="34bc4-108">Return value</span></span>
------------

<span data-ttu-id="34bc4-109">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="34bc4-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="34bc4-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="34bc4-110">Remarks</span></span>

<span data-ttu-id="34bc4-111">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="34bc4-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="34bc4-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="34bc4-112">Requirements</span></span>
------------
><span data-ttu-id="34bc4-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="34bc4-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="34bc4-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="34bc4-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="34bc4-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34bc4-115">See also</span></span>


[<span data-ttu-id="34bc4-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="34bc4-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)