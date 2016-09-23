---
title: Atalhos do teclado para o ISE do Windows PowerShell
ms.date: 2016-05-11
keywords: PowerShell, cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 8328b946-0f02-4ef4-ac28-2743a1b4043b
translationtype: Human Translation
ms.sourcegitcommit: 466b7169b81d773cc226adbf853b46fdb956c2f1
ms.openlocfilehash: 852b927ba0f5edffa5c7943b45e0e7b1bdd273f5

---

# Atalhos do teclado para o ISE do Windows PowerShell
Use os atalhos de teclado a seguir para executar ações no ISE (Ambiente de Script Integrado) do Windows PowerShell®. O ISE do Windows PowerShell está disponível como parte dos sistemas operacionais cliente Windows Server e Windows, mas também pode ser instalado em alguns sistemas operacionais Windows mais antigos como parte do [pacote de download do Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881).

## Atalhos de teclado para edição de texto
Você pode usar os seguintes atalhos de teclado ao editar texto.

|Ação|Atalhos do teclado|Usar em|
|----------|----------------------|----------|
|**Ajuda**|F1|Painel de Script **Importante:** você pode especificar que a Ajuda com F1 venha da Biblioteca do TechNet na Web ou da Ajuda baixada (veja Update-Help). Para selecionar, clique em **Ferramentas**, **Opções** e, na guia **Configurações Gerais**, defina ou apague **Usar conteúdo da Ajuda local em vez do conteúdo online.**|
|**Cópia**|Ctrl+C|Painel de Script, Painel de Comando e Painel de Saída|
|**Recortar**|Ctrl+X|Painel de Script, Painel de Comando|
|**Expandir ou Recolher a Estrutura de Tópicos**|Ctrl+M|Painel de Script|
|**Localizar no Script**|Ctrl+F|Painel de Script|
|**Localizar Próximo no Script**|F3|Painel de Script|
|**Localizar Anterior no Script**|Shift+F3|Painel de Script|
|**Localizar Chave Correspondente**|Ctrl+]|Painel de Script|
|**Colar**|Ctrl+V|Painel de Script, Painel de Comando|
|**Refazer**|Ctrl+Y|Painel de Script, Painel de Comando|
|**Substituir no Script**|Ctrl+H|Painel de Script|
|**Salvar**|Ctrl+S|Painel de Script|
|**Selecionar Tudo**|Ctrl+A|Painel de Script, Painel de Comando e Painel de Saída|
|**Mostrar Trechos de Código**|Ctrl+J|Painel de Script, Painel de Comando|
|**Desfazer**|Ctrl+Z|Painel de Script, Painel de Comando|

## Atalhos de teclado para execução de scripts
Você pode usar os seguintes atalhos de teclado ao executar scripts no Painel de Script.

|Ação|Atalho do Teclado|
|----------|---------------------|
|**Novo**|Ctrl+N|
|**Abrir**|Ctrl+O|
|**Executar**|F5|
|**Executar Seleção**|F8|
|**Parar Execução**|Ctrl+Break. Ctrl+C pode ser usado quando o contexto é ambíguo (quando não há texto selecionado).|
|**Tab** (para o próximo script)|Ctrl+Tab **Observação:** Tab para o próximo script só funciona quando você tem uma única guia do Windows PowerShell aberta ou caso tenha mais de uma guia do Windows PowerShell aberta, mas o foco está no Painel de Script.|
|**Tab** (para o script anterior)|Ctrl+Shift+Tab **Observação:** Tab para o script anterior só funciona quando você tem uma única guia do Windows PowerShell aberta ou caso tenha mais de uma guia do Windows PowerShell aberta, mas o foco está no Painel de Script.|

## Atalhos de teclado para personalizar a exibição
Você pode usar os seguintes atalhos de teclado para personalizar a exibição no ISE do Windows PowerShell. Eles são acessíveis de todos os painéis no aplicativo.

|Ação|Atalho do Teclado|
|----------|---------------------|
|**Ir para Painel de Comando (v2) ou do Console (v3 e posterior)**|Ctrl+D|
|**Ir para o Painel de Saída (v2)**|Ctrl+Shift+O|
|**Ir para o Painel de Script**|Ctrl+I|
|**Mostrar Painel de Script**|Ctrl+R|
|**Ocultar Painel de Script**|Ctrl+R|
|**Mover o Painel de Script para cima**|Ctrl+1|
|**Mover o Painel de Script para a direita**|Ctrl+2|
|**Maximizar o Painel de Script**|Ctrl+3|
|**Ampliar**|Ctrl+Sinal de adição|
|**Reduzir**|Ctrl+Sinal de subtração|

## Atalhos de teclado para depuração de scripts
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
> Você também pode usar os atalhos de teclado projetados para o console do Windows PowerShell ao depurar scripts no ISE do Windows PowerShell. Para usar esses atalhos, você deve digitar o atalho no Painel de Comando e pressionar Enter.

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

## Atalhos do teclado para as guias do Windows PowerShell
Você pode usar os seguintes atalhos do teclado ao utilizar as guias do Windows PowerShell.

|Ação|Atalho do Teclado|
|----------|---------------------|
|**Fechar a guia do PowerShell**|Ctrl+W|
|**Nova guia do PowerShell**|Ctrl+T|
|**Guia anterior do PowerShell**|Ctrl+Shift+Tab. Este atalho funciona somente quando nenhum arquivo estiver aberto em qualquer uma das guias do Windows PowerShell.|
|**Próxima guia do Windows PowerShell**|Ctrl+Tab. Este atalho funciona somente quando nenhum arquivo estiver aberto em qualquer uma das guias do Windows PowerShell.|

## Atalhos de teclado para iniciar e sair
Você pode usar os seguintes atalhos de teclado para iniciar o console do Windows PowerShell (PowerShell.exe) ou para sair do ISE do Windows PowerShell.

|Ação|Atalho do Teclado|
|----------|---------------------|
|**Sair**|Alt+F4|
|**Iniciar o PowerShell.exe** (console do Windows PowerShell)|Ctrl+Shift+P|

## Consulte Também
[PowerShell Magazine: a lista completa de atalhos de teclado do ISE do Windows PowerShell](http://www.powershellmagazine.com/2013/01/29/the-complete-list-of-powershell-ise-3-0-keyboard-shortcuts/)




<!--HONumber=Sep16_HO3-->


