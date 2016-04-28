---
title: Novidades no ISE do Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 38648d47-7c27-4b37-a40e-ad29948519c2
---
# Novidades no ISE do Windows PowerShell
Este tópico explica os recursos novos e atualizados que foram introduzidos em versões do [!INCLUDE[ise_1](../Token/ise_1_md.md)].

## <a name="overview"></a>Descrição do recurso
O [!INCLUDE[ise_2](../Token/ise_2_md.md)] é um aplicativo host que permite gravar, executar e testar scripts e módulos em um ambiente gráfico e intuitivo. Recursos importantes como cores de sintaxe, preenchimento com Tab, depuração visual, conformidade com Unicode e Ajuda contextual proporcionam uma experiência avançada de script.

Para ter uma visão geral do [!INCLUDE[ise_2](../Token/ise_2_md.md)], consulte [Visão Geral do Ambiente de Script Integrado do Windows PowerShell](assetId:///3c1892c2-bf84-4cb6-af26-1f453be9e671).

## <a name="versions"></a>Funcionalidades novas e alteradas no ISE do Windows PowerShell
A tabela a seguir lista os recursos novos e alterados para esta versão do [!INCLUDE[ise_2](../Token/ise_2_md.md)] em [!INCLUDE[wps_2](../Token/wps_2_md.md)].

|Recurso/funcionalidade|[!INCLUDE[ise_2](../Token/ise_2_md.md)] 4.0|[!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0|[!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|**[Intellisense](#BKMK_Intellisense)**|X|X||
|**[Trechos de código](#bkmk_snippets)**|X|X||
|**[Ferramentas complementares](#BKMK_AddOnTools)**|X|X||
|**[Gerenciador de Reinicialização e Salvamento Automático](#BKMK_RestartMgr)**|X|X||
|**[Painel de console](#BKMK_ConsolePane)**|X|X||
|**[Lista de recém-usados](#BKMK_MRU)**|X|X||
|**[Opções de linha de comando](#BKMK_CommandLine)**|X|X||
|**[Novos recursos do editor](#BKMK_NewEditorFeatures)**|X|X||
|**[Janela do novo visualizador da ajuda](#BKMK_NewHelpViewer)**|X|X||
|**[Cmdlet Show-Command](#BKMK_ShowCommand)**|X|X||

### <a name="BKMK_Intellisense"></a>Intellisense
**Adicionado no ISE 3.0**

O IntelliSense é um recurso de assistência de preenchimento automático que faz parte do [!INCLUDE[ise_2](../Token/ise_2_md.md)]. O Intellisense exibe menus clicáveis dos cmdlets, parâmetros, valores de parâmetro, arquivos ou pastas potencialmente correspondentes conforme você digita.

**Qual é o valor agregado desta alteração?**

Com a adição do Intellisense, ficou mais fácil de descobrir cmdlets e sintaxe ao usar o [!INCLUDE[ise_2](../Token/ise_2_md.md)] para criar scripts. Você também pode usar o [!INCLUDE[ise_2](../Token/ise_2_md.md)] para aprender a usar o [!INCLUDE[wps_2](../Token/wps_2_md.md)] ao criar novos scripts.

**O que passou a funcionar de maneira diferente?**

Quando você digita cmdlets no [!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0 ou posterior, um menu arrastável e clicável é exibido, permitindo que você navegue e selecione os comandos apropriados.

### <a name="BKMK_Snippets"></a>Trechos de código
**Adicionado no ISE 3.0**

*Trechos de código* são sessões de código [!INCLUDE[wps_2](../Token/wps_2_md.md)] curtas que você pode inserir facilmente nos scritps que cria no [!INCLUDE[ise_2](../Token/ise_2_md.md)]. O [!INCLUDE[ise_2](../Token/ise_2_md.md)] vem com um conjunto padrão de trechos de código. Você pode adicionar trechos de código usando o cmdlet **New-Snippet** cmdlet enquanto trabalha no [!INCLUDE[ise_2](../Token/ise_2_md.md)].

**Qual é o valor agregado desta alteração?**

Usando trechos de código, você pode montar e criar scripts para automatizar seu ambiente rapidamente.

**O que passou a funcionar de maneira diferente?**

Para usar trechos de código no [!INCLUDE[wps_2](../Token/wps_2_md.md)] 3.0 ou posterior, no menu **Editar**, clique em **Iniciar Trechos de Código** ou pressione **Ctrl-J**.

### <a name="BKMK_AddOnTools"></a>Ferramentas complementares
**Adicionado no PowerShell 3.0**

O [!INCLUDE[ise_2](../Token/ise_2_md.md)] agora dá suporte a ferramentas complementares, que são controles do WPF (Windows Presentation Foundation) que são adicionados usando o modelo de objeto. As ferramentas complementares podem ser exibidas como um painel vertical ou horizontal no console. Várias ferramentas complementares em um painel são exibidas como um controle com guias. Você também pode adicionar ou remover ferramentas complementares produzidas por terceiros. Para saber mais sobre como importar ou remover ferramentas complementares, consulte [Operações do ISE do Windows PowerShell](http://technet.microsoft.com/library/cc732148.aspx).

**Qual é o valor agregado desta alteração?**

Complementos permitem estender e personalizar o [!INCLUDE[ise_2](../Token/ise_2_md.md)] com ferramentas que podem melhorar sua experiência com scripts ou agregar funcionalidades ao [!INCLUDE[ise_2](../Token/ise_2_md.md)].

**O que passou a funcionar de maneira diferente?**

O [!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0 e posterior vêm com o complemento **Commands**. O complemento **Commands** permite que você procure cmdlets e acesse a Ajuda para os cmdlets lado a lado com os painéis de **Script** e **Console**.

Complementos adicionais podem ser encontrados usando o comando **Open Add-on Tools Website** no menu **Complementos**.

### <a name="BKMK_RestartMgr"></a>Gerenciador de reinicialização e salvamento automático
**Adicionado no PowerShell 3.0**

O [!INCLUDE[ise_2](../Token/ise_2_md.md)] agora salva automaticamente os scripts abertos a cada dois minutos em um local separado.  Se o [!INCLUDE[ise_2](../Token/ise_2_md.md)] parar de funcionar ou o sistema operacional for reiniciado, depois de o [!INCLUDE[ise_2](../Token/ise_2_md.md)] reiniciar, ele recuperará os scripts que estavam abertos na última sessão, mesmo que eles não tenham sido salvos.

Para alterar o intervalo de salvamento automático, execute o seguinte comando no painel de console: **$psise.Options.AutoSaveMinuteInterval**.

**Qual é o valor agregado desta alteração?**

Agora você pode trabalhar no [!INCLUDE[ise_2](../Token/ise_2_md.md)] sabendo que os scripts abertos são salvos automaticamente em caso de uma reinicialização inesperada.

**O que passou a funcionar de maneira diferente?**

O [!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0 não salva os scripts automaticamente em caso de reinicialização.

### <a name="BKMK_MRU"></a>Lista de recém-usados
**Adicionado no PowerShell 3.0**

O [!INCLUDE[ise_2](../Token/ise_2_md.md)] agora tem uma lista de arquivos recém-usados. Quando você abre um arquivo no [!INCLUDE[ise_2](../Token/ise_2_md.md)], ele é adicionado à lista de recém-usados no menu **Arquivo**.

Para alterar o número padrão de arquivos na lista usada de recém-usados, execute o seguinte comando no painel de console: **$psise.Options.MruCount**.

**Qual é o valor agregado desta alteração?**

Agora você pode usar a lista de recém-usados para acessar facilmente os arquivos usados frequentemente.

**O que passou a funcionar de maneira diferente?**

O [!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0 não tem uma lista de recém-usados.

### <a name="BKMK_ConsolePane"></a>Painel de console
**Adicionado no PowerShell 3.0**

Os painéis separados de comando e saída que estavam disponíveis na primeira versão do [!INCLUDE[ise_2](../Token/ise_2_md.md)] foram combinados em um painel de console único. O painel de console é semelhante, em termos de função e aparência, a um console típico do [!INCLUDE[wps_2](../Token/wps_2_md.md)], mas ele inclui os aprimoramentos a seguir (a maioria deles é descrito neste tópico).

-   Cores de sintaxe para texto de entrada (não para texto de saída), incluindo sintaxe XML

-   Intellisense

-   Correspondência de chaves

-   Indicação de erros

-   Suporte total a Unicode

-   Ajuda contextual com **F1**

-   **Ctrl+F1** Show-Command contextual

-   Suporte a scripts complexos e leitura da direita para a esquerda

-   Suporte a fontes

-   Zoom

-   Modos de seleção de linha e seleção de blocos

-   Preservação do conteúdo digitado na linha de comando quando você pressiona a seta **para cima** para exibir o histórico no console

**Qual é o valor agregado desta alteração?**

A adição dessas alterações do painel de console fornece uma experiência de script que é mais consistente com a interface do console.

**O que passou a funcionar de maneira diferente?**

O [!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0 tem painéis de comando e de saída separados.

### <a name="BKMK_CommandLine"></a>Opções de linha de comando
**Adicionado no PowerShell 3.0**

Se você iniciar o [!INCLUDE[ise_2](../Token/ise_2_md.md)] com a linha de comando (digitando **Powershell_ise.exe**), será possível adicionar as novas opções de linha de comando a seguir.

-   *-NoProfile*: inicia o [!INCLUDE[ise_2](../Token/ise_2_md.md)] sem executar **$profile**

-   *-Help*: exibe uma janela de ajuda

-   *-mta*: inicia o [!INCLUDE[ise_2](../Token/ise_2_md.md)] no modo Multi-Threaded Apartment. O modo de operação padrão para o [!INCLUDE[ise_2](../Token/ise_2_md.md)] é o modo de single-threaded apartment ou *-sta*.

**Qual é o valor agregado desta alteração?**

A adição dessas opções de linha de comando permitem controlar o ambiente no qual o [!INCLUDE[ise_2](../Token/ise_2_md.md)] é executado.

**O que passou a funcionar de maneira diferente?**

O [!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0 não reconhece essas opções de linha de comando.

### <a name="BKMK_NewEditorFeatures"></a>Novos recursos do editor
**Adicionado no PowerShell 3.0**

Outros recursos de edição do [!INCLUDE[ise_2](../Token/ise_2_md.md)] incluem:

-   **Cores de sintaxe XML**[!INCLUDE[ise_2](../Token/ise_2_md.md)] agora tem sintaxe XML colorida da mesma maneira que a sintaxe colorida do [!INCLUDE[wps_2](../Token/wps_2_md.md)].

-   **Correspondência de chaves** O [!INCLUDE[ise_2](../Token/ise_2_md.md)] inclui o destaque e correspondência de chaves colchetes e pode ser usado das seguintes maneiras: (por exemplo, usar o comando **Ir para Correspondência** ou **Ctrl+]** localizará a chave de fechamento, se você tiver selecionado uma chave de abertura).

-   **Exibição de estrutura de tópicos** O painel de script dá suporte à exibição de estruturas de tópicos, que permitem recolher ou expandir seções de códigos com cliques nos sinais de adição ou subtração na margem esquerda. Você pode usar chaves ou as marcas **#region** e **#endregion** para marcar o início ou o final de uma seção recolhível. Para expandir ou recolher todas as regiões, pressione **Ctrl+M**.

-   **Edição de texto com arrastar e soltar**[!INCLUDE[ise_2](../Token/ise_2_md.md)] agora dá suporte à edição de texto com arrastar e soltar. Você pode selecionar qualquer bloco de texto e arrastar o texto para outro local no editor ou no console para mover o texto. Se você mantiver pressionada a tecla Ctrl enquanto arrasta o texto selecionado, quando soltar o botão do mouse, o texto será copiado para o novo local. Nesta versão do [!INCLUDE[ise_2](../Token/ise_2_md.md)], bem como a versão anterior do [!INCLUDE[ise_2](../Token/ise_2_md.md)], quando você arrasta e soltar arquivos para o [!INCLUDE[ise_2](../Token/ise_2_md.md)], o [!INCLUDE[ise_2](../Token/ise_2_md.md)] abre o arquivo.

-   **Analisar a exibição de erro** Erros de análise são indicados com um sublinhado vermelho. Quando você passa o cursor sobre um erro indicado, o texto da dica de ferramenta exibe o problema encontrado no código.

-   **Zoom** É possível definir o percentual de zoom do conteúdo do console usando o controle deslizante de zoom (no canto inferior direito da janela do [!INCLUDE[ise_2](../Token/ise_2_md.md)]) ou digitando o comando **$psise.options.Zoom** no painel de console.

-   **Copiar e colar rich text** A cópia para a área de transferência em [!INCLUDE[ise_2](../Token/ise_2_md.md)] preserva as informações de fonte, tamanho e cor da seleção original.

-   **Seleção de bloco** Você pode selecionar um bloco de texto segurando a tecla ALT enquanto seleciona o texto no painel de script com o mouse ou pressionando **Alt+Shift+Seta**.

**Qual é o valor agregado desta alteração?**

Os recursos de edição adicionais fornecem um ambiente de edição mais consistente e eficiente.

**O que passou a funcionar de maneira diferente?**

Esses aprimoramentos na edição não estavam presentes no [!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0.

### <a name="BKMK_NewHelpViewer"></a>Janela do novo visualizador da ajuda
**Adicionado no PowerShell 3.0**

Se você pressionar **F1** quando o cursor estiver em um cmdlet ou se parte de um cmdlet estiver realçada, o novo visualizador da Ajuda abrirá uma ajuda contextual sobre o cmdlet realçado. Para exibir a ajuda conceitual do [!INCLUDE[wps_2](../Token/wps_2_md.md)], digite **operators** no painel de console e pressione **F1**.

Antes de usar este recurso, baixe a versão mais atual da ajuda do [!INCLUDE[wps_2](../Token/wps_2_md.md)] no site da Microsoft. O método mais simples para baixar os tópicos da Ajuda é executar o cmdlet **Update-Help** no painel de console durante a execução do [!INCLUDE[ise_2](../Token/ise_2_md.md)] como administrador.

Você pode alterar onde a tecla **F1** busca Ajuda. No menu **Ferramentas**/**Opções**, na guia **Configurações Gerais** em **Outras Configurações**, você pode marcar ou desmarcar a caixa de seleção **Usar conteúdo da Ajuda local em vez de conteúdo online**. Se estiver selecionado, o cliente procurará o cmdlet Help na Ajuda baixada encontrada na pasta de módulos.  Se a caixa de seleção estiver desmarcada, o cliente procurará na Biblioteca do TechNet para obter a Ajuda do cmdlet.

**Qual é o valor agregado desta alteração?**

A Ajuda contextual sem deixar seu cmdlet ou script atual fornece uma experiência de aprendizado contínuo.

**O que passou a funcionar de maneira diferente?**

Pressionar o F1 em versões anteriores do [!INCLUDE[ise_2](../Token/ise_2_md.md)] abria o arquivo de Ajuda no computador local. No [!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0 e posterior, é aberta uma janela que contém a Ajuda para o cmdlet que é configurável e pesquisável. Essa experiência da Ajuda é nova para o [!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0 e a Ajuda Atualizável é nova para o [!INCLUDE[wps_2](../Token/wps_2_md.md)] 3.0.

### <a name="BKMK_ShowCommand"></a>Cmdlet Show-Command
**Adicionado no PowerShell 3.0**

O cmdlet **Show-Command** permite compor ou executar um cmdlet ou função preenchendo um formulário gráfico. O formulário permite que os usuários trabalhem com o [!INCLUDE[wps_2](../Token/wps_2_md.md)] em um ambiente gráfico. **Show-Command** também permite que os desenvolvedores de scripts avançados criem rapidamente uma GUI baseada no [!INCLUDE[wps_2](../Token/wps_2_md.md)].

**Qual é o valor agregado desta alteração?**

Usando **Show-Command** em seu scripts do [!INCLUDE[wps_2](../Token/wps_2_md.md)], você pode fornecer aos usuários o ambiente gráfico com os quais eles estão familiarizados. **Show-Command** também pode ajudar os usuários iniciantes a aprender sobre o [!INCLUDE[wps_2](../Token/wps_2_md.md)].

**O que passou a funcionar de maneira diferente?**

Show-Command é novo do [!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0.

## <a name="BKMK_LINKS"></a>Consulte também
Para obter mais informações sobre como usar o [!INCLUDE[ise_2](../Token/ise_2_md.md)] no [!INCLUDE[wps_2](../Token/wps_2_md.md)], consulte os links a seguir.

-   [Usando o Ambiente de Script Integrado do Windows PowerShell](assetId:///777ea82b-dd73-4269-b61a-69a17e6ff16f)

-   [ISE no TechNet Wiki](http://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)

-   [Central de Scripts](http://technet.microsoft.com/scriptcenter/default)



<!--HONumber=Apr16_HO1-->


