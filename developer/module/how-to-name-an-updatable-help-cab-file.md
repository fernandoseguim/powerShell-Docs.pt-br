---
title: Como nomear um arquivo CAB de ajuda atualizável | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 0b58d5ee19a85bed26bc6549ced48b890cd62f64
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794750"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="ee3d2-102">Como nomear um arquivo CAB de ajuda atualizável</span><span class="sxs-lookup"><span data-stu-id="ee3d2-102">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="ee3d2-103">Este tópico explica o formato de nome necessário para o arquivo de gabinete de ajuda atualizável (. Arquivos CAB).</span><span class="sxs-lookup"><span data-stu-id="ee3d2-103">This topic explains the required name format for the Updatable Help cabinet (.CAB) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="ee3d2-104">Como nomear um arquivo CAB de ajuda atualizável</span><span class="sxs-lookup"><span data-stu-id="ee3d2-104">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="ee3d2-105">Atualizável é um gabinete (. Arquivo CAB) deve ter um nome com o seguinte formato.</span><span class="sxs-lookup"><span data-stu-id="ee3d2-105">A Updatable cabinet (.CAB) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="ee3d2-106">Os elementos do nome são da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="ee3d2-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="ee3d2-107">ModuleName o valor da **nome** propriedade da **ModuleInfo** do objeto que o [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet retorna.</span><span class="sxs-lookup"><span data-stu-id="ee3d2-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="ee3d2-108">ModuleGUID o valor da **GUID** chave no manifesto de módulo.</span><span class="sxs-lookup"><span data-stu-id="ee3d2-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="ee3d2-109">Cultura de UICulture a interface do usuário dos arquivos de Ajuda no arquivo CAB.</span><span class="sxs-lookup"><span data-stu-id="ee3d2-109">UICulture The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="ee3d2-110">Esse valor deve corresponder ao valor de um dos **UICulture** elementos no arquivo XML HelpInfo para o módulo.</span><span class="sxs-lookup"><span data-stu-id="ee3d2-110">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="ee3d2-111">Por exemplo, se o nome do módulo é "TestModule", o GUID do módulo é 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 e a cultura de interface do usuário é "en-US", o nome do arquivo CAB seria:</span><span class="sxs-lookup"><span data-stu-id="ee3d2-111">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`