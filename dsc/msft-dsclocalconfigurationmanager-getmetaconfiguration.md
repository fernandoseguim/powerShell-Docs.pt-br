---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método GetMetaConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ebf2b65f152c622ccf42e12545b0048a0b96d963
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219769"
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="be1bb-103">Método GetMetaConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="be1bb-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="be1bb-104">Obtém as configurações do Gerenciador de Configurações Local usadas para controlar o Agente de Configuração.</span><span class="sxs-lookup"><span data-stu-id="be1bb-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="be1bb-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="be1bb-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="be1bb-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="be1bb-106">Parameters</span></span>
----------

<span data-ttu-id="be1bb-107">*MetaConfiguration* \[out\] No retorno, contém uma instância inserida da classe **MSFT_DSCMetaConfiguration** que define as configurações.</span><span class="sxs-lookup"><span data-stu-id="be1bb-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="be1bb-108">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="be1bb-108">Return value</span></span>
------------

<span data-ttu-id="be1bb-109">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="be1bb-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="be1bb-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="be1bb-110">Remarks</span></span>

<span data-ttu-id="be1bb-111">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="be1bb-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="be1bb-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="be1bb-112">Requirements</span></span>
------------
><span data-ttu-id="be1bb-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="be1bb-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="be1bb-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="be1bb-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="be1bb-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be1bb-115">See also</span></span>


[<span data-ttu-id="be1bb-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="be1bb-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)