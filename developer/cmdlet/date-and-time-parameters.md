---
title: Parâmetros de data e hora | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71da921b-7c32-4155-b2f8-b19f30ec774d
caps.latest.revision: 7
ms.openlocfilehash: 5b1f093de5db364ac806e58c4ed8dbf2948cb6c6
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251346"
---
# <a name="date-and-time-parameters"></a>Parâmetros de data e hora

A tabela a seguir lista os nomes recomendados e funcionalidade para os parâmetros que lidam com informações de data e hora. Parâmetros de data e hora normalmente são usados para registrar quando algo for criado ou acessado.

|Parâmetro|Funcionalidade|
|---|---|
|**Accessed**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que quando ele é especificado o cmdlet opera sobre os recursos que foram acessados com base na data e hora especificada pelo **antes de** e **após** parâmetros. Se esse parâmetro for especificado, o **Created** e **modificado** parâmetros devem não ser especificado.|
|**Depois de**<br>Tipo de dados: DateTime|Implemente esse parâmetro para especificar a data e hora após o qual o cmdlet foi usado. Para o **após** parâmetro funcione, o cmdlet também deve ter uma **acessado**, **criado**, ou **modificado** parâmetro. E, esse parâmetro deve ser definido como **verdadeira** quando o cmdlet é chamado.|
|**Antes de**<br>Tipo de dados: DateTime|Implemente esse parâmetro para especificar a data e hora antes que o cmdlet foi usado. Para o **antes de** parâmetro funcione, o cmdlet também deve ter uma **acessado**, **criado**, ou **modificado** parâmetro. E, esse parâmetro deve ser definido como **verdadeira** quando o cmdlet é chamado.|
|**Criado**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que quando ele é especificado o cmdlet opera nos recursos que foram criados com base na data e hora especificada pelo **antes de** e **após** parâmetros. Se esse parâmetro for especificado, o **acessadas** e **modificado** parâmetros não devem ser especificados.|
|**Exact**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que quando ele é especificado o termo de recursos deve corresponder ao nome do recurso exatamente. Quando o parâmetro não for especificado o termo de recurso e o nome não precisa de uma correspondência exata.|
|**Modificado**<br>Tipo de dados: DateTime|Implemente esse parâmetro para que quando ele é especificado o cmdlet opera em recursos que foram alterados com base na data e hora especificada pelo **antes de** e **após** parâmetros. Se esse parâmetro for especificado, o **acessadas** e **criado** parâmetros não devem ser especificados.|
## <a name="see-also"></a>Consulte Também

[Parâmetros do cmdlet](./cmdlet-parameters.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
