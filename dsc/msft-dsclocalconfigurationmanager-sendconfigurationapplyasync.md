---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método SendConfigurationApplyAsync da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: e680bfd1c5b39d364c90cf5ef6b43d0a568af23a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0a685-103">Método SendConfigurationApplyAsync da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="0a685-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0a685-104">Envia o documento de configuração de maneira assíncrona para o nó gerenciado e usa o Agente de Configuração para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="0a685-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="0a685-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0a685-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="0a685-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0a685-106">Parameters</span></span>
----------

<span data-ttu-id="0a685-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="0a685-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="0a685-108">Dados do ambiente para a configuração.</span><span class="sxs-lookup"><span data-stu-id="0a685-108">The environment data for the configuration.</span></span>

<span data-ttu-id="0a685-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="0a685-109">*force* \[in\]</span></span>  
<span data-ttu-id="0a685-110">**true** para forçar a configuração a parar.</span><span class="sxs-lookup"><span data-stu-id="0a685-110">**true** to force the configuration to stop.</span></span>

<span data-ttu-id="0a685-111">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="0a685-111">*jobId* \[in\]</span></span>  
<span data-ttu-id="0a685-112">A ID do trabalho para a qual enviar a configuração.</span><span class="sxs-lookup"><span data-stu-id="0a685-112">The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="0a685-113">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="0a685-113">Return value</span></span>
------------

<span data-ttu-id="0a685-114">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="0a685-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0a685-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="0a685-115">Remarks</span></span>

<span data-ttu-id="0a685-116">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="0a685-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0a685-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0a685-117">Requirements</span></span>
------------
><span data-ttu-id="0a685-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0a685-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="0a685-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0a685-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="0a685-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a685-120">See also</span></span>


[<span data-ttu-id="0a685-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0a685-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



