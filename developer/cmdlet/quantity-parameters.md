---
title: Parâmetros de quantidade | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c0bd8a9-1749-4885-ab24-38c0a4d9f2cb
caps.latest.revision: 6
ms.openlocfilehash: 7a3efc60fcc8729d833f6de070016cfd08cc9b88
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251363"
---
# <a name="quantity-parameters"></a>Parâmetros de quantidade

A tabela a seguir lista os nomes recomendados e a funcionalidade para os parâmetros de quantidade.

|Parâmetro|Funcionalidade|
|---|---|
|**Todos os**<br>Tipo de dados: Booliano|Implementar esse parâmetro, de modo que `true` indica que todos os recursos devem ser tratados em vez de um subconjunto do padrão de recursos. Implementar esse parâmetro, de modo que `false` indica um subconjunto dos recursos.|
|**alocação**<br>Tipo de dados: Int32|Implemente esse parâmetro para que o usuário pode especificar o número de itens para alocar.|
|**BlockCount**<br>Tipo de dados: Int64|Implemente esse parâmetro para que o usuário pode especificar a contagem de bloco.|
|**Contagem**<br>Tipo de dados: Int64|Implemente esse parâmetro para que o usuário pode especificar a contagem.|
|**Escopo**<br>Tipo de dados: Palavra-chave|Implemente esse parâmetro para que o usuário pode especificar o escopo no qual operar.|

## <a name="see-also"></a>Consulte Também

[Parâmetros do cmdlet](./cmdlet-parameters.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
