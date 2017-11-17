---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método GetMetaConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 4f209014e9fde5841a9bce743f5364e6677d1e41
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4bcb2-103">Método GetMetaConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4bcb2-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4bcb2-104">Obtém as configurações do Gerenciador de Configurações Local usadas para controlar o Agente de Configuração.</span><span class="sxs-lookup"><span data-stu-id="4bcb2-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="4bcb2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4bcb2-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="4bcb2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4bcb2-106">Parameters</span></span>
----------

<span data-ttu-id="4bcb2-107">*MetaConfiguration* \[out\]</span><span class="sxs-lookup"><span data-stu-id="4bcb2-107">*MetaConfiguration* \[out\]</span></span>  
<span data-ttu-id="4bcb2-108">No retorno, contém uma instância incorporada da classe **MSFT_DSCMetaConfiguration** que define as configurações.</span><span class="sxs-lookup"><span data-stu-id="4bcb2-108">On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="4bcb2-109">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="4bcb2-109">Return value</span></span>
------------

<span data-ttu-id="4bcb2-110">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="4bcb2-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4bcb2-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="4bcb2-111">Remarks</span></span>

<span data-ttu-id="4bcb2-112">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="4bcb2-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4bcb2-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4bcb2-113">Requirements</span></span>
------------
><span data-ttu-id="4bcb2-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4bcb2-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="4bcb2-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4bcb2-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="4bcb2-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4bcb2-116">See also</span></span>


[<span data-ttu-id="4bcb2-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4bcb2-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



