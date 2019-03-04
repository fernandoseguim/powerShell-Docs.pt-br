---
title: Como testar a Ajuda atualizável | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: f2f319a3cab4b4bd91e9b634dda57d58a6476b62
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854732"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="4f2cb-102">Como testar a ajuda atualizável</span><span class="sxs-lookup"><span data-stu-id="4f2cb-102">How to Test Updatable Help</span></span>

<span data-ttu-id="4f2cb-103">Este tópico descreve abordagens para testar a Ajuda atualizável para um módulo.</span><span class="sxs-lookup"><span data-stu-id="4f2cb-103">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="4f2cb-104">Uso detalhado para detectar erros</span><span class="sxs-lookup"><span data-stu-id="4f2cb-104">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="4f2cb-105">Depois de carregar o arquivo XML HelpInfo e os arquivos CAB para o seu módulo, os arquivos de teste, executando uma [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) com o **detalhado** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4f2cb-105">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="4f2cb-106">O **Verbose** parâmetro direciona `Update-Help` para relatar as etapas essenciais em suas ações, de leitura a **HelpInfoUri** chave no manifesto de módulo para validar os tipos de arquivo no arquivo CAB descompactado e colocar os arquivos no diretório do módulo de idioma específico.</span><span class="sxs-lookup"><span data-stu-id="4f2cb-106">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>
<span data-ttu-id="4f2cb-107">Depois de carregar o arquivo XML HelpInfo e os arquivos CAB para o seu módulo, os arquivos de teste, executando uma [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) com o **detalhado** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4f2cb-107">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="4f2cb-108">O **Verbose** parâmetro direciona `Update-Help` para relatar as etapas essenciais em suas ações, de leitura a **HelpInfoUri** chave no manifesto de módulo para validar os tipos de arquivo no arquivo CAB descompactado e colocar os arquivos no diretório do módulo de idioma específico.</span><span class="sxs-lookup"><span data-stu-id="4f2cb-108">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="4f2cb-109">Quando todas as mensagens detalhadas são resolvidas, executar uma `Update-Help` com o **depurar** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4f2cb-109">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span> <span data-ttu-id="4f2cb-110">Esse parâmetro deve detectar problemas restantes com os arquivos de ajuda atualizável.</span><span class="sxs-lookup"><span data-stu-id="4f2cb-110">This parameter should detect any remaining problems with the Updatable Help files.</span></span>