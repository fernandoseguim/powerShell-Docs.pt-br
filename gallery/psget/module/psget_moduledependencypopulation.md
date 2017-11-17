---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: psget_moduledependencypopulation
ms.openlocfilehash: 126cd65ac35a31f4118474bc36dac1836ec0f22e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="logic-for-preparing-the-module-dependencies-during-publish-operation"></a><span data-ttu-id="46e48-103">Lógica para preparar as dependências do módulo durante a operação de publicação</span><span class="sxs-lookup"><span data-stu-id="46e48-103">Logic for preparing the module dependencies during Publish operation</span></span>
1.  <span data-ttu-id="46e48-104">Módulos listados como parte de RequiredModules são considerados dependências.</span><span class="sxs-lookup"><span data-stu-id="46e48-104">Modules listed as part of RequiredModules are considered as dependencies.</span></span>
2.  <span data-ttu-id="46e48-105">Módulos listados como parte de NestedModules, cuja base do módulo não está sob a base do módulo especificado, são considerados dependências.</span><span class="sxs-lookup"><span data-stu-id="46e48-105">Modules listed as part of NestedModules, whose module base is not under the specified module base, are considered as dependencies.</span></span>

3.  <span data-ttu-id="46e48-106">As dependências acima devem estar disponíveis no mesmo repositório de destino, caso contrário, a operação de publicação resultará em um erro.</span><span class="sxs-lookup"><span data-stu-id="46e48-106">Above dependencies should be available on the same target repository, otherwise publish operation will result in an error.</span></span>
    <span data-ttu-id="46e48-107">Por exemplo: se "SnippetPx" não estiver disponível no repositório, o erro abaixo será gerado.</span><span class="sxs-lookup"><span data-stu-id="46e48-107">For example: If 'SnippetPx' is not available on the repository, below error will be thrown.</span></span>
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  <span data-ttu-id="46e48-108">Algumas dependências de módulo podem ser gerenciadas externamente. Nesse caso, elas devem ser adicionadas à entrada ExternalModuleDependencies na seção PSData do manifesto do módulo.</span><span class="sxs-lookup"><span data-stu-id="46e48-108">Some module dependencies can be managed externally, in that case they should be added to the ExternalModuleDependencies entry in the PSData section of the module manifest.</span></span>
    <span data-ttu-id="46e48-109">Abaixo da parte na mensagem de erro acima</span><span class="sxs-lookup"><span data-stu-id="46e48-109">Below part in the above error message</span></span>
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

<span data-ttu-id="46e48-110">*Durante a instalação do módulo, a lista de dependências acima é usada para instalar as dependências.*</span><span class="sxs-lookup"><span data-stu-id="46e48-110">*During the module installation, above prepared dependencies list is used for installing the dependencies.*</span></span>

<span data-ttu-id="46e48-111">*Certifique-se de que as dependências do seu módulo estejam disponíveis em $env:PSModulePath no sistema durante a operação de publicação.*</span><span class="sxs-lookup"><span data-stu-id="46e48-111">*Please ensure that your module’s dependencies are available under $env:PSModulePath on your system during publish operation.*</span></span>

