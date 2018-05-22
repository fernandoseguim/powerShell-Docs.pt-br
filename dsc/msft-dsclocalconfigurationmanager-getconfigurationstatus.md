---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 725b1a2a62510a4e9b59aabdec8a7e502c737bfc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4fae2-103">Método GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4fae2-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4fae2-104">Obtém o histórico do status de configuração.</span><span class="sxs-lookup"><span data-stu-id="4fae2-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="4fae2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4fae2-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="4fae2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4fae2-106">Parameters</span></span>
----------

<span data-ttu-id="4fae2-107">*All* \[in\] **true** caso esse método deva retornar informações sobre todos as configurações executadas no computador, inclusive a configuração de aplicativo e a verificação de consistência.</span><span class="sxs-lookup"><span data-stu-id="4fae2-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="4fae2-108">*configurationStatus* \[out\] No retorno, contém uma instância inserida da classe **MSFT_DSCConfigurationStatus** que define as configurações.</span><span class="sxs-lookup"><span data-stu-id="4fae2-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="4fae2-109">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="4fae2-109">Return value</span></span>
------------

<span data-ttu-id="4fae2-110">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="4fae2-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4fae2-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="4fae2-111">Remarks</span></span>

<span data-ttu-id="4fae2-112">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="4fae2-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4fae2-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4fae2-113">Requirements</span></span>
------------
><span data-ttu-id="4fae2-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4fae2-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="4fae2-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4fae2-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="4fae2-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4fae2-116">See also</span></span>


[<span data-ttu-id="4fae2-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4fae2-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)