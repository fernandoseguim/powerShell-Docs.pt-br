<a id="style-guide-for-powershell-docs" class="xliff"></a>
# Guia de estilo para o PowerShell-Docs


<a id="titlesheadings" class="xliff"></a>
## Títulos

* Os títulos (prefixados por \#) devem ser seguidos por uma nova linha
* Somente a primeira letra de um título e os nomes próprios nesse título devem estar em letras maiúsculas
* Somente um H1 por documento
* Ao editar o conteúdo de referência, os H2s são prescritos pelo platyPS e não devem ser adicionados ou removidos, uma vez que isso causará uma interrupção da compilação
* Use somente os estilos de cabeçalho do \# (em vez de = ou cabeçalhos de estilo do \-)

<a id="correct" class="xliff"></a>
### Correto

```
# Header 1

## Header 2

### Header 3

```

<a id="incorrect" class="xliff"></a>
### Incorreto

```
Header 1
========

Header 2
--------

### Header 3
```

<a id="syntax" class="xliff"></a>
## Sintaxe

* Ao falar sobre um cmdlet em um parágrafo, use \` para realçar os nomes do cmdlet
  * Exemplo correto: Este Cmdlet `Write-Host` pode...
  * Exemplo incorreto: Este Cmdlet **Write-Host** pode... e pipeline para que o Cmdlet out-file...
* Ao escrever um artigo (em vez de um conteúdo de referência), a primeira instância de um nome de cmdlet deve ser um link para a documentação do cmdlet
* Todos os blocos de sintaxe do PowerShell devem usar o &#96;&#96;&#96;powershell
* Não inicie os comandos do PowerShell com "`PS C:\>`"
  * Exemplo correto:
  ```powershell
  Get-Process
  ```
  * Exemplo incorreto:
  ```powershell
  PS C:\> Get-Process
  ```
* A saída gerada pelos comandos do PowerShell deve ser comentada para impedir que ela receba realce de sintaxe
* Os nomes de propriedades e nomes de parâmetros devem estar em **negrito**
* O cmdlets do PowerShell seguem a capitalização"[Pascal Case](https://en.wikipedia.org/wiki/PascalCase)". Os verbos são separados dos substantivos por um hífen.

<a id="lists" class="xliff"></a>
## Listas

* Não encerre os itens da lista com um ponto (a menos que eles tenham várias sentenças)
* Se sua lista contiver várias sentenças, considere usar um cabeçalho 3/4/5 (conforme aplicável) abaixo da ideia principal

<a id="links" class="xliff"></a>
## Links

* Os links são sempre marcados usando a sintaxe MarkDown `[friendlyname](url)`
* Os links devem ter um nome amigável quando aplicável, preferencialmente o título da página vinculada
  * **Exceção**: os links direcionados a sites que não sejam da Microsoft só devem ter uma URL
* Todos os itens da seção "links relacionados" na parte inferior devem ser hiperlinks. 

<a id="line-breaks" class="xliff"></a>
## Quebras de linha

* Inclua quebras de linha semânticas
* Limite as linhas a 100 caracteres (Item aberto: ferramentas para nos ajudar a validar isso)
* Você PODE remover quebras de linhas adicionais para PS4+, NÃO para ps3 (precisa de validação)
