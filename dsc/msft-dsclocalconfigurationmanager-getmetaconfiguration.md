---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método GetMetaConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 695be4ee6490567295fda0cc44635870362d24b8
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="6077a-103">Método GetMetaConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="6077a-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="6077a-104">Obtém as configurações do Gerenciador de Configurações Local usadas para controlar o Agente de Configuração.</span><span class="sxs-lookup"><span data-stu-id="6077a-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="6077a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6077a-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="6077a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6077a-106">Parameters</span></span>
----------

<span data-ttu-id="6077a-107">*MetaConfiguration* \[out\]</span><span class="sxs-lookup"><span data-stu-id="6077a-107">*MetaConfiguration* \[out\]</span></span>  
<span data-ttu-id="6077a-108">No retorno, contém uma instância incorporada da classe **MSFT_DSCMetaConfiguration** que define as configurações.</span><span class="sxs-lookup"><span data-stu-id="6077a-108">On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="6077a-109">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="6077a-109">Return value</span></span>
------------

<span data-ttu-id="6077a-110">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="6077a-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="6077a-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="6077a-111">Remarks</span></span>

<span data-ttu-id="6077a-112">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="6077a-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6077a-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6077a-113">Requirements</span></span>
------------
><span data-ttu-id="6077a-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="6077a-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="6077a-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="6077a-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="6077a-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6077a-116">See also</span></span>


[<span data-ttu-id="6077a-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="6077a-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



