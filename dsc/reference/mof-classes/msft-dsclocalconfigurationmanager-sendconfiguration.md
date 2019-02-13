---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método SendConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 3529bc56ecba19ed0fbbf070a4e86d0692824d39
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675537"
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="06cdd-103">Método SendConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="06cdd-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="06cdd-104">Envia o documento de configuração para o nó gerenciado e o salva como alteração pendente.</span><span class="sxs-lookup"><span data-stu-id="06cdd-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="06cdd-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="06cdd-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="06cdd-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="06cdd-106">Parameters</span></span>

<span data-ttu-id="06cdd-107">*ConfigurationData* \[in\] Dados de ambiente da configuração.</span><span class="sxs-lookup"><span data-stu-id="06cdd-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="06cdd-108">*force* \[in\] **true** para forçar a configuração a parar.</span><span class="sxs-lookup"><span data-stu-id="06cdd-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="06cdd-109">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="06cdd-109">Return value</span></span>

<span data-ttu-id="06cdd-110">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="06cdd-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="06cdd-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="06cdd-111">Remarks</span></span>

<span data-ttu-id="06cdd-112">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="06cdd-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="06cdd-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="06cdd-113">Requirements</span></span>

<span data-ttu-id="06cdd-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="06cdd-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="06cdd-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="06cdd-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="06cdd-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="06cdd-116">See also</span></span>

[<span data-ttu-id="06cdd-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="06cdd-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)