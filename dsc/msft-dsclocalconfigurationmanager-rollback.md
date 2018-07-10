---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método de reversão da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893011"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="2338f-103">Método de reversão da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="2338f-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="2338f-104">Reverte a configuração a uma versão anterior.</span><span class="sxs-lookup"><span data-stu-id="2338f-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="2338f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2338f-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="2338f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2338f-106">Parameters</span></span>

<span data-ttu-id="2338f-107">*configurationNumber* \[in\] Especifica a configuração solicitada.</span><span class="sxs-lookup"><span data-stu-id="2338f-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="2338f-108">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="2338f-108">Return value</span></span>

<span data-ttu-id="2338f-109">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="2338f-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2338f-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="2338f-110">Remarks</span></span>

<span data-ttu-id="2338f-111">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="2338f-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2338f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2338f-112">Requirements</span></span>

<span data-ttu-id="2338f-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2338f-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="2338f-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2338f-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="2338f-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2338f-115">See also</span></span>

[<span data-ttu-id="2338f-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2338f-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)