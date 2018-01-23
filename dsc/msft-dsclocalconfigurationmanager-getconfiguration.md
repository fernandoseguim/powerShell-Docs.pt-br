---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Método GetConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 60f4b49575dbb28ce74af0500e6982ec5d2e7a66
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="79593-103">Método GetConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="79593-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="79593-104">Envia o documento de configuração para o nó gerenciado e usa o método **Get** do Agente de Configuração para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="79593-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="79593-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="79593-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="79593-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="79593-106">Parameters</span></span>
----------

<span data-ttu-id="79593-107">*configurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="79593-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="79593-108">Especifica os dados de configuração para envio.</span><span class="sxs-lookup"><span data-stu-id="79593-108">Specifies the configuration data to send.</span></span>

<span data-ttu-id="79593-109">*configurations* \[out\]</span><span class="sxs-lookup"><span data-stu-id="79593-109">*configurations* \[out\]</span></span>  
<span data-ttu-id="79593-110">No retorno, contém uma instância incorporada das configurações.</span><span class="sxs-lookup"><span data-stu-id="79593-110">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="79593-111">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="79593-111">Return value</span></span>
------------

<span data-ttu-id="79593-112">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="79593-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="79593-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="79593-113">Remarks</span></span>

<span data-ttu-id="79593-114">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="79593-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="79593-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="79593-115">Requirements</span></span>
------------
><span data-ttu-id="79593-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="79593-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="79593-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="79593-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="79593-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79593-118">See also</span></span>


[<span data-ttu-id="79593-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="79593-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



