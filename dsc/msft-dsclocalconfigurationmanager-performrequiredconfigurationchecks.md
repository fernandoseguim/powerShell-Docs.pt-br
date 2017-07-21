---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método PerformRequiredConfigurationChecks da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 26110b3920104da7343b8d55cf63440c12accbbc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="2235f-103">Método PerformRequiredConfigurationChecks da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="2235f-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="2235f-104">Inicia uma verificação de consistência usando o Agendador de Tarefas.</span><span class="sxs-lookup"><span data-stu-id="2235f-104">Starts a consistency check by using the Task Scheduler.</span></span>

<a name="syntax"></a><span data-ttu-id="2235f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2235f-105">Syntax</span></span>
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a><span data-ttu-id="2235f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2235f-106">Parameters</span></span>
----------

<span data-ttu-id="2235f-107">*Flags* \[in\]</span><span class="sxs-lookup"><span data-stu-id="2235f-107">*Flags* \[in\]</span></span>  
<span data-ttu-id="2235f-108">Um bitmask que especifica o tipo de verificação de consistência a ser executada.</span><span class="sxs-lookup"><span data-stu-id="2235f-108">A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="2235f-109">Os seguintes valores são válidos e podem ser combinados usando um operação **OR** bit a bit:</span><span class="sxs-lookup"><span data-stu-id="2235f-109">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="2235f-110">Valor</span><span class="sxs-lookup"><span data-stu-id="2235f-110">Value</span></span> |<span data-ttu-id="2235f-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="2235f-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="2235f-112">**1**</span><span class="sxs-lookup"><span data-stu-id="2235f-112">**1**</span></span> | <span data-ttu-id="2235f-113">Uma verificação de consistência normal.</span><span class="sxs-lookup"><span data-stu-id="2235f-113">A normal consistency check.</span></span> |
|<span data-ttu-id="2235f-114">**2**</span><span class="sxs-lookup"><span data-stu-id="2235f-114">**2**</span></span> | <span data-ttu-id="2235f-115">Uma continuação de uma verificação de consistência após uma reinicialização.</span><span class="sxs-lookup"><span data-stu-id="2235f-115">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="2235f-116">Esse valor não deve ser combinado com outros valores.</span><span class="sxs-lookup"><span data-stu-id="2235f-116">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="2235f-117">**4**</span><span class="sxs-lookup"><span data-stu-id="2235f-117">**4**</span></span> | <span data-ttu-id="2235f-118">A configuração deve ser extraída do servidor de pull especificado na metaconfiguração do nó.</span><span class="sxs-lookup"><span data-stu-id="2235f-118">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="2235f-119">Esse valor deve sempre ser combinado com **1**, para um valor de **5**.</span><span class="sxs-lookup"><span data-stu-id="2235f-119">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="2235f-120">**8**</span><span class="sxs-lookup"><span data-stu-id="2235f-120">**8**</span></span> | <span data-ttu-id="2235f-121">Envie status para o servidor de relatório.</span><span class="sxs-lookup"><span data-stu-id="2235f-121">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="2235f-122">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="2235f-122">Return value</span></span>
------------

<span data-ttu-id="2235f-123">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="2235f-123">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2235f-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="2235f-124">Remarks</span></span>

<span data-ttu-id="2235f-125">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="2235f-125">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2235f-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2235f-126">Requirements</span></span>
------------
><span data-ttu-id="2235f-127">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2235f-127">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="2235f-128">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2235f-128">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="2235f-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2235f-129">See also</span></span>


[<span data-ttu-id="2235f-130">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2235f-130">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



