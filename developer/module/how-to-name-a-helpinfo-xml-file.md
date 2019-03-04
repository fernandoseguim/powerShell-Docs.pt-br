---
title: Como nomear um arquivo XML HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: a3e8ae664d5c0e29d0f84174950bebe6a1da6a81
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857822"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a>Como nomear um arquivo XML HelpInfo

Este tópico explica o formato de nome necessário para os arquivos de informações de ajuda atualizável, comumente conhecido como arquivos XML HelpInfo.

## <a name="how-to-name-a-helpinfo-xml-file"></a>Como nomear um arquivo XML HelpInfo

Um arquivo XML HelpInfo deve ter um nome com o seguinte formato.

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

Os elementos do nome são da seguinte maneira.

ModuleName o valor da **nome** propriedade da **ModuleInfo** do objeto que o [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet retorna.
O valor da **nome** propriedade da **ModuleInfo** do objeto que o [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet retorna.

ModuleGUID o valor da **GUID** chave no manifesto de módulo.

Por exemplo, se o nome do módulo é "TestModule" e o GUID do módulo é 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, o nome do arquivo XML HelpInfo para o módulo seria:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`