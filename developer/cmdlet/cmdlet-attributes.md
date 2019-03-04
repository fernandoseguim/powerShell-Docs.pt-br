---
title: Atributos de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.assetid: d3f4f652-d929-4c27-9358-9baa390a094c
caps.latest.revision: 14
ms.openlocfilehash: b06faf7204213b383b25685837941ad63dcb225b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853912"
---
# <a name="cmdlet-attributes"></a>Atributos de cmdlet

Windows PowerShell define vários atributos que você pode usar para adicionar funcionalidade comum para seus cmdlets sem implementar essa funcionalidade em seu próprio código. Isso inclui o atributo de Cmdlet que identifica uma classe do Microsoft .NET Framework como uma classe do cmdlet, o atributo de tipo de saída que especifica os tipos do .NET Framework retornados pelo cmdlet, o atributo de parâmetro que identifica as propriedades públicas como o cmdlet parâmetros e muito mais.

## <a name="in-this-section"></a>Nesta seção

[Atributos no código do Cmdlet](./attributes-in-cmdlet-code.md) descreve a vantagem de usar atributos no código do cmdlet.

[Tipos de atributo](./attribute-types.md) descreve os atributos diferentes que podem decorar uma classe cmdlet.

[Declaração de atributo de alias](./alias-attribute-declaration.md) descreve como definir aliases para um nome de parâmetro de cmdlet.

[Declaração de atributo do cmdlet](./cmdlet-attribute-declaration.md) descreve como definir uma classe do .NET Framework como um cmdlet.

[Declaração de atributo de credencial](./credential-attribute-declaration.md) descreve como adicionar suporte para converter a entrada de cadeia de caracteres em um [pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto.

[Atributo OutputType declaração](./outputtype-attribute-declaration.md) descreve como especificar tipos do .NET Framework retornados pelo cmdlet.

[Declaração de atributo de parâmetro](./parameter-attribute-declaration.md) descreve como definir os parâmetros de um cmdlet.

[Declaração de atributo ValidateCount](./validatecount-attribute-declaration.md) descreve como definir quantos argumentos são permitidos para um parâmetro.

[Declaração de atributo ValidateLength](./validatelength-attribute-declaration.md) descreve como definir o comprimento (em caracteres) de um argumento do parâmetro.

[Declaração de atributo ValidatePattern](./validatepattern-attribute-declaration.md) descreve como definir os padrões de válido para um argumento de parâmetro.

[Declaração de atributo ValidateRange](./validaterange-attribute-declaration.md) descreve como definir o intervalo válido para um argumento de parâmetro.

[Declaração de atributo ValidateSet](./validateset-attribute-declaration.md) descreve como definir os valores possíveis para um argumento de parâmetro.

## <a name="reference"></a>Referência

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
