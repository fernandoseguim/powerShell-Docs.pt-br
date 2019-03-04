---
title: Escrever ajuda para funções e Scripts do PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859a6e22-75b1-43d4-ba62-62c107803b37
caps.latest.revision: 7
ms.openlocfilehash: 98a3f61ff4fa2367f69357173d4e8e14288ff429
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857472"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a>Escrever ajuda para funções e Scripts do PowerShell

Funções e scripts do PowerShell devem ser totalmente documentadas sempre que eles são compartilhados com outras pessoas.
O `Get-Help` cmdlet exibe os tópicos de Ajuda do script e a função no mesmo formato que ele exibe a Ajuda para cmdlets e todos o `Get-Help` parâmetros funcionam nos tópicos de Ajuda do script e a função.

Scripts do PowerShell podem incluir um tópico da Ajuda sobre o script e os tópicos da Ajuda sobre cada funções no script.
Funções que são compartilhadas independentemente dos scripts podem incluir suas próprias tópicos da Ajuda.

Este documento explica o formato e o posicionamento correto dos tópicos da Ajuda e sugere as diretrizes para o conteúdo.

## <a name="types-of-script-and-function-help"></a>Tipos de Script e ajuda de função

### <a name="comment-based-help"></a>Ajuda baseada em comentário
O tópico da Ajuda que descreve um script ou função pode ser implementado como um conjunto de comentários no script ou função.
Ao escrever a Ajuda baseada em comentário para um script e para funções em um script, preste bastante atenção as regras para colocar a Ajuda baseada em comentário.
O posicionamento determinará se o `Get-Help` cmdlet associa o tópico de ajuda com o script ou uma função.
Para obter mais informações sobre como escrever tópicos de ajuda baseada em comentários, consulte [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

### <a name="xml-based-command-help"></a>Ajuda de comando baseado em XML
O tópico da Ajuda que descreve um script ou função pode ser implementado em um arquivo XML que usa o esquema de ajuda de comando.
Para associar o script ou função com o arquivo XML, use o `ExternalHelp` comentar a palavra-chave seguida pelo caminho e nome do arquivo XML.

Quando o `ExternalHelp` comentar a palavra-chave estiver presente, ela terá precedência sobre a Ajuda baseada em comentário, mesmo quando `Get-Help` não é possível localizar um arquivo de Ajuda que corresponde ao valor do `ExternalHelp` palavra-chave.

### <a name="online-help"></a>Ajuda Online
Você pode postar seus tópicos da Ajuda na Internet e, em seguida, direcionar `Get-Help` para abrir os tópicos.
Para obter mais informações sobre como escrever tópicos de ajuda baseada em comentários, consulte [suporte à Ajuda Online](../module/supporting-online-help.md).

Não há nenhum método estabelecido para gravação tópicos para scripts e funções ("sobre").
No entanto, você pode postar tópicos conceituais sobre a lista de Internet os tópicos e as URLs na seção Links relacionados de um tópico de ajuda de comando.

## <a name="content-considerations-for-script-and-function-help"></a>Considerações de conteúdo para o Script e a função de ajuda

- Se você estiver escrevendo um tópico da ajuda muito breve com apenas algumas das seções de ajuda de comando disponíveis, certifique-se de incluir claras descrições dos parâmetros de script ou função. Também incluem um ou dois comandos de exemplo na seção de exemplos, mesmo se você optar por omitir as descrições de exemplo.

- Em todas as descrições, consulte o comando como um script ou função. Essas informações ajudam o usuário a entender e gerenciar o comando.

  Por exemplo, a descrição detalhada a seguir indica que o comando New-tópico é um script. Isso informa os usuários precisam para especificar o caminho e o nome completo quando eles o executam.

  > "O script New-tópico cria um tópico conceitual em branco para cada nome de tópico no arquivo de entrada..."

  A descrição detalhada a seguir declara que `Disable-PSRemoting` é uma função. Essa informação é particularmente útil para os usuários quando a sessão inclui vários comandos com o mesmo nome, algumas das quais podem estar oculto por um comando com precedência mais alta.

  > O `Disable-PSRemoting` função desabilita todas as configurações de sessão no computador local...

- Em um tópico de Ajuda do script, explicam como usar o script como um todo. Se você também estiver escrevendo tópicos de ajuda para funções no script, Mencione as funções do seu tópico de Ajuda do script e incluem referências a tópicos de ajuda de função na seção Links relacionados do tópico da Ajuda do script. Por outro lado, quando uma função é parte de um script, explique no tópico da Ajuda de função a função que a função desempenha no script e como ele pode ser usado de forma independente. Em seguida, liste o tópico de Ajuda do script na seção Links relacionados do tópico da Ajuda de função.

- Ao escrever exemplos, para um tópico de Ajuda do script, certifique-se de incluir o caminho para o arquivo de script no exemplo de comando. Isso lembra os usuários que eles devem especificar o caminho explicitamente, mesmo quando o script estiver no diretório atual.

- Em um tópico de ajuda de função, lembre os usuários que a função existe apenas na sessão atual e, para usá-la em outras sessões, eles precisam para adicioná-lo, ou adicioná-lo um perfil do PowerShell.

- `Get-Help` Exibe o tópico de ajuda para uma função ou script apenas quando o arquivo de script e arquivos de tópicos de ajuda são salvos nos locais corretos. Portanto, não é útil incluir instruções para instalar o PowerShell, ou salvar ou instalando o script ou função em um tópico de Ajuda do script ou função. Em vez disso, inclua quaisquer instruções de instalação no documento que você usar para distribuir o script ou função.

## <a name="see-also"></a>Consulte Também

 [Escrevendo XML com base em tópicos da Ajuda para Scripts e funções](./writing-xml-based-help-topics-for-scripts-and-functions.md)

 [Escrevendo XML com base em tópicos de ajuda para comandos](./writing-xml-based-help-topics-for-commands.md)

 [Escrever tópicos de ajuda baseados em comentário](./writing-comment-based-help-topics.md)
