---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: 9ca12ad3f0729a2e9595d7ca5ccf9041e47658a3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="archive-cmdlets"></a><span data-ttu-id="3ee62-102">Cmdlets Archive</span><span class="sxs-lookup"><span data-stu-id="3ee62-102">Archive cmdlets</span></span>

<span data-ttu-id="3ee62-103">Dois novos cmdlets, **Compress-Archive** e **Expand-Archive**, permitem compactar e expandir arquivos ZIP.</span><span class="sxs-lookup"><span data-stu-id="3ee62-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="3ee62-104">Compress-Archive</span><span class="sxs-lookup"><span data-stu-id="3ee62-104">Compress-Archive</span></span>
<span data-ttu-id="3ee62-105">O cmdlet **Compress-Archive** cria um novo arquivo morto dos arquivos especificados.</span><span class="sxs-lookup"><span data-stu-id="3ee62-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="3ee62-106">Um arquivo morto permite que vários arquivos sejam empacotados e, opcionalmente, compactados em um único arquivo para facilitar o tratamento e armazenamento.</span><span class="sxs-lookup"><span data-stu-id="3ee62-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="3ee62-107">Um arquivo morto pode ser compactado usando um algoritmo de compactação especificado no parâmetro **-CompressionLevel**.</span><span class="sxs-lookup"><span data-stu-id="3ee62-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="3ee62-108">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="3ee62-108">Expand-Archive</span></span>
<span data-ttu-id="3ee62-109">O cmdlet **Expand-Archive** extrai os arquivos de um arquivo morto especificado.</span><span class="sxs-lookup"><span data-stu-id="3ee62-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="3ee62-110">Um arquivo morto permite que vários arquivos sejam empacotados e, opcionalmente, compactados em um único arquivo para facilitar o tratamento e armazenamento.</span><span class="sxs-lookup"><span data-stu-id="3ee62-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```
