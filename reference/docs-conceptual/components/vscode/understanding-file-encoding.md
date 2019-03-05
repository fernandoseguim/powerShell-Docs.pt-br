---
title: Entendendo a codificação de arquivos no VSCode e PowerShell
description: Configurar a codificação do arquivo no VSCode e o PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: f3b133b4bee7688821a5960429e2f26b69b01e12
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251465"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a>Entendendo a codificação de arquivos no VSCode e PowerShell

Ao usar o VS Code para criar e editar scripts do PowerShell, é importante que os arquivos são salvos usando o formato de codificação de caracteres correto.

## <a name="what-is-file-encoding-and-why-is-it-important"></a>O que é a codificação do arquivo e por que é importante?

VSCode gerencia a interface entre um humano inserindo cadeias de caracteres em caracteres em um buffer e blocos de leitura/gravação de bytes para o sistema de arquivos. Quando o VSCode salva um arquivo, ele usa um codificação de texto para fazer isso.

Da mesma forma, quando um script do PowerShell executa deve converter os bytes em um arquivo em caracteres para reconstruir o arquivo em um programa do PowerShell. Como VSCode grava o arquivo e PowerShell lê o arquivo, eles precisam usar o mesmo sistema de codificação. Esse processo de análise de um script do PowerShell vai: *bytes* -> *caracteres* -> *tokens*  ->   *árvore de sintaxe abstrata* -> *execução*.

O VSCode e o PowerShell são instalados com uma configuração de codificação padrão adequado. No entanto, a codificação padrão usada pelo PowerShell foi alterado com a versão do PowerShell Core (v6. x). Para garantir que você não têm problemas usando o PowerShell ou a extensão do PowerShell no VSCode, você precisa configurar suas configurações VSCode e o PowerShell corretamente.

## <a name="common-causes-of-encoding-issues"></a>Causas comuns de problemas de codificação

Problemas de codificação ocorrem quando a codificação do VSCode ou no seu arquivo de script não coincide com a codificação esperada do PowerShell. Não há nenhuma maneira para o PowerShell determinar automaticamente a codificação do arquivo.

Você está mais probabilidade de ter problemas de codificação quando você estiver usando caracteres não está no [conjunto de caracteres ASCII de 7 bits](https://ascii.cl/). Por exemplo:

- Acentuadas caracteres latinos (`É`, `ü`)
- Caracteres não latinos, como Cirílico (`Д`, `Ц`)
- Henrique chinês (`脚`, `本`)

Motivos comuns para problemas de codificação são:

- As codificações do VSCode e do PowerShell não foram alteradas em relação aos padrões. Para o PowerShell 5.1 ou posterior, o padrão de codificação é diferente do VSCode.
- Outro editor tem aberto e substituído o arquivo em uma nova codificação. Isso costuma acontecer com o ISE.
- O arquivo é verificado no controle de origem em uma codificação diferente do VSCode ou do PowerShell espera. Isso pode acontecer quando colaboradores usam editores com diferentes configurações de codifica.

### <a name="how-to-tell-when-you-have-encoding-issues"></a>Como saber quando você tiver problemas de codificação

Se analisar erros em scripts apresentam erros de codificação com frequência. Se você encontrar sequências de caracteres estranhos em seu script, isso pode ser o problema. No exemplo a seguir, um traço (`–`) é exibido como os caracteres `â€“`:

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

Esse problema ocorre porque o VSCode codifica o caractere `–` em UTF-8 como os bytes `0xE2 0x80 0x93`.
Quando esses bytes são decodificados como Windows-1252, eles são interpretados como caracteres `â€“`.

Algumas sequências de caracteres estranhos que você pode ver incluem:

- `â€“` em vez de `–`
- `â€”` em vez de `—`
- `Ã„2` em vez de `Ä`
- `Â` em vez de ` ` (um espaço incondicional)
- `Ã©` em vez de `é`

Nesse útil [referência](https://www.i18nqa.com/debug/utf8-debug.html) lista os padrões comuns que indicam um problema de codificação UTF-8/Windows-1252.

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a>Como a extensão do PowerShell no VSCode interage com codificações

A extensão do PowerShell interage com scripts de várias maneiras:

1. Quando os scripts são editados no VSCode, o conteúdo é enviado com o VSCode para a extensão. O [protocolo de idioma do servidor][] exige que esse conteúdo é transferido em UTF-8. Portanto, não é possível que a extensão obter a codificação errada.
2. Quando os scripts são executados diretamente no Console integrado, que estão lidas do arquivo pelo PowerShell diretamente. A codificação de Tf PowerShell difere do VSCode, algo pode dar errado aqui.
3. Quando um script que está aberto no VSCode faz referência a outro script que não está aberto no VSCode, a extensão de volta ao carregar o conteúdo do script do sistema de arquivos. A extensão do PowerShell padrão é a codificação UTF-8, mas utiliza [marca de ordem de byte][], ou BOM, detecção para selecionar a codificação correta.

O problema ocorre quando supondo que a codificação da BOM sem formatos (como [UTF-8][] sem BOM e [Windows-1252][]).
A extensão do PowerShell padrão é UTF-8. A extensão não pode alterar as configurações de codificação do VSCode.
Para obter mais informações, consulte [emitir 824 #](https://github.com/Microsoft/vscode/issues/824).

## <a name="choosing-the-right-encoding"></a>Escolher a codificação à direita

Aplicativos e sistemas diferentes podem usar codificações diferentes:

- No .NET Standard, na web e no mundo Linux, UTF-8 é agora a codificação dominante.
- Muitos aplicativos do .NET Framework usam [UTF-16][]. Por razões históricas, às vezes, isso é chamado de "Unicode", um termo que agora se refere a uma ampla [standard](https://en.wikipedia.org/wiki/Unicode) que inclui o UTF-8 e UTF-16.
- No Windows, muitos aplicativos nativos que são anteriores ao Unicode continuam a usar o Windows-1252 por padrão.

Codificações Unicode também tem o conceito de uma ordem de byte (BOM) de marcar. BOMs ocorrerem no início do texto para informar um decodificador qual codificação é usando o texto. Codificações de vários bytes, a BOM também indica [endianness](https://en.wikipedia.org/wiki/Endianness) da codificação. BOMs são projetados para serem bytes que raramente ocorrem em texto não-Unicode, permitindo que uma estimativa razoável de que o texto é Unicode quando um BOM estiver presente.

BOMs são opcionais e adoção não é tão popular no mundo Linux como uma convenção de confiável de UTF-8 é usada em todos os lugares. A maioria dos aplicativos do Linux presumem que a entrada de texto está codificada em UTF-8. Embora muitos aplicativos Linux reconhecerá e lidar corretamente com um BOM, um número não fizer isso, levando a artefatos no texto manipulado com esses aplicativos.

**Portanto**:

- Se você trabalha principalmente com aplicativos do Windows e Windows PowerShell, você deve preferir uma codificação como UTF-8 com BOM ou UTF-16.
- Se funcionar entre plataformas, você deve preferir UTF-8 com BOM.
- Se você trabalha principalmente em contextos associados ao Linux, você deve preferir UTF-8 sem BOM.
- Windows-1252 e latin 1 são codificações herdadas, essencialmente, você deve evitar se possível.
  No entanto, alguns aplicativos do Windows mais antigos podem dependem deles.
- Também vale a pena observar que a assinatura de script é [dependente de codificação](https://github.com/PowerShell/PowerShell/issues/3466), que significa que uma alteração de codificação em um script assinado exigirá a assinar novamente.

## <a name="configuring-vscode"></a>Configurando o VSCode

Da VSCode codificação padrão é UTF-8 sem BOM.

Para definir [a codificação do VSCode][], vá para as configurações do VSCode (<kbd>Ctrl<kbd>+</kbd>,</kbd>) e defina o `"files.encoding"` configuração:

```json
"files.encoding": "utf8bom"
```

Alguns valores possíveis são:

- `utf8`: [UTF-8] sem BOM
- `utf8bom`: [UTF-8] com BOM
- `utf16le`: Little endian [UTF-16]
- `utf16be`: Big endian [UTF-16]
- `windows1252`: [Windows-1252]

Você deve obter uma lista suspensa para isso no modo de exibição de GUI ou exibição de preenchimentos para ele no JSON.

Você também pode adicionar o seguinte para detecção automática de codificação quando possível:

```json
"files.autoGuessEncoding": true
```

Se você não quiser que essas configurações afetam todos os tipos de arquivos, o VSCode também permite que configurações por idioma. Criar uma configuração específica do idioma, colocando as configurações um `[<language-name>]` campo. Por exemplo:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a>Configurar o PowerShell

Da PowerShell codificação padrão varia dependendo da versão:

- No PowerShell 6 +, a codificação padrão é UTF-8 sem BOM em todas as plataformas.
- No Windows PowerShell, a codificação padrão geralmente é uma extensão do Windows-1252, [latin 1][], também conhecido como ISO 8859-1.

No PowerShell 5 +, você pode encontrar sua codificação padrão com este:

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

O seguinte [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) pode ser usado para determinar o que a codificação de sua sessão do PowerShell infere para um script sem uma BOM.

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

É possível configurar o PowerShell para usar uma codificação fornecida de modo geral, usando as configurações de perfil. Veja os artigos a seguir:

- [@mklement0]do [resposta sobre a codificação do PowerShell no StackOverflow](https://stackoverflow.com/a/40098904).
- [@rkeithhill]do [postagem de blog sobre como lidar com a entrada de UTF-8 sem BOM no PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).

Não é possível forçar o PowerShell para usar uma codificação de entrada específica. PowerShell 5.1 e abaixo do padrão de codificação quando não há nenhuma BOM do Windows-1252. Por motivos de interoperabilidade, é melhor Salvar scripts em um formato Unicode com um BOM.

> [!IMPORTANT]
> Qualquer outra ferramenta que você tem que toque PowerShell scripts podem ser afetados pelas suas escolhas de codifica ou recodificar em seus scripts para outra codificação.

### <a name="existing-scripts"></a>Scripts existentes

Scripts já está no sistema de arquivos talvez precise ser codificada novamente para sua nova codificação escolhida. A barra de parte inferior do VSCode, você verá o rótulo UTF-8. Clique para abrir a barra de ação e selecione **salvar com codificação**. Agora você pode escolher uma nova codificação para esse arquivo. Ver [A codificação do VSCode][] para obter instruções completas.

Se você precisar codificar em vários arquivos, você pode usar o script a seguir:

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a>O (ISE) Ambiente de Script Integrado do PowerShell

Se você também pode editar scripts usando o ISE do PowerShell, você precisará sincronizar suas configurações de codificação.

O ISE deve honrar uma BOM, mas também é possível usar a reflexão para [defina a codificação](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).
Observe que isso não seria ser persistentes entre empresas iniciantes.

### <a name="source-control-software"></a>Software de controle do código-fonte

Algumas ferramentas de controle do código-fonte, como git, ignorar codificações; o git apenas controla os bytes.
Outros, como o TFS ou Mercurial, talvez não tenham. Até mesmo algumas ferramentas baseadas em git dependem de decodificação de texto.

Quando esse for o caso, certifique-se de você:

- Configure o texto no controle de origem para corresponder à sua configuração do VSCode de codificação.
- Certifique-se de que todos os arquivos são verificados no controle do código-fonte na codificação relevante.
- Esteja atento a alterações para a codificação recebida por meio do controle do código-fonte. Um sinal de chave deste é uma comparação que indica as alterações, mas onde nada parece ter sido alterado (porque têm de bytes, mas caracteres não têm).

### <a name="collaborators-environments"></a>Ambientes de colaboradores

Na parte superior, configurando o controle de origem, certifique-se de que seus colaboradores em quaisquer arquivos que você compartilha não tem configurações que substituem a codificação de sua codificação novamente os arquivos do PowerShell.

### <a name="other-programs"></a>Outros programas

Qualquer outro programa que lê ou grava um script do PowerShell pode codificá-lo novamente.

Alguns exemplos são:

- Usando a área de transferência para copiar e colar um script. Isso é comum em cenários como:
  - Copiar um script em uma VM
  - Copiar um script fora de um email ou página da Web
  - Copiar um script para dentro ou fora de um documento do Microsoft Word ou PowerPoint
- Outros editores de texto, como:
  - Bloco de notas
  - vim
  - Qualquer outro editor de script do PowerShell
- Texto de edição de utilitários, como:
  - `Get-Content`/`Set-Content`/`Out-File`
  - Operadores de redirecionamento do PowerShell, como `>` e `>>`
  - `sed`/`awk`
- Programas de transferência de arquivos, como:
  - Um navegador da web, ao fazer o download de scripts
  - Um compartilhamento de arquivos

Algumas dessas ferramentas lidam de bytes em vez de texto, mas outros oferecem configurações de codifica. Nesses casos em que você precisa configurar uma codificação, você precisará fazer o mesmo que o seu editor de codificação para evitar problemas.

## <a name="other-resources-on-encoding-in-powershell"></a>Outros recursos na codificação no PowerShell

Há algumas outras postagens interessantes sobre codificação e configurar a codificação do PowerShell que merecem uma leitura:

- [@mklement0]do [resumo de codificação do PowerShell no StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)
- Problemas anteriores aberto no vscode do PowerShell para problemas de codificação:
  - [#1308](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [#1628](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [#1680](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [#1744](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [#1751](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [O clássico *Joel on Software* escrever sobre Unicode](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [Codificação no .NET Standard](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin 1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[marca de ordem de byte]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Protocolo de idioma do servidor]: https://microsoft.github.io/language-server-protocol/
[A codificação do VSCode]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support