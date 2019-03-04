---
title: Aliases de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860502"
---
# <a name="cmdlet-aliases"></a>Aliases de cmdlet

Você pode usar aliases de cmdlet para melhorar a experiência de usuário do cmdlet. Você pode adicionar aliases para cmdlets usados com frequência para reduzir a digitação e tornar mais fácil para concluir tarefas rapidamente. Você pode incluir aliases internos em seus cmdlets ou os usuários podem definir seus próprios aliases personalizados.

Por exemplo, o [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet tem um interno `gcm` alias. Você também pode usar aliases para adicionar nomes de comando em outras linguagens, para que os usuários não precisam aprender novos comandos.

## <a name="alias-guidelines"></a>Diretrizes de alias

Siga estas diretrizes ao criar aliases internos para seus cmdlets:

- Antes de atribuir aliases, inicie o Windows PowerShell e, em seguida, execute as [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet para ver os aliases que já são usados.

- Inclua um prefixo de alias que referencia o verbo do nome do cmdlet e um sufixo de alias que referencia o substantivo do nome do cmdlet. Por exemplo, o alias para o `Import-Module` cmdlet é "ipmo". Para obter uma lista de todos os verbos e seus aliases, consulte [verbos de Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

- Para cmdlets que têm o mesmo verbo, inclua o mesmo prefixo de alias. Por exemplo, os aliases para todos os cmdlets do Windows PowerShell que têm o verbo "Get" em seus nomes usam o prefixo "g".

- Para cmdlets que têm o mesmo substantivo, inclua o mesmo sufixo de alias. Por exemplo, os aliases para todos os cmdlets do Windows PowerShell que têm o substantivo "Sessão" em seu nome de usam o sufixo "sn".

- Para cmdlets que são equivalentes aos comandos em outros idiomas, use o nome do comando.

- Em geral, fazer aliases tão curtas quanto possível. Verifique se que o alias tem pelo menos um caractere distinto para o verbo e um caractere distinto para o substantivo. Adicione mais caracteres conforme necessário para tornar o alias exclusivo.

## <a name="see-also"></a>Consulte Também

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
