---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método ApplyConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 559ff1793a18e28dad2f176bdb20eb53bc08630d
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046990"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="6fab2-103">Método ApplyConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="6fab2-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="6fab2-104">Usa o Agente de Configuração para aplicar a configuração pendente.</span><span class="sxs-lookup"><span data-stu-id="6fab2-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="6fab2-105">Se não houver nenhuma configuração pendente, esse método reaplicará a configuração atual.</span><span class="sxs-lookup"><span data-stu-id="6fab2-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="6fab2-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6fab2-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="6fab2-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6fab2-107">Parameters</span></span>

<span data-ttu-id="6fab2-108">*force* \[in\] Se for **true**, a configuração atual será reaplicada, mesmo que haja uma configuração pendente.</span><span class="sxs-lookup"><span data-stu-id="6fab2-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="6fab2-109">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="6fab2-109">Return value</span></span>

<span data-ttu-id="6fab2-110">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="6fab2-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="6fab2-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="6fab2-111">Remarks</span></span>

<span data-ttu-id="6fab2-112">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="6fab2-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6fab2-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6fab2-113">Requirements</span></span>

<span data-ttu-id="6fab2-114">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="6fab2-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="6fab2-115">namespace {0} Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="6fab2-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="6fab2-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6fab2-116">See also</span></span>

[<span data-ttu-id="6fab2-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="6fab2-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)