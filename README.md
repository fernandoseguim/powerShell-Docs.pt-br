---
ms.openlocfilehash: 6e36e6599e36218ce2a925dceda7aa0ee6811057
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "58142199"
---
# <a name="microsoft-open-source-code-of-conduct"></a><span data-ttu-id="2a3b7-101">Código de Conduta Aberto da Microsoft</span><span class="sxs-lookup"><span data-stu-id="2a3b7-101">Microsoft Open Source Code of Conduct</span></span>

<span data-ttu-id="2a3b7-102">Este projeto adotou o [Código de Conduta Aberto da Microsoft](https://opensource.microsoft.com/codeofconduct/).</span><span class="sxs-lookup"><span data-stu-id="2a3b7-102">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="2a3b7-103">Para saber mais, confira as [Perguntas Frequentes sobre o Código de Conduta](https://opensource.microsoft.com/codeofconduct/faq/) ou contate [opencode@microsoft.com](mailto:opencode@microsoft.com) com perguntas ou comentários adicionais.</span><span class="sxs-lookup"><span data-stu-id="2a3b7-103">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

<span data-ttu-id="2a3b7-104">[![Status do build](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)</span><span class="sxs-lookup"><span data-stu-id="2a3b7-104">[![Build status](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)</span></span>

## <a name="powershell-documentation"></a><span data-ttu-id="2a3b7-105">Documentação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="2a3b7-105">PowerShell Documentation</span></span>

<span data-ttu-id="2a3b7-106">Bem-vindo ao repositório de documentos do PowerShell, que abriga a documentação oficial do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2a3b7-106">Welcome to the PowerShell-Docs repository, housing the official PowerShell documentation.</span></span>

## <a name="repository-structure"></a><span data-ttu-id="2a3b7-107">Estrutura do Repositório</span><span class="sxs-lookup"><span data-stu-id="2a3b7-107">Repository Structure</span></span>

<span data-ttu-id="2a3b7-108">Cada uma das seguintes pastas de nível superior neste repositório contém um DocSet publicado no [Microsoft Docs](https://docs.microsoft.com/powershell).</span><span class="sxs-lookup"><span data-stu-id="2a3b7-108">Each of the following top-level folders in this repo contain a DocSet that is published to [Microsoft Docs](https://docs.microsoft.com/powershell).</span></span>

- <span data-ttu-id="2a3b7-109">[/developer/](https://docs.microsoft.com/powershell/developer/) é o futuro lar da documentação do SDK do PowerShell</span><span class="sxs-lookup"><span data-stu-id="2a3b7-109">[/developer/](https://docs.microsoft.com/powershell/developer/) is the future home of the PowerShell SDK documentation</span></span>
  - <span data-ttu-id="2a3b7-110">Estamos em processo de migração deste conteúdo do MSDN</span><span class="sxs-lookup"><span data-stu-id="2a3b7-110">We are in the process of migrating this content from MSDN</span></span>
- <span data-ttu-id="2a3b7-111">[/dsc/](https://docs.microsoft.com/powershell/dsc/) é para o recurso de Configuração do Estado Desejado</span><span class="sxs-lookup"><span data-stu-id="2a3b7-111">[/dsc/](https://docs.microsoft.com/powershell/dsc/) is for the Desired State Configuration feature</span></span>
- <span data-ttu-id="2a3b7-112">[/gallery/](https://docs.microsoft.com/powershell/gallery) é para a [Galeria do PowerShell](https://www.powershellgallery.com/)</span><span class="sxs-lookup"><span data-stu-id="2a3b7-112">[/gallery/](https://docs.microsoft.com/powershell/gallery) is for the [PowerShell Gallery](https://www.powershellgallery.com/)</span></span>
- <span data-ttu-id="2a3b7-113">[/jea/](https://docs.microsoft.com/powershell/jea/) é para o recurso Administração Just Enough</span><span class="sxs-lookup"><span data-stu-id="2a3b7-113">[/jea/](https://docs.microsoft.com/powershell/jea/) is for the Just Enough Administration feature</span></span>
- <span data-ttu-id="2a3b7-114">[/reference/](https://docs.microsoft.com/powershell/scripting/) é para os tópicos conceituais do PowerShell e a referência de módulo entre as versões 3.0, 4.0, 5.0, 5.1 e 6.0</span><span class="sxs-lookup"><span data-stu-id="2a3b7-114">[/reference/](https://docs.microsoft.com/powershell/scripting/) is for PowerShell conceptual topics and module reference across versions 3.0, 4.0, 5.0, 5.1, and 6.0</span></span>
  - <span data-ttu-id="2a3b7-115">Este conteúdo também é a origem do conteúdo da Ajuda recuperado pelo cmdlet `Get-Help`</span><span class="sxs-lookup"><span data-stu-id="2a3b7-115">This content is also the source of help content retrieved by the `Get-Help` cmdlet</span></span>
- <span data-ttu-id="2a3b7-116">[/wmf](https://docs.microsoft.com/powershell/wmf/readme) contém notas de versão do Windows Management Framework, o pacote usado para distribuir novas versões do PowerShell para versões anteriores do Windows.</span><span class="sxs-lookup"><span data-stu-id="2a3b7-116">[/wmf](https://docs.microsoft.com/powershell/wmf/readme) contains release notes for the Windows Management Framework, the package used to distribute new versions of PowerShell to previous versions of Windows.</span></span>

## <a name="contributing"></a><span data-ttu-id="2a3b7-117">Contribuindo</span><span class="sxs-lookup"><span data-stu-id="2a3b7-117">Contributing</span></span>

<span data-ttu-id="2a3b7-118">Ativamente mesclamos contribuições neste repositório via [solicitação pull](https://help.github.com/articles/using-pull-requests/) para o branch de *preparo*.</span><span class="sxs-lookup"><span data-stu-id="2a3b7-118">We actively merge contributions into this repository via [pull request](https://help.github.com/articles/using-pull-requests/) into the *staging* branch.</span></span>
<span data-ttu-id="2a3b7-119">Observe que antes de enviar uma solicitação pull, você deve [assinar um Contrato de Licença de Contribuição](https://cla.microsoft.com/) para garantir que a comunidade está livre para usar seus envios.</span><span class="sxs-lookup"><span data-stu-id="2a3b7-119">Please note that before you submit a pull request you must [sign a Contribution License Agreement](https://cla.microsoft.com/) to ensure that the community is free to use your submissions.</span></span>

<span data-ttu-id="2a3b7-120">Saiba mais sobre como contribuir no [guia do colaborador](CONTRIBUTING.md).</span><span class="sxs-lookup"><span data-stu-id="2a3b7-120">For more information on contributing, read our [contributor's guide](CONTRIBUTING.md).</span></span>
<span data-ttu-id="2a3b7-121">Ele traz informações detalhadas sobre como contribuir com a documentação, ferramentas sugeridas e requisitos de formatação e estilo.</span><span class="sxs-lookup"><span data-stu-id="2a3b7-121">The contributor's guide contains detail information about how to contribute documentation, suggested tools, and style and formatting requirements.</span></span>
<span data-ttu-id="2a3b7-122">Use os modelos de Solicitação Pull e de Problemas para ajudar a manter a consistência da documentação em diferentes versões.</span><span class="sxs-lookup"><span data-stu-id="2a3b7-122">Please use the Issue and Pull Request templates to help keep documentation consistent across versions.</span></span>

## <a name="licenses"></a><span data-ttu-id="2a3b7-123">Licenças</span><span class="sxs-lookup"><span data-stu-id="2a3b7-123">Licenses</span></span>

<span data-ttu-id="2a3b7-124">Há dois arquivos de licença para este projeto.</span><span class="sxs-lookup"><span data-stu-id="2a3b7-124">There are two license files for this project.</span></span>
<span data-ttu-id="2a3b7-125">A licença do MIT aplica-se ao código contido neste repositório.</span><span class="sxs-lookup"><span data-stu-id="2a3b7-125">The MIT License applies to the code contained in this repo.</span></span>
<span data-ttu-id="2a3b7-126">A licença Creative Commons aplica-se à documentação.</span><span class="sxs-lookup"><span data-stu-id="2a3b7-126">The Creative Commons license applies to the documentation.</span></span>