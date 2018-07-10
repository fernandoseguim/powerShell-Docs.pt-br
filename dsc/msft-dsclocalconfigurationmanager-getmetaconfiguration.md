---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Método GetMetaConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e14237ef68b95d68e2f14071aa1fa6ba0717f39f
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892834"
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="932de-103">Método GetMetaConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="932de-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="932de-104">Obtém as configurações do Gerenciador de Configurações Local usadas para controlar o Agente de Configuração.</span><span class="sxs-lookup"><span data-stu-id="932de-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="932de-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="932de-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="932de-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="932de-106">Parameters</span></span>

<span data-ttu-id="932de-107">*MetaConfiguration* \[out\] No retorno, contém uma instância inserida da classe **MSFT_DSCMetaConfiguration** que define as configurações.</span><span class="sxs-lookup"><span data-stu-id="932de-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="932de-108">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="932de-108">Return value</span></span>

<span data-ttu-id="932de-109">Retorna zero em caso de êxito; caso contrário, retorna um código de erro.</span><span class="sxs-lookup"><span data-stu-id="932de-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="932de-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="932de-110">Remarks</span></span>

<span data-ttu-id="932de-111">Esse é um método estático.</span><span class="sxs-lookup"><span data-stu-id="932de-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="932de-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="932de-112">Requirements</span></span>

<span data-ttu-id="932de-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="932de-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="932de-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="932de-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="932de-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="932de-115">See also</span></span>

[<span data-ttu-id="932de-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="932de-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)