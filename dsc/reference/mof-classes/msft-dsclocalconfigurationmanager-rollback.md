---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método de reversão da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047043"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e3f3e-103">Método de reversão da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e3f3e-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e3f3e-104">Reverte a configuração a uma versão anterior.</span><span class="sxs-lookup"><span data-stu-id="e3f3e-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="e3f3e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3f3e-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="e3f3e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e3f3e-106">Parameters</span></span>

<span data-ttu-id="e3f3e-107">*configurationNumber* \[in\] Especifica a configuração solicitada.</span><span class="sxs-lookup"><span data-stu-id="e3f3e-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="e3f3e-108">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="e3f3e-108">Return value</span></span>

<span data-ttu-id="e3f3e-109">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="e3f3e-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e3f3e-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="e3f3e-110">Remarks</span></span>

<span data-ttu-id="e3f3e-111">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="e3f3e-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e3f3e-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e3f3e-112">Requirements</span></span>

<span data-ttu-id="e3f3e-113">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e3f3e-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e3f3e-114">namespace {0} Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e3f3e-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e3f3e-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3f3e-115">See also</span></span>

[<span data-ttu-id="e3f3e-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e3f3e-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)