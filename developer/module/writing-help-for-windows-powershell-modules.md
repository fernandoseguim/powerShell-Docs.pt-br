---
title: Escrever ajuda para módulos do Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854062"
---
# <a name="writing-help-for-windows-powershell-modules"></a>Escrever ajuda para módulos do Windows PowerShell

Módulos do Windows PowerShell podem incluir tópicos da Ajuda sobre o módulo e sobre os membros do módulo, como cmdlets, provedores, funções e scripts. O `Get-Help` cmdlet exibe os tópicos de Ajuda do módulo no mesmo formato que exibe a Ajuda para outros itens do Windows PowerShell e os usuários usam o padrão `Get-Help` comandos para obter os tópicos da Ajuda.

Este documento explica o formato e o posicionamento correto dos tópicos de Ajuda do módulo e sugere as diretrizes para o conteúdo da Ajuda de módulo.

## <a name="types-of-module-help"></a>Tipos de Ajuda do módulo

Um módulo pode incluir os seguintes tipos de Ajuda.

- **A Ajuda do cmdlet**. Os tópicos da Ajuda que descrevem os cmdlets em um módulo são arquivos XML que usam o comando ajudam do esquema

- **Ajuda do provedor**. Os tópicos da Ajuda que descrevem os provedores em um módulo são arquivos XML que usam o provedor de ajudam do esquema.

- **Ajuda de função**. Os tópicos da Ajuda que descrevem as funções em um módulo pode ser arquivos XML que usam o comando ajudam do esquema ou os tópicos da Ajuda baseada em comentário em função, ou o script ou módulo de script

- **Script Help**. Os tópicos da Ajuda que descrevem os scripts em um módulo pode ser arquivos XML que usam o comando ajudam tópicos de ajuda baseados em comentário no script ou módulo de script ou de esquema.

- **Ajuda ("sobre")**. Você pode usar um tópico da Ajuda ("sobre") conceitual para descrever o módulo e seus membros e explicar como os membros podem ser usados juntos para executar tarefas. Tópicos de ajuda conceituais são arquivos de texto com a codificação Unicode (UTF-8). O nome do arquivo deve usar o `about_<name>.help.txt` formato, como about_MyModule.help.txt. Por padrão, Windows PowerShell inclui mais de 100 destes tópicos conceituais sobre da Ajuda, e eles são formatados como o exemplo a seguir.

  ```
  TOPIC
      about_<subject or module name>

  SHORT DESCRIPTION
      A short, one-line description of the topic contents.

  LONG DESCRIPTION
      A detailed, full description of the subject or purpose of the module.

  EXAMPLES
      Examples of how to use the module or how the subject feature works in practice.

  KEYWORDS
      Terms or titles on which you might expect your users to search for the information in this topic.

  SEE ALSO
      Text-only references for further reading. Hyperlinks cannot work in the Windows PowerShell console.

  ```

## <a name="placement-of-module-help"></a>Posicionamento de Ajuda do módulo

O `Get-Help` cmdlet procura arquivos de tópico da Ajuda de módulo em subdiretórios específicos do idioma do diretório do módulo.

Por exemplo, o diagrama de estrutura de diretório a seguir mostra o local dos tópicos da Ajuda para o módulo SampleModule.

```
<ModulePath>
         \SampleModule
               \<en-US>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml
               \<fr-FR>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml

```

> [!NOTE]
> No exemplo, o  *\<ModulePath >* espaço reservado representa um dos caminhos no `PSModulePath` variável de ambiente, como home\Documents\Modules $, $pshome\Modules ou um caminho personalizado que especifica o usuário.

## <a name="getting-module-help"></a>Obtendo Ajuda do módulo

Quando um usuário importa um módulo em uma sessão, os tópicos da Ajuda do módulo são importados para a sessão, juntamente com o módulo. Você pode listar os arquivos de tópico da Ajuda no valor da chave FileList no manifesto do módulo, mas os tópicos da Ajuda não são afetados pelo `Export-ModuleMember` cmdlet.

Você pode fornecer os tópicos de ajuda de módulo em idiomas diferentes. O `Get-Help` cmdlet exibe automaticamente os tópicos de Ajuda do módulo no idioma especificado para o usuário atual no item no painel de controle Opções regionais e idiomas. No Windows Vista e versões posteriores do Windows, `Get-Help` procura os tópicos da Ajuda em subdiretórios específicos do idioma do diretório do módulo de acordo com os padrões de fallback de idioma estabelecidas para Windows.

A partir do Windows PowerShell 3.0, executando um `Get-Help` comando para um cmdlet ou função dispara a importação automática do módulo. O `Get-Help` imediatamente, o cmdlet exibe o conteúdo dos tópicos da Ajuda no módulo.

Se o módulo não contém tópicos da Ajuda e não há nenhum tópicos da Ajuda para os comandos no módulo no computador do usuário, `Get-Help` exibe a Ajuda gerada automaticamente. A Ajuda gerada automaticamente inclui a sintaxe de comando, parâmetros e tipos de entrada e saída, mas não inclui todas as descrições. A Ajuda gerada automaticamente inclui o texto que direciona o usuário a tentar usar o `Update-Help` cmdlet para baixar a Ajuda para o comando da Internet ou de um compartilhamento de arquivos. Ele também recomenda o uso de **Online** parâmetro do `Get-Help` para obter a versão online do tópico da Ajuda.

## <a name="supporting-updatable-help"></a>Suporte à ajuda atualizável

Os usuários do Windows PowerShell 3.0 e versões posteriores do Windows PowerShell podem baixar e instalar arquivos de Ajuda atualizados para um módulo da Internet ou de um compartilhamento de arquivos local. O `Update-Help` e `Save-Help` cmdlets ocultar os detalhes de gerenciamento do usuário. Os usuários executem o `Update-Help` cmdlet e, em seguida, use o `Get-Help` cmdlet para ler os arquivos de ajuda mais recentes para o módulo no prompt de comando do Windows PowerShell. Os usuários não é necessário reiniciar o Windows ou Windows PowerShell.

Os usuários por trás de firewalls e aqueles sem acesso à Internet podem usar a Ajuda atualizável, também. Acessam a administradores com a Internet usem o `Save-Help` cmdlet para baixar e instalar os arquivos de ajuda mais recentes para um compartilhamento de arquivos. Em seguida, os usuários usam o **caminho** parâmetro do `Update-Help` para obter os arquivos de ajuda mais recentes do compartilhamento de arquivos.

Os autores de módulo podem incluir arquivos de Ajuda no módulo e usar a Ajuda atualizável para atualizar os arquivos de Ajuda ou omitir os arquivos de Ajuda do módulo e usar a Ajuda atualizável para instalar e atualizá-los.

Para obter mais informações sobre a Ajuda atualizável, consulte [suporte à Ajuda atualizável](./supporting-updatable-help.md).

## <a name="supporting-online-help"></a>Suporte à ajuda online

Os usuários que não é possível ou não instalam atualizavam ajuda arquivos em seus computadores frequentemente contam com a versão online dos tópicos de Ajuda do módulo. O **Online** parâmetro do `Get-Help` cmdlet abre a versão online de um cmdlet ou função avançada de tópico de ajuda para o usuário no seu navegador de Internet padrão.

O `Get-Help` cmdlet usa o valor de **HelpUri** propriedade do cmdlet ou função para localizar a versão online do tópico da Ajuda.

Começando no Windows PowerShell 3.0, você pode ajudar os usuários a localizar a versão online dos tópicos de ajuda de cmdlet e a função definindo o atributo HelpUri na classe do cmdlet ou o **HelpUri** propriedade do **CmdletBinding** atributo. O valor do atributo é o valor da **HelpUri** propriedade do cmdlet ou função.

Para obter mais informações, consulte [suporte à Ajuda Online](./supporting-online-help.md).

## <a name="see-also"></a>Consulte Também

[Escrevendo um módulo do Windows PowerShell](./writing-a-windows-powershell-module.md)

[Suporte à Ajuda atualizável](./supporting-updatable-help.md)

[Suporte à Ajuda Online](./supporting-online-help.md)