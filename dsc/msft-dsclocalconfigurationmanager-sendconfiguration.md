---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método SendConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 8457189538ceb0181a8e65b57a9fc3e911cbcec4
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="306b4-103">Método SendConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="306b4-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="306b4-104">Envia o documento de configuração para o nó gerenciado e o salva como alteração pendente.</span><span class="sxs-lookup"><span data-stu-id="306b4-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="306b4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="306b4-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="306b4-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="306b4-106">Parameters</span></span>
----------

<span data-ttu-id="306b4-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="306b4-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="306b4-108">Dados do ambiente para a configuração.</span><span class="sxs-lookup"><span data-stu-id="306b4-108">The environment data for the configuration.</span></span>

<span data-ttu-id="306b4-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="306b4-109">*force* \[in\]</span></span>  
<span data-ttu-id="306b4-110">**true** para forçar a configuração a parar.</span><span class="sxs-lookup"><span data-stu-id="306b4-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="306b4-111">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="306b4-111">Return value</span></span>
------------

<span data-ttu-id="306b4-112">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="306b4-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="306b4-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="306b4-113">Remarks</span></span>

<span data-ttu-id="306b4-114">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="306b4-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="306b4-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="306b4-115">Requirements</span></span>
------------
><span data-ttu-id="306b4-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="306b4-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="306b4-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="306b4-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="306b4-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="306b4-118">See also</span></span>


[<span data-ttu-id="306b4-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="306b4-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



