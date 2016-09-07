---
title: Acessibilidade no ISE do Windows PowerShell
ms.date: 2016-05-11
keywords: PowerShell, cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: a078f9d1-dd6b-4323-b16d-0622cd993aa8
translationtype: Human Translation
ms.sourcegitcommit: 3222a0ba54e87b214c5ebf64e587f920d531956a
ms.openlocfilehash: b4d97b1c96a99bcfc43fb20ce9a4ecfa528ea024

---

# Acessibilidade no ISE do Windows PowerShell
Este tópico descreve os recursos de acessibilidade do ISE (Ambiente de Script Integrado) do Windows PowerShell® que podem ser úteis.

* [Como alterar o tamanho e o local dos Painéis de Console e de Script](#bkmk_1)
* [Atalhos de teclado para edição de texto](#bkmk_2)
* [Atalhos de teclado para execução de scripts](#bkmk_3)
* [Atalhos de teclado para personalizar a exibição](#bkmk_4)
* [Atalhos de teclado para depuração de scripts](#bkmk_5)
* [Atalhos do teclado para as guias do Windows PowerShell](#bkmk_6)
* [Atalhos de teclado para iniciar e sair](#bkmk_7)

A Microsoft tem o compromisso de facilitar o uso de seus produtos e serviços para todos. Os tópicos a seguir fornecem informações sobre os recursos, produtos e serviços que tornam o ISE do Windows PowerShell mais acessível para pessoas portadoras de deficiência.

O ISE do Windows PowerShell dá suporte ao modo de alto contraste. Para os deficientes visuais, informações de ponto de interrupção estão disponíveis por meio dos cmdlets para gerenciar pontos de interrupção, como [Get-PSBreakpoint](https://technet.microsoft.com/en-us/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) e [Set-PSBreakpoint](https://technet.microsoft.com/en-us/library/6afd5d2c-a285-4796-8607-3cbf49471420). Para obter mais informações, consulte "Como gerenciar pontos de interrupção" em [Como depurar scripts no ISE do Windows PowerShell](../core-powershell/ise/How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md#bkmk_1). Além dos recursos de acessibilidade e utilitários no Microsoft Windows, os seguintes recursos tornam o ISE do Windows PowerShell mais acessível a pessoas com deficiências:

-   Atalhos do teclado

-   Tabela de cores de sintaxe e a capacidade de modificar várias outras configurações de cor usando o objeto de script [$psISE.Options](https://technet.microsoft.com/en-us/library/75e2a76f-f3d1-490b-ad5d-e3829946aabb).

-   Alteração do tamanho do texto

## <a name="bkmk_1"></a>Como alterar o tamanho e o local dos Painéis de Console e de Script
Você pode usar as etapas a seguir para alterar o tamanho e o local do Painel de Console e do Painel de Script. Quando você abrir o ISE do Windows PowerShell novamente, as alterações de tamanho e localização feitas serão mantidas.

### Para redimensionar o Painel de Script e o Painel de Console

1.  Coloque o ponteiro na linha de divisão entre o Painel de Script e o Painel de Console.

2.  Quando o ponteiro do mouse mudar para uma seta dupla, arraste a borda para alterar o tamanho do painel.

### Para mover o Painel de Script e o Painel de Console
Realize um dos seguintes procedimentos:

-   Para mover o Painel de Script acima do Painel Console, pressione **Ctrl+1** ou, na barra de ferramentas, clique no ícone **Mostrar Painel de Script Acima** ou então, no menu **Exibir**, clique em **Mostrar Painel de Script Acima**.

-   Para mover o Painel de Script para a direita do Painel Console, pressione **Ctrl+2** ou, na barra de ferramentas, clique no ícone **Mostrar Painel de Script à Direita** ou então, no menu **Exibir**, clique em **Mostrar Painel de Script à Direita**.

-   Para maximizar o Painel de Script, pressione **Ctrl+3** ou, na barra de ferramentas, clique no ícone **Mostrar Painel de Script Maximizado** ou então, no menu **Exibir**, clique em **Mostrar Painel de Script Maximizado**.

-   Para maximizar o Painel de Console e ocultar o Painel de Script, na extrema borda direita da linha de guias, clique no ícone **Ocultar Painel de Script**, no menu **Exibir**, clique para desmarcar a opção de menu **Mostrar Painel de Script**.

-   Para exibir o Painel de Script quando o Painel de Console está maximizado, na extrema borda direita da linha de guias, clique no ícone **Ocultar Painel de Script** ou então, no menu **Exibir**, clique para marcar a opção de menu **Mostrar Painel de Script**.

## <a name="bkmk_2"></a>Atalhos de teclado para edição de texto
Você pode usar os seguintes atalhos de teclado ao editar texto.

|Ação|Atalhos do teclado|Usar em|
|----------|----------------------|----------|
|**Cópia**|Ctrl+C|Painel de script, o painel de console|
|**Recortar**|Ctrl+X|Painel de script, o painel de console|
|**Localizar no Script**|Ctrl+F|Painel de Script|
|**Localizar Próximo no Script**|F3|Painel de Script|
|**Localizar Anterior no Script**|Shift+F3|Painel de Script|
|**Colar**|Ctrl+V|Painel de script, o painel de console|
|**Refazer**|Ctrl+Y|Painel de script, o painel de console|
|**Substituir no Script**|Ctrl+H|Painel de Script|
|**Salvar**|Ctrl+S|Painel de Script|
|**Selecionar Tudo**|Ctrl+A|Painel de script, o painel de console|
|**Desfazer**|Ctrl+Z|Painel de script, o painel de console|

## <a name="bkmk_3"></a>Atalhos de teclado para execução de scripts
Você pode usar os seguintes atalhos de teclado ao executar scripts no Painel de Script.

|Ação|Atalho do Teclado|
|----------|---------------------|
|**Novo**|Ctrl+N|
|**Abrir**|Ctrl+O|
|**Executar**|F5|
|**Executar Seleção**|F8|
|**Parar Execução**|Ctrl+Break. Ctrl+C pode ser usado quando o contexto é ambíguo (quando não há texto selecionado).|
|**Tab** (para o próximo script)|Ctrl+Tab **Observação:** Tab para o próximo script só funcionará quando você tiver uma única guia do PowerShell aberta ou se tiver mais de uma guia do PowerShell aberta, mas o foco estiver no Painel de Script.|
|**Tab** (para o script anterior)|Ctrl+Shift+Tab **Observação:** Tab para o script anterior só funcionará quando você tiver uma única guia do PowerShell aberta ou se tiver mais de uma guia do PowerShell aberta, mas o foco estiver no Painel de Script.|

## <a name="bkmk_4"></a>Atalhos de teclado para personalizar a exibição
Você pode usar os seguintes atalhos de teclado para personalizar a exibição no ISE do Windows PowerShell. Eles são acessíveis de todos os painéis no aplicativo.

|Ação|Atalho do Teclado|
|----------|---------------------|
|**Ir para Painel de Console**|Ctrl+D|
|**Ir para o Painel de Script**|Ctrl+I|
|**Mostrar Painel de Script**|Ctrl+R|
|**Ocultar Painel de Script**|Ctrl+R|
||
|**Mover o Painel de Script para cima**|Ctrl+1|
|**Mover o Painel de Script para a direita**|Ctrl+2|
|**Maximizar o Painel de Script**|Ctrl+3|
|**Ampliar**|Ctrl+Sinal de adição|
|**Reduzir**|Ctrl+Sinal de subtração|

## <a name="bkmk_5"></a>Atalhos de teclado para depuração de scripts
Você pode usar os seguintes atalhos do teclado ao depurar scripts.

|Ação|Atalho do Teclado|Usar em|
|----------|---------------------|----------|
|**Executar/continuar**|F5|Painel de Script ao depurar um script|
|**Intervir**|F11|Painel de Script ao depurar um script|
|**Contornar**|F10|Painel de Script ao depurar um script|
|**Sair**|Shift+F11|Painel de Script ao depurar um script|
|**Exibir Pilha de Chamadas**|Ctrl+Shift+D|Painel de Script ao depurar um script|
|**Listar Pontos de Interrupção**|Ctrl+Shift+L|Painel de Script ao depurar um script|
|**Alternar Ponto de Interrupção**|F9|Painel de Script ao depurar um script|
|**Remover Todos os Pontos de Interrupção**|Ctrl+Shift+F9|Painel de Script ao depurar um script|
|**Parar Depurador**|Shift+F5|Painel de Script ao depurar um script|

> [!NOTE]
> Você também pode usar os atalhos de teclado projetados para o console do Windows PowerShell ao depurar scripts no ISE do Windows PowerShell. Para usar esses atalhos, você deve digitar o atalho no Painel de Console e pressionar Enter.

|Ação|Atalho do Teclado|Usar em|
|----------|---------------------|----------|
|**Continuar**|C|Painel de Console ao depurar um script|
|**Intervir**|S|Painel de Console ao depurar um script|
|**Contornar**|V|Painel de Console ao depurar um script|
|**Sair**|O|Painel de Console ao depurar um script|
|**Repetir Último Comando** (para Intervir ou Contornar)|Enter|Painel de Console ao depurar um script|
|**Exibir Pilha de Chamadas**|K|Painel de Console ao depurar um script|
|**Parar Depuração**|Q|Painel de Console ao depurar um script|
|**Listar o Script**|L|Painel de Console ao depurar um script|
|**Exibir Comandos de Depuração do Console**|H ou ?|Painel de Console ao depurar um script|

## <a name="bkmk_6"></a>Atalhos do teclado para as guias do Windows PowerShell
Você pode usar os seguintes atalhos do teclado ao utilizar as guias do Windows PowerShell.

|Ação|Atalho do Teclado|
|----------|---------------------|
|**Fechar a guia do PowerShell**|Ctrl+W|
|**Nova guia do PowerShell**|Ctrl+T|
|**Guia anterior do PowerShell**|Ctrl+Shift+Tab. Este atalho funciona somente quando nenhum arquivo estiver aberto em qualquer uma das guias do PowerShell.|
|**Próxima guia do Windows PowerShell**|Ctrl+Tab. Este atalho funciona somente quando nenhum arquivo estiver aberto em qualquer uma das guias do PowerShell.|

## <a name="bkmk_7"></a>Atalhos de teclado para iniciar e sair
Você pode usar os seguintes atalhos de teclado para iniciar o console do Windows PowerShell (PowerShell.exe) ou para sair do ISE do Windows PowerShell.

|Ação|Atalho do Teclado|
|----------|---------------------|
|**Sair**|Alt+F4|
|**Iniciar o PowerShell.exe** (console do Windows PowerShell)|Ctrl+Shift+P|

## Consulte Também
[Usando o ISE do Windows PowerShell](../core-powershell/ise/Using-the-Windows-PowerShell-ISE.md)




<!--HONumber=Aug16_HO4-->


