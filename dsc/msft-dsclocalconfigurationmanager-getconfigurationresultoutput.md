---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método GetConfigurationResultOutput da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: f6106bb28dc20004b5bbb6df2d8e719cf0c453f0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b4e5b-103">Método GetConfigurationResultOutput da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b4e5b-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b4e5b-104">Obtém a saída do Agente de Configuração associada a um trabalho específico.</span><span class="sxs-lookup"><span data-stu-id="b4e5b-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="b4e5b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b4e5b-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="b4e5b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b4e5b-106">Parameters</span></span>
----------

<span data-ttu-id="b4e5b-107">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b4e5b-107">*jobId* \[in\]</span></span>  
<span data-ttu-id="b4e5b-108">A ID do trabalho para o qual obter dados de saída.</span><span class="sxs-lookup"><span data-stu-id="b4e5b-108">The ID of the job for which to get output data.</span></span>

<span data-ttu-id="b4e5b-109">*resumeOutputBookmark* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b4e5b-109">*resumeOutputBookmark* \[in\]</span></span>  
<span data-ttu-id="b4e5b-110">Especifica que a saída deve ser uma continuação de um indicador anterior.</span><span class="sxs-lookup"><span data-stu-id="b4e5b-110">Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="b4e5b-111">*output* \[out\]</span><span class="sxs-lookup"><span data-stu-id="b4e5b-111">*output* \[out\]</span></span>  
<span data-ttu-id="b4e5b-112">A saída para o trabalho especificado.</span><span class="sxs-lookup"><span data-stu-id="b4e5b-112">The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="b4e5b-113">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="b4e5b-113">Return value</span></span>
------------

<span data-ttu-id="b4e5b-114">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="b4e5b-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b4e5b-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="b4e5b-115">Remarks</span></span>

<span data-ttu-id="b4e5b-116">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="b4e5b-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b4e5b-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b4e5b-117">Requirements</span></span>
------------
><span data-ttu-id="b4e5b-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b4e5b-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="b4e5b-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b4e5b-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="b4e5b-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4e5b-120">See also</span></span>


[<span data-ttu-id="b4e5b-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b4e5b-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



