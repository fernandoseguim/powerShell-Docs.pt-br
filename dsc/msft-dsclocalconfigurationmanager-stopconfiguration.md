---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método StopConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 66d00cb40750e91e4b369a2e8cebb449697406d9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="18fbc-103">Método StopConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="18fbc-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="18fbc-104">Interrompe a alteração da configuração em andamento.</span><span class="sxs-lookup"><span data-stu-id="18fbc-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="18fbc-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="18fbc-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="18fbc-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="18fbc-106">Parameters</span></span>
----------

<span data-ttu-id="18fbc-107">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="18fbc-107">*force* \[in\]</span></span>  
<span data-ttu-id="18fbc-108">**true** para forçar a configuração a parar.</span><span class="sxs-lookup"><span data-stu-id="18fbc-108">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="18fbc-109">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="18fbc-109">Return value</span></span>
------------

<span data-ttu-id="18fbc-110">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="18fbc-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="18fbc-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="18fbc-111">Remarks</span></span>

<span data-ttu-id="18fbc-112">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="18fbc-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="18fbc-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="18fbc-113">Requirements</span></span>
------------
><span data-ttu-id="18fbc-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="18fbc-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="18fbc-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="18fbc-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="18fbc-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="18fbc-116">See also</span></span>


[<span data-ttu-id="18fbc-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="18fbc-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



