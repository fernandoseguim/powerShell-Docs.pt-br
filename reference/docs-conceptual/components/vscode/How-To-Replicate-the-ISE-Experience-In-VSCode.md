---
title: Como replicar a experiência do ISE no Visual Studio Code
description: Como replicar a experiência do ISE no Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 983da850c13d72bcdc7b2d33970c6e9e06b3d869
ms.sourcegitcommit: 9df29dfc637191b62ca591893c251c1e02d4eb4c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54012476"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="91b07-103">Como replicar a experiência do ISE no Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="91b07-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="91b07-104">Enquanto a extensão do PowerShell para VSCode não busca de paridade de recursos completo com o PowerShell ISE, há recursos em vigor para tornar a experiência de VSCode mais natural para usuários do ISE.</span><span class="sxs-lookup"><span data-stu-id="91b07-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="91b07-105">Este documento tenta configurações de lista, que você pode definir no VSCode para tornar o usuário enfrentar um pouco mais familiar em comparação com o ISE.</span><span class="sxs-lookup"><span data-stu-id="91b07-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="91b07-106">Associações de teclas</span><span class="sxs-lookup"><span data-stu-id="91b07-106">Key bindings</span></span>

| <span data-ttu-id="91b07-107">Função</span><span class="sxs-lookup"><span data-stu-id="91b07-107">Function</span></span>                              | <span data-ttu-id="91b07-108">Associação de ISE</span><span class="sxs-lookup"><span data-stu-id="91b07-108">ISE Binding</span></span>                  | <span data-ttu-id="91b07-109">Associação de VSCode</span><span class="sxs-lookup"><span data-stu-id="91b07-109">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="91b07-110">Interromper e interromper o depurador</span><span class="sxs-lookup"><span data-stu-id="91b07-110">Interrupt and break debugger</span></span>          | <span data-ttu-id="91b07-111"><kbd>CTRL</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="91b07-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="91b07-112"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="91b07-112"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="91b07-113">Executar o texto de linha/realçada atual</span><span class="sxs-lookup"><span data-stu-id="91b07-113">Execute current line/highlighted text</span></span> | <span data-ttu-id="91b07-114"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="91b07-114"><kbd>F8</kbd></span></span>                | <span data-ttu-id="91b07-115"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="91b07-115"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="91b07-116">Lista de trechos de código disponíveis</span><span class="sxs-lookup"><span data-stu-id="91b07-116">List available snippets</span></span>               | <span data-ttu-id="91b07-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="91b07-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="91b07-118"><kbd>CTRL</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="91b07-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="91b07-119">Associações de teclas personalizadas</span><span class="sxs-lookup"><span data-stu-id="91b07-119">Custom Key bindings</span></span>

<span data-ttu-id="91b07-120">Você pode [configurar suas próprias associações de teclas](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) no VSCode também.</span><span class="sxs-lookup"><span data-stu-id="91b07-120">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="tab-completion"></a><span data-ttu-id="91b07-121">Preenchimento de guias</span><span class="sxs-lookup"><span data-stu-id="91b07-121">Tab completion</span></span>

<span data-ttu-id="91b07-122">Para habilitar o preenchimento com tab mais semelhante a ISE, adicione essa configuração:</span><span class="sxs-lookup"><span data-stu-id="91b07-122">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> <span data-ttu-id="91b07-123">Essa configuração foi adicionada diretamente para VSCode (em vez de na extensão).</span><span class="sxs-lookup"><span data-stu-id="91b07-123">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="91b07-124">Seu comportamento é determinado pelo VSCode diretamente e não pode ser alterado pela extensão.</span><span class="sxs-lookup"><span data-stu-id="91b07-124">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="91b07-125">Sem foco no console ao executar</span><span class="sxs-lookup"><span data-stu-id="91b07-125">No focus on console when executing</span></span>

<span data-ttu-id="91b07-126">Para manter o foco no editor quando você executa com <kbd>F8</kbd>:</span><span class="sxs-lookup"><span data-stu-id="91b07-126">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

<span data-ttu-id="91b07-127">O padrão é `true` para fins de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="91b07-127">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="91b07-128">Não inicie o console integrado na inicialização</span><span class="sxs-lookup"><span data-stu-id="91b07-128">Don't start integrated console on startup</span></span>

<span data-ttu-id="91b07-129">Para interromper o console integrado na inicialização, defina:</span><span class="sxs-lookup"><span data-stu-id="91b07-129">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="91b07-130">O processo do PowerShell do plano de fundo ainda será iniciado como que fornece o IntelliSense, análise de script, navegação de símbolo, etc. Mas o console não será mostrado.</span><span class="sxs-lookup"><span data-stu-id="91b07-130">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="91b07-131">Suponha que arquivos sejam PowerShell por padrão</span><span class="sxs-lookup"><span data-stu-id="91b07-131">Assume files are PowerShell by default</span></span>

<span data-ttu-id="91b07-132">Para tornar os arquivos novos/sem título, registre-se como o PowerShell por padrão:</span><span class="sxs-lookup"><span data-stu-id="91b07-132">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a><span data-ttu-id="91b07-133">Esquema de cores</span><span class="sxs-lookup"><span data-stu-id="91b07-133">Color scheme</span></span>

<span data-ttu-id="91b07-134">Há um número de temas do ISE para VSCode fazer com que o editor pareça muito mais como o ISE.</span><span class="sxs-lookup"><span data-stu-id="91b07-134">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="91b07-135">No [paleta de comandos] tipo `theme` para obter `Preferences: Color Theme` e pressione <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="91b07-135">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="91b07-136">Na lista suspensa, selecione `PowerShell ISE`.</span><span class="sxs-lookup"><span data-stu-id="91b07-136">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="91b07-137">Você pode definir este tema nas configurações com:</span><span class="sxs-lookup"><span data-stu-id="91b07-137">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a><span data-ttu-id="91b07-138">Gerenciador de comando do PowerShell</span><span class="sxs-lookup"><span data-stu-id="91b07-138">PowerShell Command Explorer</span></span>

<span data-ttu-id="91b07-139">Graças ao trabalho do [ @corbob ](https://github.com/corbob), a extensão do PowerShell tem os inícios de seu próprio Gerenciador de comando.</span><span class="sxs-lookup"><span data-stu-id="91b07-139">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="91b07-140">No [paleta de comandos], insira `PowerShell Command Explorer` e pressione <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="91b07-140">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="91b07-141">Abrir no ISE</span><span class="sxs-lookup"><span data-stu-id="91b07-141">Open in the ISE</span></span>

<span data-ttu-id="91b07-142">Se você terminar de que deseja abrir um arquivo no ISE, mesmo assim, você pode usar <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="91b07-142">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="91b07-143">Outros recursos</span><span class="sxs-lookup"><span data-stu-id="91b07-143">Other resources</span></span>

- <span data-ttu-id="91b07-144">tem 4sysops [um ótimo artigo](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) sobre como configurar o VSCode para ser mais como o ISE.</span><span class="sxs-lookup"><span data-stu-id="91b07-144">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="91b07-145">Tem Mike F Robbins [um ótimo post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) sobre como configurar o VSCode.</span><span class="sxs-lookup"><span data-stu-id="91b07-145">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="91b07-146">Saiba o PowerShell tem [uma excelente gravação](https://www.learnpwsh.com/setup-vs-code-for-powershell/) sobre como obter o VSCode de instalação para o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="91b07-146">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="91b07-147">Mais configurações</span><span class="sxs-lookup"><span data-stu-id="91b07-147">More settings</span></span>

<span data-ttu-id="91b07-148">Se você souber de mais maneiras de tornar o VSCode se sentir mais familiar para os usuários do ISE, contribuir para este documento. Se há uma configuração de compatibilidade que você está procurando, mas você não é possível localizar nenhuma forma para habilitá-lo, [abra um problema](https://github.com/PowerShell/vscode-powershell/issues/new/choose) e pergunte sem medo!</span><span class="sxs-lookup"><span data-stu-id="91b07-148">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="91b07-149">Estamos sempre aceitamos PRs e contribuições também!</span><span class="sxs-lookup"><span data-stu-id="91b07-149">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="91b07-150">Dicas de VSCode</span><span class="sxs-lookup"><span data-stu-id="91b07-150">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="91b07-151">Paleta de comandos</span><span class="sxs-lookup"><span data-stu-id="91b07-151">Command Palette</span></span>

<span data-ttu-id="91b07-152"><kbd>F1</kbd> ou <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd> Deslocar</kbd>+<kbd>P</kbd> no macOS)</span><span class="sxs-lookup"><span data-stu-id="91b07-152"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="91b07-153">Uma maneira útil de execução de comandos no VSCode.</span><span class="sxs-lookup"><span data-stu-id="91b07-153">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="91b07-154">Para obter mais informações, consulte [documentos do VSCode](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span><span class="sxs-lookup"><span data-stu-id="91b07-154">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[Paleta de comandos]: #command-palette
[Command Palette]: #command-palette
