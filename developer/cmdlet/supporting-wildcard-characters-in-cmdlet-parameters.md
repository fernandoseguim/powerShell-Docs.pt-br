---
title: Suporte a caracteres curinga em parâmetros do Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wildcards [PowerShell Programer's Guide]
- parameters [PowerShell Programmer's Guide], wildcards
ms.assetid: 9b26e1e9-9350-4a5a-aad5-ddcece658d93
caps.latest.revision: 12
ms.openlocfilehash: 296490e4692e72f823be0b00aee90dc8c3dc9131
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862512"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a>Suporte a caracteres curinga em parâmetros de cmdlet

Muitas vezes, você precisará de um cmdlet para executar em relação a um grupo de recursos, em vez de em relação a um único recurso de design. Por exemplo, um cmdlet, talvez seja necessário localizar todos os arquivos em um repositório de dados que têm o mesmo nome ou a extensão. Você deve fornecer suporte para caracteres curinga, quando você projeta um cmdlet que será executado em relação a um grupo de recursos.

> [!NOTE]
> Usando caracteres curinga é, às vezes, conhecido como *recurso de curinga*.

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a>Cmdlets do Windows PowerShell que usam curingas

 Muitos cmdlets do Windows PowerShell dão suporte a caracteres curinga para seus valores de parâmetro. Por exemplo, quase todos os cmdlets que tem um `Name` ou `Path` parâmetro dá suporte a caracteres curinga para esses parâmetros. (Embora a maioria dos cmdlets que têm uma `Path` parâmetro também têm um `LiteralPath` parâmetro que não oferece suporte a caracteres curinga.) O comando a seguir mostra como um caractere curinga é usado para retornar todos os cmdlets na sessão atual, cujo nome contém o verbo Get.

 **PS > get-command get -\***

## <a name="supported-wildcard-characters"></a>Caracteres curinga suportados

Windows PowerShell suporta os seguintes caracteres curinga.

|caractere curinga|Descrição|Exemplo|Correspondências|Não corresponde|
|------------------------|-----------------|-------------|-------------|--------------------|
|*|Corresponde a zero ou mais caracteres, começando na posição especificada|a*|Um, ag, Apple||
|?|Anycharacter correspondências na posição especificada|?n|Um, no, no|ran|
|[ ]|Corresponde a um intervalo de caracteres|[a-l]ook|catálogo, cook, aparência|levou|
|[ ]|Corresponde a caracteres especificados|[bc]ook|catálogo, cook|aparência|

Quando você projeta cmdlets que oferecem suporte a caracteres curinga, permitir combinações de caracteres curinga. Por exemplo, o comando a seguir usa o `Get-ChildItem` cmdlet para recuperar todos os arquivos. txt que estão na pasta c:\Techdocs e que começam com as letras "a" "l" por meio.

**get-childitem c:\techdocs\\[a-l]\*.txt**

O comando anterior usa o curinga de intervalo **[a-l]** para especificar o nome do arquivo deve começar com os caracteres "a" "l" por meio. O comando, em seguida, usa o * caractere curinga como um espaço reservado para todos os caracteres entre a primeira letra do nome do arquivo e a extensão. txt.

O exemplo a seguir usa um padrão de curinga de intervalo que exclui a letra "d", mas inclui todas as outras letras de "a" a "f."

**get-childitem c:\techdocs\\[a-cef]\*.txt**

## <a name="handling-literal-characters-in-wildcard-patterns"></a>Tratamento de caracteres literais em padrões de curinga

Se o padrão de curinga especificado contém caracteres literais, use o caractere de acento grave (') como um caractere de escape. Quando você especificar caracteres literais programaticamente, use um acento grave único. Quando você especifica os caracteres literais no prompt de comando, use dois backticks. Por exemplo, o padrão a seguir contém dois colchetes que devem ser interpretadas literalmente.

"John Smith \`[*']" (especificado por meio de programação)

"John Smith \` \`[*\`']" (especificado no prompt de comando)

Este padrão corresponde a "John Smith [Marketing]" ou "John Smith [desenvolvimento do]".

## <a name="cmdlet-output-and-wildcard-characters"></a>Saída do cmdlet e caracteres curinga

Quando os parâmetros de cmdlet dá suporte a caracteres curinga, uma operação do cmdlet normalmente gera uma saída de matriz. Ocasionalmente, ele não faz sentido para dar suporte a uma matriz de saída porque o usuário pode usar apenas um único item por vez. Por exemplo, o `Set-Location` cmdlet oferece suporte a uma matriz de saída porque o usuário define apenas um único local. Nesse caso, o cmdlet ainda ofereça suporte a caracteres curinga, mas ele força a resolução para um único local.

## <a name="see-also"></a>Consulte Também

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)

[Classe WildcardPattern](/dotnet/api/system.management.automation.wildcardpattern)
