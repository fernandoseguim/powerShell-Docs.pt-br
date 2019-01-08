---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método GetConfigurationResultOutput da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ea572a4a66befd4e4b8d83e2957632b1b5ed7d93
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047004"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e161a-103">Método GetConfigurationResultOutput da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e161a-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e161a-104">Obtém a saída do Agente de Configuração associada a um trabalho específico.</span><span class="sxs-lookup"><span data-stu-id="e161a-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="e161a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e161a-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="e161a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e161a-106">Parameters</span></span>

<span data-ttu-id="e161a-107">*jobId* \[in\] A ID do trabalho para o qual obter dados de saída.</span><span class="sxs-lookup"><span data-stu-id="e161a-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="e161a-108">*resumeOutputBookmark* \[in\] Especifica que a saída deve ser uma continuação de um indicador anterior.</span><span class="sxs-lookup"><span data-stu-id="e161a-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="e161a-109">*output* \[out\] A saída para o trabalho especificado.</span><span class="sxs-lookup"><span data-stu-id="e161a-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="e161a-110">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="e161a-110">Return value</span></span>

<span data-ttu-id="e161a-111">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="e161a-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e161a-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="e161a-112">Remarks</span></span>

<span data-ttu-id="e161a-113">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="e161a-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e161a-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e161a-114">Requirements</span></span>

<span data-ttu-id="e161a-115">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e161a-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e161a-116">namespace {0} Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e161a-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e161a-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e161a-117">See also</span></span>

[<span data-ttu-id="e161a-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e161a-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)