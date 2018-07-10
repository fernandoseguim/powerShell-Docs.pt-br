---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método SendConfigurationApply da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: da3a08307122ab38ee4a6fd5d4a9b97579a988f7
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893164"
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="55663-103">Método SendConfigurationApply da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="55663-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="55663-104">Envia o documento de configuração para o nó gerenciado e usa o Agente de Configuração para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="55663-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="55663-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="55663-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="55663-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="55663-106">Parameters</span></span>

<span data-ttu-id="55663-107">*ConfigurationData* \[in\] Dados de ambiente da configuração.</span><span class="sxs-lookup"><span data-stu-id="55663-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="55663-108">*force* \[in\] **true** para forçar a configuração a parar.</span><span class="sxs-lookup"><span data-stu-id="55663-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="55663-109">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="55663-109">Return value</span></span>

<span data-ttu-id="55663-110">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="55663-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="55663-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="55663-111">Remarks</span></span>

<span data-ttu-id="55663-112">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="55663-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="55663-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="55663-113">Requirements</span></span>

<span data-ttu-id="55663-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="55663-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="55663-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="55663-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="55663-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55663-116">See also</span></span>

[<span data-ttu-id="55663-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="55663-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)