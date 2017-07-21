---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: e02ed81a7b8436323bc68aaa2587a445e6a5adf9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="bd305-103">Método GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="bd305-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="bd305-104">Obtém o histórico do status de configuração.</span><span class="sxs-lookup"><span data-stu-id="bd305-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="bd305-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bd305-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="bd305-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bd305-106">Parameters</span></span>
----------

<span data-ttu-id="bd305-107">*All* \[in\]</span><span class="sxs-lookup"><span data-stu-id="bd305-107">*All* \[in\]</span></span>  
<span data-ttu-id="bd305-108">**true** caso esse método deva retornar informações sobre todos as configurações executadas no computador, incluindo o aplicativo de configuração e a verificação de consistência.</span><span class="sxs-lookup"><span data-stu-id="bd305-108">**true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="bd305-109">*configurationStatus* \[out\]</span><span class="sxs-lookup"><span data-stu-id="bd305-109">*configurationStatus* \[out\]</span></span>  
<span data-ttu-id="bd305-110">No retorno, contém uma instância incorporada da classe **MSFT_DSCConfigurationStatus** que define as configurações.</span><span class="sxs-lookup"><span data-stu-id="bd305-110">On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="bd305-111">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="bd305-111">Return value</span></span>
------------

<span data-ttu-id="bd305-112">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="bd305-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bd305-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="bd305-113">Remarks</span></span>

<span data-ttu-id="bd305-114">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="bd305-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bd305-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bd305-115">Requirements</span></span>
------------
><span data-ttu-id="bd305-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bd305-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="bd305-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bd305-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="bd305-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd305-118">See also</span></span>


[<span data-ttu-id="bd305-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="bd305-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



