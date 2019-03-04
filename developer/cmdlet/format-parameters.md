---
title: Formatar parâmetros | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251176"
---
# <a name="format-parameters"></a>Parâmetros de formato

A tabela a seguir lista nomes recomendados e funcionalidade para os parâmetros que são usadas para formatar ou para gerar dados.

|Parâmetro|Funcionalidade|
|---|---|
|**como**<br>Tipo de dados: Palavra-chave|Implemente esse parâmetro para especificar o formato de saída do cmdlet. Por exemplo, os valores possíveis poderiam ser texto ou Script.|
|**binário**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para indicar que o cmdlet lida com valores binários.|
|**Encoding**<br>Tipo de dados: Palavra-chave|Implemente esse parâmetro para especificar o tipo de codificação com suporte. Por exemplo, os valores possíveis poderiam ser ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, bytes e cadeia de caracteres.|
|**NewLine**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que os caracteres de nova linha são suportados quando o parâmetro for especificado.|
|**ShortName**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que nomes curtos têm suporte quando o parâmetro for especificado.|
|**Width**<br>Tipo de dados: Int32|Implemente esse parâmetro para que o usuário pode especificar a largura do dispositivo de saída.|
|**Quebra automática de linha**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que a quebra automática de texto tem suporte quando o parâmetro for especificado.|
## <a name="see-also"></a>Consulte Também

[Parâmetros do cmdlet](./cmdlet-parameters.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
