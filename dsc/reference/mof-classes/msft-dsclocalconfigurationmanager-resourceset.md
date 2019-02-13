---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método ResourceSet da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 2712b7ff0a19e643c1f343d436c084f8970c9dd4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675755"
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="03a9d-103">Método ResourceSet da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="03a9d-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="03a9d-104">Chama diretamente o método **Set** de um recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="03a9d-104">Directly calls the **Set** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="03a9d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03a9d-105">Syntax</span></span>

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a><span data-ttu-id="03a9d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="03a9d-106">Parameters</span></span>

<span data-ttu-id="03a9d-107">*ResourceType* \[in\] O nome do recurso a chamar.</span><span class="sxs-lookup"><span data-stu-id="03a9d-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="03a9d-108">*ModuleName* \[in\] O nome do módulo que contém o recurso a chamar.</span><span class="sxs-lookup"><span data-stu-id="03a9d-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="03a9d-109">*resourceProperty* \[in\] Especifica o nome da propriedade do recurso e o respectivo valor em uma tabela de hash como chave e valor, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="03a9d-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="03a9d-110">Use o cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) para descobrir as propriedades de recurso e seus tipos.</span><span class="sxs-lookup"><span data-stu-id="03a9d-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="03a9d-111">*RebootRequired* \[out\] No retorno, essa propriedade será definida como **true**, se for necessário reiniciar o nó de destino.</span><span class="sxs-lookup"><span data-stu-id="03a9d-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="03a9d-112">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="03a9d-112">Return value</span></span>

<span data-ttu-id="03a9d-113">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="03a9d-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="03a9d-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="03a9d-114">Remarks</span></span>

<span data-ttu-id="03a9d-115">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="03a9d-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="03a9d-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="03a9d-116">Requirements</span></span>

<span data-ttu-id="03a9d-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="03a9d-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="03a9d-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="03a9d-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="03a9d-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03a9d-119">See also</span></span>

[<span data-ttu-id="03a9d-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="03a9d-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)