---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método ResourceTest da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 799b1cd91dfacf25c0e5e734ca96d20a776103f0
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="48230-103">Método ResourceTest da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="48230-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="48230-104">Chama diretamente o método **Test** de um recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="48230-104">Directly calls the **Test** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="48230-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48230-105">Syntax</span></span>
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a><span data-ttu-id="48230-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="48230-106">Parameters</span></span>
----------

<span data-ttu-id="48230-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="48230-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="48230-108">O nome do recurso a chamar.</span><span class="sxs-lookup"><span data-stu-id="48230-108">The name of the resource to call.</span></span>

<span data-ttu-id="48230-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="48230-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="48230-110">O nome do módulo que contém o recurso a chamar.</span><span class="sxs-lookup"><span data-stu-id="48230-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="48230-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="48230-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="48230-112">Especifica o nome da propriedade de recurso e seu valor em uma tabela de hash como chave e valor, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="48230-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="48230-113">Use o cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) para descobrir as propriedades de recurso e seus tipos.</span><span class="sxs-lookup"><span data-stu-id="48230-113">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="48230-114">*InDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="48230-114">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="48230-115">No retorno, essa propriedade será definida como **true** se o nó de destino estiver no estado desejado.</span><span class="sxs-lookup"><span data-stu-id="48230-115">On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="48230-116">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="48230-116">Return value</span></span>
------------

<span data-ttu-id="48230-117">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="48230-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="48230-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="48230-118">Remarks</span></span>

<span data-ttu-id="48230-119">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="48230-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="48230-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="48230-120">Requirements</span></span>
------------
><span data-ttu-id="48230-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="48230-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="48230-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="48230-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="48230-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48230-123">See also</span></span>


[<span data-ttu-id="48230-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="48230-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



