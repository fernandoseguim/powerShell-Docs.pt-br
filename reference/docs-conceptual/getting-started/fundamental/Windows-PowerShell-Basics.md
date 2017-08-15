---
ms.date: 2017-06-05T00:00:00.000Z
keywords: PowerShell, cmdlet
title: "Noções básicas do Windows PowerShell"
ms.assetid: 6b3cbbc8-060c-4877-b00b-7300dbbe4e28
ms.openlocfilehash: f8a520f1fbe97737c7d0c2acab0129f88b5ed425
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/03/2017
---
# <a name="windows-powershell-basics"></a>Noções básicas do Windows PowerShell
Interfaces do usuário gráficas usam alguns conceitos básicos que são conhecidos para a maioria dos usuários do computador. Os usuários contam com a familiaridade dessas interfaces para realizar tarefas. Os sistemas operacionais apresentam aos usuários uma representação gráfica dos itens que podem ser explorados, geralmente com menus suspensos para acesso a funcionalidades específicas e menus de contexto para acesso a funcionalidades específicas de contexto.

Uma CLI (Interface de Linha de Comando), como o Windows PowerShell, deve usar uma abordagem diferente para expor informações, pois não apresenta menus ou sistemas gráficos para ajudar o usuário. Você precisa saber os nomes de comando para poder usá-los. Embora seja possível digitar comandos complexos que são equivalentes aos recursos em um ambiente de GUI, você deve se familiarizar com os comandos mais frequentemente usados e os parâmetros de comando.

A maioria das CLIs não tem padrões que podem ajudar o usuário a aprender a interface. Como as CLIs foram os primeiros shells de sistema operacional, muitos nomes de comandos e parâmetros foram selecionados arbitrariamente. Nomes de comando concisos geralmente eram escolhidos em vez de nomes claros. Embora os sistemas de ajuda e padrões de design de comando estejam integrados à maioria das CLIs, eles em geral foram projetados para compatibilidade com os comandos mais antigos, portanto o conjunto de comandos ainda é modelado por decisões tomadas décadas atrás.

O Windows PowerShell foi projetado para aproveitar o conhecimento histórico de um usuário de CLIs. Neste capítulo, abordaremos algumas ferramentas e conceitos básicos que você pode usar para aprender a usar o Windows PowerShell rapidamente. Elas incluem:

-   Uso de Get-Command

-   Usar comandos de Cmd.exe e de UNIX

-   Usar comandos externos

-   Uso de Tab-Completion

-   Uso de Get-Help

