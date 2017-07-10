---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
ms.openlocfilehash: d23cfc2aaa680c247aaab91d8875c64c9d62187e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
<a id="archive-cmdlets" class="xliff"></a>
# Cmdlets Archive

Dois novos cmdlets, **Compress-Archive** e **Expand-Archive**, permitem compactar e expandir arquivos ZIP.

<a id="compress-archive" class="xliff"></a>
## Compress-Archive
O cmdlet **Compress-Archive** cria um novo arquivo morto dos arquivos especificados. Um arquivo morto permite que vários arquivos sejam empacotados e, opcionalmente, compactados em um único arquivo para facilitar o tratamento e armazenamento. Um arquivo morto pode ser compactado usando um algoritmo de compactação especificado no parâmetro **-CompressionLevel**.
```PowerShell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>] 
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

<a id="expand-archive" class="xliff"></a>
## Expand-Archive
O cmdlet **Expand-Archive** extrai os arquivos de um arquivo morto especificado. Um arquivo morto permite que vários arquivos sejam empacotados e, opcionalmente, compactados em um único arquivo para facilitar o tratamento e armazenamento.
```PowerShell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```

