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
# <a name="archive-cmdlets"></a>Cmdlets Archive

Dois novos cmdlets, **Compress-Archive** e **Expand-Archive**, permitem compactar e expandir arquivos ZIP.

## <a name="compress-archive"></a>Compress-Archive
O cmdlet **Compress-Archive** cria um novo arquivo morto dos arquivos especificados. Um arquivo morto permite que vários arquivos sejam empacotados e, opcionalmente, compactados em um único arquivo para facilitar o tratamento e armazenamento. Um arquivo morto pode ser compactado usando um algoritmo de compactação especificado no parâmetro **-CompressionLevel**.
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a>Expand-Archive
O cmdlet **Expand-Archive** extrai os arquivos de um arquivo morto especificado. Um arquivo morto permite que vários arquivos sejam empacotados e, opcionalmente, compactados em um único arquivo para facilitar o tratamento e armazenamento.
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```