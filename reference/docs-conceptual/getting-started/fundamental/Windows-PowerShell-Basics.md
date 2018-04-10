---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Noções básicas do Windows PowerShell
ms.assetid: 6b3cbbc8-060c-4877-b00b-7300dbbe4e28
ms.openlocfilehash: b21c6cd84ea29d5e8085ccf8df2a5a9199e1d859
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="windows-powershell-basics"></a>Noções básicas do Windows PowerShell
Interfaces do usuário gráficas usam alguns conceitos básicos que são conhecidos para a maioria dos usuários do computador. Os usuários contam com a familiaridade dessas interfaces para realizar tarefas. Os sistemas operacionais apresentam aos usuários uma representação gráfica dos itens que podem ser explorados, geralmente com menus suspensos para acesso a funcionalidades específicas e menus de contexto para acesso a funcionalidades específicas de contexto.

Uma CLI (Interface de Linha de Comando), como o Windows PowerShell, deve usar uma abordagem diferente para expor informações, pois não apresenta menus ou sistemas gráficos para ajudar o usuário. Você precisa saber os nomes de comando para poder usá-los. Embora seja possível digitar comandos complexos que são equivalentes aos recursos em um ambiente de GUI, você deve se familiarizar com os comandos mais frequentemente usados e os parâmetros de comando.

A maioria das CLIs não tem padrões que podem ajudar o usuário a aprender a interface. Como as CLIs foram os primeiros shells de sistema operacional, muitos nomes de comandos e parâmetros foram selecionados arbitrariamente. Nomes de comando concisos geralmente eram escolhidos em vez de nomes claros. Embora os sistemas de ajuda e padrões de design de comando estejam integrados à maioria das CLIs, eles em geral foram projetados para compatibilidade com os comandos mais antigos, portanto o conjunto de comandos ainda é modelado por decisões tomadas décadas atrás.

O Windows PowerShell foi projetado para aproveitar o conhecimento histórico de um usuário de CLIs. Neste capítulo, abordaremos algumas ferramentas e conceitos básicos que você pode usar para aprender a usar o Windows PowerShell rapidamente. Elas incluem:

- Como usar [Get-Command](/powershell/module/Microsoft.PowerShell.Core/get-command)

- Como usar os comandos [Cmd.exe](/windows-server/administration/windows-commands/cmd) e [UNIX](/windows/wsl/reference)

- [Como usar Tab-Completion](../../core-powershell/console/using-tab-expansion.md)

- [Como usar Get-Help](./getting-detailed-help-information.md)