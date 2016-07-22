---
title: "O que há de novo no ISE do PowerShell 50"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 38648d47-7c27-4b37-a40e-ad29948519c2
translationtype: Human Translation
ms.sourcegitcommit: 5b978b9c939759bd47ee73d4f7ffa6e3a66df788
ms.openlocfilehash: ababa1b3ce913528a3ac7089d91ef74c5eb27737

---

# Novidades no ISE do Windows PowerShell
Este tópico explica os recursos novos e atualizados que foram introduzidos em versões do ISE (Ambiente de Script Integrado) do Windows PowerShell®.

## <a name="overview"></a>Descrição do recurso
O ISE do Windows PowerShell é um aplicativo host que permite gravar, executar e testar scripts e módulos em um ambiente gráfico e intuitivo. Recursos importantes como coloração de sintaxe, preenchimento de guias, depuração visual, conformidade com Unicode e Ajuda contextual permitem uma experiência avançada de script.

Para ter uma visão geral do ISE do Windows PowerShell, consulte [Visão geral do Ambiente de Script Integrado do Windows PowerShell](https://technet.microsoft.com/en-us/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).

## <a name="versions"></a>Funcionalidades novas e alteradas no ISE do Windows PowerShell
A tabela a seguir lista os recursos novos e alterados para esta versão do ISE do Windows PowerShell no Windows PowerShell.

|Recurso/funcionalidade|ISE do Windows PowerShell 4.0|ISE do Windows PowerShell 3.0|ISE do Windows PowerShell 2.0|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|**[IntelliSense](#BKMK_Intellisense)**|X|X||
|**[Trechos de código](#bkmk_snippets)**|X|X||
|**[Ferramentas complementares](#BKMK_AddOnTools)**|X|X||
|**[Gerenciador de Reinicialização e Salvamento Automático](#BKMK_RestartMgr)**|X|X||
|**[Painel de Console](#BKMK_ConsolePane)**|X|X||
|**[Lista de recém-usados](#BKMK_MRU)**|X|X||
|**[Opções de linha de comando](#BKMK_CommandLine)**|X|X||
|**[Novos recursos do editor](#BKMK_NewEditorFeatures)**|X|X||
|**[Janela do novo visualizador da ajuda](#BKMK_NewHelpViewer)**|X|X||
|**[Cmdlet Show-Command](#BKMK_ShowCommand)**|X|X||

### <a name="BKMK_Intellisense"></a>IntelliSense
**Adicionado no ISE 3.0**

O IntelliSense é um recurso de assistência de preenchimento automático que faz parte do ISE do Windows PowerShell. O IntelliSense exibe menus clicáveis dos cmdlets, parâmetros, valores de parâmetro, arquivos ou pastas potencialmente correspondentes conforme você digita.

**Qual é o valor agregado desta alteração?**

Com a adição do IntelliSense, ficou mais fácil de descobrir cmdlets e sintaxe ao usar o ISE do Windows PowerShell para criar scripts. Você também pode usar o ISE do Windows PowerShell para conhecer o Windows PowerShell enquanto cria novos scripts.

**O que passou a funcionar de maneira diferente?**

Quando você digita cmdlets no ISE do Windows PowerShell 3.0 ou posterior, um menu rolável e clicável é exibido, permitindo que você navegue e selecione os comandos apropriados.

### <a name="BKMK_Snippets"></a>Trechos de código
**Adicionado no ISE 3.0**

*Trechos de código* são sessões de código Windows PowerShell curtas que você pode inserir nos scritps que cria no ISE do Windows PowerShell. O ISE do Windows PowerShell vem com um conjunto padrão de trechos de código. Você pode adicionar trechos de código usando o cmdlet **New-Snippet** enquanto trabalha no ISE do Windows PowerShell.

**Qual é o valor agregado desta alteração?**

Usando trechos de código, você pode montar e criar scripts para automatizar seu ambiente rapidamente.

**O que passou a funcionar de maneira diferente?**

Para usar trechos de código no Windows PowerShell 3.0 ou posterior, no menu **Editar**, clique em **Iniciar Trechos de Código** ou pressione **Ctrl-J**.

### <a name="BKMK_AddOnTools"></a>Ferramentas complementares
**Adicionado no PowerShell 3.0**

O ISE do Windows PowerShell agora dá suporte para ferramentas complementares, que são controles do WPF (Windows Presentation Foundation) que são adicionados usando o modelo de objeto. As ferramentas complementares podem ser exibidas como um painel vertical ou horizontal no console. Várias ferramentas complementares em um painel são exibidas como um controle com guias. Você também pode adicionar ou remover ferramentas complementares produzidas por terceiros. Para obter mais informações sobre como importar ou remover ferramentas complementares, confira [Windows PowerShell ISE Operations](http://technet.microsoft.com/library/cc732148.aspx) (Operações do ISE do Windows PowerShell).

**Qual é o valor agregado desta alteração?**

Os complementos permitem estender e personalizar o ISE do Windows PowerShell com ferramentas que podem melhorar sua experiência com scripts ou adicionar funcionalidades ao ISE do Windows PowerShell.

**O que passou a funcionar de maneira diferente?**

O ISE do Windows PowerShell 3.0 e posterior vêm com o complemento **Comandos**. O complemento **Comandos** permite que você procure cmdlets e acesse a Ajuda para os cmdlets lado a lado com os Painéis de **Script** e **Console**.

Complementos adicionais podem ser encontrados usando o comando **Abrir o Site de Ferramentas Complementares** no menu **Complementos**.

### <a name="BKMK_RestartMgr"></a>Gerenciador de Reinicialização e Salvamento Automático
**Adicionado no PowerShell 3.0**

O ISE do Windows PowerShell agora salva automaticamente os scripts abertos a cada dois minutos em uma localização separada.  Se o ISE do Windows PowerShell parar de funcionar ou o sistema operacional for reiniciado, depois do ISE do Windows PowerShell reiniciar, ele recuperará os scripts que estavam abertos na última sessão, mesmo que eles não tenham sido salvos.

Para alterar o intervalo de salvamento automático, execute o seguinte comando no painel de console: **$psise.Options.AutoSaveMinuteInterval**.

**Qual é o valor agregado desta alteração?**

Agora você pode trabalhar no ISE do Windows PowerShell sabendo que os scripts abertos são salvos automaticamente em caso de uma reinicialização inesperada.

**O que passou a funcionar de maneira diferente?**

O ISE do Windows PowerShell 2.0 não salva os scripts automaticamente em caso de reinicialização.

### <a name="BKMK_MRU"></a>Lista de recém-usados
**Adicionado no PowerShell 3.0**

O ISE do Windows PowerShell agora tem uma lista de arquivos recém-usados. Quando você abre um arquivo no ISE do Windows PowerShell, ele é adicionado à lista de recém-usados no menu **Arquivo**.

Para alterar o número padrão de arquivos na lista de recém-usados, execute o seguinte comando no Painel de Console: **$psise.Options.MruCount**.

**Qual é o valor agregado desta alteração?**

Agora você pode usar a lista de recém-usados para acessar facilmente os arquivos usados frequentemente.

**O que passou a funcionar de maneira diferente?**

O ISE do Windows PowerShell 2.0 não tem uma lista de recém-usados.

### <a name="BKMK_ConsolePane"></a>Painel de Console
**Adicionado no PowerShell 3.0**

Os Painéis de Comando e Saída separados que estavam disponíveis na primeira versão do ISE do Windows PowerShell foram combinados em um Painel de Console único. O Painel de Console é semelhante, em termos de função e aparência, a um console típico do Windows PowerShell, mas ele inclui as melhorias a seguir (a maioria delas é descrita neste tópico).

-   Cores de sintaxe para texto de entrada (não para texto de saída), incluindo sintaxe XML

-   IntelliSense

-   Correspondência de chaves

-   Indicação de erros

-   Suporte total a Unicode

-   Ajuda contextual com **F1**

-   Show-Command contextual com **Ctrl+F1**

-   Suporte a scripts complexos e leitura da direita para a esquerda

-   Suporte a fontes

-   Zoom

-   Modos de seleção de linha e seleção de blocos

-   Preservação do conteúdo digitado na linha de comando quando você pressiona a seta **para cima** para exibir o histórico no console

**Qual é o valor agregado desta alteração?**

A adição dessas alterações do Painel de Console fornece uma experiência de script que é mais consistente com a interface do console.

**O que passou a funcionar de maneira diferente?**

O ISE do Windows PowerShell 2.0 tem Painéis de Comando e de Saída separados.

### <a name="BKMK_CommandLine"></a>Opções de linha de comando
**Adicionado no PowerShell 3.0**

Se você iniciar o ISE do Windows PowerShell com a linha de comando (digitando **powershell_ise.exe**), será possível adicionar as novas opções de linha de comando a seguir.

-   *-NoProfile*: inicia o ISE do Windows PowerShell sem executar **$profile**

-   *-Help*: exibe uma janela de Ajuda

-   *-mta*: inicia o ISE do Windows PowerShell no modo Multi-Threaded Apartment. O modo de operação padrão para o ISE do Windows PowerShell é o modo Single-Threaded Apartment ou *-STA*.

**Qual é o valor agregado desta alteração?**

A adição dessas opções de linha de comando permite controlar o ambiente no qual o ISE do Windows PowerShell é executado.

**O que passou a funcionar de maneira diferente?**

O ISE do Windows PowerShell 2.0 não reconhece essas opções de linha de comando.

### <a name="BKMK_NewEditorFeatures"></a>Novos recursos do editor
**Adicionado no PowerShell 3.0**

Outros recursos de edição do ISE do Windows PowerShell incluem:

-   **Cores de sintaxe de XML**Agora o ISE do Windows PowerShell tem sintaxe XML colorida da mesma maneira que a sintaxe colorida do Windows PowerShell.

-   **Correspondência de chaves** O ISE do Windows PowerShell inclui o realce e a correspondência de chaves e pode ser usado das seguintes maneiras: (por exemplo, o uso do comando **Ir para Correspondência** ou **Ctrl + ]** localizará a chave de fechamento, se você tiver selecionado uma chave de abertura).

-   **Exibição de estrutura de tópicos** O Painel de Script dá suporte à exibição das estruturas de tópicos, que permitem recolher ou expandir seções de códigos com cliques nos sinais de adição ou subtração na margem esquerda. Você pode usar chaves ou as marcas **#region** e **#endregion** para marcar o início ou o final de uma seção recolhível. Para expandir ou recolher todas as regiões, pressione **Ctrl + M**.

-   **Edição de texto com arrastar e soltar**O ISE do Windows PowerShell agora dá suporte à edição de texto com arrasta e soltar. Você pode selecionar qualquer bloco de texto e arrastar o texto para outro local no editor ou no console para mover o texto. Se você mantiver pressionada a tecla Ctrl enquanto arrasta o texto selecionado, quando soltar o botão do mouse, o texto será copiado para o novo local. Nesta versão do ISE do Windows PowerShell, bem como sua versão anterior, quando você arrasta e solta arquivos no ISE do Windows PowerShell, ele abre o arquivo.

-   **Analisar a exibição de erro** Erros de análise são indicados com um sublinhado vermelho. Quando você passa o cursor sobre um erro indicado, o texto da dica de ferramenta exibe o problema encontrado no código.

-   **Zoom** É possível definir o percentual de zoom do conteúdo do console usando o controle deslizante de zoom (no canto inferior direito da janela do ISE do Windows PowerShell) ou digitando o comando **$psise.options.Zoom** no Painel de Console.

-   **Copiar e colar rich text** A cópia para a área de transferência no ISE do Windows PowerShell preserva as informações de fonte, tamanho e cor da seleção original.

-   **Seleção de bloco** Você pode selecionar um bloco de texto mantendo a tecla ALT pressionada enquanto seleciona o texto no Painel de Script com o mouse ou pressionando **Alt+Shift+Seta**.

**Qual é o valor agregado desta alteração?**

Os recursos de edição adicionais fornecem um ambiente de edição mais consistente e eficiente.

**O que passou a funcionar de maneira diferente?**

Esses aprimoramentos na edição não estavam presentes no ISE do Windows PowerShell 2.0.

### <a name="BKMK_NewHelpViewer"></a>Janela do novo visualizador da ajuda
**Adicionado no PowerShell 3.0**

Se você pressionar **F1** quando o cursor estiver em um cmdlet ou se parte de um cmdlet estiver realçada, o novo visualizador da Ajuda abrirá uma ajuda contextual sobre o cmdlet realçado. Para exibir a ajuda conceitual do Windows PowerShell, digite **operators** no painel de console e pressione **F1**.

Antes de usar este recurso, baixe a versão mais atual dos tópicos de ajuda do Windows PowerShell do site da Microsoft. O método mais simples para baixar os tópicos da Ajuda é executar o cmdlet **Update-Help** no Painel de Console durante a execução do ISE do Windows PowerShell como administrador.

Você pode alterar onde a tecla **F1** busca Ajuda. No menu **Ferramentas**/**Opções**, na guia **Configurações Gerais** em **Outras Configurações**, você pode marcar ou desmarcar a caixa de seleção **Usar conteúdo da ajuda local em vez de conteúdo online**. Se estiver selecionado, o cliente procurará o cmdlet Help na Ajuda baixada encontrada na pasta de módulos.  Se a caixa de seleção estiver desmarcada, o cliente procurará na Biblioteca do TechNet para obter a Ajuda do cmdlet.

**Qual é o valor agregado desta alteração?**

A ajuda contextual sem deixar seu cmdlet ou script atual fornece uma experiência de aprendizado contínuo.

**O que passou a funcionar de maneira diferente?**

Pressionar o F1 em versões anteriores do ISE do Windows PowerShell abria o arquivo de ajuda no computador local. No ISE do Windows PowerShell 3.0 e posterior, é aberta uma janela que contém a ajuda para o cmdlet que é configurável e pesquisável. Essa experiência da ajuda é uma novidade no ISE do Windows PowerShell 3.0 e a Ajuda Atualizável é uma novidade no Windows PowerShell 3.0.

### <a name="BKMK_ShowCommand"></a>Cmdlet Show-Command
**Adicionado no PowerShell 3.0**

O cmdlet **Show-Command** permite compor ou executar um cmdlet ou função preenchendo um formulário gráfico. O formulário permite que os usuários trabalhem com o Windows PowerShell em um ambiente gráfico. **Show-Command** também permite que os desenvolvedores de scripts avançados criem rapidamente uma GUI baseada no Windows PowerShell.

**Qual é o valor agregado desta alteração?**

Usando **Show-Command** em seus scripts do Windows PowerShell, você pode fornecer aos usuários o ambiente gráfico com o qual eles estão familiarizados. **Show-Command** também pode ajudar os usuários iniciantes a aprender sobre o Windows PowerShell.

**O que passou a funcionar de maneira diferente?**

O Show-Command é uma novidade no ISE do Windows PowerShell 3.0.

## <a name="BKMK_LINKS"></a>Consulte também
Para mais informações sobre o ISE do Windows PowerShell no Windows PowerShell, consulte os links a seguir.

-   [Usando o Ambiente de Script Integrado do Windows PowerShell](../core-powershell/ise/Using-the-Windows-PowerShell-ISE.md)

-   [ISE no TechNet Wiki](http://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)

-   [Central de Scripts](http://technet.microsoft.com/scriptcenter/default)




<!--HONumber=Jul16_HO2-->


