---
title: Entendendo a codificação de arquivos no VSCode e PowerShell
description: Configurar a codificação do arquivo no VSCode e o PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: 9cf445ebd0c2bb2dbdf4438f02dafe3df3a5d1e2
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429798"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a><span data-ttu-id="176c5-103">Entendendo a codificação de arquivos no VSCode e PowerShell</span><span class="sxs-lookup"><span data-stu-id="176c5-103">Understanding file encoding in VSCode and PowerShell</span></span>

<span data-ttu-id="176c5-104">Ao usar o VS Code para criar e editar scripts do PowerShell, é importante que os arquivos são salvos usando o formato de codificação de caracteres correto.</span><span class="sxs-lookup"><span data-stu-id="176c5-104">When using VS Code to create and edit PowerShell scripts, it is important that your files are saved using the correct character encoding format.</span></span>

## <a name="what-is-file-encoding-and-why-is-it-important"></a><span data-ttu-id="176c5-105">O que é a codificação do arquivo e por que é importante?</span><span class="sxs-lookup"><span data-stu-id="176c5-105">What is file encoding and why is it important?</span></span>

<span data-ttu-id="176c5-106">VSCode gerencia a interface entre um humano inserindo cadeias de caracteres em caracteres em um buffer e blocos de leitura/gravação de bytes para o sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="176c5-106">VSCode manages the interface between a human entering strings of characters into a buffer and reading/writing blocks of bytes to the filesystem.</span></span> <span data-ttu-id="176c5-107">Quando o VSCode salva um arquivo, ele usa um codificação de texto para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="176c5-107">When VSCode saves a file, it uses a text encoding to do this.</span></span>

<span data-ttu-id="176c5-108">Da mesma forma, quando um script do PowerShell executa deve converter os bytes em um arquivo em caracteres para reconstruir o arquivo em um programa do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="176c5-108">Similarly, when PowerShell runs a script it must convert the bytes in a file to characters to reconstruct the file into a PowerShell program.</span></span> <span data-ttu-id="176c5-109">Como VSCode grava o arquivo e PowerShell lê o arquivo, eles precisam usar o mesmo sistema de codificação.</span><span class="sxs-lookup"><span data-stu-id="176c5-109">Since VSCode writes the file and PowerShell reads the file, they need to use the same encoding system.</span></span> <span data-ttu-id="176c5-110">Esse processo de análise de um script do PowerShell vai: *bytes* -> *caracteres* -> *tokens*  ->   *árvore de sintaxe abstrata* -> *execução*.</span><span class="sxs-lookup"><span data-stu-id="176c5-110">This process of parsing a PowerShell script goes: *bytes* -> *characters* -> *tokens* -> *abstract syntax tree* -> *execution*.</span></span>

<span data-ttu-id="176c5-111">O VSCode e o PowerShell são instalados com uma configuração de codificação padrão adequado.</span><span class="sxs-lookup"><span data-stu-id="176c5-111">Both VSCode and PowerShell are installed with a sensible default encoding configuration.</span></span> <span data-ttu-id="176c5-112">No entanto, a codificação padrão usada pelo PowerShell foi alterado com a versão do PowerShell Core (v6. x).</span><span class="sxs-lookup"><span data-stu-id="176c5-112">However, the default encoding used by PowerShell has changed with the release of PowerShell Core (v6.x).</span></span> <span data-ttu-id="176c5-113">Para garantir que você não têm problemas usando o PowerShell ou a extensão do PowerShell no VSCode, você precisa configurar suas configurações VSCode e o PowerShell corretamente.</span><span class="sxs-lookup"><span data-stu-id="176c5-113">To ensure you have no problems using PowerShell or the PowerShell extension in VSCode, you need to configure your VSCode and PowerShell settings properly.</span></span>

## <a name="common-causes-of-encoding-issues"></a><span data-ttu-id="176c5-114">Causas comuns de problemas de codificação</span><span class="sxs-lookup"><span data-stu-id="176c5-114">Common causes of encoding issues</span></span>

<span data-ttu-id="176c5-115">Problemas de codificação ocorrem quando a codificação do VSCode ou no seu arquivo de script não coincide com a codificação esperada do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="176c5-115">Encoding problems occur when the encoding of VSCode or your script file does not match the expected encoding of PowerShell.</span></span> <span data-ttu-id="176c5-116">Não há nenhuma maneira para o PowerShell determinar automaticamente a codificação do arquivo.</span><span class="sxs-lookup"><span data-stu-id="176c5-116">There is no way for PowerShell to automatically determine the file encoding.</span></span>

<span data-ttu-id="176c5-117">Você está mais probabilidade de ter problemas de codificação quando você estiver usando caracteres não está no [conjunto de caracteres ASCII de 7 bits](https://ascii.cl/).</span><span class="sxs-lookup"><span data-stu-id="176c5-117">You're more likely to have encoding problems when you're using characters not in the [7-bit ASCII character set](https://ascii.cl/).</span></span> <span data-ttu-id="176c5-118">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="176c5-118">For example:</span></span>

- <span data-ttu-id="176c5-119">Acentuadas caracteres latinos (`É`, `ü`)</span><span class="sxs-lookup"><span data-stu-id="176c5-119">Accented latin characters (`É`, `ü`)</span></span>
- <span data-ttu-id="176c5-120">Caracteres não latinos, como Cirílico (`Д`, `Ц`)</span><span class="sxs-lookup"><span data-stu-id="176c5-120">Non-latin characters like Cyrillic (`Д`, `Ц`)</span></span>
- <span data-ttu-id="176c5-121">Henrique chinês (`脚`, `本`)</span><span class="sxs-lookup"><span data-stu-id="176c5-121">Han Chinese (`脚`, `本`)</span></span>

<span data-ttu-id="176c5-122">Motivos comuns para problemas de codificação são:</span><span class="sxs-lookup"><span data-stu-id="176c5-122">Common reasons for encoding issues are:</span></span>

- <span data-ttu-id="176c5-123">As codificações do VSCode e do PowerShell não foram alteradas em relação aos padrões.</span><span class="sxs-lookup"><span data-stu-id="176c5-123">The encodings of VSCode and PowerShell have not been changed from their defaults.</span></span> <span data-ttu-id="176c5-124">Para o PowerShell 5.1 ou posterior, o padrão de codificação é diferente do VSCode.</span><span class="sxs-lookup"><span data-stu-id="176c5-124">For PowerShell 5.1 and below, the default encoding is different from VSCode's.</span></span>
- <span data-ttu-id="176c5-125">Outro editor tem aberto e substituído o arquivo em uma nova codificação.</span><span class="sxs-lookup"><span data-stu-id="176c5-125">Another editor has opened and overwritten the file in a new encoding.</span></span> <span data-ttu-id="176c5-126">Isso costuma acontecer com o ISE.</span><span class="sxs-lookup"><span data-stu-id="176c5-126">This often happens with the ISE.</span></span>
- <span data-ttu-id="176c5-127">O arquivo é verificado no controle de origem em uma codificação diferente do VSCode ou do PowerShell espera.</span><span class="sxs-lookup"><span data-stu-id="176c5-127">The file is checked into source control in an encoding that is different from what VSCode or PowerShell expects.</span></span> <span data-ttu-id="176c5-128">Isso pode acontecer quando colaboradores usam editores com diferentes configurações de codifica.</span><span class="sxs-lookup"><span data-stu-id="176c5-128">This can happen when collaborators use editors with different encoding configurations.</span></span>

### <a name="how-to-tell-when-you-have-encoding-issues"></a><span data-ttu-id="176c5-129">Como saber quando você tiver problemas de codificação</span><span class="sxs-lookup"><span data-stu-id="176c5-129">How to tell when you have encoding issues</span></span>

<span data-ttu-id="176c5-130">Se analisar erros em scripts apresentam erros de codificação com frequência.</span><span class="sxs-lookup"><span data-stu-id="176c5-130">Often encoding errors present themselves as parse errors in scripts.</span></span> <span data-ttu-id="176c5-131">Se você encontrar sequências de caracteres estranhos em seu script, isso pode ser o problema.</span><span class="sxs-lookup"><span data-stu-id="176c5-131">If you find strange character sequences in your script, this can be the problem.</span></span> <span data-ttu-id="176c5-132">No exemplo a seguir, um traço (`–`) é exibido como os caracteres `â€“`:</span><span class="sxs-lookup"><span data-stu-id="176c5-132">In the example below, an en-dash (`–`) appears as the characters `â€“`:</span></span>

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

<span data-ttu-id="176c5-133">Esse problema ocorre porque o VSCode codifica o caractere `–` em UTF-8 como os bytes `0xE2 0x80 0x93`.</span><span class="sxs-lookup"><span data-stu-id="176c5-133">This problem occurs because VSCode encodes the character `–` in UTF-8 as the bytes `0xE2 0x80 0x93`.</span></span>
<span data-ttu-id="176c5-134">Quando esses bytes são decodificados como Windows-1252, eles são interpretados como caracteres `â€“`.</span><span class="sxs-lookup"><span data-stu-id="176c5-134">When these bytes are decoded as Windows-1252, they are interpreted as the characters `â€“`.</span></span>

<span data-ttu-id="176c5-135">Algumas sequências de caracteres estranhos que você pode ver incluem:</span><span class="sxs-lookup"><span data-stu-id="176c5-135">Some strange character sequences that you might see include:</span></span>

- <span data-ttu-id="176c5-136">`â€“` em vez de `–`</span><span class="sxs-lookup"><span data-stu-id="176c5-136">`â€“` instead of `–`</span></span>
- <span data-ttu-id="176c5-137">`â€”` em vez de `—`</span><span class="sxs-lookup"><span data-stu-id="176c5-137">`â€”` instead of `—`</span></span>
- <span data-ttu-id="176c5-138">`Ã„2` em vez de `Ä`</span><span class="sxs-lookup"><span data-stu-id="176c5-138">`Ã„2` instead of `Ä`</span></span>
- <span data-ttu-id="176c5-139">`Â` em vez de ` ` (um espaço incondicional)</span><span class="sxs-lookup"><span data-stu-id="176c5-139">`Â` instead of ` `  (a non-breaking space)</span></span>
- <span data-ttu-id="176c5-140">`Ã©` em vez de `é`</span><span class="sxs-lookup"><span data-stu-id="176c5-140">`Ã©` instead of `é`</span></span>

<span data-ttu-id="176c5-141">Nesse útil [referência](https://www.i18nqa.com/debug/utf8-debug.html) lista os padrões comuns que indicam um problema de codificação UTF-8/Windows-1252.</span><span class="sxs-lookup"><span data-stu-id="176c5-141">This handy [reference](https://www.i18nqa.com/debug/utf8-debug.html) lists the common patterns that indicate a UTF-8/Windows-1252 encoding problem.</span></span>

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a><span data-ttu-id="176c5-142">Como a extensão do PowerShell no VSCode interage com codificações</span><span class="sxs-lookup"><span data-stu-id="176c5-142">How the PowerShell extension in VSCode interacts with encodings</span></span>

<span data-ttu-id="176c5-143">A extensão do PowerShell interage com scripts de várias maneiras:</span><span class="sxs-lookup"><span data-stu-id="176c5-143">The PowerShell extension interacts with scripts in a number of ways:</span></span>

1. <span data-ttu-id="176c5-144">Quando os scripts são editados no VSCode, o conteúdo é enviado com o VSCode para a extensão.</span><span class="sxs-lookup"><span data-stu-id="176c5-144">When scripts are edited in VSCode, the contents are sent by VSCode to the extension.</span></span> <span data-ttu-id="176c5-145">O [protocolo de idioma do servidor][] exige que esse conteúdo é transferido em UTF-8.</span><span class="sxs-lookup"><span data-stu-id="176c5-145">The [Language Server Protocol][] mandates that this content is transferred in UTF-8.</span></span> <span data-ttu-id="176c5-146">Portanto, não é possível que a extensão obter a codificação errada.</span><span class="sxs-lookup"><span data-stu-id="176c5-146">Therefore, it is not possible for the extension to get the wrong encoding.</span></span>
2. <span data-ttu-id="176c5-147">Quando os scripts são executados diretamente no Console integrado, que estão lidas do arquivo pelo PowerShell diretamente.</span><span class="sxs-lookup"><span data-stu-id="176c5-147">When scripts are executed directly in the Integrated Console, they're read from the file by PowerShell directly.</span></span> <span data-ttu-id="176c5-148">Se a codificação do PowerShell difere do VSCode, algo pode dar errado aqui.</span><span class="sxs-lookup"><span data-stu-id="176c5-148">If PowerShell's encoding differs from VSCode's, something can go wrong here.</span></span>
3. <span data-ttu-id="176c5-149">Quando um script que está aberto no VSCode faz referência a outro script que não está aberto no VSCode, a extensão de volta ao carregar o conteúdo do script do sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="176c5-149">When a script that is open in VSCode references another script that is not open in VSCode, the extension falls back to loading that script's content from the file system.</span></span> <span data-ttu-id="176c5-150">A extensão do PowerShell padrão é a codificação UTF-8, mas utiliza [marca de ordem de byte][], ou BOM, detecção para selecionar a codificação correta.</span><span class="sxs-lookup"><span data-stu-id="176c5-150">The PowerShell extension defaults to UTF-8 encoding, but uses [byte-order mark][], or BOM, detection to select the correct encoding.</span></span>

<span data-ttu-id="176c5-151">O problema ocorre quando supondo que a codificação da BOM sem formatos (como [UTF-8][] sem BOM e [Windows-1252][]).</span><span class="sxs-lookup"><span data-stu-id="176c5-151">The problem occurs when assuming the encoding of BOM-less formats (like [UTF-8][] with no BOM and [Windows-1252][]).</span></span>
<span data-ttu-id="176c5-152">A extensão do PowerShell padrão é UTF-8.</span><span class="sxs-lookup"><span data-stu-id="176c5-152">The PowerShell extension defaults to UTF-8.</span></span> <span data-ttu-id="176c5-153">A extensão não pode alterar as configurações de codificação do VSCode.</span><span class="sxs-lookup"><span data-stu-id="176c5-153">The extension cannot change VSCode's encoding settings.</span></span>
<span data-ttu-id="176c5-154">Para obter mais informações, consulte [emitir 824 #](https://github.com/Microsoft/vscode/issues/824).</span><span class="sxs-lookup"><span data-stu-id="176c5-154">For more information, see [issue #824](https://github.com/Microsoft/vscode/issues/824).</span></span>

## <a name="choosing-the-right-encoding"></a><span data-ttu-id="176c5-155">Escolher a codificação à direita</span><span class="sxs-lookup"><span data-stu-id="176c5-155">Choosing the right encoding</span></span>

<span data-ttu-id="176c5-156">Aplicativos e sistemas diferentes podem usar codificações diferentes:</span><span class="sxs-lookup"><span data-stu-id="176c5-156">Different systems and applications can use different encodings:</span></span>

- <span data-ttu-id="176c5-157">No .NET Standard, na web e no mundo Linux, UTF-8 é agora a codificação dominante.</span><span class="sxs-lookup"><span data-stu-id="176c5-157">In .NET Standard, on the web, and in the Linux world, UTF-8 is now the dominant encoding.</span></span>
- <span data-ttu-id="176c5-158">Muitos aplicativos do .NET Framework usam [UTF-16][].</span><span class="sxs-lookup"><span data-stu-id="176c5-158">Many .NET Framework applications use [UTF-16][].</span></span> <span data-ttu-id="176c5-159">Por razões históricas, às vezes, isso é chamado de "Unicode", um termo que agora se refere a uma ampla [standard](https://en.wikipedia.org/wiki/Unicode) que inclui o UTF-8 e UTF-16.</span><span class="sxs-lookup"><span data-stu-id="176c5-159">For historical reasons, this is sometimes called "Unicode", a term that now refers to a broad [standard](https://en.wikipedia.org/wiki/Unicode) that includes both UTF-8 and UTF-16.</span></span>
- <span data-ttu-id="176c5-160">No Windows, muitos aplicativos nativos que são anteriores ao Unicode continuam a usar o Windows-1252 por padrão.</span><span class="sxs-lookup"><span data-stu-id="176c5-160">On Windows, many native applications that predate Unicode continue to use Windows-1252 by default.</span></span>

<span data-ttu-id="176c5-161">Codificações Unicode também tem o conceito de uma ordem de byte (BOM) de marcar.</span><span class="sxs-lookup"><span data-stu-id="176c5-161">Unicode encodings also have the concept of a byte-order mark (BOM).</span></span> <span data-ttu-id="176c5-162">BOMs ocorrerem no início do texto para informar um decodificador qual codificação é usando o texto.</span><span class="sxs-lookup"><span data-stu-id="176c5-162">BOMs occur at the beginning of text to tell a decoder which encoding the text is using.</span></span> <span data-ttu-id="176c5-163">Codificações de vários bytes, a BOM também indica [endianness](https://en.wikipedia.org/wiki/Endianness) da codificação.</span><span class="sxs-lookup"><span data-stu-id="176c5-163">For multi-byte encodings, the BOM also indicates [endianness](https://en.wikipedia.org/wiki/Endianness) of the encoding.</span></span> <span data-ttu-id="176c5-164">BOMs são projetados para serem bytes que raramente ocorrem em texto não-Unicode, permitindo que uma estimativa razoável de que o texto é Unicode quando um BOM estiver presente.</span><span class="sxs-lookup"><span data-stu-id="176c5-164">BOMs are designed to be bytes that rarely occur in non-Unicode text, allowing a reasonable guess that text is Unicode when a BOM is present.</span></span>

<span data-ttu-id="176c5-165">BOMs são opcionais e adoção não é tão popular no mundo Linux como uma convenção de confiável de UTF-8 é usada em todos os lugares.</span><span class="sxs-lookup"><span data-stu-id="176c5-165">BOMs are optional and their adoption isn't as popular in the Linux world because a dependable convention of UTF-8 is used everywhere.</span></span> <span data-ttu-id="176c5-166">A maioria dos aplicativos do Linux presumem que a entrada de texto está codificada em UTF-8.</span><span class="sxs-lookup"><span data-stu-id="176c5-166">Most Linux applications presume that text input is encoded in UTF-8.</span></span> <span data-ttu-id="176c5-167">Embora muitos aplicativos Linux reconhecerá e lidar corretamente com um BOM, um número não fizer isso, levando a artefatos no texto manipulado com esses aplicativos.</span><span class="sxs-lookup"><span data-stu-id="176c5-167">While many Linux applications will recognize and correctly handle a BOM, a number do not, leading to artifacts in text manipulated with those applications.</span></span>

<span data-ttu-id="176c5-168">**Portanto**:</span><span class="sxs-lookup"><span data-stu-id="176c5-168">**Therefore**:</span></span>

- <span data-ttu-id="176c5-169">Se você trabalha principalmente com aplicativos do Windows e Windows PowerShell, você deve preferir uma codificação como UTF-8 com BOM ou UTF-16.</span><span class="sxs-lookup"><span data-stu-id="176c5-169">If you work primarily with Windows applications and Windows PowerShell, you should prefer an encoding like UTF-8 with BOM or UTF-16.</span></span>
- <span data-ttu-id="176c5-170">Se funcionar entre plataformas, você deve preferir UTF-8 com BOM.</span><span class="sxs-lookup"><span data-stu-id="176c5-170">If you work across platforms, you should prefer UTF-8 with BOM.</span></span>
- <span data-ttu-id="176c5-171">Se você trabalha principalmente em contextos associados ao Linux, você deve preferir UTF-8 sem BOM.</span><span class="sxs-lookup"><span data-stu-id="176c5-171">If you work mainly in Linux-associated contexts, you should prefer UTF-8 without BOM.</span></span>
- <span data-ttu-id="176c5-172">Windows-1252 e latin 1 são codificações herdadas, essencialmente, você deve evitar se possível.</span><span class="sxs-lookup"><span data-stu-id="176c5-172">Windows-1252 and latin-1 are essentially legacy encodings that you should avoid if possible.</span></span>
  <span data-ttu-id="176c5-173">No entanto, alguns aplicativos do Windows mais antigos podem dependem deles.</span><span class="sxs-lookup"><span data-stu-id="176c5-173">However, some older Windows applications may depend on them.</span></span>
- <span data-ttu-id="176c5-174">Também vale a pena observar que a assinatura de script é [dependente de codificação](https://github.com/PowerShell/PowerShell/issues/3466), que significa que uma alteração de codificação em um script assinado exigirá a assinar novamente.</span><span class="sxs-lookup"><span data-stu-id="176c5-174">It's also worth noting that script signing is [encoding-dependent](https://github.com/PowerShell/PowerShell/issues/3466), meaning a change of encoding on a signed script will require resigning.</span></span>

## <a name="configuring-vscode"></a><span data-ttu-id="176c5-175">Configurando o VSCode</span><span class="sxs-lookup"><span data-stu-id="176c5-175">Configuring VSCode</span></span>

<span data-ttu-id="176c5-176">Da VSCode codificação padrão é UTF-8 sem BOM.</span><span class="sxs-lookup"><span data-stu-id="176c5-176">VSCode's default encoding is UTF-8 without BOM.</span></span>

<span data-ttu-id="176c5-177">Para definir [a codificação do VSCode][], vá para as configurações do VSCode (<kbd>Ctrl<kbd>+</kbd>,</kbd>) e defina o `"files.encoding"` configuração:</span><span class="sxs-lookup"><span data-stu-id="176c5-177">To set [VSCode's encoding][], go to the VSCode settings (<kbd>Ctrl<kbd>+</kbd>,</kbd>) and set the `"files.encoding"` setting:</span></span>

```json
"files.encoding": "utf8bom"
```

<span data-ttu-id="176c5-178">Alguns valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="176c5-178">Some possible values are:</span></span>

- <span data-ttu-id="176c5-179">`utf8`: [UTF-8] sem BOM</span><span class="sxs-lookup"><span data-stu-id="176c5-179">`utf8`: [UTF-8] without BOM</span></span>
- <span data-ttu-id="176c5-180">`utf8bom`: [UTF-8] com BOM</span><span class="sxs-lookup"><span data-stu-id="176c5-180">`utf8bom`: [UTF-8] with BOM</span></span>
- <span data-ttu-id="176c5-181">`utf16le`: Little endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="176c5-181">`utf16le`: Little endian [UTF-16]</span></span>
- <span data-ttu-id="176c5-182">`utf16be`: Big endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="176c5-182">`utf16be`: Big endian [UTF-16]</span></span>
- <span data-ttu-id="176c5-183">`windows1252`: [Windows-1252]</span><span class="sxs-lookup"><span data-stu-id="176c5-183">`windows1252`: [Windows-1252]</span></span>

<span data-ttu-id="176c5-184">Você deve obter uma lista suspensa para isso no modo de exibição de GUI ou exibição de preenchimentos para ele no JSON.</span><span class="sxs-lookup"><span data-stu-id="176c5-184">You should get a dropdown for this in the GUI view, or completions for it in the JSON view.</span></span>

<span data-ttu-id="176c5-185">Você também pode adicionar o seguinte para detecção automática de codificação quando possível:</span><span class="sxs-lookup"><span data-stu-id="176c5-185">You can also add the following to autodetect encoding when possible:</span></span>

```json
"files.autoGuessEncoding": true
```

<span data-ttu-id="176c5-186">Se você não quiser que essas configurações afetam todos os tipos de arquivos, o VSCode também permite que configurações por idioma.</span><span class="sxs-lookup"><span data-stu-id="176c5-186">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="176c5-187">Criar uma configuração específica do idioma, colocando as configurações um `[<language-name>]` campo.</span><span class="sxs-lookup"><span data-stu-id="176c5-187">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="176c5-188">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="176c5-188">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a><span data-ttu-id="176c5-189">Configurar o PowerShell</span><span class="sxs-lookup"><span data-stu-id="176c5-189">Configuring PowerShell</span></span>

<span data-ttu-id="176c5-190">Da PowerShell codificação padrão varia dependendo da versão:</span><span class="sxs-lookup"><span data-stu-id="176c5-190">PowerShell's default encoding varies depending on version:</span></span>

- <span data-ttu-id="176c5-191">No PowerShell 6 +, a codificação padrão é UTF-8 sem BOM em todas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="176c5-191">In PowerShell 6+, the default encoding is UTF-8 without BOM on all platforms.</span></span>
- <span data-ttu-id="176c5-192">No Windows PowerShell, a codificação padrão geralmente é uma extensão do Windows-1252, [latin-1][], também conhecido como ISO 8859-1.</span><span class="sxs-lookup"><span data-stu-id="176c5-192">In Windows PowerShell, the default encoding is usually Windows-1252, an extension of [latin-1][], also known as ISO 8859-1.</span></span>

<span data-ttu-id="176c5-193">No PowerShell 5 +, você pode encontrar sua codificação padrão com este:</span><span class="sxs-lookup"><span data-stu-id="176c5-193">In PowerShell 5+ you can find your default encoding with this:</span></span>

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

<span data-ttu-id="176c5-194">O seguinte [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) pode ser usado para determinar o que a codificação de sua sessão do PowerShell infere para um script sem uma BOM.</span><span class="sxs-lookup"><span data-stu-id="176c5-194">The following [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) can be used to determine what encoding your PowerShell session infers for a script without a BOM.</span></span>

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

<span data-ttu-id="176c5-195">É possível configurar o PowerShell para usar uma codificação fornecida de modo geral, usando as configurações de perfil.</span><span class="sxs-lookup"><span data-stu-id="176c5-195">It's possible to configure PowerShell to use a given encoding more generally using profile settings.</span></span> <span data-ttu-id="176c5-196">Veja os artigos a seguir:</span><span class="sxs-lookup"><span data-stu-id="176c5-196">See the following articles:</span></span>

- <span data-ttu-id="176c5-197">[@mklement0]do [resposta sobre a codificação do PowerShell no StackOverflow](https://stackoverflow.com/a/40098904).</span><span class="sxs-lookup"><span data-stu-id="176c5-197">[@mklement0]'s [answer about PowerShell encoding on StackOverflow](https://stackoverflow.com/a/40098904).</span></span>
- <span data-ttu-id="176c5-198">[@rkeithhill]do [postagem de blog sobre como lidar com a entrada de UTF-8 sem BOM no PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span><span class="sxs-lookup"><span data-stu-id="176c5-198">[@rkeithhill]'s [blog post about dealing with BOM-less UTF-8 input in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span></span>

<span data-ttu-id="176c5-199">Não é possível forçar o PowerShell para usar uma codificação de entrada específica.</span><span class="sxs-lookup"><span data-stu-id="176c5-199">It's not possible to force PowerShell to use a specific input encoding.</span></span> <span data-ttu-id="176c5-200">PowerShell 5.1 e abaixo do padrão de codificação quando não há nenhuma BOM do Windows-1252.</span><span class="sxs-lookup"><span data-stu-id="176c5-200">PowerShell 5.1 and below default to Windows-1252 encoding when there's no BOM.</span></span> <span data-ttu-id="176c5-201">Por motivos de interoperabilidade, é melhor Salvar scripts em um formato Unicode com um BOM.</span><span class="sxs-lookup"><span data-stu-id="176c5-201">For interoperability reasons, it's best to save scripts in a Unicode format with a BOM.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="176c5-202">Qualquer outra ferramenta que você tem que toque PowerShell scripts podem ser afetados pelas suas escolhas de codifica ou recodificar em seus scripts para outra codificação.</span><span class="sxs-lookup"><span data-stu-id="176c5-202">Any other tools you have that touch PowerShell scripts may be affected by your encoding choices or re-encode your scripts to another encoding.</span></span>

### <a name="existing-scripts"></a><span data-ttu-id="176c5-203">Scripts existentes</span><span class="sxs-lookup"><span data-stu-id="176c5-203">Existing scripts</span></span>

<span data-ttu-id="176c5-204">Scripts já está no sistema de arquivos talvez precise ser codificada novamente para sua nova codificação escolhida.</span><span class="sxs-lookup"><span data-stu-id="176c5-204">Scripts already on the file system may need to be re-encoded to your new chosen encoding.</span></span> <span data-ttu-id="176c5-205">A barra de parte inferior do VSCode, você verá o rótulo UTF-8.</span><span class="sxs-lookup"><span data-stu-id="176c5-205">In the bottom bar of VSCode, you'll see the label UTF-8.</span></span> <span data-ttu-id="176c5-206">Clique para abrir a barra de ação e selecione **salvar com codificação**.</span><span class="sxs-lookup"><span data-stu-id="176c5-206">Click it to open the action bar and select **Save with encoding**.</span></span> <span data-ttu-id="176c5-207">Agora você pode escolher uma nova codificação para esse arquivo.</span><span class="sxs-lookup"><span data-stu-id="176c5-207">You can now pick a new encoding for that file.</span></span> <span data-ttu-id="176c5-208">Ver [A codificação do VSCode][] para obter instruções completas.</span><span class="sxs-lookup"><span data-stu-id="176c5-208">See [VSCode's encoding][] for full instructions.</span></span>

<span data-ttu-id="176c5-209">Se você precisar codificar em vários arquivos, você pode usar o script a seguir:</span><span class="sxs-lookup"><span data-stu-id="176c5-209">If you need to re-encode multiple files, you can use the following script:</span></span>

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="176c5-210">O (ISE) Ambiente de Script Integrado do PowerShell</span><span class="sxs-lookup"><span data-stu-id="176c5-210">The PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="176c5-211">Se você também pode editar scripts usando o ISE do PowerShell, você precisará sincronizar suas configurações de codificação.</span><span class="sxs-lookup"><span data-stu-id="176c5-211">If you also edit scripts using the PowerShell ISE, you need to synchronize your encoding settings there.</span></span>

<span data-ttu-id="176c5-212">O ISE deve honrar uma BOM, mas também é possível usar a reflexão para [defina a codificação](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span><span class="sxs-lookup"><span data-stu-id="176c5-212">The ISE should honor a BOM, but it's also possible to use reflection to [set the encoding](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span></span>
<span data-ttu-id="176c5-213">Observe que isso não seria ser persistentes entre empresas iniciantes.</span><span class="sxs-lookup"><span data-stu-id="176c5-213">Note that this wouldn't be persisted between startups.</span></span>

### <a name="source-control-software"></a><span data-ttu-id="176c5-214">Software de controle do código-fonte</span><span class="sxs-lookup"><span data-stu-id="176c5-214">Source control software</span></span>

<span data-ttu-id="176c5-215">Algumas ferramentas de controle do código-fonte, como git, ignorar codificações; o git apenas controla os bytes.</span><span class="sxs-lookup"><span data-stu-id="176c5-215">Some source control tools, such as git, ignore encodings; git just tracks the bytes.</span></span>
<span data-ttu-id="176c5-216">Outros, como o TFS ou Mercurial, talvez não tenham.</span><span class="sxs-lookup"><span data-stu-id="176c5-216">Others, like TFS or Mercurial, may not.</span></span> <span data-ttu-id="176c5-217">Até mesmo algumas ferramentas baseadas em git dependem de decodificação de texto.</span><span class="sxs-lookup"><span data-stu-id="176c5-217">Even some git-based tools rely on decoding text.</span></span>

<span data-ttu-id="176c5-218">Quando esse for o caso, certifique-se de você:</span><span class="sxs-lookup"><span data-stu-id="176c5-218">When this is the case, make sure you:</span></span>

- <span data-ttu-id="176c5-219">Configure o texto no controle de origem para corresponder à sua configuração do VSCode de codificação.</span><span class="sxs-lookup"><span data-stu-id="176c5-219">Configure the text encoding in your source control to match your VSCode configuration.</span></span>
- <span data-ttu-id="176c5-220">Certifique-se de que todos os arquivos são verificados no controle do código-fonte na codificação relevante.</span><span class="sxs-lookup"><span data-stu-id="176c5-220">Ensure all your files are checked into source control in the relevant encoding.</span></span>
- <span data-ttu-id="176c5-221">Esteja atento a alterações para a codificação recebida por meio do controle do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="176c5-221">Be wary of changes to the encoding received through source control.</span></span> <span data-ttu-id="176c5-222">Um sinal de chave deste é uma comparação que indica as alterações, mas onde nada parece ter sido alterado (porque têm de bytes, mas caracteres não têm).</span><span class="sxs-lookup"><span data-stu-id="176c5-222">A key sign of this is a diff indicating changes but where nothing seems to have changed (because bytes have but characters have not).</span></span>

### <a name="collaborators-environments"></a><span data-ttu-id="176c5-223">Ambientes de colaboradores</span><span class="sxs-lookup"><span data-stu-id="176c5-223">Collaborators' environments</span></span>

<span data-ttu-id="176c5-224">Na parte superior, configurando o controle de origem, certifique-se de que seus colaboradores em quaisquer arquivos que você compartilha não tem configurações que substituem a codificação de sua codificação novamente os arquivos do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="176c5-224">On top of configuring source control, ensure that your collaborators on any files you share don't have settings that override your encoding by re-encoding PowerShell files.</span></span>

### <a name="other-programs"></a><span data-ttu-id="176c5-225">Outros programas</span><span class="sxs-lookup"><span data-stu-id="176c5-225">Other programs</span></span>

<span data-ttu-id="176c5-226">Qualquer outro programa que lê ou grava um script do PowerShell pode codificá-lo novamente.</span><span class="sxs-lookup"><span data-stu-id="176c5-226">Any other program that reads or writes a PowerShell script may re-encode it.</span></span>

<span data-ttu-id="176c5-227">Alguns exemplos são:</span><span class="sxs-lookup"><span data-stu-id="176c5-227">Some examples are:</span></span>

- <span data-ttu-id="176c5-228">Usando a área de transferência para copiar e colar um script.</span><span class="sxs-lookup"><span data-stu-id="176c5-228">Using the clipboard to copy and paste a script.</span></span> <span data-ttu-id="176c5-229">Isso é comum em cenários como:</span><span class="sxs-lookup"><span data-stu-id="176c5-229">This is common in scenarios like:</span></span>
  - <span data-ttu-id="176c5-230">Copiar um script em uma VM</span><span class="sxs-lookup"><span data-stu-id="176c5-230">Copying a script into a VM</span></span>
  - <span data-ttu-id="176c5-231">Copiar um script fora de um email ou página da Web</span><span class="sxs-lookup"><span data-stu-id="176c5-231">Copying a script out of an email or webpage</span></span>
  - <span data-ttu-id="176c5-232">Copiar um script para dentro ou fora de um documento do Microsoft Word ou PowerPoint</span><span class="sxs-lookup"><span data-stu-id="176c5-232">Copying a script into or out of a Microsoft Word or PowerPoint document</span></span>
- <span data-ttu-id="176c5-233">Outros editores de texto, como:</span><span class="sxs-lookup"><span data-stu-id="176c5-233">Other text editors, such as:</span></span>
  - <span data-ttu-id="176c5-234">Bloco de notas</span><span class="sxs-lookup"><span data-stu-id="176c5-234">Notepad</span></span>
  - <span data-ttu-id="176c5-235">vim</span><span class="sxs-lookup"><span data-stu-id="176c5-235">vim</span></span>
  - <span data-ttu-id="176c5-236">Qualquer outro editor de script do PowerShell</span><span class="sxs-lookup"><span data-stu-id="176c5-236">Any other PowerShell script editor</span></span>
- <span data-ttu-id="176c5-237">Texto de edição de utilitários, como:</span><span class="sxs-lookup"><span data-stu-id="176c5-237">Text editing utilities, like:</span></span>
  - `Get-Content`/`Set-Content`/`Out-File`
  - <span data-ttu-id="176c5-238">Operadores de redirecionamento do PowerShell, como `>` e `>>`</span><span class="sxs-lookup"><span data-stu-id="176c5-238">PowerShell redirection operators like `>` and `>>`</span></span>
  - `sed`/`awk`
- <span data-ttu-id="176c5-239">Programas de transferência de arquivos, como:</span><span class="sxs-lookup"><span data-stu-id="176c5-239">File transfer programs, like:</span></span>
  - <span data-ttu-id="176c5-240">Um navegador da web, ao fazer o download de scripts</span><span class="sxs-lookup"><span data-stu-id="176c5-240">A web browser, when downloading scripts</span></span>
  - <span data-ttu-id="176c5-241">Um compartilhamento de arquivos</span><span class="sxs-lookup"><span data-stu-id="176c5-241">A file share</span></span>

<span data-ttu-id="176c5-242">Algumas dessas ferramentas lidam de bytes em vez de texto, mas outros oferecem configurações de codifica.</span><span class="sxs-lookup"><span data-stu-id="176c5-242">Some of these tools deal in bytes rather than text, but others offer encoding configurations.</span></span> <span data-ttu-id="176c5-243">Nesses casos em que você precisa configurar uma codificação, você precisará fazer o mesmo que o seu editor de codificação para evitar problemas.</span><span class="sxs-lookup"><span data-stu-id="176c5-243">In those cases where you need to configure an encoding, you need to make it the same as your editor encoding to prevent problems.</span></span>

## <a name="other-resources-on-encoding-in-powershell"></a><span data-ttu-id="176c5-244">Outros recursos na codificação no PowerShell</span><span class="sxs-lookup"><span data-stu-id="176c5-244">Other resources on encoding in PowerShell</span></span>

<span data-ttu-id="176c5-245">Há algumas outras postagens interessantes sobre codificação e configurar a codificação do PowerShell que merecem uma leitura:</span><span class="sxs-lookup"><span data-stu-id="176c5-245">There are a few other nice posts on encoding and configuring encoding in PowerShell that are worth a read:</span></span>

- <span data-ttu-id="176c5-246">[@mklement0]do [resumo de codificação do PowerShell no StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span><span class="sxs-lookup"><span data-stu-id="176c5-246">[@mklement0]'s [summary of PowerShell encoding on StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span></span>
- <span data-ttu-id="176c5-247">Problemas anteriores aberto no vscode do PowerShell para problemas de codificação:</span><span class="sxs-lookup"><span data-stu-id="176c5-247">Previous issues opened on vscode-PowerShell for encoding problems:</span></span>
  - [<span data-ttu-id="176c5-248">#1308</span><span class="sxs-lookup"><span data-stu-id="176c5-248">#1308</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [<span data-ttu-id="176c5-249">#1628</span><span class="sxs-lookup"><span data-stu-id="176c5-249">#1628</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [<span data-ttu-id="176c5-250">#1680</span><span class="sxs-lookup"><span data-stu-id="176c5-250">#1680</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [<span data-ttu-id="176c5-251">#1744</span><span class="sxs-lookup"><span data-stu-id="176c5-251">#1744</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [<span data-ttu-id="176c5-252">#1751</span><span class="sxs-lookup"><span data-stu-id="176c5-252">#1751</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [<span data-ttu-id="176c5-253">O clássico *Joel on Software* escrever sobre Unicode</span><span class="sxs-lookup"><span data-stu-id="176c5-253">The classic *Joel on Software* write up about Unicode</span></span>](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [<span data-ttu-id="176c5-254">Codificação no .NET Standard</span><span class="sxs-lookup"><span data-stu-id="176c5-254">Encoding in .NET Standard</span></span>](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[marca de ordem de byte]: https://wikipedia.org/wiki/Byte_order_mark
[byte-order mark]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Protocolo de idioma do servidor]: https://microsoft.github.io/language-server-protocol/
[Language Server Protocol]: https://microsoft.github.io/language-server-protocol/
[A codificação do VSCode]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[VSCode's encoding]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
