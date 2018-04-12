---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC,powershell,configuração,instalação
title: Método SendMetaConfigurationApply da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ab82b239ddfdb4075d9440cd66343266b3c08eda
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ad44c-103">Método SendMetaConfigurationApply da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="ad44c-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ad44c-104">Define as configurações do Gerenciador de Configurações Local usadas para controlar o Agente de Configuração.</span><span class="sxs-lookup"><span data-stu-id="ad44c-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="ad44c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ad44c-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="ad44c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ad44c-106">Parameters</span></span>
----------

<span data-ttu-id="ad44c-107">*ConfigurationData* \[in\] Dados de ambiente da configuração.</span><span class="sxs-lookup"><span data-stu-id="ad44c-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="ad44c-108">*force* \[in\] **true** para forçar a configuração a parar.</span><span class="sxs-lookup"><span data-stu-id="ad44c-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="ad44c-109">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="ad44c-109">Return value</span></span>
------------

<span data-ttu-id="ad44c-110">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="ad44c-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ad44c-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="ad44c-111">Remarks</span></span>

<span data-ttu-id="ad44c-112">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="ad44c-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ad44c-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ad44c-113">Requirements</span></span>
------------
><span data-ttu-id="ad44c-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ad44c-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ad44c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ad44c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="ad44c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad44c-116">See also</span></span>


[<span data-ttu-id="ad44c-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ad44c-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)