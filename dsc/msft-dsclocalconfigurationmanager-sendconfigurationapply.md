---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método SendConfigurationApply da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 20f732d35860cccde4e507dc6916e27d0cf8c5f6
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4b592-103">Método SendConfigurationApply da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4b592-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4b592-104">Envia o documento de configuração para o nó gerenciado e usa o Agente de Configuração para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="4b592-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="4b592-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4b592-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="4b592-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4b592-106">Parameters</span></span>
----------

<span data-ttu-id="4b592-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="4b592-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="4b592-108">Dados do ambiente para a configuração.</span><span class="sxs-lookup"><span data-stu-id="4b592-108">The environment data for the configuration.</span></span>

<span data-ttu-id="4b592-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="4b592-109">*force* \[in\]</span></span>  
<span data-ttu-id="4b592-110">**true** para forçar a configuração a parar.</span><span class="sxs-lookup"><span data-stu-id="4b592-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="4b592-111">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="4b592-111">Return value</span></span>
------------

<span data-ttu-id="4b592-112">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="4b592-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4b592-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="4b592-113">Remarks</span></span>

<span data-ttu-id="4b592-114">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="4b592-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4b592-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4b592-115">Requirements</span></span>
------------
><span data-ttu-id="4b592-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4b592-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="4b592-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4b592-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="4b592-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b592-118">See also</span></span>


[<span data-ttu-id="4b592-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4b592-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



