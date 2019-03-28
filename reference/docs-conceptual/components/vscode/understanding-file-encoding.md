---
title: Entendendo a codificação de arquivos no VSCode e PowerShell
description: Configurar a codificação de arquivos no VSCode e no PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: ec06d8f5d446a92e6cd9d2d70b11260d1d0afda8
ms.sourcegitcommit: 396509cd0d415acc306b68758b6f833406e26bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2019
ms.locfileid: "58320397"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a>Entendendo a codificação de arquivos no VSCode e PowerShell

Ao usar o VS Code para criar e editar scripts do PowerShell, é importante que os arquivos sejam salvos usando o formato de codificação de caracteres correto.

## <a name="what-is-file-encoding-and-why-is-it-important"></a>O que é codificação de arquivos e por que ela é importante?

O VSCode gerencia a interface entre um humano inserindo cadeias de caracteres em um buffer e lendo/gravando blocos de bytes no sistema de arquivos. Quando salva um arquivo, o VSCode usa uma codificação de texto para fazer isso.

De forma semelhante, quando o PowerShell executa um script, ele precisa converter os bytes em um arquivo em caracteres para reconstruir o arquivo em um programa do PowerShell. Como o VSCode grava o arquivo e o PowerShell lê o arquivo, eles precisam usar o mesmo sistema de codificação. O processo de análise de um script do PowerShell é: *bytes* -> *caracteres* -> *tokens*  ->  *árvore de sintaxe abstrata* -> *execução*.

O VSCode e o PowerShell são instalados com uma configuração de codificação padrão adequada. No entanto, a codificação padrão usada pelo PowerShell foi alterada com o lançamento do PowerShell Core (v6. x). Para garantir que não tenha problemas para usar o PowerShell ou a extensão do PowerShell no VSCode, você precisa definir corretamente suas configurações do VSCode e do PowerShell.

## <a name="common-causes-of-encoding-issues"></a>Causas comuns de problemas de codificação

Problemas de codificação ocorrem quando a codificação do VSCode ou seu arquivo de script não coincidem com a codificação esperada do PowerShell. Não há nenhuma maneira de o PowerShell determinar automaticamente a codificação do arquivo.

Você tem mais probabilidade de ter problemas de codificação quando usa caracteres que não estão no [conjunto de caracteres ASCII de 7 bits](https://ascii.cl/). Por exemplo:

- Caracteres latinos acentuados (`É`, `ü`)
- Caracteres não latinos, como cirílico (`Д`, `Ц`)
- Chinês Han (`脚`, `本`)

Motivos comuns para problemas de codificação são:

- As codificações do VSCode e do PowerShell não foram alteradas em relação aos padrões. Para o PowerShell 5.1 e versões anteriores, a codificação padrão é diferente da codificação do VSCode.
- Outro editor abriu e substituiu o arquivo em uma nova codificação. Isso costuma acontecer com o ISE.
- É feito o check-in do arquivo no controle do código-fonte com uma codificação diferente da esperada pelo VSCode ou PowerShell. Isso pode acontecer quando colaboradores usam editores com configurações de codificação diferentes.

### <a name="how-to-tell-when-you-have-encoding-issues"></a>Como saber que você tem problemas de codificação

Com frequência, erros de codificação são apresentados como erros de análise nos scripts. Se você encontrar sequências de caracteres estranhos em seu script, esse poderá ser o problema. No exemplo a seguir, um traço (`–`) é exibido como os caracteres `â€“`:

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

Esse problema ocorre porque o VSCode codifica o caractere `–` em UTF-8 como os bytes `0xE2 0x80 0x93`.
Quando são decodificados como Windows-1252, esses bytes são interpretados como caracteres `â€“`.

Algumas sequências de caracteres estranhos que você pode ver incluem:

<!-- markdownlint-disable MD038 -->
- `â€“` em vez de `–`
- `â€”` em vez de `—`
- `Ã„2` em vez de `Ä`
- `Â` em vez de ` ` (um espaço contínuo)
- `Ã©` em vez de `é`
<!-- markdownlint-enable MD038 -->

Esta [referência](https://www.i18nqa.com/debug/utf8-debug.html) útil lista os padrões comuns que indicam que há um problema de codificação UTF-8/Windows-1252.

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a>Como a extensão do PowerShell no VSCode interage com codificações

A extensão do PowerShell interage com scripts de várias maneiras:

1. Quando scripts são editados no VSCode, o conteúdo é enviado pelo VSCode para a extensão. O [Protocolo de servidor de linguagem][] exige que esse conteúdo seja transferido em UTF-8. Portanto, não é possível que a extensão obtenha a codificação errada.
2. Quando são executados diretamente no Console integrado, os scripts são lidos do arquivo diretamente pelo PowerShell. Se a codificação do PowerShell for diferente da codificação do VSCode, algo poderá dar errado aqui.
3. Quando um script aberto no VSCode faz referência a outro script que não está aberto no VSCode, a extensão volta a carregar o conteúdo do script do sistema de arquivos. A extensão do PowerShell usa por padrão a codificação UTF-8, mas usa a detecção de [marca de ordem de byte][], ou BOM, para selecionar a codificação correta.

O problema ocorre ao assumir a codificação de formatos sem BOM (como [UTF-8][] sem BOM e [Windows-1252][]).
A extensão do PowerShell usa UTF-8 por padrão. A extensão não pode alterar as configurações de codificação do VSCode.
Para obter mais informações, confira [problema #824](https://github.com/Microsoft/vscode/issues/824).

## <a name="choosing-the-right-encoding"></a>Escolher a codificação correta

Aplicativos e sistemas diferentes podem usar codificações diferentes:

- No .NET Standard, na Web e no universo Linux, UTF-8 é a codificação dominante.
- Muitos aplicativos .NET Framework usam [UTF-16][]. Por razões históricas, às vezes ele é chamado de "Unicode", um termo que hoje se refere a um [padrão](https://en.wikipedia.org/wiki/Unicode) amplo que inclui UTF-8 e UTF-16.
- No Windows, muitos aplicativos nativos anteriores ao Unicode continuam usando o Windows-1252 por padrão.

Codificações Unicode também têm o conceito de uma BOM (marca de ordem de byte). BOMs ocorrem no início do texto para informar ao decodificador qual codificação o texto está usando. Para codificações de múltiplos bytes, a BOM também indica a [ordenação](https://en.wikipedia.org/wiki/Endianness) da codificação. BOMs são designadas como bytes que raramente ocorrem em texto não Unicode, permitindo presumir de forma razoável que o texto é Unicode quando uma BOM está presente.

BOMs são opcionais e sua adoção não é tão popular no universo Linux, pois uma convenção confiável de UTF-8 é usada em todo lugar. A maioria dos aplicativos Linux presume que a entrada de texto está codificada em UTF-8. Embora muitos aplicativos Linux reconheçam e lidem corretamente com uma BOM, vários deles não fazem isso, levando a artefatos nos textos manipulados com esses aplicativos.

**Portanto**:

- se trabalha principalmente com aplicativos do Windows e Windows PowerShell, você deve preferir uma codificação como UTF-8 com BOM ou UTF-16.
- Se trabalha com plataformas cruzadas, você deve preferir UTF-8 com BOM.
- Se trabalha principalmente em contextos associados ao Linux, você deve preferir UTF-8 sem BOM.
- Windows-1252 e latin-1 são essencialmente codificações herdadas que você deve evitar se possível.
  No entanto, alguns aplicativos do Windows mais antigos podem depender delas.
- Também vale observar que a assinatura de script é [dependente da codificação](https://github.com/PowerShell/PowerShell/issues/3466), o que significa que uma alteração na codificação de um script assinado exigirá uma nova assinatura.

## <a name="configuring-vscode"></a>Configurando o VSCode

A codificação padrão do VSCode é UTF-8 sem BOM.

Para definir a [codificação do VSCode][], vá até as configurações do VSCode (<kbd>Ctrl<kbd>+</kbd>,</kbd>) e defina a configuração `"files.encoding"`:

```json
"files.encoding": "utf8bom"
```

Alguns valores possíveis são:

- `utf8`: [UTF-8] sem BOM
- `utf8bom`: [UTF-8] com BOM
- `utf16le`: [UTF-16] little endian
- `utf16be`: [UTF-16] big endian
- `windows1252`: [Windows-1252]

Você deve obter uma lista suspensa deles no modo de exibição de GUI ou preenchimentos no modo de exibição JSON.

Você também pode adicionar o seguinte para obter detecção automática da codificação quando possível:

```json
"files.autoGuessEncoding": true
```

Caso não queira que essas configurações afetem todos os tipos de arquivos, o VSCode também permite configurações por idioma. Crie uma configuração específica a um idioma colocando as configurações em um campo `[<language-name>]`. Por exemplo:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a>Configurar o PowerShell

A codificação padrão do PowerShell varia dependendo da versão:

- No PowerShell 6 +, a codificação padrão é UTF-8 sem BOM em todas as plataformas.
- No Windows PowerShell, a codificação padrão geralmente é Windows-1252, uma extensão de [latin-1][], também conhecida como ISO 8859-1.

No PowerShell 5 +, você pode encontrar sua codificação padrão usando:

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

O seguinte [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) pode ser usado para determinar qual codificação sua sessão do PowerShell infere para um script sem BOM.

```powershell
$badBytes = [byte[]]@(0xC3, 0x80)
$utf8Str = [System.Text.Encoding]::UTF8.GetString($badBytes)
$bytes = [System.Text.Encoding]::ASCII.GetBytes('Write-Output "') + [byte[]]@(0xC3, 0x80) + [byte[]]@(0x22)
$path = Join-Path ([System.IO.Path]::GetTempPath()) 'encodingtest.ps1'

try
{
    [System.IO.File]::WriteAllBytes($path, $bytes)

    switch (& $path)
    {
        $utf8Str
        {
            return 'UTF-8'
            break
        }

        default
        {
            return 'Windows-1252'
            break
        }
    }
}
finally
{
    Remove-Item $path
}
```

É possível configurar o PowerShell para usar uma determinada codificação de modo mais geral usando configurações de perfil. Veja os artigos a seguir:

- [Resposta de [@mklement0] sobre a codificação do PowerShell no StackOverflow](https://stackoverflow.com/a/40098904).
- [Postagem no blob de [@rkeithhill] sobre como lidar com entradas UTF-8 sem BOM no PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).

Não é possível forçar o PowerShell a usar uma codificação de entrada específica. O PowerShell 5.1 e anteriores usam por padrão a codificação Windows-1252 quando não há uma BOM. Por motivos de interoperabilidade, é melhor salvar os scripts em um formato Unicode com uma BOM.

> [!IMPORTANT]
> Qualquer outra ferramenta que você tiver que tocar os scripts do PowerShell poderão ser afetadas por suas escolhas de codificação ou recodificar seus scripts com outra codificação.

### <a name="existing-scripts"></a>Scripts existentes

Scripts que já estão no sistema de arquivos poderão precisar ser codificados novamente para sua codificação escolhida. Na barra inferior do VSCode, você verá o rótulo UTF-8. Clique nele para abrir a barra de ação e selecione **Salvar com codificação**. Agora, você pode escolher uma nova codificação para o arquivo. Confira [Codificação do VSCode][] para obter instruções completas.

Se precisar codificar vários arquivos novamente, você poderá usar o script a seguir:

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a>O (ISE) Ambiente de Script Integrado do PowerShell

Caso também edite scripts usando o ISE do PowerShell, você precisará sincronizar suas configurações de codificação nele.

O ISE deve honrar uma BOM, mas também é possível usar reflexão para [definir a codificação](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).
Observe que isso não persistiria entre inicializações.

### <a name="source-control-software"></a>Software de controle do código-fonte

Algumas ferramentas de controle do código-fonte, como git, ignoram as codificações; o git apenas controla os bytes.
Outros, como Azure DevOps ou Mercurial, podem não fazer isso. Até mesmo algumas ferramentas baseadas em git dependem da decodificação de texto.

Quando for esse o caso, não deixe de:

- Configurar a codificação de texto no controle do código-fonte para corresponder à sua configuração do VSCode.
- Garantir que todos os arquivos sejam verificados no controle do código-fonte na codificação relevante.
- Estar atento a alterações na codificação recebidas por meio do controle do código-fonte. Um sinal importante disto é uma comparação indicando alterações, mas em que nada parece ter sido alterado (porque os bytes foram, mas os caracteres não).

### <a name="collaborators-environments"></a>Ambientes de colaboradores

Além de configurar o controle do código-fonte, certifique-se de que seus colaboradores em todos os arquivos que você compartilha não tenham configurações que substituem sua codificação codificando novamente os arquivos do PowerShell.

### <a name="other-programs"></a>Outros programas

Qualquer outro programa que lê ou grava um script do PowerShell pode codificá-lo novamente.

Alguns exemplos são:

- Usar a área de transferência para copiar e colar um script. Isso é comum em cenários como:
  - Copiar um script para uma VM
  - Copiar um script para fora de um email ou página da Web
  - Copiar um script de ou para um documento do Microsoft Word ou PowerPoint
- Outros editores de texto, como:
  - Bloco de notas
  - vim
  - Qualquer outro editor de script do PowerShell
- Utilitários de edição de texto, como:
  - `Get-Content`/`Set-Content`/`Out-File`
  - Operadores de redirecionamento do PowerShell, como `>` e `>>`
  - `sed`/`awk`
- Programas de transferência de arquivos, como:
  - Um navegador da Web, ao baixar scripts
  - Um compartilhamento de arquivo

Algumas dessas ferramentas lidam com bytes em vez de texto, mas outras oferecem configurações de codificação. Nos casos em que precisa configurar uma codificação, você precisa fazer com que ela seja igual à codificação de seu editor para evitar problemas.

## <a name="other-resources-on-encoding-in-powershell"></a>Outros recursos sobre codificação no PowerShell

Há algumas outras postagens interessantes sobre codificação e configuração da codificação do PowerShell que merecem uma leitura:

- [Resumo de [@mklement0] sobre a codificação do PowerShell no StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)
- Problemas anteriores abertos no vscode-PowerShell referentes a problemas de codificação:
  - [#1308](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [#1628](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [#1680](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [#1744](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [#1751](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [O artigo clássico de *Joel on Software* sobre Unicode](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [Codificação no .NET Standard](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[marca de ordem de byte]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Protocolo de servidor de linguagem]: https://microsoft.github.io/language-server-protocol/
[Codificação do VSCode]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
