---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método ResourceSet da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 7291641098578226449f8cbd360da0a3f9842598
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5de04-103">Método ResourceSet da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="5de04-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5de04-104">Chama diretamente o método **Set** de um recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="5de04-104">Directly calls the **Set** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="5de04-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5de04-105">Syntax</span></span>
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a><span data-ttu-id="5de04-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5de04-106">Parameters</span></span>
----------

<span data-ttu-id="5de04-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="5de04-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="5de04-108">O nome do recurso a chamar.</span><span class="sxs-lookup"><span data-stu-id="5de04-108">The name of the resource to call.</span></span>

<span data-ttu-id="5de04-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="5de04-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="5de04-110">O nome do módulo que contém o recurso a chamar.</span><span class="sxs-lookup"><span data-stu-id="5de04-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="5de04-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="5de04-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="5de04-112">Especifica o nome da propriedade de recurso e seu valor em uma tabela de hash como chave e valor, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="5de04-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="5de04-113">Use o cmdlet [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) para descobrir as propriedades de recurso e seus tipos.</span><span class="sxs-lookup"><span data-stu-id="5de04-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="5de04-114">*RebootRequired* \[out\]</span><span class="sxs-lookup"><span data-stu-id="5de04-114">*RebootRequired* \[out\]</span></span>  
<span data-ttu-id="5de04-115">No retorno, essa propriedade será definida como **true** se o nó de destino precisar ser reiniciado.</span><span class="sxs-lookup"><span data-stu-id="5de04-115">On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="5de04-116">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="5de04-116">Return value</span></span>
------------

<span data-ttu-id="5de04-117">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="5de04-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5de04-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="5de04-118">Remarks</span></span>

<span data-ttu-id="5de04-119">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="5de04-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5de04-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5de04-120">Requirements</span></span>
------------
><span data-ttu-id="5de04-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5de04-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="5de04-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5de04-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="5de04-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5de04-123">See also</span></span>


[<span data-ttu-id="5de04-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5de04-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



