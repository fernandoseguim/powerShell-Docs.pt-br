---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método SendConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 72c59b5aad293fa561146e5ad6822f27f40f321f
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="54614-103">Método SendConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="54614-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="54614-104">Envia o documento de configuração para o nó gerenciado e o salva como alteração pendente.</span><span class="sxs-lookup"><span data-stu-id="54614-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="54614-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="54614-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="54614-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="54614-106">Parameters</span></span>
----------

<span data-ttu-id="54614-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="54614-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="54614-108">Dados do ambiente para a configuração.</span><span class="sxs-lookup"><span data-stu-id="54614-108">The environment data for the configuration.</span></span>

<span data-ttu-id="54614-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="54614-109">*force* \[in\]</span></span>  
<span data-ttu-id="54614-110">**true** para forçar a configuração a parar.</span><span class="sxs-lookup"><span data-stu-id="54614-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="54614-111">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="54614-111">Return value</span></span>
------------

<span data-ttu-id="54614-112">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="54614-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="54614-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="54614-113">Remarks</span></span>

<span data-ttu-id="54614-114">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="54614-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="54614-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="54614-115">Requirements</span></span>
------------
><span data-ttu-id="54614-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="54614-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="54614-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="54614-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="54614-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54614-118">See also</span></span>


[<span data-ttu-id="54614-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="54614-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



