---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método ResourceGet da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 30cbaa907d4dc3a921c9e5fe61ffddc5d61c2347
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="29a90-103">Método ResourceGet da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="29a90-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="29a90-104">Chama diretamente o método **Get** de um recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="29a90-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="29a90-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29a90-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="29a90-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="29a90-106">Parameters</span></span>
----------

<span data-ttu-id="29a90-107">*ResourceType* \[in\] O nome do recurso a chamar.</span><span class="sxs-lookup"><span data-stu-id="29a90-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="29a90-108">*ModuleName* \[in\] O nome do módulo que contém o recurso a chamar.</span><span class="sxs-lookup"><span data-stu-id="29a90-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="29a90-109">*resourceProperty* \[in\] Especifica o nome da propriedade do recurso e o respectivo valor em uma tabela de hash como chave e valor, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="29a90-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="29a90-110">Use o cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) para descobrir as propriedades de recurso e seus tipos.</span><span class="sxs-lookup"><span data-stu-id="29a90-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="29a90-111">*configurations* \[out\] No retorno, contém uma instância inserida das configurações.</span><span class="sxs-lookup"><span data-stu-id="29a90-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="29a90-112">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="29a90-112">Return value</span></span>
------------

<span data-ttu-id="29a90-113">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="29a90-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="29a90-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="29a90-114">Remarks</span></span>

<span data-ttu-id="29a90-115">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="29a90-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="29a90-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="29a90-116">Requirements</span></span>
------------
><span data-ttu-id="29a90-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="29a90-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="29a90-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="29a90-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="29a90-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29a90-119">See also</span></span>


[<span data-ttu-id="29a90-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="29a90-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)