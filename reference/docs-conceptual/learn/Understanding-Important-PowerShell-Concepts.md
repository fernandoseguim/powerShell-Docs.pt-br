---
ms.date: 08/23/2018
keywords: powershell, cmdlet
title: Compreender conceitos importantes do PowerShell
ms.assetid: 3e601e38-4520-4578-a48d-b6779f1d35ee
ms.openlocfilehash: fad64563d1a7a6abd4f0e430331f81f91f43d312
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400110"
---
# <a name="understanding-important-powershell-concepts"></a>Compreender conceitos importantes do PowerShell

O design do PowerShell integra conceitos de muitos ambientes diferentes. As pessoas com experiência em shells ou ambientes de programação conhecerão vários conceitos. No entanto, poucas conhecerão todos eles. Examinar alguns desses conceitos fornece uma visão geral útil do shell.

## <a name="output-is-object-based"></a>A saída é baseada em objeto

Ao contrário de interfaces de linha de comando tradicionais, os cmdlets do PowerShell são projetados para lidar com objetos.
Um objeto representa informações estruturadas que vão além da uma cadeia de caracteres exibida na tela. A saída do comando sempre acompanha informações extras que poderão ser usadas quando necessário.

Se você já usou ferramentas de processamento de texto para processar dados, perceberá que elas se comportam de maneira diferente quando usadas no PowerShell. Na maioria dos casos, você não precisa de ferramentas de processamento de texto para extrair informações específicas. Você acessa diretamente partes dos dados usando a sintaxe de objeto padrão do PowerShell.

## <a name="the-command-family-is-extensible"></a>A família de comandos é extensível

Interfaces como **cmd.exe** não fornecem uma maneira de expandir diretamente o conjunto de comandos interno. Você pode criar ferramentas de linha de comando externas para execução no **cmd.exe**. Mas essas ferramentas externas não têm serviços, como a integração com a Ajuda. O **cmd.exe** não sabe automaticamente que essas ferramentas externas são comandos válidos.

Os comandos nativos do PowerShell são conhecidos como *cmdlets* (pronuncia-se comand-lets). Você pode criar seus próprios módulos e funções de cmdlets usando código compilado ou scripts. Os módulos podem adicionar cmdlets e provedores ao shell. O PowerShell também dá suporte a scripts análogos aos scripts de shell do Unix e a arquivos de lote do **cmd.exe**.

## <a name="powershell-handles-console-input-and-display"></a>O PowerShell manipula a exibição e a entrada do console

Quando você digita um comando, o PowerShell sempre processa a linha de comando de entrada diretamente. O PowerShell também formata a saída exibida na tela. Essa diferença é considerável porque reduz o trabalho necessário em cada cmdlet. Isso garante que você possa fazer as coisas sempre da mesma maneira com qualquer cmdlet. Os desenvolvedores de cmdlet não precisam escrever códigos para analisar os argumentos de linha de comando ou formatar a saída.

Ferramentas de linha de comando tradicionais têm seus próprios esquemas para solicitar e exibir a Ajuda. Algumas ferramentas de linha de comando usam **/?** para disparar a exibição da Ajuda; outras usam **-?**, **/H** ou até mesmo **//**. Algumas delas exibem a Ajuda em uma janela GUI em vez de na exibição do console. Se você usar o parâmetro errado, a ferramenta poderá ignorar o que você digitou e começar a executar uma tarefa automaticamente.
Como o PowerShell analisa e processa automaticamente a linha de comando, o parâmetro **-?** sempre significa "mostre-me a Ajuda para este comando".

> [!NOTE]
> Se você executar um aplicativo gráfico no PowerShell, a janela do aplicativo se abrirá.
> O PowerShell intervém apenas no processamento da entrada da linha de comando que você fornece ou quando a saída do aplicativo retorna para a janela do console. Ele não afeta a maneira como o aplicativo funciona internamente.

## <a name="powershell-uses-some-c-syntax"></a>O PowerShell usa parte da sintaxe C#

PowerShell baseia-se no .NET Framework. Ele compartilha alguns recursos de sintaxe e palavras-chave com a linguagem de programação C#. Aprender PowerShell facilita bastante o aprendizado de C#. Se você já estiver familiarizado com C#, as semelhanças poderão facilitar bastante o aprendizado do PowerShell.
