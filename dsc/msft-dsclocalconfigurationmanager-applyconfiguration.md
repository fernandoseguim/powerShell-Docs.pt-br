---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC,powershell,configuração,instalação
title: Método ApplyConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 2844e354e0d054b13b92267ce314536d88a1c33e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c79b3-103">Método ApplyConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c79b3-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c79b3-104">Usa o Agente de Configuração para aplicar a configuração pendente.</span><span class="sxs-lookup"><span data-stu-id="c79b3-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="c79b3-105">Se não houver nenhuma configuração pendente, esse método reaplicará a configuração atual.</span><span class="sxs-lookup"><span data-stu-id="c79b3-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="c79b3-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c79b3-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="c79b3-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c79b3-107">Parameters</span></span>
----------

<span data-ttu-id="c79b3-108">*force* \[in\] Se for **true**, a configuração atual será reaplicada, mesmo que haja uma configuração pendente.</span><span class="sxs-lookup"><span data-stu-id="c79b3-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="c79b3-109">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="c79b3-109">Return value</span></span>
------------

<span data-ttu-id="c79b3-110">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="c79b3-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c79b3-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="c79b3-111">Remarks</span></span>

<span data-ttu-id="c79b3-112">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="c79b3-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c79b3-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c79b3-113">Requirements</span></span>
------------
><span data-ttu-id="c79b3-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c79b3-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="c79b3-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c79b3-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="c79b3-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c79b3-116">See also</span></span>


[<span data-ttu-id="c79b3-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c79b3-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)