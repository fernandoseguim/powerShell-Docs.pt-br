---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método SendMetaConfigurationApply da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 350555220757b1939b1de34ab423e963635eb53c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="860e1-103">Método SendMetaConfigurationApply da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="860e1-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="860e1-104">Define as configurações do Gerenciador de Configurações Local usadas para controlar o Agente de Configuração.</span><span class="sxs-lookup"><span data-stu-id="860e1-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="860e1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="860e1-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="860e1-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="860e1-106">Parameters</span></span>
----------

<span data-ttu-id="860e1-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="860e1-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="860e1-108">Dados do ambiente para a configuração.</span><span class="sxs-lookup"><span data-stu-id="860e1-108">The environment data for the configuration.</span></span>

<span data-ttu-id="860e1-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="860e1-109">*force* \[in\]</span></span>  
<span data-ttu-id="860e1-110">**true** para forçar a configuração a parar.</span><span class="sxs-lookup"><span data-stu-id="860e1-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="860e1-111">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="860e1-111">Return value</span></span>
------------

<span data-ttu-id="860e1-112">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="860e1-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="860e1-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="860e1-113">Remarks</span></span>

<span data-ttu-id="860e1-114">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="860e1-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="860e1-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="860e1-115">Requirements</span></span>
------------
><span data-ttu-id="860e1-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="860e1-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="860e1-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="860e1-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="860e1-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="860e1-118">See also</span></span>


[<span data-ttu-id="860e1-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="860e1-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



