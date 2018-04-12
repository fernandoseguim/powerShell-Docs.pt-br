---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC,powershell,configuração,instalação
title: Método StopConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: dadb6912af2e4450381958ed465799056da49946
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="50cf7-103">Método StopConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="50cf7-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="50cf7-104">Interrompe a alteração da configuração em andamento.</span><span class="sxs-lookup"><span data-stu-id="50cf7-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="50cf7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="50cf7-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="50cf7-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="50cf7-106">Parameters</span></span>
----------

<span data-ttu-id="50cf7-107">*force* \[in\] **true** para forçar a configuração a parar.</span><span class="sxs-lookup"><span data-stu-id="50cf7-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="50cf7-108">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="50cf7-108">Return value</span></span>
------------

<span data-ttu-id="50cf7-109">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="50cf7-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="50cf7-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="50cf7-110">Remarks</span></span>

<span data-ttu-id="50cf7-111">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="50cf7-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="50cf7-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="50cf7-112">Requirements</span></span>
------------
><span data-ttu-id="50cf7-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="50cf7-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="50cf7-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="50cf7-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="50cf7-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50cf7-115">See also</span></span>


[<span data-ttu-id="50cf7-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="50cf7-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)