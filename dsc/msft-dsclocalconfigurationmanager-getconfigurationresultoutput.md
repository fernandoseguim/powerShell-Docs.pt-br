---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método GetConfigurationResultOutput da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 09862fd3c19e1e517c9bf5df878113ba3f10d8a6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="cb72b-103">Método GetConfigurationResultOutput da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="cb72b-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="cb72b-104">Obtém a saída do Agente de Configuração associada a um trabalho específico.</span><span class="sxs-lookup"><span data-stu-id="cb72b-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="cb72b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb72b-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="cb72b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cb72b-106">Parameters</span></span>
----------

<span data-ttu-id="cb72b-107">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="cb72b-107">*jobId* \[in\]</span></span>  
<span data-ttu-id="cb72b-108">A ID do trabalho para o qual obter dados de saída.</span><span class="sxs-lookup"><span data-stu-id="cb72b-108">The ID of the job for which to get output data.</span></span>

<span data-ttu-id="cb72b-109">*resumeOutputBookmark* \[in\]</span><span class="sxs-lookup"><span data-stu-id="cb72b-109">*resumeOutputBookmark* \[in\]</span></span>  
<span data-ttu-id="cb72b-110">Especifica que a saída deve ser uma continuação de um indicador anterior.</span><span class="sxs-lookup"><span data-stu-id="cb72b-110">Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="cb72b-111">*output* \[out\]</span><span class="sxs-lookup"><span data-stu-id="cb72b-111">*output* \[out\]</span></span>  
<span data-ttu-id="cb72b-112">A saída para o trabalho especificado.</span><span class="sxs-lookup"><span data-stu-id="cb72b-112">The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="cb72b-113">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="cb72b-113">Return value</span></span>
------------

<span data-ttu-id="cb72b-114">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="cb72b-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="cb72b-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="cb72b-115">Remarks</span></span>

<span data-ttu-id="cb72b-116">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="cb72b-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="cb72b-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cb72b-117">Requirements</span></span>
------------
><span data-ttu-id="cb72b-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="cb72b-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="cb72b-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="cb72b-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="cb72b-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb72b-120">See also</span></span>


[<span data-ttu-id="cb72b-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="cb72b-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



