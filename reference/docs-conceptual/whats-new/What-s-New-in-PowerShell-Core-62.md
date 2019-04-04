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
# <a name="whats-new-in-powershell-core-62"></a><span data-ttu-id="bf37b-103">Novidades no PowerShell Core 6.2</span><span class="sxs-lookup"><span data-stu-id="bf37b-103">What's New in PowerShell Core 6.2</span></span>

<span data-ttu-id="bf37b-104">Abaixo, uma seleção de alguns dos principais recursos novos e alterações que foram introduzidos no PowerShell Core 6.2.</span><span class="sxs-lookup"><span data-stu-id="bf37b-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.2.</span></span>

<span data-ttu-id="bf37b-105">Também há **toneladas** de "coisas chatas" que tornam o PowerShell mais rápido e mais estável (além de muitas e muitas correções de bugs)!</span><span class="sxs-lookup"><span data-stu-id="bf37b-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span>
<span data-ttu-id="bf37b-106">Para obter uma lista completa de alterações, confira nosso [log de alterações no GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span><span class="sxs-lookup"><span data-stu-id="bf37b-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="bf37b-107">Apesar de citarmos alguns nomes abaixo, obrigado a [todos os colaboradores da comunidade](https://github.com/PowerShell/PowerShell/graphs/contributors) que possibilitaram esta versão.</span><span class="sxs-lookup"><span data-stu-id="bf37b-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="engine-updates-and-fixes"></a><span data-ttu-id="bf37b-108">Atualizações e correções do mecanismo</span><span class="sxs-lookup"><span data-stu-id="bf37b-108">Engine Updates and Fixes</span></span>

- <span data-ttu-id="bf37b-109">Adição de mensagens de aviso do cmdlet habilitar/desabilitar o PowerShell remoto ([#9203][])</span><span class="sxs-lookup"><span data-stu-id="bf37b-109">Add PowerShell remoting enable/disable cmdlet warning messages ([#9203][])</span></span>
- <span data-ttu-id="bf37b-110">Correção para regressão de desserialização remoto de `FormatTable` ([#9116][])</span><span class="sxs-lookup"><span data-stu-id="bf37b-110">Fix for `FormatTable` remote deserialization regression ([#9116][])</span></span>
- <span data-ttu-id="bf37b-111">Atualização de APIs `async` baseadas em tarefa adicionadas ao PowerShell para retornar um objeto Tarefa diretamente ([#9079][])</span><span class="sxs-lookup"><span data-stu-id="bf37b-111">Update the task-based `async` APIs added to PowerShell to return a Task object directly ([#9079][])</span></span>
- <span data-ttu-id="bf37b-112">Adição de cinco sobrecargas `InvokeAsync` e `StopAsync` para o tipo `PowerShell` ([#8056][]) (Obrigado @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="bf37b-112">Add 5 `InvokeAsync` overloads and `StopAsync` to the `PowerShell` type ([#8056][]) (Thanks @KirkMunro!)</span></span>

## <a name="general-cmdlet-updates-and-fixes"></a><span data-ttu-id="bf37b-113">Atualizações e correções gerais do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bf37b-113">General Cmdlet Updates and Fixes</span></span>

- <span data-ttu-id="bf37b-114">Habilitação de cmdlets `SecureString` para não Windows, armazenando o texto sem formatação ([#9199][])</span><span class="sxs-lookup"><span data-stu-id="bf37b-114">Enable `SecureString` cmdlets for non-Windows by storing the plain text ([#9199][])</span></span>
- <span data-ttu-id="bf37b-115">Adição da mensagem Obsoleto ao `Send-MailMessage` ([#9178][])</span><span class="sxs-lookup"><span data-stu-id="bf37b-115">Add Obsolete message to `Send-MailMessage` ([#9178][])</span></span>
- <span data-ttu-id="bf37b-116">Correção de `Restart-Computer` para trabalhar em `localhost` quando o WinRM não está presente ([#9160][])</span><span class="sxs-lookup"><span data-stu-id="bf37b-116">Fix `Restart-Computer` to work on `localhost` when WinRM is not present ([#9160][])</span></span>
- <span data-ttu-id="bf37b-117">Fazer o `Start-Job` lançar o erro de encerramento quando PowerShell estiver sendo hospedado ([#9128][])</span><span class="sxs-lookup"><span data-stu-id="bf37b-117">Make `Start-Job` throw terminating error when PowerShell is being hosted ([#9128][])</span></span>
- <span data-ttu-id="bf37b-118">Atualização da versão de `PowerShell.Native` e testes de hospedagem ([#8983][])</span><span class="sxs-lookup"><span data-stu-id="bf37b-118">Update version for `PowerShell.Native` and hosting tests ([#8983][])</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="bf37b-119">Alterações da falha</span><span class="sxs-lookup"><span data-stu-id="bf37b-119">Breaking Changes</span></span>

<span data-ttu-id="bf37b-120">Correção – comportamento NoEnumerate na Gravação-Saída para ser consistente com o Windows PowerShell ([#9069][]) (Obrigado @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="bf37b-120">Fix -NoEnumerate behavior in Write-Output to be consistent with Windows PowerShell ([#9069][]) (Thanks @vexx32!)</span></span>

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
