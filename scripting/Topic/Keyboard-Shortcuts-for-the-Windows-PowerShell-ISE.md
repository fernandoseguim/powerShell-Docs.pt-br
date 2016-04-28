---
title: Atalhos do teclado para o ISE do Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8328b946-0f02-4ef4-ac28-2743a1b4043b
---
# Atalhos do teclado para o ISE do Windows PowerShell
Use os seguintes atalhos de teclado para executar ações no [!INCLUDE[ise_1](../Token/ise_1_md.md)]. O [!INCLUDE[ise_2](../Token/ise_2_md.md)] está disponível como parte dos sistemas operacionais cliente Windows Server e Windows, mas também pode ser instalado em alguns sistemas operacionais Windows mais antigos como parte do [pacote de download do Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881).

## Atalhos de teclado para edição de texto
Você pode usar os seguintes atalhos de teclado ao editar texto.

|Ação|Atalhos do teclado|Usar em|
|----------|----------------------|----------|
|**Ajuda**|F1|Painel de Script **Importante:** você pode especificar que a Ajuda com F1 venha da Biblioteca do TechNet na Web ou da Ajuda baixada (consulte Update-Help). Para selecionar, clique em **Ferramentas**, **Opções** e, na guia **Configurações Gerais**, defina ou apague **Usar conteúdo da Ajuda local em vez do conteúdo online.**|
|**Cópia**|CTRL+C|Painel de Script, Painel de Comando e Painel de Saída|
|**Recortar**|CTRL+X|Painel de Script, Painel de Comando|
|**Expandir ou Recolher a Estrutura de Tópicos**|CTRL+M|Painel de Script|
|**Localizar no Script**|CTRL+F|Painel de Script|
|**Localizar Próximo no Script**|F3|Painel de Script|
|**Localizar Anterior no Script**|SHIFT+F3|Painel de Script|
|**Localizar Chave Correspondente**|CTRL+]|Painel de Script|
|**Colar**|CTRL+V|Painel de Script, Painel de Comando|
|**Refazer**|CTRL+Y|Painel de Script, Painel de Comando|
|**Substituir no Script**|CTRL+H|Painel de Script|
|**Salvar**|CTRL+S|Painel de Script|
|**Selecionar Tudo**|CTRL+A|Painel de Script, Painel de Comando e Painel de Saída|
|**Mostrar Trechos de Código**|CTRL+J|Painel de Script, Painel de Comando|
|**Desfazer**|CTRL+Z|Painel de Script, Painel de Comando|

## Atalhos de teclado para execução de scripts
Você pode usar os seguintes atalhos de teclado ao executar scripts no Painel de Script.

|Ação|Atalho do Teclado|
|----------|---------------------|
|**Novo**|CTRL+N|
|**Abrir**|CTRL+O|
|**Executar**|F5|
|**Executar Seleção**|F8|
|**Parar Execução**|CTRL+BREAK. CTRL+C pode ser usado quando o contexto é ambíguo (quando não há nenhum texto selecionado).|
|**Tab** (para o próximo script)|CTRL+TAB **Observação:** Tab para o próximo script só funciona quando você tem uma única guia do Windows PowerShell aberta ou caso tenha mais de uma guia do Windows PowerShell aberta, mas o foco está no Painel de Script.|
|**Tab** (para o script anterior)|CTRL+SHIFT+TAB **Observação:** Tab para o script anterior só funciona quando você tem uma única guia do Windows PowerShell aberta ou caso tenha mais de uma guia do Windows PowerShell aberta, mas o foco está no Painel de Script.|

## Atalhos de teclado para personalizar a exibição
Você pode usar os seguintes atalhos de teclado ao personalizar a exibição no [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)]. Eles são acessíveis de todos os painéis no aplicativo.

|Ação|Atalho do Teclado|
|----------|---------------------|
|**Ir para Painel de Comando (v2) ou do Console (v3 e posterior)**|CTRL+D|
|**Ir para o Painel de Saída (v2)**|CTRL+SHIFT+O|
|**Ir para o Painel de Script**|CTRL+I|
|**Mostrar Painel de Script**|CTRL+R|
|**Ocultar Painel de Script**|CTRL+R|
|**Mover o Painel de Script para cima**|CTRL+1|
|**Mover o Painel de Script para a direita**|CTRL+2|
|**Maximizar o Painel de Script**|CTRL+3|
|**Ampliar**|CTRL+SINAL DE ADIÇÃO|
|**Reduzir**|CTRL+SINAL DE SUBTRAÇÃO|

## Atalhos de teclado para depuração de scripts
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
|**Continuar**|C|Painel de Console ao depurar um script|
|**Intervir**|S|Painel de Console ao depurar um script|
|**Contornar**|V|Painel de Console ao depurar um script|
|**Sair**|O|Painel de Console ao depurar um script|
|**Repetir Último Comando** (para Intervir ou Contornar)|ENTER|Painel de Console ao depurar um script|
|**Exibir Pilha de Chamadas**|K|Painel de Console ao depurar um script|
|**Parar Depuração**|Q|Painel de Console ao depurar um script|
|**Listar o Script**|L|Painel de Console ao depurar um script|
|**Exibir Comandos de Depuração do Console**|H ou ?|Painel de Console ao depurar um script|

## Atalhos do teclado para as guias do Windows PowerShell
Você pode usar os seguintes atalhos do teclado ao utilizar as guias do Windows PowerShell.

|Ação|Atalho do Teclado|
|----------|---------------------|
|**Fechar a guia do PowerShell**|CTRL+W|
|**Nova guia do PowerShell**|CTRL+T|
|**Guia anterior do PowerShell**|CTRL+SHIFT+TAB. Este atalho funciona somente quando nenhum arquivo estiver aberto em qualquer uma das guias do Windows PowerShell.|
|**Próxima guia do Windows PowerShell**|CTRL+TAB. Este atalho funciona somente quando nenhum arquivo estiver aberto em qualquer uma das guias do Windows PowerShell.|

## Atalhos de teclado para iniciar e sair
Você pode usar os seguintes atalhos de teclado para iniciar o console do Windows PowerShell (PowerShell.exe) ou para sair do [!INCLUDE[ise_2](../Token/ise_2_md.md)].

|Ação|Atalho do Teclado|
|----------|---------------------|
|**Sair**|ALT+F4|
|**Iniciar o PowerShell.exe** ([!INCLUDE[psconsole](../Token/psconsole_md.md)])|CTRL+SHIFT+P|

## Consulte Também
[PowerShell Magazine: a lista completa de atalhos de teclado do ISE do Windows PowerShell](http://www.powershellmagazine.com/2013/01/29/the-complete-list-of-powershell-ise-3-0-keyboard-shortcuts/)



<!--HONumber=Apr16_HO1-->


