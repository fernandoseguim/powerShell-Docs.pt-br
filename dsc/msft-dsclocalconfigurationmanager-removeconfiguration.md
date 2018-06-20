---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: c68d17d38336dec08e078366ea5f2071fcf7c5a8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189730"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0cd55-103">Método RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="0cd55-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0cd55-104">Remove os arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="0cd55-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="0cd55-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0cd55-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="0cd55-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0cd55-106">Parameters</span></span>
----------

<span data-ttu-id="0cd55-107">*Stage* \[in\] Especifica qual documento de configuração deve ser removido.</span><span class="sxs-lookup"><span data-stu-id="0cd55-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="0cd55-108">Os seguintes valores são válidos:</span><span class="sxs-lookup"><span data-stu-id="0cd55-108">The following values are valid:</span></span>

|<span data-ttu-id="0cd55-109">Valor</span><span class="sxs-lookup"><span data-stu-id="0cd55-109">Value</span></span> |<span data-ttu-id="0cd55-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="0cd55-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="0cd55-111">**1**</span><span class="sxs-lookup"><span data-stu-id="0cd55-111">**1**</span></span> | <span data-ttu-id="0cd55-112">O documento de configuração **atual** (current.mof).</span><span class="sxs-lookup"><span data-stu-id="0cd55-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="0cd55-113">**2**</span><span class="sxs-lookup"><span data-stu-id="0cd55-113">**2**</span></span> | <span data-ttu-id="0cd55-114">O documento de configuração **Pendente** (current.mof).</span><span class="sxs-lookup"><span data-stu-id="0cd55-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="0cd55-115">**4**</span><span class="sxs-lookup"><span data-stu-id="0cd55-115">**4**</span></span> | <span data-ttu-id="0cd55-116">O documento de configuração **Anterior** (current.mof).</span><span class="sxs-lookup"><span data-stu-id="0cd55-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="0cd55-117">*Force* \[in\] **true** para forçar a remoção da configuração.</span><span class="sxs-lookup"><span data-stu-id="0cd55-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="0cd55-118">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="0cd55-118">Return value</span></span>
------------

<span data-ttu-id="0cd55-119">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="0cd55-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0cd55-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="0cd55-120">Remarks</span></span>

<span data-ttu-id="0cd55-121">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="0cd55-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0cd55-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0cd55-122">Requirements</span></span>
------------
><span data-ttu-id="0cd55-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0cd55-123">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="0cd55-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0cd55-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="0cd55-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0cd55-125">See also</span></span>


[<span data-ttu-id="0cd55-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0cd55-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)