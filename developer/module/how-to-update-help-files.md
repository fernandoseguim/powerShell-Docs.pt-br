---
title: Como atualizar os arquivos de ajuda | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855522"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="a7ead-102">Como atualizar os arquivos de ajuda</span><span class="sxs-lookup"><span data-stu-id="a7ead-102">How to Update Help Files</span></span>

<span data-ttu-id="a7ead-103">Este tópico explica como atualizar os arquivos de ajuda para um módulo que dá suporte à Ajuda atualizável.</span><span class="sxs-lookup"><span data-stu-id="a7ead-103">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="a7ead-104">Atualizando arquivos de ajuda</span><span class="sxs-lookup"><span data-stu-id="a7ead-104">Updating Help Files</span></span>

<span data-ttu-id="a7ead-105">Há muitas razões para atualizar os arquivos de Ajuda, como corrigir erros, esclarecendo um conceito, responder a uma pergunta frequentes, adicionando novos arquivos ou adicionando novos e melhores exemplos.</span><span class="sxs-lookup"><span data-stu-id="a7ead-105">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="a7ead-106">Para atualizar um arquivo de Ajuda:</span><span class="sxs-lookup"><span data-stu-id="a7ead-106">To update a help file:</span></span>

1. <span data-ttu-id="a7ead-107">Altere os arquivos.</span><span class="sxs-lookup"><span data-stu-id="a7ead-107">Change the files.</span></span>

2. <span data-ttu-id="a7ead-108">Converta os arquivos em outras culturas de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="a7ead-108">Translate the files into other UI cultures.</span></span>

3. <span data-ttu-id="a7ead-109">Colete todos os arquivos de Ajuda (novos, alterados e inalterados) para o módulo de cada cultura de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="a7ead-109">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>

4. <span data-ttu-id="a7ead-110">Valide os arquivos em relação ao esquema XML.</span><span class="sxs-lookup"><span data-stu-id="a7ead-110">Validate the files against the XML schema.</span></span>

5. <span data-ttu-id="a7ead-111">Recompile os arquivos CAB para cada cultura de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="a7ead-111">Rebuild the CAB files for each UI culture.</span></span>

6. <span data-ttu-id="a7ead-112">No arquivo XML HelpInfo, incremente os números de versão do arquivo CAB para cada cultura de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="a7ead-112">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>

7. <span data-ttu-id="a7ead-113">Carregar os novos arquivos CAB para o local que é especificado pelo valor de **HelpContentUri** elemento no arquivo XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="a7ead-113">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="a7ead-114">Substitua os arquivos mais antigos do CAB com os novos arquivos CAB.</span><span class="sxs-lookup"><span data-stu-id="a7ead-114">Replace the older CAB files with the new CAB files.</span></span>

8. <span data-ttu-id="a7ead-115">Carregar o arquivo XML HelpInfo atualizado para o local especificado pelo **HelpInfoUri** chave no manifesto de módulo.</span><span class="sxs-lookup"><span data-stu-id="a7ead-115">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="a7ead-116">Substitua o arquivo XML HelpInfo mais antigo com o novo arquivo.</span><span class="sxs-lookup"><span data-stu-id="a7ead-116">Replace the older HelpInfo XML file with the new file.</span></span>