---
title: Declaração de classe do cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 3e410087438ac99526049f99e5c768c017a29848
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854442"
---
# <a name="cmdlet-class-declaration"></a>Declaração de classe do cmdlet

Uma classe do Microsoft .NET Framework é declarada como um cmdlet, especificando o **Cmdlet** atributo como metadados para a classe. (O **Cmdlet** é o único atributo necessário para todos os cmdlets). Quando você especifica o **Cmdlet** atributo, você deve especificar o par do verbo e substantivo que identifica o cmdlet para o usuário. E, então, você deve descrever a funcionalidade do Windows PowerShell que o cmdlet oferece suporte. Para obter mais informações sobre a sintaxe de declaração que é usada para especificar o **Cmdlet** atributo, consulte [declaração de atributo do Cmdlet](./cmdlet-attribute-declaration.md).

> [!NOTE]
> O **Cmdlet** atributo é definido pela [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) classe. As propriedades dessa classe correspondem aos parâmetros de declaração que são usados quando você declara o atributo.

## <a name="nouns"></a>Substantivos

O substantivo do cmdlet especifica os recursos sobre os quais o cmdlet atua. O substantivo diferencia seus cmdlets de outros cmdlets.

Substantivos nos nomes de cmdlet devem ser específico e, no caso de substantivos genéricos, como *server*, é melhor adicionar um prefixo curto que diferencia o recurso de outros recursos semelhantes. Por exemplo, um nome de cmdlet que inclui um substantivo com um prefixo é `Get-SQLServer`. A combinação de um substantivo específico com um verbo mais geral permite que o usuário localizar rapidamente o cmdlet por sua ação e, em seguida, identifique o cmdlet por seus recursos, evitando duplicação de nome de cmdlet desnecessários.

Para obter uma lista de caracteres especiais que não podem ser usados em nomes de cmdlet, consulte [diretrizes de desenvolvimento necessárias](./required-development-guidelines.md).

## <a name="verbs"></a>Verbos

Quando você especifica um verbo, as diretrizes de desenvolvimento exigem que você use um dos verbos predefinidos fornecidos pelo Windows PowerShell. Usando um desses verbos predefinidos, você terá de garantir a consistência entre os cmdlets que você escreve e os cmdlets que são gravados pela Microsoft e por outras pessoas. Por exemplo, o verbo "Get" é usado para os cmdlets que recuperam dados.

Para obter mais informações sobre as diretrizes para verbos, consulte [nomes de verbos de Cmdlet](./approved-verbs-for-windows-powershell-commands.md). Para obter uma lista de caracteres especiais que não podem ser usados em nomes de cmdlet, consulte [diretrizes de desenvolvimento necessárias](./required-development-guidelines.md).

## <a name="supporting-windows-powershell-functionality"></a>Suporte à funcionalidade do Windows PowerShell

O **Cmdlet** atributo também permite que você especifique que seu cmdlet oferece suporte a algumas das funcionalidades comuns que é fornecida pelo Windows PowerShell. Isso inclui suporte para funcionalidades comuns como confirmação de comentários do usuário (conhecida como suporte para o recurso de ShouldProcess) e suporte para transações. (O suporte para transações foi introduzido no Windows PowerShell 2.0).

Para obter mais informações sobre a sintaxe de declaração que é usada para especificar o **Cmdlet** atributo, consulte [declaração de atributo do Cmdlet](./cmdlet-attribute-declaration.md).

## <a name="cmdlet-class-definition"></a>Definição de classe do cmdlet

O código a seguir é a definição de uma classe do cmdlet GetProc. Observe que Pascal de maiusculas e minúsculas é usada e que o nome da classe inclui o verbo e substantivo do cmdlet.

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a>Maiusculas e minúsculas de Pascal

Ao nomear cmdlets, use o casing Pascal casing. Por exemplo, o `Get-Item` e `Get-ItemProperty` cmdlets mostrar a maneira correta de usar maiusculas quando você está nomeando cmdlets.

## <a name="see-also"></a>Consulte Também

[System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute)

[Declaração CmdletAttribute](./cmdlet-attribute-declaration.md)

[Nomes de verbos de cmdlet](./approved-verbs-for-windows-powershell-commands.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
