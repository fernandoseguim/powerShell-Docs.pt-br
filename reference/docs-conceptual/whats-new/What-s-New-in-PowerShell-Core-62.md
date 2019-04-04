---
title: Novidades no PowerShell Core 6.2
description: Novos recursos e alterações liberados no PowerShell Core 6.2
ms.date: 03/28/2019
ms.openlocfilehash: 2224d23a244175059a705c07001e8ad8d6ab3aa0
ms.sourcegitcommit: 8dd4394cf867005a8b9ef0bb74b744c964fbc332
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2019
ms.locfileid: "58750044"
---
# <a name="whats-new-in-powershell-core-62"></a>Novidades no PowerShell Core 6.2

Abaixo, uma seleção de alguns dos principais recursos novos e alterações que foram introduzidos no PowerShell Core 6.2.

Também há **toneladas** de "coisas chatas" que tornam o PowerShell mais rápido e mais estável (além de muitas e muitas correções de bugs)!
Para obter uma lista completa de alterações, confira nosso [log de alterações no GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).

Apesar de citarmos alguns nomes abaixo, obrigado a [todos os colaboradores da comunidade](https://github.com/PowerShell/PowerShell/graphs/contributors) que possibilitaram esta versão.

## <a name="engine-updates-and-fixes"></a>Atualizações e correções do mecanismo

- Adição de mensagens de aviso do cmdlet habilitar/desabilitar o PowerShell remoto ([#9203][])
- Correção para regressão de desserialização remoto de `FormatTable` ([#9116][])
- Atualização de APIs `async` baseadas em tarefa adicionadas ao PowerShell para retornar um objeto Tarefa diretamente ([#9079][])
- Adição de cinco sobrecargas `InvokeAsync` e `StopAsync` para o tipo `PowerShell` ([#8056][]) (Obrigado @KirkMunro!)

## <a name="general-cmdlet-updates-and-fixes"></a>Atualizações e correções gerais do Cmdlet

- Habilitação de cmdlets `SecureString` para não Windows, armazenando o texto sem formatação ([#9199][])
- Adição da mensagem Obsoleto ao `Send-MailMessage` ([#9178][])
- Correção de `Restart-Computer` para trabalhar em `localhost` quando o WinRM não está presente ([#9160][])
- Fazer o `Start-Job` lançar o erro de encerramento quando PowerShell estiver sendo hospedado ([#9128][])
- Atualização da versão de `PowerShell.Native` e testes de hospedagem ([#8983][])

## <a name="breaking-changes"></a>Alterações da falha

Correção – comportamento NoEnumerate na Gravação-Saída para ser consistente com o Windows PowerShell ([#9069][]) (Obrigado @vexx32!)

<!-- Link references -->
[#8056]: https://github.com/PowerShell/PowerShell/pull/8056
[#8983]: https://github.com/PowerShell/PowerShell/pull/8983
[#9069]: https://github.com/PowerShell/PowerShell/pull/9069
[#9079]: https://github.com/PowerShell/PowerShell/pull/9079
[#9116]: https://github.com/PowerShell/PowerShell/pull/9116
[#9128]: https://github.com/PowerShell/PowerShell/pull/9128
[#9160]: https://github.com/PowerShell/PowerShell/pull/9160
[#9178]: https://github.com/PowerShell/PowerShell/pull/9178
[#9199]: https://github.com/PowerShell/PowerShell/pull/9199
[#9203]: https://github.com/PowerShell/PowerShell/pull/9203
