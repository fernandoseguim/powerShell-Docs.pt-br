---
title: Parâmetros de propriedade | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d17e0d66-42ea-4e4c-a85b-3ca09b146492
caps.latest.revision: 6
ms.openlocfilehash: cc0742b86a7a36e5712707c077fd1952691f3f4b
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251414"
---
# <a name="property-parameters"></a>Parâmetros de propriedade

A tabela a seguir lista os nomes recomendados e a funcionalidade para os parâmetros de propriedade.

|Parâmetro|Funcionalidade|
|---|---|
|**Contagem**<br>Tipo de dados: Int32|Implemente esse parâmetro para que o usuário pode especificar o número de objetos a serem processados.|
|**Descrição**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar uma descrição para um recurso.|
|**De**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar o objeto de referência para obter informações de.|
|**Id**<br>Tipo de dados: Recursos dependentes|Implemente esse parâmetro para que o usuário pode especificar o identificador de um recurso.|
|**entrada**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar a especificação de arquivo de entrada.|
|**Local**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar o local do recurso.|
|**LogName**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar o nome do arquivo de log para processar ou usar.|
|**Nome**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar o nome do recurso.|
|**Saída**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar o arquivo de saída.|
|**Proprietário**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar o nome do proprietário do recurso.|
|**Propriedade**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar o nome ou nomes de propriedades a serem usadas.|
|**Reason**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar, por que esse cmdlet está sendo invocado.|
|**Regex**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que as expressões regulares são usadas quando o parâmetro for especificado. Quando esse parâmetro for especificado, os caracteres curinga não são resolvidos.|
|**Velocidade**<br>Tipo de dados: Int32|Implemente esse parâmetro para que o usuário pode especificar a taxa de transmissão. O usuário define esse parâmetro para a velocidade do recurso.|
|**Estado**<br>Tipo de dados: Matriz de palavra-chave|Implemente esse parâmetro para que o usuário pode especificar os nomes dos estados, como KEYDOWN.|
|**Valor**<br>Tipo de dados: Objeto|Implemente esse parâmetro para que o usuário pode especificar um valor a ser fornecido para o cmdlet.|
|**Versão**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar a versão da propriedade.|

## <a name="see-also"></a>Consulte Também

[Parâmetros do cmdlet](./cmdlet-parameters.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
