---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método StopConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: f0b550615b20f07f99c8ed7009805c45794bfe22
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="1e2d8-103">Método StopConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="1e2d8-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="1e2d8-104">Interrompe a alteração da configuração em andamento.</span><span class="sxs-lookup"><span data-stu-id="1e2d8-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="1e2d8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1e2d8-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="1e2d8-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1e2d8-106">Parameters</span></span>
----------

<span data-ttu-id="1e2d8-107">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="1e2d8-107">*force* \[in\]</span></span>  
<span data-ttu-id="1e2d8-108">**true** para forçar a configuração a parar.</span><span class="sxs-lookup"><span data-stu-id="1e2d8-108">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="1e2d8-109">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="1e2d8-109">Return value</span></span>
------------

<span data-ttu-id="1e2d8-110">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="1e2d8-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1e2d8-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="1e2d8-111">Remarks</span></span>

<span data-ttu-id="1e2d8-112">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="1e2d8-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1e2d8-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1e2d8-113">Requirements</span></span>
------------
><span data-ttu-id="1e2d8-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="1e2d8-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="1e2d8-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1e2d8-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="1e2d8-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e2d8-116">See also</span></span>


[<span data-ttu-id="1e2d8-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="1e2d8-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



