---
title: Palavras-chave de ajuda baseados em comentário | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab90ec96-77f5-42e3-9c7e-2f4156ec207f
caps.latest.revision: 6
ms.openlocfilehash: af8a151070d26ffe236800076115c964f625e572
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058072"
---
# <a name="comment-based-help-keywords"></a>Palavras-chave de ajuda baseada em comentários

Este tópico lista e descreve as palavras-chave na Ajuda baseada em comentário.

## <a name="keywords-in-comment-based-help"></a>Palavras-chave na Ajuda baseada em comentários

A seguir é válidos baseados em comentário ajuda palavras-chave. Eles são listados na ordem em que eles normalmente são exibidos em um tópico de Ajuda, juntamente com seu uso pretendido. Essas palavras-chave pode aparecer em qualquer ordem na Ajuda baseada em comentários e eles não diferenciam maiusculas de minúsculas.

Observe que o `.ExternalHelp` palavra-chave tem precedência sobre todas as outras ajuda baseada em comentário as palavras-chave. Quando `.ExternalHelp` estiver presente, o [Microsoft.PowerShell.Commands.Get ajuda](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help) cmdlet não exibe a Ajuda baseada em comentários, mesmo quando ele não é possível localizar um arquivo de Ajuda que corresponde ao valor da palavra-chave.

`.Synopsis` Uma breve descrição da função ou script. Essa palavra-chave pode ser usado apenas uma vez em cada tópico.

`.Description` Uma descrição detalhada da função ou script. Essa palavra-chave pode ser usado apenas uma vez em cada tópico.

`.Parameter` *\<Nome do parâmetro >* a descrição de um parâmetro. Você pode incluir um `.Parameter` palavra-chave para cada parâmetro na função ou script.

O `.Parameter` palavras-chave podem aparecer em qualquer ordem no bloco de comentário, mas a ordem na qual os parâmetros aparecem no `Param` declaração de função ou instrução determina a ordem na qual os parâmetros aparecem no tópico da Ajuda. Para alterar a ordem dos parâmetros no tópico da Ajuda, alterar a ordem dos parâmetros no `Param` declaração de função ou instrução.

Você também pode especificar uma descrição do parâmetro, colocando um comentário no `Param` instrução imediatamente antes do nome da variável de parâmetro. Se você usar ambos um `Param` comentário de instrução e uma `.Parameter` palavra-chave, a descrição associada a `.Parameter` palavra-chave é usada e o `Param` instrução comentário é ignorado.

`.Example` Um comando de exemplo que usa a função ou script, opcionalmente seguido por um exemplo de saída e uma descrição. Repita essa palavra-chave para cada exemplo.

`.Inputs` Os tipos de Microsoft .NET Framework de objetos que podem ser redirecionados para a função ou script. Você também pode incluir uma descrição dos objetos de entrada.

`.Outputs` O tipo do .NET Framework dos objetos que o cmdlet retorna. Você também pode incluir uma descrição dos objetos retornados.

`.Notes` Informações adicionais sobre a função ou script.

`.Link` O nome de um tópico relacionado. Repita essa palavra-chave para cada tópico relacionado. Este conteúdo é exibido na seção Links relacionados do tópico da Ajuda.

O `.Link` conteúdo de palavra-chave também pode incluir um identificador de URI (Uniform Resource) para uma versão online do mesmo tópico da Ajuda. A versão online é aberto quando você usa o `Online` parâmetro de Get-Help. O URI deve começar com "http" ou "https".

`.Component` A tecnologia ou recurso que usa a função ou script, ou para o qual ele está relacionado. Este conteúdo é exibido quando o comando Get-Help inclui o `Component` parâmetro de Get-Help.

`.Role` A função de usuário para o tópico da Ajuda. Este conteúdo é exibido quando o comando Get-Help inclui o `Role` parâmetro de Get-Help.

`.Functionality` O uso pretendido da função. Este conteúdo é exibido quando o comando Get-Help inclui o `Functionality` parâmetro de Get-Help.

`.ForwardHelpTargetName` `<Command-Name>` Redireciona para o tópico da Ajuda para o comando especificado. Você pode redirecionar os usuários a qualquer tópico de Ajuda, incluindo tópicos de ajuda para uma função, o script, o cmdlet ou o provedor.

`.ForwardHelpCategory` `<Category>` Especifica a categoria de Ajuda do item no ForwardHelpTargetName. Valores válidos são Alias, Cmdlet, HelpFile, função, provedor, gerais, perguntas Frequentes, glossário, ScriptCommand, ExternalScript, filtro ou todos. Use essa palavra-chave para evitar conflitos quando há comandos com o mesmo nome.

`.RemoteHelpRunspace` `<PSSession-variable>` Especifica uma sessão que contém o tópico da Ajuda. Insira uma variável que contém uma PSSession. Essa palavra-chave é usada pelo `Export-PSSession` cmdlet para localizar os tópicos de ajuda para os comandos exportados.

`.ExternalHelp` `<XML Help File>` Especifica o caminho e/ou o nome de um arquivo de ajuda baseados em XML para o script ou função.

O `.ExternalHelp` palavra-chave informa o [Microsoft.PowerShell.Commands.Get ajuda](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help) cmdlet para obter ajuda para o script ou função em um arquivo baseado em XML. O **. ExternalHelp** palavra-chave é necessária ao usar um arquivo de ajuda baseados em XML para uma função ou script. Sem ele, `Get-Help` não encontrará um arquivo de ajuda para a função ou script.

O `.ExternalHelp` palavra-chave tem precedência sobre todas as outras ajuda baseada em comentário as palavras-chave. Quando `.ExternalHelp` estiver presente, o [Microsoft.PowerShell.Commands.Get ajuda](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help) cmdlet não exibe a Ajuda baseada em comentários, mesmo quando ele não é possível localizar um arquivo de Ajuda que corresponde ao valor da palavra-chave.

Quando a função seja exportada por um módulo de script, o valor de `.ExternalHelp` deve ser um nome de arquivo sem um caminho. `Get-Help` procura o arquivo em um subdiretório específico de localidade do diretório do módulo. Não há nenhum requisito para o nome do arquivo, mas uma prática recomendada é usar o seguinte formato de nome de arquivo: `<ScriptModule>.psm1-help.xml`.

Quando a função não está associada um módulo, incluir um nome de arquivo e caminho no valor da **. ExternalHelp** palavra-chave. Se o caminho especificado para o arquivo XML contiver subpastas específicas da cultura de interface do usuário, `Get-Help` pesquisa recursivamente o subdiretórios para um arquivo XML com o nome do script ou função de acordo com o idioma de fallback padrões estabelecidos para Windows, assim como faz em todos os tópicos de ajuda baseados em XML.

Para obter mais informações sobre o formato de arquivo de ajuda baseada em XML de Ajuda do cmdlet, consulte [escrita Windows PowerShell Cmdlet ajuda](./writing-help-for-windows-powershell-cmdlets.md).