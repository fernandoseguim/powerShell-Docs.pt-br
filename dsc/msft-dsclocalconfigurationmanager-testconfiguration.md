---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método TestConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 8e9986837aaf41b1396a2399c58675bc51b0b708
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="40fa1-103">Método TestConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="40fa1-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="40fa1-104">Envia o documento de configuração para o nó gerenciado e verifica a configuração atual de acordo com o documento.</span><span class="sxs-lookup"><span data-stu-id="40fa1-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

<a name="syntax"></a><span data-ttu-id="40fa1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="40fa1-105">Syntax</span></span>
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a><span data-ttu-id="40fa1-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="40fa1-106">Parameters</span></span>
----------

<span data-ttu-id="40fa1-107">*configurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="40fa1-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="40fa1-108">Dados de ambiente de configuration.</span><span class="sxs-lookup"><span data-stu-id="40fa1-108">Environment data for the confuguration.</span></span>

<span data-ttu-id="40fa1-109">*InDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="40fa1-109">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="40fa1-110">No retorno, especifica se o nó gerenciado está no estado especificado pelo documento de configuração.</span><span class="sxs-lookup"><span data-stu-id="40fa1-110">On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="40fa1-111">*ResourcesInDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="40fa1-111">*ResourcesInDesiredState* \[out\]</span></span>  
<span data-ttu-id="40fa1-112">No retorno, contém uma instância incorporada da classe **MSFT_ResourceInDesiredState** que especifica os recursos que estão no estado desejado.</span><span class="sxs-lookup"><span data-stu-id="40fa1-112">On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="40fa1-113">*ResourcesNotInDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="40fa1-113">*ResourcesNotInDesiredState* \[out\]</span></span>  
<span data-ttu-id="40fa1-114">No retorno, contém uma instância incorporada da classe **MSFT_ResourceNotInDesiredState** que especifica os recursos que não estão no estado desejado.</span><span class="sxs-lookup"><span data-stu-id="40fa1-114">On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="40fa1-115">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="40fa1-115">Return value</span></span>
------------

<span data-ttu-id="40fa1-116">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="40fa1-116">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="40fa1-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="40fa1-117">Remarks</span></span>

<span data-ttu-id="40fa1-118">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="40fa1-118">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="40fa1-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="40fa1-119">Requirements</span></span>
------------
><span data-ttu-id="40fa1-120">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="40fa1-120">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="40fa1-121">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="40fa1-121">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="40fa1-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40fa1-122">See also</span></span>


[<span data-ttu-id="40fa1-123">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="40fa1-123">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



