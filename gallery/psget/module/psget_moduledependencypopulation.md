---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: psget_moduledependencypopulation
ms.openlocfilehash: c4c9f203e9c526ff532c2388acb6334515d66934
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="logic-for-preparing-the-module-dependencies-during-publish-operation"></a>Lógica para preparar as dependências do módulo durante a operação de publicação
1.  Módulos listados como parte de RequiredModules são considerados dependências.
2.  Módulos listados como parte de NestedModules, cuja base do módulo não está sob a base do módulo especificado, são considerados dependências.

3.  As dependências acima devem estar disponíveis no mesmo repositório de destino, caso contrário, a operação de publicação resultará em um erro.
    Por exemplo: se "SnippetPx" não estiver disponível no repositório, o erro abaixo será gerado.
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  Algumas dependências de módulo podem ser gerenciadas externamente. Nesse caso, elas devem ser adicionadas à entrada ExternalModuleDependencies na seção PSData do manifesto do módulo.
    Abaixo da parte na mensagem de erro acima
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

*Durante a instalação do módulo, a lista de dependências acima é usada para instalar as dependências.*

*Certifique-se de que as dependências do seu módulo estejam disponíveis em $env:PSModulePath no sistema durante a operação de publicação.*