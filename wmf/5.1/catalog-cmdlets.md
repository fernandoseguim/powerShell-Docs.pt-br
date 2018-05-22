---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,instalação
title: Cmdlets de Catálogo
ms.openlocfilehash: 7eaca09667af0eb5d719f23e987bb112e8514978
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="catalog-cmdlets"></a><span data-ttu-id="203de-103">Cmdlets de Catálogo</span><span class="sxs-lookup"><span data-stu-id="203de-103">Catalog Cmdlets</span></span>

<span data-ttu-id="203de-104">Adicionamos dois novos cmdlets no módulo [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) para gerar e validar os arquivos de catálogo do Windows.</span><span class="sxs-lookup"><span data-stu-id="203de-104">We have added two new cmdlets in [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) module to generate and validate windows catalog files.</span></span>

## <a name="new-filecatalog"></a><span data-ttu-id="203de-105">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="203de-105">New-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="203de-106">`New-FileCatalog` cria um arquivo de catálogo do Windows para o conjunto de arquivos e pastas.</span><span class="sxs-lookup"><span data-stu-id="203de-106">`New-FileCatalog` creates a windows catalog file for set of folders and files.</span></span> <span data-ttu-id="203de-107">Um arquivo de catálogo contém hashes para todos os arquivos nos caminhos especificados.</span><span class="sxs-lookup"><span data-stu-id="203de-107">A catalog file contains hashes for all files in specified paths.</span></span> <span data-ttu-id="203de-108">Os usuários podem distribuir o conjunto de pastas juntamente com a correspondência do arquivo de catálogo que representa essas pastas.</span><span class="sxs-lookup"><span data-stu-id="203de-108">Users can distribute the set of folders along with corresponding the catalog file that represents those folders.</span></span> <span data-ttu-id="203de-109">Um arquivo de catálogo pode ser usado pelo destinatário de conteúdo para validar se foram feitas alterações nas pastas depois que o catálogo foi criado.</span><span class="sxs-lookup"><span data-stu-id="203de-109">A catalog file can be used by the recipient of content to validate whether any changes were made to the folders after the catalog was created.</span></span>

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<span data-ttu-id="203de-110">Há suporte para a criação do catálogo nas versões 1 e 2.</span><span class="sxs-lookup"><span data-stu-id="203de-110">We support creating catalog version 1 and 2.</span></span> <span data-ttu-id="203de-111">A versão 1 usa o algoritmo de hash SHA1 para criar hashes de arquivo e a versão 2 usa SHA256.</span><span class="sxs-lookup"><span data-stu-id="203de-111">Version 1 uses SHA1 hashing algorithm to create file hashes and version 2 uses SHA256.</span></span> <span data-ttu-id="203de-112">Não há suporte para a versão 2 do catálogo no *Windows Server 2008 R2* e no *Windows 7*.</span><span class="sxs-lookup"><span data-stu-id="203de-112">Catalog version 2 is not supported on *Windows Server 2008 R2* and *Windows 7*.</span></span> <span data-ttu-id="203de-113">É recomendável usar a versão 2 do catálogo, caso esteja usando as plataformas *Windows 8*, *Windows Server 2012* e superiores.</span><span class="sxs-lookup"><span data-stu-id="203de-113">It is recommended to use catalog version 2 if using platforms *Windows 8*, *Windows Server 2012* and above.</span></span>

<span data-ttu-id="203de-114">Para usar este comando em um módulo existente, especifique as variáveis CatalogFilePath e Path para corresponder ao local do manifesto do módulo.</span><span class="sxs-lookup"><span data-stu-id="203de-114">To use this command on an existing module, specify the CatalogFilePath and Path variables to match the location of the module manifest.</span></span> <span data-ttu-id="203de-115">O exemplo a seguir, o manifesto de módulo está em C:\Program Files\Windows PowerShell\Modules\Pester.</span><span class="sxs-lookup"><span data-stu-id="203de-115">In the example below, the module manifest is in C:\Program Files\Windows PowerShell\Modules\Pester.</span></span>

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="203de-116">Isso cria o arquivo de catálogo.</span><span class="sxs-lookup"><span data-stu-id="203de-116">This creates the catalog file.</span></span>

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

<span data-ttu-id="203de-117">Para verificar a integridade de um arquivo de catálogo (Pester.cat no exemplo acima), ele deve ser assinado usando o cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx).</span><span class="sxs-lookup"><span data-stu-id="203de-117">To verify the integrity of a catalog file (Pester.cat in above exmaple) it should be signed using the [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span></span>


## <a name="test-filecatalog"></a><span data-ttu-id="203de-118">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="203de-118">Test-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="203de-119">`Test-FileCatalog` valida o catálogo que representa um conjunto de pastas.</span><span class="sxs-lookup"><span data-stu-id="203de-119">`Test-FileCatalog` validates the catalog representing a set of folders.</span></span>

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="203de-120">Esse cmdlet compara os hashes de todos os arquivos e seus caminhos relativos encontrados no arquivo de catálogo, com os hashes e caminhos dos arquivos salvos em disco.</span><span class="sxs-lookup"><span data-stu-id="203de-120">This cmdlet compares the hashes of all files and their relative paths found in the catalog file with ones saved to disk.</span></span> <span data-ttu-id="203de-121">Se detectar qualquer incompatibilidade entre os hashes e caminhos de arquivo, será retornado o status de `ValidationFailed`.</span><span class="sxs-lookup"><span data-stu-id="203de-121">If it detects any mismatch between file hashes and paths it returns a status of `ValidationFailed`.</span></span>
<span data-ttu-id="203de-122">Os usuários podem recuperar todas essas informações usando o comutador `Detailed`.</span><span class="sxs-lookup"><span data-stu-id="203de-122">Users can retrieve all this information using the `Detailed` switch.</span></span> <span data-ttu-id="203de-123">O status da assinatura do catálogo é exibido como o campo `Signature`, que é o mesmo que chamar o cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) no arquivo de catálogo.</span><span class="sxs-lookup"><span data-stu-id="203de-123">The signing status of the catalog is displayed as the `Signature` field, which is same as calling the [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) cmdlet on the catalog file.</span></span>
<span data-ttu-id="203de-124">Os usuários também podem ignorar qualquer arquivo durante a validação usando o parâmetro `FilesToSkip`.</span><span class="sxs-lookup"><span data-stu-id="203de-124">Users can also skip any file during validation by using the `FilesToSkip` parameter.</span></span>
