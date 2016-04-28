---
title: Acessibilidade no ISE do Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a078f9d1-dd6b-4323-b16d-0622cd993aa8
---
# Acessibilidade no ISE do Windows PowerShell
Este tópico descreve os recursos de acessibilidade do [!INCLUDE[ise_1](../Token/ise_1_md.md)] que podem ser úteis.

[Como alterar o tamanho e o local dos Painéis de Console e de Script](#bkmk_1)
[Atalhos de teclado para edição de texto](#bkmk_2)
[Atalhos de teclado para execução de scripts](#bkmk_3)
[Atalhos de teclado para personalizar a exibição](#bkmk_4)
[Atalhos de teclado para depuração de scripts](#bkmk_5)
[Atalhos do teclado para as guias do Windows PowerShell](#bkmk_6)
[Atalhos de teclado para iniciar e sair](#bkmk_7)
A Microsoft tem o compromisso de facilitar o uso de seus produtos e serviços para todos. Os tópicos a seguir fornecem informações sobre os recursos, produtos e serviços que tornam o [!INCLUDE[ise_2](../Token/ise_2_md.md)] mais acessível para pessoas portadoras de deficiência.

O [!INCLUDE[ise_2](../Token/ise_2_md.md)] dá suporte ao modo de alto contraste. Para os deficientes visuais, informações de ponto de interrupção estão disponíveis por meio dos cmdlets para gerenciar pontos de interrupção, como [Get-PSBreakpoint](assetId:///0bf48936-00ab-411c-b5e0-9b10a812a3c6) e [Set-PSBreakpoint](assetId:///6afd5d2c-a285-4796-8607-3cbf49471420). Para obter mais informações, consulte "Como gerenciar pontos de interrupção" em [Como depurar scripts no ISE do Windows PowerShell](../Topic/How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md#bkmk_1). Além dos recursos de acessibilidade e utilitários no Microsoft Windows, os seguintes recursos tornam o ISE do Windows PowerShell mais acessível a pessoas com deficiências:

-   Atalhos do teclado

-   Tabela de cores de sintaxe e a capacidade de modificar várias outras configurações de cor usando o objeto de script [$psISE.Options](assetId:///75e2a76f-f3d1-490b-ad5d-e3829946aabb).

-   Alteração do tamanho do texto

## <a name="bkmk_1"></a>Como alterar o tamanho e o local dos Painéis de Console e de Script
Você pode usar as etapas a seguir para alterar o tamanho e o local do Painel de Console e do Painel de Script. Quando você abrir o [!INCLUDE[ise_2](../Token/ise_2_md.md)] novamente, as alterações de tamanho e local feitas serão mantidas.

### Para redimensionar o Painel de Script e o Painel de Console

1.  Coloque o ponteiro na linha de divisão entre o Painel de Script e o Painel de Console.

2.  Quando o ponteiro do mouse mudar para uma seta dupla, arraste a borda para alterar o tamanho do painel.

### Para mover o Painel de Script e o Painel de Console
Realize um dos seguintes procedimentos:

-   Para mover o Painel de Script acima dos Painéis de Comando e de Saída, pressione **CTRL+1** ou, na barra de ferramentas, clique no ícone **Mostrar o Painel de Script na Parte Superior** ou então, no menu **Exibir**, clique em **Mostrar o Painel de Script na Parte Superior**.

-   Para mover o Painel de Script à direita do Painel de Console, pressione **CTRL+2** ou, na barra de ferramentas, clique no ícone **Mostrar o Painel de Script à Direita** ou então, no menu **Exibir**, clique em **Mostrar o Painel de Script à Direita**.

-   Para maximizar o Painel de Script, pressione **CTRL+3** ou, na barra de ferramentas, clique no ícone **Mostrar o Painel de Script Maximizado** ou então, no menu **Exibir**, clique em **Mostrar o Painel de Script Maximizado**.

-   Para maximizar o Painel de Console e ocultar o Painel de Script, na extrema borda direita da linha de guias, clique no ícone **Ocultar Painel de Script**, no menu **Exibir**, clique para desmarcar a opção de menu **Mostrar Painel de Script**.

-   Para exibir o Painel de Script quando o Painel de Console está maximizado, na extrema borda direita da linha de guias, clique no ícone **Ocultar Painel de Script** ou então, no menu **Exibir**, clique para marcar a opção de menu **Mostrar Painel de Script**.

## <a name="bkmk_2"></a>Atalhos de teclado para edição de texto
Você pode usar os seguintes atalhos de teclado ao editar texto.

|Ação|Atalhos do teclado|Usar em|
|----------|----------------------|----------|
|**Cópia**|CTRL+C|Painel de Script, Painel de Comando e Painel de Saída|
|**Recortar**|CTRL+X|Painel de Script, Painel de Comando|
|**Localizar no Script**|CTRL+F|Painel de Script|
|**Localizar Próximo no Script**|F3|Painel de Script|
|**Localizar Anterior no Script**|SHIFT+F3|Painel de Script|
|**Colar**|CTRL+V|Painel de Script, Painel de Comando|
|**Refazer**|CTRL+Y|Painel de Script, Painel de Comando|
|**Substituir no Script**|CTRL+H|Painel de Script|
|**Salvar**|CTRL+S|Painel de Script|
|**Selecionar Tudo**|CTRL+A|Painel de Script, Painel de Comando e Painel de Saída|
|**Desfazer**|CTRL+Z|Painel de Script, Painel de Comando|

## <a name="bkmk_3"></a>Atalhos de teclado para execução de scripts
Você pode usar os seguintes atalhos de teclado ao executar scripts no Painel de Script.

|Ação|Atalho do Teclado|
|----------|---------------------|
|**Novo**|CTRL+N|
|**Abrir**|CTRL+O|
|**Executar**|F5|
|**Executar Seleção**|F8|
|**Parar Execução**|CTRL+BREAK. CTRL+C pode ser usado quando o contexto é ambíguo (quando não há nenhum texto selecionado).|
|**Tab** (para o próximo script)|CTRL+TAB **Observação:** Tab para o próximo script só funcionará quando você tiver uma única guia do PowerShell aberta ou se tiver mais de uma guia do PowerShell aberta, mas o foco estiver no Painel de Script.|
|**Tab** (para o script anterior)|CTRL+SHIFT+TAB **Observação:** Tab para o script anterior só funcionará quando você tiver uma única guia do PowerShell aberta ou se tiver mais de uma guia do PowerShell aberta, mas o foco estiver no Painel de Script.|

## <a name="bkmk_4"></a>Atalhos de teclado para personalizar a exibição
Você pode usar os seguintes atalhos de teclado ao personalizar a exibição no [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)]. Eles são acessíveis de todos os painéis no aplicativo.

|Ação|Atalho do Teclado|
|----------|---------------------|
|**Ir para o Painel de Comando**|CTRL+D|
|**Ir para o Painel de Saída**|CTRL+SHIFT+O|
|**Ir para o Painel de Script**|CTRL+I|
|**Mostrar Painel de Script**|CTRL+R|
|**Ocultar Painel de Script**|CTRL+R|
||
|**Mover o Painel de Script para cima**|CTRL+1|
|**Mover o Painel de Script para a direita**|CTRL+2|
|**Maximizar o Painel de Script**|CTRL+3|
|**Ampliar**|CTRL+SINAL DE ADIÇÃO|
|**Reduzir**|CTRL+SINAL DE SUBTRAÇÃO|

## <a name="bkmk_5"></a>Atalhos de teclado para depuração de scripts
Você pode usar os seguintes atalhos do teclado ao depurar scripts.

|Ação|Atalho do Teclado|Usar em|
|----------|---------------------|----------|
|**Execução/Continuar**|F5|Painel de Script ao depurar um script|
|**Intervir**|F11|Painel de Script ao depurar um script|
|**Contornar**|F10|Painel de Script ao depurar um script|
|**Sair**|SHIFT+F11|Painel de Script ao depurar um script|
|**Exibir Pilha de Chamadas**|CTRL+SHIFT+D|Painel de Script ao depurar um script|
|**Listar Pontos de Interrupção**|CTRL+SHIFT+L|Painel de Script ao depurar um script|
|**Alternar Ponto de Interrupção**|F9|Painel de Script ao depurar um script|
|**Remover Todos os Pontos de Interrupção**|CTRL+SHIFT+F9|Painel de Script ao depurar um script|
|**Parar Depurador**|SHIFT+F5|Painel de Script ao depurar um script|

> [!NOTE]
> Você também pode usar os atalhos de teclado projetados para o console do Windows PowerShell ao depurar scripts no ISE do Windows PowerShell. Para usar esses atalhos, você deve digitar o atalho no Painel de Comando e pressionar ENTER.

|Ação|Atalho do Teclado|Usar em|
|----------|---------------------|----------|
|**Continuar**|C|Painel de Comando ao depurar um script|
|**Intervir**|S|Painel de Comando ao depurar um script|
|**Contornar**|V|Painel de Comando ao depurar um script|
|**Sair**|O|Painel de Comando ao depurar um script|
|**Repetir Último Comando** (para Intervir ou Contornar)|ENTER|Painel de Comando ao depurar um script|
|**Exibir Pilha de Chamadas**|K|Painel de Comando ao depurar um script|
|**Parar Depuração**|Q|Painel de Comando ao depurar um script|
|**Listar o Script**|L|Painel de Comando ao depurar um script|
|**Exibir Comandos de Depuração do Console**|H ou ?|Painel de Comando ao depurar um script|

## <a name="bkmk_6"></a>Atalhos do teclado para as guias do Windows PowerShell
Você pode usar os seguintes atalhos do teclado ao utilizar as guias do Windows PowerShell.

|Ação|Atalho do Teclado|
|----------|---------------------|
|**Fechar a guia do PowerShell**|CTRL+W|
|**Nova guia do PowerShell**|CTRL+T|
|**Guia anterior do PowerShell**|CTRL+SHIFT+TAB. Este atalho funciona somente quando nenhum arquivo estiver aberto em qualquer uma das guias do PowerShell.|
|**Próxima guia do Windows PowerShell**|CTRL+TAB. Este atalho funciona somente quando nenhum arquivo estiver aberto em qualquer uma das guias do PowerShell.|

## <a name="bkmk_7"></a>Atalhos de teclado para iniciar e sair
Você pode usar os seguintes atalhos de teclado para iniciar o console do Windows PowerShell (PowerShell.exe) ou para sair do [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)].

|Ação|Atalho do Teclado|
|----------|---------------------|
|**Sair**|ALT+F4|
|**Iniciar o PowerShell.exe** ([!INCLUDE[psconsole](../Token/psconsole_md.md)])|CTRL+SHIFT+P|

## Consulte Também
[Usando o ISE do Windows PowerShell](../Topic/Using-the-Windows-PowerShell-ISE.md)



<!--HONumber=Apr16_HO1-->


