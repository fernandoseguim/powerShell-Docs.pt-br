---
title: Referência do Windows PowerShell - quais são as novidades
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 364d081ddf2f87ceeaa47732266a35f4a126246f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858542"
---
# <a name="whats-new"></a>Novidades

Windows PowerShell 2.0 fornece os seguintes novos recursos para uso durante a gravação de cmdlets, provedores e aplicativos host.

## <a name="modules"></a>Módulos

Agora você pode empacotar e distribuir soluções do Windows PowerShell por meio de módulos. Módulos permitem a partição, organizam e abstraem o código do Windows PowerShell em unidades independentes e reutilizáveis. Para obter mais informações sobre os módulos, consulte Escrevendo um módulo do Windows PowerShell.

## <a name="the-powershell-class"></a>A classe do PowerShell

A classe do PowerShell fornece uma solução mais simples para a criação de aplicativos, chamados de aplicativos de host, que são executados por meio de programação de comandos. Essa classe permite que você criar um pipeline de comandos, especifique o espaço de execução que é usado para executar os comandos e especifique a invocar os comandos de forma síncrona ou assíncrona.

## <a name="the-runspacepool-class"></a>A classe RunspacePool

Pools de Runspace permitem que você crie vários espaços de execução usando uma única chamada. O método CreateRunspacePool fornece várias sobrecargas que podem ser usadas para criar espaços de execução que têm os mesmos recursos, como o mesmo host, o estado de sessão inicial e informações de conexão.

## <a name="the-initialsessionstate-class"></a>A classe InitialSessionState

A classe InitialSessionState permite que você crie uma configuração de estado de sessão que é usada quando um runspace for aberto. Você pode criar uma configuração personalizada, uma configuração padrão que inclui os comandos fornecidos pelo mshshort e uma configuração cujos comandos são restritos com base nos recursos da sessão.

## <a name="remote-runspaces"></a>Espaços de execução remotos

Agora você pode criar espaços de execução que podem ser abertos em computadores remotos, permitindo que você execute comandos no computador remoto e coletar os resultados localmente. Para criar um runspace remoto, você deve especificar informações sobre a conexão remota ao criar o espaço de execução. Consulte os métodos CreateRunspace e CreateRunspacePool para obter exemplos. As informações de conexão são definidas pela classe RunspaceConnectionInfo.

## <a name="private-runspace-elements"></a>Elementos de runspace privado

Agora você pode criar espaços de execução cujos elementos são públicos ou privados. Isso permite que você crie espaços de execução cujos elementos estão disponíveis para o espaço de execução, mas não estão disponíveis para o usuário. Consulte a classe ConstrainedSessionStateEntry para descobrir quais elementos de runspace podem ser feitos particulares.

## <a name="runspace-threading-modes-and-apartment-state"></a>Runspace modos e estado de apartment threading

Agora você pode especificar como os threads são criados e usados ao executar comandos em um runspace. Consulte as propriedades System.Management.Automation.Runspaces.Runspace.ThreadOptions e System.Management.Automation.Runspaces.RunspacePool.ThreadOptions.

Agora você pode obter o estado de apartment dos threads que são usados para executar comandos em um runspace. Consulte as propriedades System.Management.Automation.Runspaces.Runspace.ApartmentState e System.Management.Automation.Runspaces.RunspacePool.ApartmentState.

## <a name="transaction-cmdlets"></a>Cmdlets de transação

Agora você pode criar cmdlets que podem ser usados dentro de uma transação. Quando um cmdlet é usado em uma transação, suas ações são temporárias e podem ser aceitas ou rejeitadas pelos cmdlets de transação fornecidos pelo Windows PowerShell.

Para obter mais informações sobre transações, consulte como oferecem suporte a transações.

## <a name="transaction-provider"></a>Provedor de transação

Agora você pode criar provedores que podem ser usados dentro de uma transação. Semelhante aos cmdlets, quando um provedor é usado em uma transação, suas ações são temporárias e podem ser aceitas ou rejeitadas pelos cmdlets de transação fornecidos pelo Windows PowerShell.

Para obter mais informações sobre como especificar o suporte para transações dentro de uma classe de provedor, consulte a propriedade System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities.

## <a name="job-cmdlets"></a>Cmdlets de trabalho

Agora você pode escrever cmdlets que podem executar sua ação como um trabalho. Esses trabalhos são executados em segundo plano sem interagir com a sessão atual. Para obter mais informações sobre como o Windows PowerShell dá suporte a trabalhos, consulte os trabalhos em segundo plano.

## <a name="cmdlet-output-types"></a>Tipos de saída do cmdlet

Agora você pode especificar os tipos do .NET Framework que são retornados por seus cmdlets declarando o atributo OutputType ao escrever seus cmdlets. Isso permitirá que outras pessoas determinar que tipos de objetos são retornados por um cmdlet, observando a propriedade de tipo de saída do cmdlet.

## <a name="event-support"></a>Suporte a eventos

Agora você pode escrever cmdlets que adicionam e consumir eventos. Consulte a classe PSEvent.

## <a name="proxy-commands"></a>Comandos de proxy

Agora você pode gravar comandos de proxy que podem ser usados para executar outro comando. Um comando de proxy permite que você controle qual funcionalidade do cmdlet do código-fonte está disponível para o usuário. Por exemplo, você pode criar um comando de proxy que remove um parâmetro que é fornecido pelo comando de origem. Consulte a classe ProxyCommand.

## <a name="multiple-choice-prompts"></a>Vários prompts de escolha

Agora você pode escrever aplicativos que podem fornecer avisos que permitem ao usuário selecionar várias opções. Consulte a interface IHostUISupportsMultipleChoiceSelection

## <a name="interactive-sessions"></a>Sessões interativas

Agora você pode escrever aplicativos que podem iniciar e interromper uma sessão interativa em um computador remoto.
Consulte a interface IHostSupportsInteractiveSession.

## <a name="custom-cmdlet-help-for-providers"></a>Ajuda do Cmdlet personalizado para provedores

Agora você pode criar tópicos da Ajuda personalizados para os cmdlets do provedor. Tópicos de Ajuda do cmdlet personalizado podem explicar como o cmdlet funciona nos provedor caminho e o documento recursos especiais, incluindo os parâmetros dinâmicos que adiciona o provedor para o cmdlet.
