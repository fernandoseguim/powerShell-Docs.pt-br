---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método SendConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 3529bc56ecba19ed0fbbf070a4e86d0692824d39
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046998"
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="06211-103">Método SendConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="06211-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="06211-104">Envia o documento de configuração para o nó gerenciado e o salva como alteração pendente.</span><span class="sxs-lookup"><span data-stu-id="06211-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="06211-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="06211-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="06211-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="06211-106">Parameters</span></span>

<span data-ttu-id="06211-107">*ConfigurationData* \[in\] Dados de ambiente da configuração.</span><span class="sxs-lookup"><span data-stu-id="06211-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="06211-108">*force* \[in\] **true** para forçar a configuração a parar.</span><span class="sxs-lookup"><span data-stu-id="06211-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="06211-109">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="06211-109">Return value</span></span>

<span data-ttu-id="06211-110">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="06211-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="06211-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="06211-111">Remarks</span></span>

<span data-ttu-id="06211-112">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="06211-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="06211-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="06211-113">Requirements</span></span>

<span data-ttu-id="06211-114">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="06211-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="06211-115">namespace {0} Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="06211-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="06211-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="06211-116">See also</span></span>

[<span data-ttu-id="06211-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="06211-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)