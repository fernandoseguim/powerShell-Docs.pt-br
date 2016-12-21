---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet
ms.date: 2016-12-12
title: Como usar o Painel de Console com o ISE do Windows PowerShell
ms.technology: powershell
ms.assetid: 44d67705-87c7-4a69-a53e-6471fdebb757
ms.openlocfilehash: 68dd5499e4f0686a77f33265016414c7c4eb0618
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="how-to-use-the-console-pane-in-the-windows-powershell-ise"></a>Como usar o Painel de Console com o ISE do Windows PowerShell
O Painel de Console no ISE (Ambiente de Script Integrado) do Windows PowerShell® funciona exatamente como a janela de console autônoma do ISE do Windows PowerShell.

Para executar um comando no Painel de Console, digite um comando e pressione Enter. Para inserir vários comandos que você deseja executar em sequência, digite Shift+Enter entre os comandos. Consulte [Como usar o preenchimento com Tab no Painel de Script e no Painel de Console](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) para ver a ajuda para digitar os comandos.

Para interromper um comando, na barra de ferramentas, clique em **Parar Operação** ou pressione Ctrl+Break. Você também poderá usar Ctrl+C para interromper um comando se o contexto não for ambíguo. Por exemplo, se algum texto foi selecionado no painel atual, Ctrl+C será mapeado para a operação de cópia.

No Windows PowerShell v3 o Painel de Saída foi combinado com o Painel de Console. Isso traz o benefício de se comportar como console autônomo do Windows PowerShell e elimina as diferenças nos procedimentos que eram necessários quando eles eram separados. Você pode:

-   Selecione e copie o texto do Painel de console para a Área de transferência para colá-lo em qualquer outra janela. Para selecionar o texto, clique e mantenha o mouse pressionado no painel de saída enquanto arrasta o mouse sobre o texto que você deseja capturar. Você também pode usar as teclas de seta enquanto mantém **Shift** pressionado para selecionar o texto. Pressione Ctrl+C ou clique no ícone **Copiar** na barra de ferramentas.

-   Cole o texto selecionado na posição atual do cursor. Clique no ícone **Colar** na barra de ferramentas.

-   Limpe todo o texto no Painel de console. Para limpar o painel Console, você pode clicar no ícone **Limpar Painel Console** na barra de ferramentas ou executar o comando **Clear-Host**, ou seu alias, **cls**.

## <a name="see-also"></a>Consulte Também
- [Usando o ISE do Windows PowerShell](Using-the-Windows-PowerShell-ISE.md)

