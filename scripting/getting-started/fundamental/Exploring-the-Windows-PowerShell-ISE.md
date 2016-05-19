---
title: Explorando o ISE do Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e0d2c6e8-5126-40e7-a1e1-d1cff29fe94a
---
# Explorando o ISE do Windows PowerShell
Você pode usar o ISE (Ambiente de Script Integrado) do Windows PowerShell® para criar, executar e depurar scripts e comandos. O ISE do Windows PowerShell é composto por uma barra de menus, guias do Windows PowerShell, a barra de ferramentas, guias de script, um Painel de Script, um Painel de Console, uma barra de status, um controle deslizante de tamanho de texto e a Ajuda contextual.

> [!NOTE]
> No ISE do Windows PowerShell 3.0 os Painéis de Comando e de Saída foram combinados em um único Painel de Console.

## Barra de menu
A barra de menus contém os menus **Arquivo**, **Editar**, **Exibir**, **Ferramentas**, **Depurar**, **Complementos** e **Ajuda**. Os botões nos menus permitem executar tarefas relacionadas à escrita e execução de scripts e execução de comandos no ISE do Windows PowerShell. Além disso, uma [ferramenta complementar](../../core-powershell/ise/The-ISEAddOnTool-Object.md) pode ser colocada na barra de menus executando os scripts que usam o [Modelo de Objeto de Script do ISE do Windows PowerShell](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md).

> [!NOTE]
> No ISE do Windows PowerShell 2.0, os menus **Ferramentas** e **Complementos** não existiam.

## Guias do Windows PowerShell
Uma guia do Windows PowerShell é o ambiente em que um script do Windows PowerShell é executado. Você pode abrir novas guias do Windows PowerShell no ISE do Windows PowerShell para criar ambientes separados em seu computador local ou em computadores remotos. Você pode ter um máximo de oito guias do PowerShell abertas simultaneamente.

## Barra de ferramentas
Os seguintes botões estão localizados na barra de ferramentas.

|Botão|Função|
|----------|------------|
|**Novo**|Abre um novo script.|
|**Abrir**|Abre um arquivo ou um script existente.|
|**Salvar**|Salva um script ou um arquivo.|
|**Recortar**|Recorta o texto selecionado e o copia para a área de transferência.|
|**Cópia**|Copia o texto selecionado para a área de transferência.|
|**Colar**|Cola o conteúdo da área de transferência na posição do cursor.|
|**Limpar o Painel de Saída**|Limpa todo o conteúdo no Painel de Saída.|
|**Desfazer**|Reverte a ação que acabou de ser executada.|
|**Refazer**|Realiza a ação que acabou de ser desfeita.|
|**Executar Script**|Executa um script.|
|**Executar a Seleção**|Executa uma parte selecionada de um script.|
|**Parar Execução**|Interrompe um script que está em execução.|
|**Nova Guia Remota do PowerShell**|Cria uma nova Guia do PowerShell que estabelece uma sessão em um computador remoto. Uma caixa de diálogo é exibida e solicita que você insira os detalhes necessários para estabelecer a conexão remota.|
|**Inicia o PowerShell.exe**|Abre o Console do Windows PowerShell.|
|**Mostrar o Painel de Script na Parte Superior**|Move o Painel de Script para cima na exibição.|
|**Mostrar o Painel de Script à Direita**|Move o Painel de Script para a direita na exibição.|
|**Mostrar o Painel de Script Maximizado**|Maximiza o Painel de Script.|

## Guia de Script
Exibe o nome do script que você está editando. Você pode clicar em uma guia de script para selecionar o script que deseja editar.

Ao apontar para a guia do script, o caminho totalmente qualificado para o arquivo de script é exibido em uma dica de ferramenta.

## Painel de Script
Permite criar e executar scripts. Você pode abrir, editar e executar scripts existentes no Painel de Script.

## Painel de Saída
Exibe os resultados dos comandos e scripts executados por você. Você também pode copiar e limpar o conteúdo do Painel de Saída.

## Painel de Comando
Permite gravar comandos. Você pode executar um comando de uma ou várias linhas no Painel de Comando. Pressione SHIFT+ENTER para inserir cada linha de comando de várias linhas e pressione ENTER após a última linha para executá-lo. O prompt exibido na parte superior do Painel de Comando mostra o caminho para o diretório de trabalho atual.

## Barra de Status
Permite que você veja se os comandos e scripts que você executou foram concluídos. A barra de status localiza-se na parte mais inferior da tela. Partes selecionadas de mensagens de erro são exibidas na barra de status.

## Controle deslizante de tamanho de texto
Aumenta ou diminui o tamanho do texto na tela.

## Ajuda
A Ajuda para o ISE do Windows PowerShell está disponível na Web na Biblioteca do TechNet. Você pode abrir a Ajuda clicando em **Ajuda do ISE do Windows PowerShell** no menu **Ajuda** ou pressionando a tecla F1 em qualquer lugar, exceto quando o cursor estiver em um nome de cmdlet no Painel de Script ou no Painel de Console. No menu **Ajuda**, você também pode executar o cmdlet Uptade-Help e exibir a Janela Comando que auxilia na construção de comandos, mostrando todos os parâmetros para um cmdlet e permitindo preencher os parâmetros em um formulário de fácil utilização.

## Consulte Também
[Usando o ISE do Windows PowerShell](../../core-powershell/ise/Using-the-Windows-PowerShell-ISE.md)


<!--HONumber=May16_HO2-->


