---
title: Instalar o SDK do Windows PowerShell
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: da1b3dbb8a599aee2cdbab9115aedcab0b4c78c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853952"
---
# <a name="installing-the-windows-powershell-sdk"></a>Instalar o SDK do Windows PowerShell

Aplica-se a: Windows PowerShell 2.0, Windows PowerShell 3.0

O tópico a seguir descreve como instalar o SDK do PowerShell em diferentes versões do Windows.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Instalando o SDK do Windows PowerShell 3.0 para Windows 8 e Windows Server 2012

O Windows PowerShell 3.0 é instalado automaticamente com o Windows 8 e Windows Server 2012. Além disso, você pode baixar e instalar os assemblies de referência para o Windows PowerShell 3.0 como parte do SDK do Windows 8. Esses assemblies permitem que você grave cmdlets, provedores e programas de host no Windows PowerShell 3.0. Quando você instala o SDK do Windows para o Windows 8, os assemblies do Windows PowerShell são instalados automaticamente na pasta do assembly de referência, em \Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0. Para obter mais informações, consulte o SDK do Windows 8 no site de download. Exemplos de código do Windows PowerShell também estão disponíveis no Centro de Desenvolvimento.
Para obter mais informações, consulte a página de exemplo de código de área de trabalho no site do Centro de desenvolvimento.

Além disso, o Windows PowerShell 3.0 é compatível com versões anteriores com o SDK do Windows PowerShell 2.0, que inclui diversos exemplos de código. Para obter mais informações sobre como baixar o SDK do Windows PowerShell 2.0, consulte abaixo. (Observe que, enquanto os exemplos de 2.0 código são compatíveis com o Windows 8 e Windows PowerShell 3.0, você não pode instalar o Windows PowerShell 2.0 em uma plataforma Windows 8).

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Instalando o SDK do Windows PowerShell 3.0 no Windows 7 e Windows Server 2008 R2

O Windows 7 e o Windows Server 2008 R2 têm o PowerShell 2.0 instalado automaticamente. Além disso, você pode instalar o PowerShell 3.0 nesses sistemas. (Para obter mais informações, consulte Instalando o Windows PowerShell.). Conforme descrito acima, você também pode instalar o SDK do Windows 8 no Windows 7 e Windows Server 2008 R2.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Instalando o SDK do Windows PowerShell 2.0 para Windows 7, Vista, XP, Server 2003 e Server 2008

O SDK do Windows PowerShell 2.0 fornece os assemblies de referência necessários para gravar cmdlets, provedores e aplicativos de hospedagem, além de fornecer o código de exemplo em C# que poderá ser usado como ponto de partida quando você começar a gravar código.

Para instalar esse SDK, consulte o SDK do Windows PowerShell 2.0.

### <a name="reference-assemblies"></a>Assemblies de referência

Assemblies de referência são instalados no seguinte local por padrão: c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0.

> [!NOTE]
>
> O código que é compilado nos assemblies do Windows PowerShell 2.0 não pode ser carregado em instalações do Windows PowerShell 1.0. No entanto, o código que é compilado em relação aos assemblies do Windows PowerShell 1.0 pode ser carregado em instalações do Windows PowerShell 2.0.


### <a name="samples"></a>Amostras

Por padrão, exemplos de código são instalados no seguinte local: C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\. As seções a seguir fornecem uma breve descrição da ação de cada amostra.

#### <a name="cmdlet-samples"></a>Amostras de cmdlet

- GetProcessSample01 - mostra como gravar um cmdlet simples que obtém todos os processos no computador local.
- GetProcessSample02 - mostra como adicionar parâmetros ao cmdlet. O cmdlet usa um ou mais nomes de processo e retorna os processos correspondentes.
- GetProcessSample03 - mostra como adicionar parâmetros que aceitam a entrada do pipeline.
- GetProcessSample04 - mostra como manipular erros sem encerramento.
- GetProcessSample05 - mostra como exibir uma lista de processos especificados.
- SelectObject - mostra como gravar um filtro para selecionar apenas determinados objetos.
- SelectString - mostra como pesquisar padrões especificados em arquivos.
- StopProcessSample01 - mostra como implementar um parâmetro PassThru e como solicitar comentários do usuário por chamadas para os métodos de ShouldContinue ShouldProcess. Os usuários especificar o parâmetro PassThru quando quiser forçar o cmdlet para retornar um objeto
- StopProcessSample02 - mostra como interromper um processo específico.
- StopProcessSample03 - mostra como declarar aliases para parâmetros e como dar suporte a curingas.
- StopProcessSample04 - mostra como declarar conjuntos de parâmetros, o objeto que o cmdlet usa como entrada e como especificar o parâmetro padrão definido para usar.

#### <a name="remoting-samples"></a>Amostras de comunicação remota

- RemoteRunspace01 - mostra como criar um runspace remoto que é usado para estabelecer uma conexão remota.
- RemoteRunspacePool01 - mostra como construir um pool de Runspaces remotos e como executar vários comandos simultaneamente usando esse pool.
- Serialization01 - mostra como examinar uma classe existente do .NET e certifique-se de que as informações das propriedades públicas selecionadas dessa classe são preservadas na serialização/desserialização.
- Serialization02 - mostra como examinar uma classe existente do .NET e certifique-se de que informações da instância dessa classe são preservadas na serialização/desserialização, quando as informações não estão disponíveis nas propriedades públicas da classe.
- Serialization03 - mostra como examinar uma classe existente do .NET e certifique-se de que instâncias dessa classe e de classes derivadas são desserializadas (reidratadas) em objetos dinâmicos do .NET.

#### <a name="event-samples"></a>Amostras de eventos

- Event01 - mostra como criar um cmdlet de registro de eventos derivando de ObjectEventRegistrationBase.
- Event02 - mostra como a mostra como receber notificações de eventos do Windows PowerShell que são gerados em computadores remotos. Ele usa o evento PSEventReceived exposto por meio da classe de Runspace.

#### <a name="hosting-application-samples"></a>Amostras de aplicativos de hospedagem

- Runspace01 - mostra como usar a classe do PowerShell para executar o `Get-Process` cmdlet sincronicamente.
O `Get-Process` cmdlet retorna objetos de processo para cada processo em execução no computador local.
- Runspace02 - mostra como usar a classe do PowerShell para executar o `Get-Process` e `Sort-Object` cmdlets de forma síncrona. O `Get-Process` cmdlet retorna objetos de processo para cada processo em execução no computador local e o `Sort-Object` classifica os objetos com base em sua propriedade de Id. Os resultados desses comandos é exibido por meio de um controle DataGridView.
- Runspace03 - mostra como usar a classe do PowerShell para executar um script de forma síncrona e como tratar erros de não finalização. O script recebe uma lista de nomes de processo e, em seguida, recupera tais processos. Os resultados do script, incluindo quaisquer erros de não encerramento gerados durante a execução do script, são exibidos em uma janela do console.
- Runspace04 - mostra como usar a classe do PowerShell para executar comandos e como capturar erros que são gerados ao executar os comandos de finalização. Dois comandos são executados e o último comando é passado um argumento de parâmetro que não é válido. Como resultado, nenhum objeto é retornado e um erro de encerramento é gerado.
- Runspace05 - mostra como adicionar um snap-in a um objeto InitialSessionState para que o cmdlet do snap-in está disponível quando o runspace for aberto. O snap-in fornece um cmdlet Get-Proc (definido pelo exemplo GetProcessSample01) que é executado de forma síncrona usando um objeto do PowerShell.
- Runspace06 - mostra como adicionar um módulo a um objeto InitialSessionState para que o módulo seja carregado quando o runspace for aberto. O módulo fornece um cmdlet Get-Proc (definido pelo GetProcessSample02 exemplo) que é executado de forma síncrona usando um objeto do PowerShell.
- Runspace07 - mostra como criar um runspace e usá-lo para executar dois cmdlets de forma síncrona usando um objeto do PowerShell.
- Runspace08 - mostra como adicionar comandos e argumentos ao pipeline de um objeto do PowerShell e como executar os comandos de forma síncrona.
- Runspace09 - mostra como adicionar um script para o pipeline de um objeto do PowerShell e como executar o script de forma assíncrona. Eventos são usados para tratar a saída do script.
- Runspace10 - mostra como criar um estado de sessão inicial padrão, como adicionar um cmdlet para o InitialSessionState, como criar um runspace que usa o estado de sessão inicial e como executar o comando usando um objeto do PowerShell.
- Runspace11 - mostra como usar a classe ProxyCommand para criar um comando de proxy que chama um cmdlet existente, mas restringe o conjunto de parâmetros disponíveis. O comando de proxy é adicionado a um estado de sessão inicial que é usado para criar um espaço de execução restrito. Isso significa que o usuário pode acessar a funcionalidade do cmdlet apenas por meio do comando proxy.
- PowerShell01 - mostra como criar um runspace restrito usando um objeto InitialSessionState.
- PowerShell02 - mostra como usar um pool de Runspaces para executar vários comandos simultaneamente.

#### <a name="host-samples"></a>Amostras de host

- Host01 - mostra como implementar um aplicativo host que usa um host personalizado. Neste exemplo que é criado um runspace que usa o host personalizado e, em seguida, a API do PowerShell é usada para executar um script que chama "Sair". O aplicativo host analisa a saída do script e imprime os resultados.
- Host02 - mostra como escrever um aplicativo host que usa o tempo de execução do Windows PowerShell, juntamente com uma implementação de host personalizado. O aplicativo host define a cultura do host para alemão, executa o `Get-Process` cmdlet e exibe os resultados como você os veria usando pwrsh.exe e, em seguida, imprime a data e hora atuais em alemão.
- Host03 - mostra como criar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, exibe os resultados no console.
- Host04 - mostra como criar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, exibe os resultados no console. Esse aplicativo host também dá suporte a exibições de avisos que permitem ao usuário especificar várias opções.
- Host05 - mostra como criar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, exibe os resultados no console. Este aplicativo host também dá suporte a chamadas para computadores remotos usando o `Enter-PsSession` e `Exit-PsSession` cmdlets.
- Host06 - mostra como criar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, exibe os resultados no console. Além disso, este exemplo usa as APIs do Criador de Token para especificar a cor do texto inserido pelo usuário.

#### <a name="provider-samples"></a>Amostras de provedor

- AccessDBProviderSample01 - mostra como declarar uma classe de provedor que deriva diretamente da classe CmdletProvider. Ele é incluído aqui apenas para fins de integridade.

- AccessDBProviderSample02 - mostra como substituir os métodos NewDrive e RemoveDrive para dar suporte a chamadas para o `New-PSDrive` e `Remove-PSDrive` cmdlets. A classe de provedor nessa amostra deriva da classe DriveCmdletProvider.

- AccessDBProviderSample03 - mostra como substituir os métodos GetItem e SetItem para dar suporte a chamadas para o `Get-Item` e `Set-Item` cmdlets. A classe de provedor nessa amostra deriva da classe ItemCmdletProvider.

- AccessDBProviderSample04 - mostra como substituir os métodos de contêiner para dar suporte a chamadas para o `Copy-Item`, `Get-ChildItem`, `New-Item`, e `Remove-Item` cmdlets. Esses métodos devem ser implementados quando o armazenamento de dados contiver itens que são contêineres. Um contêiner é um grupo de itens filho em um item pai comum. A classe de provedor nessa amostra deriva da classe ItemCmdletProvider.

- AccessDBProviderSample05 - mostra como substituir os métodos de contêiner para dar suporte a chamadas para o `Move-Item` e `Join-Path` cmdlets. Esses métodos deverão ser implementados quando o usuário precisar mover itens dentro de um contêiner e se o armazenamento de dados contiver contêineres aninhados. A classe de provedor nessa amostra deriva da classe NavigationCmdletProvider.

- AccessDBProviderSample06 - mostra como substituir os métodos de conteúdo para dar suporte a chamadas para o `Clear-Content`, `Get-Content`, e `Set-Content` cmdlets. Esses métodos devem ser implementados quando o usuário precisa gerenciar o conteúdo dos itens no armazenamento de dados. A classe de provedor nessa amostra deriva da classe de NavigationCmdletProvider e ele implementa a interface IContentCmdletProvider.
