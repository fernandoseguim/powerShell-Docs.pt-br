---
title: Módulos e Snap-ins | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860492"
---
# <a name="modules-and-snap-ins"></a>Módulos e snap-ins

Cmdlets podem ser adicionados a uma sessão usando o snap-ins ou módulos (introduzidos pelo Windows PowerShell 2.0). Depois que o cmdlet é adicionado à sessão, que ele pode ser executado programaticamente por um aplicativo host ou interativamente na linha de comando.

É recomendável que você use módulos como o método de entrega para adicionar os cmdlets para uma sessão pelos seguintes motivos:

- Módulos permitem que você adicionar cmdlets carregando o assembly em que o cmdlet é definido. Não é necessário implementar uma classe de snap-in.

- Os módulos permitem que você adicione outros recursos, como variáveis, funções, scripts, tipos e formatação arquivos e muito mais.

- Snap-ins podem ser usados apenas para adicionar os cmdlets e provedores para a sessão.

## <a name="see-also"></a>Consulte Também

[Escrevendo um módulo do Windows PowerShell](../module/writing-a-windows-powershell-module.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
