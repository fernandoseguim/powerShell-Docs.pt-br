---
title: Como usar o Painel de Console com o ISE do Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 44d67705-87c7-4a69-a53e-6471fdebb757
---
# Como usar o Painel de Console com o ISE do Windows PowerShell
O Painel de console do [!INCLUDE[ise_1](../Token/ise_1_md.md)] opera exatamente como a janela de console autônoma do [!INCLUDE[ise_2](../Token/ise_2_md.md)].

Para executar um comando no Painel de Console, digite um comando e pressione ENTER. Para inserir vários comandos que você deseja executar em sequência, digite SHIFT+ENTER entre os comandos. Consulte [Como usar o preenchimento com Tab no Painel de Script e no Painel de Console](../Topic/How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) para ver a ajuda para digitar os comandos.

Para interromper um comando, na barra de ferramentas, clique em **Parar Operação** ou pressione CTRL+BREAK. Você também poderá usar CTRL+C para interromper um comando se o contexto não for ambíguo. Por exemplo, se algum texto foi selecionado no painel atual, CTRL+C é mapeado para a operação de cópia.

Começando do [!INCLUDE[wps_2](../Token/wps_2_md.md)] v3, o Painel de saída foi combinado com o Painel de Console. Isso traz o benefício de se comportar como console autônomo do [!INCLUDE[wps_2](../Token/wps_2_md.md)] e elimina as diferenças nos procedimentos que eram necessários quando eles existiam separados. Você pode:

-   Selecione e copie o texto do Painel de console para a Área de transferência para colá-lo em qualquer outra janela. Para selecionar o texto, clique e mantenha o mouse pressionado no painel de saída enquanto arrasta o mouse sobre o texto que você deseja capturar. Você também pode usar as teclas de seta enquanto mantém **SHIFT** pressionado para selecionar o texto. Pressione CTRL+C ou clique no ícone **Copiar** na barra de ferramentas.

-   Cole o texto selecionado na posição atual do cursor. Clique no ícone **Colar** na barra de ferramentas.

-   Limpe todo o texto no Painel de console. Para limpar o Painel de console, você pode clicar no ícone **Limpar o Painel de Console** na barra de ferramentas ou executar o comando **Clear-Host** ou seu alias, **cls**.

## Consulte Também
[Usando o ISE do Windows PowerShell](../Topic/Using-the-Windows-PowerShell-ISE.md)



<!--HONumber=Apr16_HO1-->


