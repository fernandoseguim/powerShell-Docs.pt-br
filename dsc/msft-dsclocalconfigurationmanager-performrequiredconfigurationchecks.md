---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC,powershell,configuração,instalação
title: Método PerformRequiredConfigurationChecks da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 9cc4384088fcc39b09979b8ae4d023fc46307b13
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="883ef-103">Método PerformRequiredConfigurationChecks da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="883ef-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="883ef-104">Inicia uma verificação de consistência usando o Agendador de Tarefas.</span><span class="sxs-lookup"><span data-stu-id="883ef-104">Starts a consistency check by using the Task Scheduler.</span></span>

<a name="syntax"></a><span data-ttu-id="883ef-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="883ef-105">Syntax</span></span>
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a><span data-ttu-id="883ef-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="883ef-106">Parameters</span></span>
----------

<span data-ttu-id="883ef-107">*Flags* \[in\] Um bitmask que especifica o tipo de verificação de consistência a ser executada.</span><span class="sxs-lookup"><span data-stu-id="883ef-107">*Flags* \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="883ef-108">Os seguintes valores são válidos e podem ser combinados usando um operação **OR** bit a bit:</span><span class="sxs-lookup"><span data-stu-id="883ef-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="883ef-109">Valor</span><span class="sxs-lookup"><span data-stu-id="883ef-109">Value</span></span> |<span data-ttu-id="883ef-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="883ef-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="883ef-111">**1**</span><span class="sxs-lookup"><span data-stu-id="883ef-111">**1**</span></span> | <span data-ttu-id="883ef-112">Uma verificação de consistência normal.</span><span class="sxs-lookup"><span data-stu-id="883ef-112">A normal consistency check.</span></span> |
|<span data-ttu-id="883ef-113">**2**</span><span class="sxs-lookup"><span data-stu-id="883ef-113">**2**</span></span> | <span data-ttu-id="883ef-114">Uma continuação de uma verificação de consistência após uma reinicialização.</span><span class="sxs-lookup"><span data-stu-id="883ef-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="883ef-115">Esse valor não deve ser combinado com outros valores.</span><span class="sxs-lookup"><span data-stu-id="883ef-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="883ef-116">**4**</span><span class="sxs-lookup"><span data-stu-id="883ef-116">**4**</span></span> | <span data-ttu-id="883ef-117">A configuração deve ser extraída do servidor de pull especificado na metaconfiguração do nó.</span><span class="sxs-lookup"><span data-stu-id="883ef-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="883ef-118">Esse valor deve sempre ser combinado com **1**, para um valor de **5**.</span><span class="sxs-lookup"><span data-stu-id="883ef-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="883ef-119">**8**</span><span class="sxs-lookup"><span data-stu-id="883ef-119">**8**</span></span> | <span data-ttu-id="883ef-120">Envie status para o servidor de relatório.</span><span class="sxs-lookup"><span data-stu-id="883ef-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="883ef-121">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="883ef-121">Return value</span></span>
------------

<span data-ttu-id="883ef-122">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="883ef-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="883ef-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="883ef-123">Remarks</span></span>

<span data-ttu-id="883ef-124">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="883ef-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="883ef-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="883ef-125">Requirements</span></span>
------------
><span data-ttu-id="883ef-126">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="883ef-126">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="883ef-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="883ef-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="883ef-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="883ef-128">See also</span></span>


[<span data-ttu-id="883ef-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="883ef-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)