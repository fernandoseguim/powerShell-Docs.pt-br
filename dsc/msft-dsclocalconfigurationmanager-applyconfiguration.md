---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método ApplyConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 72fbedf30e5058d8003ed620400d6b443d50dff6
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9b1ad-103">Método ApplyConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="9b1ad-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9b1ad-104">Usa o Agente de Configuração para aplicar a configuração pendente.</span><span class="sxs-lookup"><span data-stu-id="9b1ad-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span> 

<span data-ttu-id="9b1ad-105">Se não houver nenhuma configuração pendente, esse método reaplicará a configuração atual.</span><span class="sxs-lookup"><span data-stu-id="9b1ad-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="9b1ad-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9b1ad-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="9b1ad-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9b1ad-107">Parameters</span></span>
----------

<span data-ttu-id="9b1ad-108">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="9b1ad-108">*force* \[in\]</span></span>  
<span data-ttu-id="9b1ad-109">Se isso for **true**, a configuração atual é reaplicada, mesmo que haja uma configuração pendente.</span><span class="sxs-lookup"><span data-stu-id="9b1ad-109">If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="9b1ad-110">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="9b1ad-110">Return value</span></span>
------------

<span data-ttu-id="9b1ad-111">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="9b1ad-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9b1ad-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="9b1ad-112">Remarks</span></span>

<span data-ttu-id="9b1ad-113">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="9b1ad-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9b1ad-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9b1ad-114">Requirements</span></span>
------------
><span data-ttu-id="9b1ad-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9b1ad-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="9b1ad-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9b1ad-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="9b1ad-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b1ad-117">See also</span></span>


[<span data-ttu-id="9b1ad-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9b1ad-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



