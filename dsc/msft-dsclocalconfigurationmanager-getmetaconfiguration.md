---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC,powershell,configuração,instalação
title: Método GetMetaConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ddc016402239bcdea060a717fbac9ab7ea42698c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4b222-103">Método GetMetaConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4b222-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4b222-104">Obtém as configurações do Gerenciador de Configurações Local usadas para controlar o Agente de Configuração.</span><span class="sxs-lookup"><span data-stu-id="4b222-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="4b222-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4b222-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="4b222-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4b222-106">Parameters</span></span>
----------

<span data-ttu-id="4b222-107">*MetaConfiguration* \[out\] No retorno, contém uma instância inserida da classe **MSFT_DSCMetaConfiguration** que define as configurações.</span><span class="sxs-lookup"><span data-stu-id="4b222-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="4b222-108">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="4b222-108">Return value</span></span>
------------

<span data-ttu-id="4b222-109">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="4b222-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4b222-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="4b222-110">Remarks</span></span>

<span data-ttu-id="4b222-111">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="4b222-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4b222-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4b222-112">Requirements</span></span>
------------
><span data-ttu-id="4b222-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4b222-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="4b222-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4b222-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="4b222-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b222-115">See also</span></span>


[<span data-ttu-id="4b222-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4b222-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)