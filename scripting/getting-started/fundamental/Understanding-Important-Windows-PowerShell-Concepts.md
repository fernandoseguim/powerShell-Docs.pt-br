---
title:  Compreendendo conceitos importantes do Windows PowerShell
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  3e601e38-4520-4578-a48d-b6779f1d35ee
---

# Compreendendo conceitos importantes do Windows PowerShell
O design do Windows PowerShell integra conceitos de muitos ambientes diferentes. Vários deles são familiares para aqueles com experiência em shells ou ambientes de programação específicos, mas poucos conhecerão todos. Examinar alguns desses conceitos fornece uma visão geral útil do shell.

### Comandos não são baseados em texto
Diferentemente dos comandos de interface de linha de comando tradicionais, os cmdlets do Windows PowerShell são projetados para lidar com informações estruturadas em objetos que são mais do que apenas uma cadeia de caracteres que aparecem na tela. A saída do comando sempre traz consigo informações extras que poderão ser usadas se você precisar delas. Abordaremos esse tópico com mais detalhes neste documento.

Se você tiver usado ferramentas de processamento de texto para processar dados de linha de comando anteriormente, verá que elas se comportarão de forma diferente se você tentar usá-las no Windows PowerShell. Na maioria dos casos, você não precisa de ferramentas de processamento de texto para extrair informações específicas. Você pode acessar partes dos dados diretamente usando comandos padrão de manipulação de objeto do Windows PowerShell.

### A família de comando é extensível
Interfaces como a do Cmd.exe não fornecem uma maneira de estender diretamente o conjunto de comandos internos. Você pode criar ferramentas de linha de comando externas que são executadas no Cmd.exe, mas essas ferramentas externas não têm serviços, como a integração da Ajuda, e o Cmd.exe não sabe automaticamente que eles são comandos válidos.

Os comandos de binário nativo no Windows PowerShell, conhecidos como *cmdlets* (pronunciado “command-lets”), podem ser aprimorados pelos cmdlets que você cria e adiciona ao Windows PowerShell usando snap-ins. Os *snap-ins* do Windows PowerShell são compilados da mesma maneira que ferramentas binárias em qualquer outra interface. Você pode usá-los para adicionar provedores do Windows PowerShell ao shell, bem como novos cmdlets.

Devido à natureza especial dos comandos internos do Windows PowerShell, eles serão chamados de *cmdlets*.

> [!NOTE]
> O Windows PowerShell pode executar outros comandos além de cmdlets. Não os abordaremos em detalhes no Guia do Usuário do Windows PowerShell, mas é úteis conhecê-los como categorias de tipos de comando. O Windows PowerShell dá suporte a scripts análogos aos scripts de shell do UNIX e a arquivos de lote do Cmd.exe, mas que têm uma extensão de nome de arquivo .ps1. O Windows PowerShell também permite criar funções internas que podem ser usadas diretamente na interface ou em scripts.

### O Windows PowerShell manipula a Exibição e a Entrada do Console
Quando você digita um comando, o Windows PowerShell sempre processa a linha de comando de entrada diretamente. O Windows PowerShell também formata a saída que você vê na tela. Isso é significativo porque reduz o trabalho necessário de cada cmdlet e garante que você pode sempre faça as coisas da mesma maneira, independentemente do cmdlet usado. Um exemplo de como isso simplifica a vida dos usuários e dos desenvolvedores de ferramentas é a Ajuda de linha de comando.

Ferramentas de linha de comando tradicionais têm seus próprios esquemas para solicitar e exibir a Ajuda. Algumas ferramentas de linha de comando usam **/?** para disparar a exibição da Ajuda; outras usam **\-?**, **\/H** ou até mesmo **\/\/**. Algumas delas exibem a Ajuda em uma janela GUI em vez de na exibição do console. Algumas ferramentas complexas, como atualizadores de aplicativos, descompactam arquivos internos antes de exibir a Ajuda. Se você usar o parâmetro errado, a ferramenta poderá ignorar o que você digitou e começar a executar uma tarefa automaticamente.

Quando você insere um comando no Windows PowerShell, tudo o que você insere é automaticamente analisado e pré-processado pelo Windows PowerShell. Se você usar o parâmetro **-?** com um cmdlet do Windows PowerShell, ele sempre significa "mostre-me a Ajuda para este comando". Os desenvolvedores de cmdlet não precisam analisar o comando, eles só precisam fornecer o texto de Ajuda.

É importante compreender que os recursos de Ajuda do Windows PowerShell estão disponíveis mesmo quando você executar ferramentas de linha de comando tradicionais no Windows PowerShell. O Windows PowerShell processa os parâmetros e passa os resultados para as ferramentas externas.

> [!NOTE]
> Se você executar um aplicativo gráfico no Windows PowerShell, a janela do aplicativo se abrirá. O Windows PowerShell intervém apenas quando a entrada da linha de comando que você forneceu ou a saída do aplicativo retornarem para a janela do console; ele não afeta a maneira como o aplicativo funciona internamente.

### O Windows PowerShell usa parte da sintaxe C#
O Windows PowerShell tem recursos de sintaxe e palavras-chave que são muito semelhantes àqueles usados na linguagem de programação C#, pois o Windows PowerShell é baseado no .NET Framework. Aprender a usar o Windows PowerShell tornará mais fácil aprender C# se você estiver interessado na linguagem.

Caso você não seja um programador de C#, essa semelhança não é importante. No entanto, se você já estiver familiarizado com C#, as semelhanças poderão facilitar muito o aprendizado do Windows PowerShell.



<!--HONumber=May16_HO2-->


