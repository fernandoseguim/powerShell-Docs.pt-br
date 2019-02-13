---
title: Como replicar a experiência do ISE no Visual Studio Code
description: Como replicar a experiência do ISE no Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 983da850c13d72bcdc7b2d33970c6e9e06b3d869
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676280"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>Como replicar a experiência do ISE no Visual Studio Code

Enquanto a extensão do PowerShell para VSCode não busca de paridade de recursos completo com o PowerShell ISE, há recursos em vigor para tornar a experiência de VSCode mais natural para usuários do ISE.

Este documento tenta configurações de lista, que você pode definir no VSCode para tornar o usuário enfrentar um pouco mais familiar em comparação com o ISE.

## <a name="key-bindings"></a>Associações de teclas

| Função                              | Associação de ISE                  | Associação de VSCode                              |
| ----------------                      | -----------                  | --------------                              |
| Interromper e interromper o depurador          | <kbd>Ctrl</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
| Executar o texto de linha/realçada atual | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
| Lista de trechos de código disponíveis               | <kbd>Ctrl</kbd>+<kbd>J</kbd> | <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd> |

### <a name="custom-key-bindings"></a>Associações de teclas personalizadas

Você pode [configurar suas próprias associações de teclas](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) no VSCode também.

## <a name="tab-completion"></a>Preenchimento de guias

Para habilitar o preenchimento com tab mais semelhante a ISE, adicione essa configuração:

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> Essa configuração foi adicionada diretamente para VSCode (em vez de na extensão). Seu comportamento é determinado pelo VSCode diretamente e não pode ser alterado pela extensão.

## <a name="no-focus-on-console-when-executing"></a>Sem foco no console ao executar

Para manter o foco no editor quando você executa com <kbd>F8</kbd>:

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

O padrão é `true` para fins de acessibilidade.

## <a name="dont-start-integrated-console-on-startup"></a>Não inicie o console integrado na inicialização

Para interromper o console integrado na inicialização, defina:

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> O processo do PowerShell do plano de fundo ainda será iniciado como que fornece o IntelliSense, análise de script, navegação de símbolo, etc. Mas o console não será mostrado.

## <a name="assume-files-are-powershell-by-default"></a>Suponha que arquivos sejam PowerShell por padrão

Para tornar os arquivos novos/sem título, registre-se como o PowerShell por padrão:

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a>Esquema de cores

Há um número de temas do ISE para VSCode fazer com que o editor pareça muito mais como o ISE.

No [paleta de comandos] tipo `theme` para obter `Preferences: Color Theme` e pressione <kbd>Enter</kbd>.
Na lista suspensa, selecione `PowerShell ISE`.

Você pode definir este tema nas configurações com:

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a>Gerenciador de comando do PowerShell

Graças ao trabalho do [ @corbob ](https://github.com/corbob), a extensão do PowerShell tem os inícios de seu próprio Gerenciador de comando.

No [paleta de comandos], insira `PowerShell Command Explorer` e pressione <kbd>Enter</kbd>.

## <a name="open-in-the-ise"></a>Abrir no ISE

Se você terminar de que deseja abrir um arquivo no ISE, mesmo assim, você pode usar <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.

## <a name="other-resources"></a>Outros recursos

- tem 4sysops [um ótimo artigo](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) sobre como configurar o VSCode para ser mais como o ISE.
- Tem Mike F Robbins [um ótimo post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) sobre como configurar o VSCode.
- Saiba o PowerShell tem [uma excelente gravação](https://www.learnpwsh.com/setup-vs-code-for-powershell/) sobre como obter o VSCode de instalação para o PowerShell.

## <a name="more-settings"></a>Mais configurações

Se você souber de mais maneiras de tornar o VSCode se sentir mais familiar para os usuários do ISE, contribuir para este documento. Se há uma configuração de compatibilidade que você está procurando, mas você não é possível localizar nenhuma forma para habilitá-lo, [abra um problema](https://github.com/PowerShell/vscode-powershell/issues/new/choose) e pergunte sem medo!

Estamos sempre aceitamos PRs e contribuições também!

## <a name="vscode-tips"></a>Dicas de VSCode

### <a name="command-palette"></a>Paleta de comandos

<kbd>F1</kbd> ou <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd> Deslocar</kbd>+<kbd>P</kbd> no macOS)

Uma maneira útil de execução de comandos no VSCode.
Para obter mais informações, consulte [documentos do VSCode](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).

[Paleta de comandos]: #command-palette
