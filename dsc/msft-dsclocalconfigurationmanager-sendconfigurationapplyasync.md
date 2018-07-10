---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método SendConfigurationApplyAsync da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b028079cf826719967858f50e357b441ba8f9d79
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893885"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="cbbaa-103">Método SendConfigurationApplyAsync da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="cbbaa-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="cbbaa-104">Envia o documento de configuração de maneira assíncrona para o nó gerenciado e usa o Agente de Configuração para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="cbbaa-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="cbbaa-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cbbaa-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="cbbaa-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cbbaa-106">Parameters</span></span>

<span data-ttu-id="cbbaa-107">*ConfigurationData* \[in\] Dados de ambiente da configuração.</span><span class="sxs-lookup"><span data-stu-id="cbbaa-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="cbbaa-108">*force* \[in\] **true** para forçar a configuração a parar.</span><span class="sxs-lookup"><span data-stu-id="cbbaa-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="cbbaa-109">*jobId* \[in\] A ID do trabalho para a qual enviar a configuração.</span><span class="sxs-lookup"><span data-stu-id="cbbaa-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="cbbaa-110">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="cbbaa-110">Return value</span></span>

<span data-ttu-id="cbbaa-111">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="cbbaa-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="cbbaa-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="cbbaa-112">Remarks</span></span>

<span data-ttu-id="cbbaa-113">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="cbbaa-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="cbbaa-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cbbaa-114">Requirements</span></span>

<span data-ttu-id="cbbaa-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="cbbaa-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="cbbaa-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="cbbaa-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="cbbaa-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cbbaa-117">See also</span></span>

[<span data-ttu-id="cbbaa-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="cbbaa-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)