# <a name="contributing-to-powershell-documentation"></a>Contribuindo para a documentação do PowerShell

Obrigado por seu interesse na documentação do PowerShell! Consulte abaixo para encontrar detalhes sobre como você pode contribuir para a nossa documentação técnica.

>Para obter informações gerais sobre a introdução ao Git e GitHub, consulte [GitHub Help](https://help.github.com/) (Ajuda do GitHub). 

## <a name="sign-a-cla"></a>Assinar um CLA

Antes de poder contribuir com qualquer repositório do PowerShell, você deve [assinar um CLA (Contrato de Licenciamento de Contribuição) da Microsoft](https://cla.microsoft.com/). Se você já tiver contribuído para repositórios do PowerShell no passado, parabéns! Você já concluiu essa etapa.

## <a name="providing-feedback-on-powershell-documentation"></a>Fornecer comentários sobre a documentação do PowerShell

Você pode apontar erros, sugerir alterações ou solicitar novos tópicos [criando uma questão](https://help.github.com/articles/creating-an-issue/) na [página de questões de repositório da documentação do PowerShell](https://github.com/PowerShell/PowerShell-Docs/issues).

As questões são revisadas regularmente por membros da equipe de documentação do PowerShell, são separadas atribuídas e tratadas de acordo.

## <a name="writing-powershell-documentation"></a>Escrevendo a documentação do PowerShell

Uma das maneiras mais fáceis de contribuir com o PowerShell é ajudando a escrever e editar a documentação. Todas as documentações hospedadas no GitHub são escritas usando o [GitHub Flavored Markdown](https://help.github.com/articles/github-flavored-markdown/).

## <a name="making-minor-edits-to-existing-topics"></a>Fazer pequenas edições em tópicos existentes

Para [editar um arquivo existente](https://help.github.com/articles/editing-files-in-another-user-s-repository/), basta navegar até ele e clicar no botão "Edit" (Editar). O GitHub automaticamente criará sua própria bifurcação do nosso repositório na qual você pode fazer as alterações. Quando terminar, salve suas alterações e envie uma [solicitação pull](https://help.github.com/articles/creating-a-pull-request/) para o branch de *preparo* do repositório da [documentação do PowerShell](https://github.com/PowerShell/PowerShell-Docs). Depois que a solicitação pull for criada, alguém da equipe de documentação do PowerShell examinará as alterações antes de mesclá-las no branch de *preparo*.

## <a name="making-major-edits-to-existing-topics"></a>Fazer grandes edições em tópicos existentes

Se você estiver fazendo alterações significativas em um artigo existente, adicionando ou alterando imagens ou contribuindo com um novo artigo, será necessário criar manualmente a bifurcação do GitHub e, em seguida, clonar a bifurcação para seu computador local. Uma bifurcação é uma réplica baseada no GitHub do repositório principal, em sua conta do GitHub, que fornece uma cópia funcional que pode ser usada isoladamente. Você criará as solicitações pull da bifurcação. Da mesma forma, um clone é uma réplica local do repositório que, nesse caso, será um clone da sua bifurcação. O clone permite que você trabalhe nos repositórios Git offline e usando ferramentas/software nativo mais poderosos.

Aqui está o fluxo de trabalho para fazer grandes edições na documentação existente:

1. [Crie uma bifurcação](https://help.github.com/articles/fork-a-repo/) do repositório da [Documentação do PowerShell](https://github.com/PowerShell/PowerShell-Docs).
2. [Crie um clone da sua bifurcação](https://help.github.com/articles/cloning-a-repository/) no computador Local.
3. Crie um novo branch no repositório clonado.
4. Faça as alterações nos arquivos que deseja atualizar no editor de Markdown. 
   Consulte abaixo os editores de Markdown normalmente usados.
5. [Envie por push sua ramificação local](https://help.github.com/articles/pushing-to-a-remote/) para sua bifurcação.
6. [Crie uma solicitação pull](https://help.github.com/articles/creating-a-pull-request/) para o branch de *preparo* do repositório da [Documentação do PowerShell](https://github.com/PowerShell/PowerShell-Docs).

## <a name="creating-new-topics"></a>Criando novos tópicos

Se você quiser contribuir com a nova documentação, verifique primeiro se há [questões marcadas como "em andamento"](https://github.com/PowerShell/PowerShell-Docs/labels/in%20progress) para certificar-se de que você não estará duplicando esforços.
Se aparentemente não houver ninguém trabalhando no que você planejou:

* Abra uma nova questão e rotule-a como “em andamento” (se você for um membro da organização PowerShell) ou adicione “em andamento” como um comentário para informar aos outros no que você está trabalhando
* Siga o mesmo fluxo de trabalho descrito acima para fazer grandes edições em tópicos existentes.
* Edite o tópico `TOC.md` (localizado na pasta de nível superior de cada conjunto de documentação) para adicionar seus novos tópicos ao sumário. 
  Determine onde o novo tópico pertence no sumário e adicione um título de nível apropriado, com um link para o tópico (`[My topic title](relative path to my topic)`).

## <a name="markdown-editors"></a>Editores de Markdown

Aqui estão alguns editores de Markdown que você pode experimentar:

* [Visual Studio Code](https://code.visualstudio.com)
* [Markdown Pad](http://markdownpad.com/)
* [Atom](https://atom.io/)
* [Sublime Text](http://www.sublimetext.com/)


## <a name="github-flavored-markdown-gfm"></a>GFM (GitHub Flavored Markdown)

Todos os artigos em uso neste repositório usam o [GFM (GitHub Flavored Markdown)](https://help.github.com/articles/github-flavored-markdown/).

Parte da sintaxe básica do GFM inclui:

* **Quebras de linhas vs. parágrafos:** No Markdown não há o elemento HTML `<br />` ou `<p />`. Em vez disso, um novo parágrafo é designado por uma linha vazia entre dois blocos de texto.

> **Observação**: adicione uma nova linha única após cada sentença para simplificar a saída de linha de comando de histórico e comparações.
Isso não é atualmente adotado em toda a documentação do PowerShell, mas trabalharemos para isso ao longo do tempo. Fique à vontade para ajudar. 

* **Itálico:** O elemento HTML `<em>some text</em>` é escrito como `*some text*`
* **Negrito:** O elemento HTML `<strong>some text</strong>` é escrito como `**some text**`
* **Títulos:** os títulos HTML são designados usando caracteres `#` no início da linha. 
  O número de caracteres `#` corresponde ao nível hierárquico do título (por exemplo, `#`  =  `<h1>` e `###`  =  ```<h3>```).
* **Listas numeradas:** para criar uma linha numerada (ordenada) inicie a linha com `1. `.  
  Se você quiser vários elementos dentro de um único elemento de lista, formate sua lista da seguinte maneira:
```        
1.  For the first element (like this one), insert a tab stop after the 1. 

    To include a second element (like this one), insert a line break after the first and align indentations.
```
para obter essa saída:

1.  Para o primeiro elemento (como este), insira uma parada de tabulação após o 1. 

    Para incluir um segundo elemento (como este), insira uma quebra de linha após a primeira e alinhe os recuos.

* **Listas com marcadores:** as listas com marcadores (não ordenadas) são praticamente idênticas às listas ordenadas, exceto que o `1. ` é substituído por `* `, `- ` ou `+ `. Listas de vários elementos funcionam da mesma forma que com listas ordenadas.
* **Links:** a sintaxe de um hiperlink é `[visible link text](link URL)`.
* **Link para outro tópico dentro do mesmo docset:** um docset é uma pasta de nível superior neste repositório (por exemplo, "dsc", "scripting").
    A sintaxe de um hiperlink para um tópico dentro do mesmo docset é `[topic title](relative path to topic)`. 
    Para obter mais informações, consulte [Relative links in READMEs](https://help.github.com/articles/relative-links-in-readmes/) (Links relativos nos LEIAMEs). 
    Para vincular a um tópico em uma pasta de nível superior diferente, use a URL da página publicada, conforme descrito acima.
