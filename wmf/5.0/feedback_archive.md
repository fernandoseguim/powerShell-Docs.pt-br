---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
ms.openlocfilehash: 0c450d765531c18c0b73c5c64262e9895f92068a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="archive-cmdlets"></a><span data-ttu-id="e98b2-102">Cmdlets Archive</span><span class="sxs-lookup"><span data-stu-id="e98b2-102">Archive cmdlets</span></span>

<span data-ttu-id="e98b2-103">Dois novos cmdlets, **Compress-Archive** e **Expand-Archive**, permitem compactar e expandir arquivos ZIP.</span><span class="sxs-lookup"><span data-stu-id="e98b2-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="e98b2-104">Compress-Archive</span><span class="sxs-lookup"><span data-stu-id="e98b2-104">Compress-Archive</span></span>
<span data-ttu-id="e98b2-105">O cmdlet **Compress-Archive** cria um novo arquivo morto dos arquivos especificados.</span><span class="sxs-lookup"><span data-stu-id="e98b2-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="e98b2-106">Um arquivo morto permite que vários arquivos sejam empacotados e, opcionalmente, compactados em um único arquivo para facilitar o tratamento e armazenamento.</span><span class="sxs-lookup"><span data-stu-id="e98b2-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="e98b2-107">Um arquivo morto pode ser compactado usando um algoritmo de compactação especificado no parâmetro **-CompressionLevel**.</span><span class="sxs-lookup"><span data-stu-id="e98b2-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="e98b2-108">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="e98b2-108">Expand-Archive</span></span>
<span data-ttu-id="e98b2-109">O cmdlet **Expand-Archive** extrai os arquivos de um arquivo morto especificado.</span><span class="sxs-lookup"><span data-stu-id="e98b2-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="e98b2-110">Um arquivo morto permite que vários arquivos sejam empacotados e, opcionalmente, compactados em um único arquivo para facilitar o tratamento e armazenamento.</span><span class="sxs-lookup"><span data-stu-id="e98b2-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```