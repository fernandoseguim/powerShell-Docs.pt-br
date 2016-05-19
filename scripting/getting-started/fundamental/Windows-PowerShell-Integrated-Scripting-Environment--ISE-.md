---
title: Ambiente de script integrado do Windows PowerShell (ISE)
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f156b92d-0203-46d2-89c7-b4989d32e3d2
---
# Ambiente de script integrado do Windows PowerShell (ISE)
O ISE (Ambiente de Script Integrado) do Windows PowerShell é um dos dois hosts para o mecanismo do Windows PowerShell e a linguagem idioma. Com ele você pode gravar, executar e testar scripts de maneiras que não estão disponíveis no Console do Windows PowerShell. O ISE adiciona cores de sintaxe, preenchimento com Tab, IntelliSense, depuração visual e ajuda contextual.

O ISE permite executar comandos em um painel de console, mas também dá suporte a painéis que você pode usar para exibir o código-fonte do seu script e outras ferramentas que podem ser conectadas ao ISE simultaneamente. Você ainda pode abrir várias janelas de script ao mesmo tempo, o que é especialmente útil quando você estiver depurando um script que usa funções definidas em outros scripts ou módulos.

## <a name="BKMK_NEW"></a>O que há de novo
Aqui estão alguns dos recursos que foram adicionados ao ISE nas versões mais recentes do PowerShell.

### Adicionado no PowerShell 3.0 (Windows Server 2012 e Windows 8)
O **IntelliSense** preenche automaticamente seus comandos exibindo menus de cmdlets, parâmetros, valores de parâmetro, arquivos ou pastas correspondentes conforme você digita.

**Trechos de código** são sessões de código curtas que você pode inserir facilmente nos scritps que você cria. Uma coleção de trechos de código útil está de fábrica caixa e é possível obter mais usando o cmdlet **New-Snippet**.

**Ferramentas complementares** que adicionam recursos ao ISE podem ser criadas escrevendo código que interage com [O Modelo de Objeto de Script do ISE do Windows PowerShell](https://technet.microsoft.com/en-us/library/dd819478.aspx). Essas ferramentas podem exibir controles em um painel com guias ou trabalhar de forma invisível em segundo plano. O complemento **Comandos** é um bom exemplo disso e está incluído na versão 3.0 e posterior para exibir uma lista dos comandos disponíveis e a Ajuda.

**Gerenciador de Reinicialização e Salvamento Automático** salvam automaticamente seus scripts a cada dois minutos para ajudar a evitar perda do trabalho em caso de falha ou de reinicialização inesperada.

**Última lista usada** agora faz parte do menu Abrir Arquivo para tornar mais fácil acessar os arquivos usados com mais frequência.

**Painel de Console mesclado**. Em versões anteriores do ISE, havia painéis separados de Comando e Saída. Agora eles são combinados em um único painel que reflete mais diretamente o que você vê no Console do Windows PowerShell.

**Opções de linha de comando**. Várias opções de linha de comando novas oferecem mais controle sobre o funcionamento do ISE. -NoProfile inicia o ISE sem executar um script de perfil. –Help abre uma janela de ajuda com o ISE. -mta inicia o ISE em modo "multi-threaded apartment". O padrão é de thread única.

**Novos recursos do editor** facilitam criar e ler seu código:

-   **Cores de sintaxe de XML**. O editor do ISE agora usa as cores de sintaxe XML da mesma maneira que a sintaxe de código do Windows PowerShell.

-   **Correspondência de chaves**. O ISE do Windows PowerShell destaca a correspondência de chaves para ajudar a garantir que você tenha o número correto de chaves de fechamento para corresponder às de abertura. Usar CTRL+[ para localizar a chave de fechamento correspondente àquela de abertura na qual o cursor está.

-   **Exibição de estrutura de tópicos**. Você pode recolher ou expandir seções do seu código clicando nos sinais de adição e subtração na margem esquerda. Isso torna mais fácil localizar o código que você está procurando em um script longo.

-   **Edição de texto com arrastar e soltar**. Você pode selecionar um bloco de texto e arrastá-lo para outro local para movê-lo. Se você mantiver a tecla CTRL pressionada enquanto arrasta o texto selecionado, você o copiará em vez mover.

-   **Exibição de erros de análise**. O Windows PowerShell examina o script conforme você digita. Se detectar um erro, ele mostrará um rabisco vermelho sob o código incorreto. Quando você focaliza o erro indicado, uma dica de ferramenta mostra o problema que foi encontrado.

-   **Zoom**. Você pode ampliar o texto para facilitar a leitura ou reduzir para ver um panorama usando o controle deslizante no canto inferior direito da janela do ISE.

-   **Copiar e colar rich text**. Quando você copia do ISE para a área de transferência, as informações de fonte, tamanho e cor do texto selecionado estão incluídas.

-   **Seleção de blocos**. Você pode selecionar uma parte do texto em bloco segurando a tecla ALT enquanto seleciona o texto no painel de script com o mouse ou pressionando **Alt+Shift+Seta**.

### Adicionado no PowerShell 2.0 (Windows Server 2008 R2 e Windows 7
O ISE foi introduzido com o PowerShell v2.0.

## Requisitos de execução do ISE do Windows PowerShell
O ISE está disponível em qualquer computador que execute o Windows PowerShell v2.0 ou posterior. Cada versão do Windows e Windows Server inclui uma versão do Windows PowerShell e do ISE, mas você pode atualizar para a versão mais recente disponível instalando o Windows Management Framework. Execute essa pesquisa para localizar a versão mais recente disponível: [Downloads](http://www.microsoft.com/en-us/search/DownloadResults.aspx?q=%22windows%20management%20framework%22%20PowerShell&sortby=Relevancy~Descending). Observe que as entradas rotuladas como "Preview" são o código da versão pré-lançamento e não são recursos completos.

> [!NOTE]
> Como o ISE do Windows PowerShell requer uma interface do usuário gráfica, você não pode executá-lo em uma opção Server Core do Windows Server.

## <a name="BKMK_LINKS"></a>Consulte também
[Usando o Ambiente de Script Integrado do Windows PowerShell](http://technet.microsoft.com/library/cc732148.aspx)



<!--HONumber=May16_HO2-->


