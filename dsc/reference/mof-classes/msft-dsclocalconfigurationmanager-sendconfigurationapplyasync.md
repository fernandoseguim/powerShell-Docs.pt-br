---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método SendConfigurationApplyAsync da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b028079cf826719967858f50e357b441ba8f9d79
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676488"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="93334-103">Método SendConfigurationApplyAsync da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="93334-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="93334-104">Envia o documento de configuração de maneira assíncrona para o nó gerenciado e usa o Agente de Configuração para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="93334-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="93334-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="93334-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="93334-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="93334-106">Parameters</span></span>

<span data-ttu-id="93334-107">*ConfigurationData* \[in\] Dados de ambiente da configuração.</span><span class="sxs-lookup"><span data-stu-id="93334-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="93334-108">*force* \[in\] **true** para forçar a configuração a parar.</span><span class="sxs-lookup"><span data-stu-id="93334-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="93334-109">*jobId* \[in\] A ID do trabalho para a qual enviar a configuração.</span><span class="sxs-lookup"><span data-stu-id="93334-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="93334-110">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="93334-110">Return value</span></span>

<span data-ttu-id="93334-111">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="93334-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="93334-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="93334-112">Remarks</span></span>

<span data-ttu-id="93334-113">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="93334-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="93334-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="93334-114">Requirements</span></span>

<span data-ttu-id="93334-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="93334-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="93334-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="93334-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="93334-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="93334-117">See also</span></span>

[<span data-ttu-id="93334-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="93334-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)