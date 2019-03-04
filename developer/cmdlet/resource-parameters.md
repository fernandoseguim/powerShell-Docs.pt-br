---
title: Parâmetros de recursos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 460c43aa-f5c5-4a1a-a6f2-5e07db143de1
caps.latest.revision: 5
ms.openlocfilehash: 9752570e5c997ef4da56a08df14f39b77ba37a4a
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251193"
---
# <a name="resource-parameters"></a>Parâmetros do recurso

A tabela a seguir lista os nomes recomendados e a funcionalidade para parâmetros de recursos. Para esses parâmetros, os recursos podem ser o assembly que contém a classe do cmdlet ou o aplicativo host que esteja executando o cmdlet.

|Parâmetro|Funcionalidade|
|---|---|
|**Aplicativo**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar um aplicativo.|
|**Assembly**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar um assembly.|
|**Atributo**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar um atributo.|
|**Classe**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar uma classe do Microsoft .NET Framework.|
|**Cluster**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar um cluster.|
|**Cultura**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar a cultura na qual executar o cmdlet.|
|**Domínio**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar o nome de domínio.|
|**Drive**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar um nome de unidade.|
|**Event**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar um nome de evento.|
|**Interface**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar um nome de interface de rede.|
|**IpAddress**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar um endereço IP.|
|**Trabalho**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar um trabalho.|
|**LiteralPath**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar o caminho para um recurso quando não há suporte para caracteres curinga. (Use o **caminho** parâmetro quando há suporte para caracteres curinga.)|
|**Mac**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar um endereço de acesso à mídia (MAC) do controlador.|
|**ParentId**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar o identificador pai.|
|**Path**<br>Tipo de dados: String, String[]|Implemente esse parâmetro para que o usuário pode indicar os caminhos para um recurso quando há suporte para caracteres curinga. (Use o **LiteralPath** parâmetro quando não há suporte para caracteres curinga.) É recomendável que você desenvolver esse parâmetro para que ele oferece suporte completo `provider:path` sintaxe usada pelos provedores. Também recomendamos desenvolvê-lo para que ele funcione com provedores de tantos quanto possível.|
|**Porta**<br>Tipo de dados: Inteiro, cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar um valor inteiro para a rede ou um valor de cadeia de caracteres como "biztalk" para outros tipos de porta.|
|**Impressora**<br>Tipo de dados: Inteiro, cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar a impressora para usar o cmdlet.|
|**Size**<br>Tipo de dados: Int32|Implemente esse parâmetro para que o usuário pode especificar um tamanho.|
|**TID**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar um identificador de transação (TID) para o cmdlet.|
|**Tipo**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar o tipo de recurso no qual operar.|
|**URL**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar um localizador URL (Uniform Resource).|
|**User**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar seu nome ou o nome de outro usuário.|

## <a name="see-also"></a>Consulte Também

[Parâmetros do cmdlet](./cmdlet-parameters.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
