---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método de reversão da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676452"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="299b8-103">Método de reversão da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="299b8-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="299b8-104">Reverte a configuração a uma versão anterior.</span><span class="sxs-lookup"><span data-stu-id="299b8-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="299b8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="299b8-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="299b8-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="299b8-106">Parameters</span></span>

<span data-ttu-id="299b8-107">*configurationNumber* \[in\] Especifica a configuração solicitada.</span><span class="sxs-lookup"><span data-stu-id="299b8-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="299b8-108">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="299b8-108">Return value</span></span>

<span data-ttu-id="299b8-109">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="299b8-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="299b8-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="299b8-110">Remarks</span></span>

<span data-ttu-id="299b8-111">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="299b8-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="299b8-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="299b8-112">Requirements</span></span>

<span data-ttu-id="299b8-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="299b8-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="299b8-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="299b8-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="299b8-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="299b8-115">See also</span></span>

[<span data-ttu-id="299b8-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="299b8-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)