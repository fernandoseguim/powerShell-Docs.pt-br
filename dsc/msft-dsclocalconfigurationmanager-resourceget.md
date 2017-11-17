---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método ResourceGet da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 7d8b185c49778253dcb4e983ad948775c4cb0842
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="decbc-103">Método ResourceGet da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="decbc-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="decbc-104">Chama diretamente o método **Get** de um recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="decbc-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="decbc-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="decbc-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="decbc-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="decbc-106">Parameters</span></span>
----------

<span data-ttu-id="decbc-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="decbc-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="decbc-108">O nome do recurso a chamar.</span><span class="sxs-lookup"><span data-stu-id="decbc-108">The name of the resource to call.</span></span>

<span data-ttu-id="decbc-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="decbc-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="decbc-110">O nome do módulo que contém o recurso a chamar.</span><span class="sxs-lookup"><span data-stu-id="decbc-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="decbc-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="decbc-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="decbc-112">Especifica o nome da propriedade de recurso e seu valor em uma tabela de hash como chave e valor, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="decbc-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="decbc-113">Use o cmdlet [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) para descobrir as propriedades de recurso e seus tipos.</span><span class="sxs-lookup"><span data-stu-id="decbc-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="decbc-114">*configurations* \[out\]</span><span class="sxs-lookup"><span data-stu-id="decbc-114">*configurations* \[out\]</span></span>  
<span data-ttu-id="decbc-115">No retorno, contém uma instância incorporada das configurações.</span><span class="sxs-lookup"><span data-stu-id="decbc-115">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="decbc-116">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="decbc-116">Return value</span></span>
------------

<span data-ttu-id="decbc-117">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="decbc-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="decbc-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="decbc-118">Remarks</span></span>

<span data-ttu-id="decbc-119">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="decbc-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="decbc-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="decbc-120">Requirements</span></span>
------------
><span data-ttu-id="decbc-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="decbc-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="decbc-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="decbc-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="decbc-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="decbc-123">See also</span></span>


[<span data-ttu-id="decbc-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="decbc-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



