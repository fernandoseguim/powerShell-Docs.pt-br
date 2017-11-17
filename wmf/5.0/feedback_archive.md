---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
ms.openlocfilehash: 7ad4a00f7beba0de70696d88cd5448c7c638c50c
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/27/2017
---
# <a name="archive-cmdlets"></a><span data-ttu-id="e51e2-102">Cmdlets Archive</span><span class="sxs-lookup"><span data-stu-id="e51e2-102">Archive cmdlets</span></span>

<span data-ttu-id="e51e2-103">Dois novos cmdlets, **Compress-Archive** e **Expand-Archive**, permitem compactar e expandir arquivos ZIP.</span><span class="sxs-lookup"><span data-stu-id="e51e2-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="e51e2-104">Compress-Archive</span><span class="sxs-lookup"><span data-stu-id="e51e2-104">Compress-Archive</span></span>
<span data-ttu-id="e51e2-105">O cmdlet **Compress-Archive** cria um novo arquivo morto dos arquivos especificados.</span><span class="sxs-lookup"><span data-stu-id="e51e2-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="e51e2-106">Um arquivo morto permite que vários arquivos sejam empacotados e, opcionalmente, compactados em um único arquivo para facilitar o tratamento e armazenamento.</span><span class="sxs-lookup"><span data-stu-id="e51e2-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="e51e2-107">Um arquivo morto pode ser compactado usando um algoritmo de compactação especificado no parâmetro **-CompressionLevel**.</span><span class="sxs-lookup"><span data-stu-id="e51e2-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>] 
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="e51e2-108">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="e51e2-108">Expand-Archive</span></span>
<span data-ttu-id="e51e2-109">O cmdlet **Expand-Archive** extrai os arquivos de um arquivo morto especificado.</span><span class="sxs-lookup"><span data-stu-id="e51e2-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="e51e2-110">Um arquivo morto permite que vários arquivos sejam empacotados e, opcionalmente, compactados em um único arquivo para facilitar o tratamento e armazenamento.</span><span class="sxs-lookup"><span data-stu-id="e51e2-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```

