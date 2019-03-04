---
title: Parâmetros de filtro de entrada | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854462"
---
# <a name="input-filter-parameters"></a>Parâmetros de filtro de entrada

Um cmdlet pode definir `Filter`, `Include`, e `Exclude` parâmetros que filtram o conjunto de objetos de entrada que afeta o cmdlet.

Normalmente, o conjunto de objetos de entrada é especificado por um `InputObject`, `Path`, ou `Name` parâmetro. Por exemplo, um cmdlet pode ter um `Path` parâmetro que aceita vários caminhos usando caracteres curinga e cada caminho aponta para um objeto de entrada. Usados juntos, o `Filter`, `Include`, e `Exclude` ainda mais parâmetros qualificam os caminhos que o cmdlet funciona em cada vez que ele é invocado.

## <a name="include-and-exclude-parameters"></a>Incluir e excluir parâmetros

O `Include` e `Exclude` parâmetros identificam os objetos que são incluídos ou excluídos do conjunto de objetos de entrada passados para o cmdlet. Use esses parâmetros quando o filtro pode ser expresso na linguagem de padrão curinga. (Para obter mais informações sobre os caracteres curinga, consulte [que dão suporte a curingas nos parâmetros de Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).) O `Include` parâmetro inclui todos os objetos cujos nomes correspondem ao filtro de inclusão. O `Exclude` parâmetro exclui todos os objetos cujos nomes correspondem ao filtro.

## <a name="filter-parameter"></a>Parâmetro de filtro

O `Filter` parâmetro especifica um filtro que não é expressado na linguagem padrão de curinga. Por exemplo, filtros de Active Directory Service Interfaces (ADSI) ou SQL podem ser passados para o cmdlet por meio de seu `Filter` parâmetro. Os cmdlets fornecidos pelo Windows PowerShell, esses filtros são especificados pelos provedores do Windows PowerShell que usa o cmdlet para acessar um armazenamento de dados. Normalmente, cada provedor define seu próprio filtro.

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>Se nenhum conjunto de objetos de entrada for especificado de filtragem

Se nenhum conjunto de objetos de entrada for especificado, isso normalmente significa filtrar em relação a todos os objetos. Para obter mais informações, consulte[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).

## <a name="see-also"></a>Consulte Também

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)