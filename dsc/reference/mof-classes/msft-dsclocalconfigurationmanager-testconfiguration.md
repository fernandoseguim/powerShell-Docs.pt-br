---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método TestConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d746832b01310f43a7aae33dd0fa70c0928bb3e0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675784"
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="847a2-103">Método TestConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="847a2-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="847a2-104">Envia o documento de configuração para o nó gerenciado e verifica a configuração atual de acordo com o documento.</span><span class="sxs-lookup"><span data-stu-id="847a2-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

## <a name="syntax"></a><span data-ttu-id="847a2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="847a2-105">Syntax</span></span>

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a><span data-ttu-id="847a2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="847a2-106">Parameters</span></span>

<span data-ttu-id="847a2-107">*configurationData* \[in\] Dados de ambiente de configuração.</span><span class="sxs-lookup"><span data-stu-id="847a2-107">*configurationData* \[in\] Environment data for the confuguration.</span></span>

<span data-ttu-id="847a2-108">*InDesiredState* \[out\] No retorno, especifica se o nó gerenciado está no estado especificado pelo documento de configuração.</span><span class="sxs-lookup"><span data-stu-id="847a2-108">*InDesiredState* \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="847a2-109">*ResourcesInDesiredState* \[out\] No retorno, contém uma instância incorporada da classe **MSFT_ResourceInDesiredState** que especifica os recursos que estão no estado desejado.</span><span class="sxs-lookup"><span data-stu-id="847a2-109">*ResourcesInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="847a2-110">*ResourcesNotInDesiredState* \[out\] No retorno, contém uma instância inserida da classe **MSFT_ResourceNotInDesiredState** que especifica os recursos que estão no estado desejado.</span><span class="sxs-lookup"><span data-stu-id="847a2-110">*ResourcesNotInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="847a2-111">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="847a2-111">Return value</span></span>

<span data-ttu-id="847a2-112">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="847a2-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="847a2-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="847a2-113">Remarks</span></span>

<span data-ttu-id="847a2-114">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="847a2-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="847a2-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="847a2-115">Requirements</span></span>

<span data-ttu-id="847a2-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="847a2-116">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="847a2-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="847a2-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="847a2-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="847a2-118">See also</span></span>

[<span data-ttu-id="847a2-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="847a2-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)