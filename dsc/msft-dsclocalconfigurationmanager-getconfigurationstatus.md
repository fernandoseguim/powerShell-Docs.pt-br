---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: a41e7a15fc935c2cd5fd4cb66d0ab13509d5d4e0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="151d0-103">Método GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="151d0-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="151d0-104">Obtém o histórico do status de configuração.</span><span class="sxs-lookup"><span data-stu-id="151d0-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="151d0-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="151d0-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="151d0-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="151d0-106">Parameters</span></span>
----------

<span data-ttu-id="151d0-107">*All* \[in\]</span><span class="sxs-lookup"><span data-stu-id="151d0-107">*All* \[in\]</span></span>  
<span data-ttu-id="151d0-108">**true** caso esse método deva retornar informações sobre todos as configurações executadas no computador, incluindo o aplicativo de configuração e a verificação de consistência.</span><span class="sxs-lookup"><span data-stu-id="151d0-108">**true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="151d0-109">*configurationStatus* \[out\]</span><span class="sxs-lookup"><span data-stu-id="151d0-109">*configurationStatus* \[out\]</span></span>  
<span data-ttu-id="151d0-110">No retorno, contém uma instância incorporada da classe **MSFT_DSCConfigurationStatus** que define as configurações.</span><span class="sxs-lookup"><span data-stu-id="151d0-110">On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="151d0-111">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="151d0-111">Return value</span></span>
------------

<span data-ttu-id="151d0-112">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="151d0-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="151d0-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="151d0-113">Remarks</span></span>

<span data-ttu-id="151d0-114">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="151d0-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="151d0-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="151d0-115">Requirements</span></span>
------------
><span data-ttu-id="151d0-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="151d0-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="151d0-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="151d0-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="151d0-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="151d0-118">See also</span></span>


[<span data-ttu-id="151d0-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="151d0-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



