---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método EnableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: fa34a583af7c3fd46d99307d582973410e4c0e31
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c46f6-103">Método EnableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c46f6-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c46f6-104">Habilita a depuração do recurso DSC.</span><span class="sxs-lookup"><span data-stu-id="c46f6-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="c46f6-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c46f6-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="c46f6-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c46f6-106">Parameters</span></span>
----------

<span data-ttu-id="c46f6-107">*BreakAll* \[in\]</span><span class="sxs-lookup"><span data-stu-id="c46f6-107">*BreakAll* \[in\]</span></span>  
<span data-ttu-id="c46f6-108">Define um ponto de interrupção em cada linha do script de recurso.</span><span class="sxs-lookup"><span data-stu-id="c46f6-108">Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="c46f6-109">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="c46f6-109">Return value</span></span>
------------

<span data-ttu-id="c46f6-110">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="c46f6-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c46f6-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="c46f6-111">Remarks</span></span>

<span data-ttu-id="c46f6-112">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="c46f6-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c46f6-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c46f6-113">Requirements</span></span>
------------
><span data-ttu-id="c46f6-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c46f6-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="c46f6-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c46f6-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="c46f6-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c46f6-116">See also</span></span>


[<span data-ttu-id="c46f6-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c46f6-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



