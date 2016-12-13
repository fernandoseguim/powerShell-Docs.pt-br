---
title: Instalar o SDK do Windows PowerShell
ms.date: 2016-05-11
keywords: powershell, cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: 8df8b9bb74eba5921263ad9d802dcece41261f9a
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="installing-the-windows-powershell-sdk"></a>Instalar o SDK do Windows PowerShell

O tópico a seguir descreve como instalar o SDK do PowerShell em diferentes versões do Windows.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Instalando o SDK do Windows PowerShell 3.0 para Windows 8 e Windows Server 2012

O Windows PowerShell 3.0 é instalado automaticamente com o Windows 8 e Windows Server 2012.
Além disso, você pode baixar e instalar os assemblies de referência para o Windows PowerShell 3.0 como parte do SDK do Windows 8.
Esses assemblies permitem que você grave cmdlets, provedores e programas de host no Windows PowerShell 3.0.
Quando você instala o SDK do Windows para o Windows 8, os assemblies do Windows PowerShell são instalados automaticamente na pasta do assembly de referência, em \Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0.
Para obter mais informações, visite o [site de download do SDK do Windows 8](http://msdn.microsoft.com/windows/hardware/hh852363.aspx).
Exemplos de código do Windows PowerShell também estão disponíveis no Centro de Desenvolvimento.
Para obter mais informações, confira a página de exemplo de código de Área de Trabalho no [site do Centro de desenvolvimento](http://code.msdn.microsoft.com/windowsdesktop/).

Além disso, o Windows PowerShell 3.0 é compatível com versões anteriores com o SDK do Windows PowerShell 2.0, que inclui diversos exemplos de código.
Para obter mais informações sobre como baixar o SDK do Windows PowerShell 2.0, consulte abaixo.
(Observe que, enquanto os exemplos de 2.0 código são compatíveis com o Windows 8 e Windows PowerShell 3.0, você não pode instalar o Windows PowerShell 2.0 em uma plataforma Windows 8).

##<a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Instalando o SDK do Windows PowerShell 3.0 no Windows 7 e Windows Server 2008 R2

O Windows 7 e o Windows Server 2008 R2 têm o PowerShell 2.0 instalado automaticamente.
Além disso, você pode instalar o PowerShell 3.0 nesses sistemas.
(Para obter mais informações, veja [Installing Windows PowerShell](Installing-Windows-PowerShell.md) [Instalando o Windows PowerShell]).
Conforme descrito acima, você também pode instalar o SDK do Windows 8 no Windows 7 e Windows Server 2008 R2.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Instalando o SDK do Windows PowerShell 2.0 para Windows 7, Vista, XP, Server 2003 e Server 2008

O SDK do Windows PowerShell 2.0 fornece os assemblies de referência necessários para gravar cmdlets, provedores e aplicativos de hospedagem, além de fornecer o código de exemplo em C# que poderá ser usado como ponto de partida quando você começar a gravar código.

Para instalar esse SDK, veja [Windows PowerShell 2.0 SDK](http://go.microsoft.com/fwlink/?LinkId=184611) (SDK do Windows PowerShell 2.0).

## <a name="reference-assemblies"></a>Assemblies de referência

Assemblies de referência são instalados, por padrão, no seguinte local: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.

> **Observação**: o código que é compilado nos assemblies do Windows PowerShell 2.0 não pode ser carregado em instalações do Windows PowerShell 1.0.
>No entanto, o código que é compilado em relação aos assemblies do Windows PowerShell 1.0 pode ser carregado em instalações do Windows PowerShell 2.0.

## <a name="samples"></a>Amostras

Exemplos de código são instalados, por padrão, no seguinte local: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.

As seções a seguir fornecem uma breve descrição da ação de cada amostra.

## <a name="cmdlet-samples"></a>Amostras de cmdlet
**GetProcessSample01**

Mostra como gravar um cmdlet simples que coloca todos os processos no computador local.

**GetProcessSample02**

Mostra como adicionar parâmetros ao cmdlet.
O cmdlet usa um ou mais nomes de processo e retorna os processos correspondentes.

**GetProcessSample03**

Mostra como adicionar parâmetros que aceitam a entrada do pipeline.

**GetProcessSample04**

Mostra como tratar erros de não encerramento.

**GetProcessSample05**

Mostra como exibir uma lista de processos especificados.

**SelectObject**

Mostra como gravar um filtro para selecionar apenas determinados objetos.

**SelectString**

Mostra como pesquisar padrões especificados em arquivos.

**StopProcessSample01**

Mostra como implementar um parâmetro *PassThru* e como solicitar comentários do usuário por chamadas para os métodos [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) e [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx).
Os usuários especificam o parâmetro *PassThru* quando querem forçar o cmdlet a retornar um objeto de parâmetro.

**StopProcessSample02**

Mostra como interromper um processo específico.

**StopProcessSample03**

Mostra como declarar aliases para parâmetros e como dar suporte a curingas.

**StopProcessSample04**

Mostra como declarar conjuntos de parâmetros, o objeto que o cmdlet usa como entrada, e como especificar o parâmetro padrão definido a ser usado.

## <a name="remoting-samples"></a>Amostras de comunicação remota

**RemoteRunspace01**

Mostra como criar um runspace remoto que é usado para estabelecer uma conexão remota.

**RemoteRunspacePool01**

Mostra como construir um pool de runspaces remotos e como executar vários comandos simultaneamente usando esse pool.

**Serialization01**

Mostra como examinar uma classe existente do .NET e garantir que as informações das propriedades públicas selecionadas dessa classe são preservadas na serialização/desserialização.

**Serialization02**

Mostra como examinar uma classe existente do .NET e garantir que as informações da instância dessa classe são preservadas na serialização/desserialização quando as informações não estão disponíveis nas propriedades públicas da classe.

**Serialization03**

Mostra como examinar uma classe existente do .NET e garantir que as instâncias dessa classe e de classes derivadas são desserializadas (reidratadas) em objetos dinâmicos do .NET.

## <a name="event-samples"></a>Amostras de eventos

**Event01**

Mostra como criar um cmdlet de registro de eventos, fazendo a derivação de ObjectEventRegistrationBase.

**Event02**

Mostra como receber notificações de eventos do Windows PowerShell gerados em computadores remotos.
Usa o evento PSEventReceived exposto por meio da classe [Runspace](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx).

## <a name="hosting-application-samples"></a>Amostras de aplicativos de hospedagem

**Runspace01**

Mostra como usar a classe [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) para executar o cmdlet [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) de forma síncrona.
O cmdlet [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) retorna os objetos [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) de cada processo em execução no computador local.

**Runspace02**

Mostra como usar a classe [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) para executar os cmdlets [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) e [Sort-Object](http://go.microsoft.com/fwlink/?LinkID=113403) de forma síncrona.
O cmdlet [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) retorna os objetos [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) de cada processo em execução no computador local e Sort-Object classifica os objetos com base em sua propriedade [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx).
Os resultados desses comandos são exibidos com o uso de um controle [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx).

**Runspace03**

Mostra como usar a classe [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) para executar um script de forma síncrona e como tratar erros de não encerramento.
O script recebe uma lista de nomes de processo e, em seguida, recupera tais processos.
Os resultados do script, incluindo quaisquer erros de não encerramento gerados durante a execução do script, são exibidos em uma janela do console.

**Runspace04**

Mostra como usar a classe [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) para executar comandos e como capturar erros de encerramento gerados durante a execução de comandos.
Dois comandos são executados e o último comando é passado um argumento de parâmetro que não é válido.
Como resultado, nenhum objeto é retornado e um erro de encerramento é gerado.

**Runspace05**

Mostra como adicionar um snap-in a um objeto [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) para que o cmdlet do snap-in esteja disponível quando o runspace for aberto.
O snap-in fornece um cmdlet Get-Proc (definido pela [Amostra GetProcessSample01](https://technet.microsoft.com/library/ff602028.aspx)) que é executado de forma síncrona usando um objeto [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx).

**Runspace06**

Mostra como adicionar um módulo a um objeto [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) para que o módulo seja carregado quando o runspace for aberto.
O módulo fornece um cmdlet Get-Proc (definido pelo [GetProcessSample02 exemplo](https://technet.microsoft.com/library/ff602027.aspx)) executado de forma síncrona com o uso de um objeto [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx).

**Runspace07**

Mostra como criar um runspace e usá-lo para executar dois cmdlets de forma síncrona usando um objeto [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx).

**Runspace08**

Mostra como adicionar comandos e argumentos ao pipeline de um objeto [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) e como executar os comandos de forma síncrona.

**Runspace09**

Mostra como adicionar um script ao pipeline de um objeto [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) e como executar o script de forma assíncrona.
Eventos são usados para tratar a saída do script.

**Runspace10**

Mostra como criar um estado de sessão inicial padrão, como adicionar um cmdlet ao [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx), como criar um runspace que usa o estado de sessão inicial e como executar o comando usando um objeto [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx).

**Runspace11**

Mostra como usar a classe [ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx) para criar um comando proxy que chama um cmdlet existente, mas restringe o conjunto de parâmetros disponíveis.
O comando de proxy é adicionado a um estado de sessão inicial que é usado para criar um espaço de execução restrito.
Isso significa que o usuário pode acessar a funcionalidade do cmdlet apenas por meio do comando proxy.

**PowerShell01**

Mostra como criar um runspace restrito usando um objeto [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx).

**PowerShell02**

Mostra como usar um pool de runspaces para executar vários comandos simultaneamente.

## <a name="host-samples"></a>Amostras de host

**Host01**

Mostra como implementar um aplicativo host que usa um host personalizado.
Nesta amostra, é criado um runspace que usa o host personalizado e, em seguida, a API [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) é usada para executar um script que chama a “saída”.
O aplicativo host analisa a saída do script e imprime os resultados.

**Host02**

Mostra como gravar um aplicativo host que usa o tempo de execução do Windows PowerShell, juntamente com uma implementação de host personalizado.
O aplicativo host define a cultura do host para alemão, executa o cmdlet [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324), exibe os resultados como seriam vistos com pwrsh.exe e imprime a data e hora atuais em alemão.

**Host03**

Mostra como criar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e exibe os resultados para o console.

**Host04**

Mostra como criar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e exibe os resultados para o console.
Esse aplicativo host também dá suporte a exibições de avisos que permitem ao usuário especificar várias opções.

**Host05**

Mostra como criar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e exibe os resultados para o console.
Este aplicativo host também dá suporte a chamadas para computadores remotos com os cmdlets [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) e [Exit-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212).

**Host06**

Mostra como criar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e exibe os resultados para o console.
Além disso, este exemplo usa as APIs do Criador de Token para especificar a cor do texto inserido pelo usuário.

## <a name="provider-samples"></a>Amostras de provedor

**AccessDBProviderSample01**

Mostra como declarar uma classe de provedor que deriva diretamente da classe [CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx).
Ele é incluído aqui apenas para fins de integridade.

**AccessDBProviderSample02**

Mostra como substituir os métodos [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) e [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) para dar suporte a chamadas para os cmdlets New-PSDrive e Remove-PSDrive.
A classe de provedor nessa amostra deriva da classe [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx).

**AccessDBProviderSample03**

Mostra como substituir os métodos [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) e [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) para dar suporte a chamadas para os cmdlets Get-Item e Set-Item.
A classe de provedor nessa amostra deriva da classe [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx).

**AccessDBProviderSample04**

Mostra como substituir os métodos de contêiner para dar suporte a chamadas para os cmdlets Copy-Item, Get-ChildItem, New-Item e Remove-Item.
Esses métodos devem ser implementados quando o armazenamento de dados contiver itens que são contêineres.
Um contêiner é um grupo de itens filho em um item pai comum.
A classe de provedor nessa amostra deriva da classe [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx).

**AccessDBProviderSample05**

Mostra como substituir os métodos de contêiner para dar suporte a chamadas para os cmdlets Move-Item e Join-Path.
Esses métodos deverão ser implementados quando o usuário precisar mover itens dentro de um contêiner e se o armazenamento de dados contiver contêineres aninhados.
A classe de provedor nessa amostra deriva da classe [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx).

**AccessDBProviderSample06**

Mostra como substituir os métodos de conteúdo para dar suporte a chamadas para os cmdlets Clear-Content, Get-Content e Set-Content.
Esses métodos devem ser implementados quando o usuário precisa gerenciar o conteúdo dos itens no armazenamento de dados.
A classe de provedor nessa amostra deriva da classe [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) e implementa a interface [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx).
