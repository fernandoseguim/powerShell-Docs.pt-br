---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método GetMetaConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e14237ef68b95d68e2f14071aa1fa6ba0717f39f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675831"
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="fafdb-103">Método GetMetaConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="fafdb-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="fafdb-104">Obtém as configurações do Gerenciador de Configurações Local usadas para controlar o Agente de Configuração.</span><span class="sxs-lookup"><span data-stu-id="fafdb-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="fafdb-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fafdb-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="fafdb-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fafdb-106">Parameters</span></span>

<span data-ttu-id="fafdb-107">*MetaConfiguration* \[out\] No retorno, contém uma instância inserida da classe **MSFT_DSCMetaConfiguration** que define as configurações.</span><span class="sxs-lookup"><span data-stu-id="fafdb-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="fafdb-108">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="fafdb-108">Return value</span></span>

<span data-ttu-id="fafdb-109">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="fafdb-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fafdb-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="fafdb-110">Remarks</span></span>

<span data-ttu-id="fafdb-111">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="fafdb-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fafdb-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fafdb-112">Requirements</span></span>

<span data-ttu-id="fafdb-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="fafdb-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="fafdb-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fafdb-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="fafdb-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fafdb-115">See also</span></span>

[<span data-ttu-id="fafdb-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="fafdb-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)