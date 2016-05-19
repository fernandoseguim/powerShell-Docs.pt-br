---
title: Objetivo do modelo de objeto de script do ISE do Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d176a131-ab0c-43ee-80c1-f824ab8e4a05
---
# Objetivo do modelo de objeto de script do ISE do Windows PowerShell
  Objetos são associados com a forma e a função do ISE (Ambiente de Script Integrado) do Windows PowerShell. A referência de modelo de objeto fornece detalhes sobre as propriedades e os métodos de membros que esses objetos expõem. Exemplos são fornecidos para mostrar como você pode usar scripts para acessar diretamente esses métodos e propriedades. O modelo de objeto de script facilita a gama de tarefas a seguir.

## Personalizando a aparência do ISE do Windows PowerShell
 Você pode usar o modelo de objeto para modificar as configurações e opções do aplicativo. Por exemplo, você pode modificá-las da seguinte forma:

-   Você pode mudar a cor de erros, avisos, saídas detalhadas e saídas de depuração.

-   Você pode obter ou definir cores de tela de fundo para o painel de Comando, painel de Saída e o painel de Script.

-   Você pode definir a cor de primeiro plano para o painel de Saída.

-   Você pode definir o nome e tamanho da fonte para o ISE do Windows PowerShell.

-   Você pode configurar alertas. Essa configuração inclui advertências que são emitidas quando um arquivo é aberto em várias guias do PowerShell ou quando um script no arquivo é executado antes que o arquivo seja salvo.

-   Você pode alternar entre uma exibição em que o painel de Script e painel de Saída estão lado em uma exibição em que o painel Script está na parte superior do painel de Saída. Você pode encaixar o painel de Comando na parte inferior ou superior do painel de Saída.

## Melhorando a funcionalidade do ISE do Windows PowerShell
 Você pode usar o modelo de objeto para melhorar a funcionalidade do ISE do Windows PowerShell. Por exemplo, você pode:

-   Adicionar e modificar a instância do próprio ISE do Windows PowerShell. Por exemplo, para alterar os menus, você pode adicionar novos itens de menu e mapear os novos itens de menu para os scripts.

-   Crie scripts que realizam algumas das tarefas que podem ser executadas usando os comandos de menu e botões no ISE do Windows PowerShell. Por exemplo, você pode adicionar, remover ou selecionar uma guia PowerShell.

-   Complemente tarefas que podem ser realizadas usando comandos e botões de menu. Por exemplo, você pode renomear uma guia do PowerShell.

-   Manipule buffers de texto para os painéis de Comando, Saída e Script associados a um arquivo. Por exemplo, você pode:

    -   Obtenha ou defina todo o texto.

    -   Obtenha ou defina uma seleção de texto.

    -   Execute um script ou uma parte selecionada de um script.

    -   Role uma linha até uma exibição.

    -   Insira texto em uma posição de cursor.

    -   Selecione um bloco de texto.

    -   Obtenha o último número de linha.

-   Execute operações de arquivo. Por exemplo, você pode:

    -   Abrir um arquivo, salvar um arquivo ou salvar um arquivo usando um nome diferente.

    -   Determine se um arquivo foi alterado depois que foi salvo pela última vez.

    -   Obtenha o nome do arquivo.

    -   Selecione um arquivo.

## Automatizando tarefas
 Você pode usar o modelo de objeto de script para criar atalhos de teclado para operações frequentes.

## Consulte Também
 [A hierarquia de modelo do objeto do ISE](The-ISE-Object-Model-Hierarchy.md) 
 [Referência de modelo de objeto do ISE do Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [O modelo de objeto de script do ISE do Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  


<!--HONumber=May16_HO2-->


