---
title: Instalar o SDK do Windows PowerShell
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 9ba9ef3efe6a8ae85d96b59db53ad3a16bf57699

---

# Instalar o SDK do Windows PowerShell
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>O tópico a seguir descreve como instalar o SDK do PowerShell em diferentes versões do Windows.</para>
  </introduction>
  <section>
    <title>A instalação do SDK do Windows PowerShell 3.0 para Windows 8 e Windows Server 2012</title>
    <content>
      <para>Windows PowerShell 3.0 é realizada automaticamente com o Windows 8 e Windows Server 2012. Além disso, você pode baixar e instalar os assemblies de referência para o Windows PowerShell 3.0 como parte do SDK do Windows 8. Esses assemblies permitem que você grave cmdlets, provedores e programas de host no Windows PowerShell 3.0. Quando você instala o SDK do Windows para o Windows 8, os assemblies do Windows PowerShell são instalados automaticamente na pasta do assembly de referência, em \Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0. Para obter mais informações, consulte o <externalLink><linkText>site de download do SDK do Windows 8</linkText><linkUri>https://developer.microsoft.com/pt-br/windows/downloads/windows-8-sdk</linkUri></externalLink>. Exemplos de código do Windows PowerShell também estão disponíveis no Centro de Desenvolvimento. Para obter mais informações, consulte a página de exemplo de código de área de trabalho no <externalLink><linkText>site do Centro de Desenvolvimento</linkText><linkUri>http://code.msdn.microsoft.com/windowsdesktop/</linkUri></externalLink>. </para>
      <para>Além disso, o Windows PowerShell 3.0 é compatível com versões anteriores com o SDK do Windows PowerShell 2.0, que inclui diversos exemplos de código. Para obter mais informações sobre como baixar o SDK do Windows PowerShell 2.0, consulte abaixo. (Observe que, enquanto os exemplos de 2.0 código são compatíveis com o Windows 8 e Windows PowerShell 3.0, você não pode instalar o Windows PowerShell 2.0 em uma plataforma Windows 8). </para>
    </content>
  </section>
  <section>
    <title>A instalação do SDK do Windows PowerShell 3.0 para Windows 7 e Windows Server 2008 R2</title>
    <content>
      <para>Windows 7 e Windows Server 2008 R2 automaticamente tem o PowerShell 2.0 instalado. Além disso, você pode instalar o PowerShell 3.0 nesses sistemas. (Para obter mais informações, consulte <link xlink:href="6fbb0409-5a54-48ec-95e6-7f8b7d8c4969">Installing Windows PowerShell</link> [Instalando o Windows PowerShell]). Conforme descrito acima, você também pode instalar o SDK do Windows 8 no Windows 7 e Windows Server 2008 R2.</para>
    </content>
  </section>
  <section>
    <title>Instalando o SDK do Windows PowerShell 2.0 para Windows 7, Vista, XP, Server 2003 e Server 2008</title>
    <content>
      <para>O SDK <token>mshshort</token> 2.0 fornece os assemblies de referência necessários para gravar cmdlets, provedores e aplicativos de hospedagem, além de fornecer o exemplo de código C# que pode ser usado como o ponto de partida quando começar a gravar código. </para>
      <para>Para instalar esse SDK, consulte <externalLink><linkText>SDK do Windows PowerShell 2.0</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=184611</linkUri></externalLink>.</para>
    </content>
    <sections>
      <section>
        <title>Assemblies de referência</title>
        <content>
          <para>Assemblies de referência são instalados no seguinte local por padrão: <codeInline>c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0</codeInline>.</para>
          <alert class="note">
            <para>Código que é compilado em relação aos assemblies do Windows PowerShell 2.0 não pode ser carregado em instalações do Windows PowerShell 1.0. No entanto, o código que é compilado em relação aos assemblies do Windows PowerShell 1.0 pode ser carregado em instalações do Windows PowerShell 2.0.</para>
          </alert>
        </content>
      </section>
      <section>
        <title>Exemplos</title>
        <content>
          <para>Exemplos de código são instalados no seguinte local por padrão: <codeInline>C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\</codeInline>.</para>
          <para>As seções a seguir fornecem uma breve descrição do que cada exemplo faz.</para>
        </content>
        <sections>
          <section>
            <title>Exemplos de cmdlet</title>
            <content>
              <definitionTable>
                <definedTerm>GetProcessSample01</definedTerm>
                <definition>
                  <para>Mostra como gravar um cmdlet simples que obtém todos os processos no computador local.</para>
                </definition>
                <definedTerm>GetProcessSample02</definedTerm>
                <definition>
                  <para>Mostra como adicionar parâmetros ao cmdlet. O cmdlet obtém um ou mais nomes de processos e retorna os processos correspondentes.</para>
                </definition>
                <definedTerm>GetProcessSample03</definedTerm>
                <definition>
                  <para>Mostra como adicionar parâmetros que aceitam entrada do pipeline.</para>
                </definition>
                <definedTerm>GetProcessSample04</definedTerm>
                <definition>
                  <para>Mostra como manipular erros sem encerramento.</para>
                </definition>
                <definedTerm>GetProcessSample05</definedTerm>
                <definition>
                  <para>Mostra como exibir uma lista de processos especificados.</para>
                </definition>
                <definedTerm>SelectObject</definedTerm>
                <definition>
                  <para>Mostra como gravar um filtro para selecionar apenas determinados objetos. </para>
                </definition>
                <definedTerm>SelectString</definedTerm>
                <definition>
                  <para>Mostra como pesquisar padrões especificados em arquivos.</para>
                </definition>
                <definedTerm>StopProcessSample01</definedTerm>
                <definition>
                  <para>Mostra como implementar um parâmetro <parameterReference>PassThru</parameterReference> e como solicitar comentários do usuário por chamadas para o método <codeEntityReference>Overload:System.Management.Automation.Cmdlet.ShouldProcess</codeEntityReference> e <codeEntityReference>Overload:System.Management.Automation.Cmdlet.ShouldContinue</codeEntityReference>. Os usuários especificam o parâmetro <parameterReference>PassThru</parameterReference> quando quiserem forçar o cmdlet a retornar um objeto, </para>
                </definition>
                <definedTerm>StopProcessSample02</definedTerm>
                <definition>
                  <para>Mostra como interromper um processo específico.</para>
                </definition>
                <definedTerm>StopProcessSample03</definedTerm>
                <definition>
                  <para>Mostra como declarar aliases para parâmetros e como oferecer suporte a caracteres curinga.</para>
                </definition>
                <definedTerm>StopProcessSample04</definedTerm>
                <definition>
                  <para>Mostra como declarar conjuntos de parâmetros, o objeto que o cmdlet aceita como entrada e como especificar o parâmetro padrão definido para usar.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>Exemplos de comunicação remota</title>
            <content>
              <definitionTable>
                <definedTerm>RemoteRunspace01</definedTerm>
                <definition>
                  <para>Mostra como criar um espaço de trabalho remoto que é usado para estabelecer uma conexão remota.</para>
                </definition>
                <definedTerm>RemoteRunspacePool01</definedTerm>
                <definition>
                  <para>Mostra como construir um pool de espaço de trabalho remoto e como executar vários comandos simultaneamente usando esse pool.</para>
                </definition>
                <definedTerm>Serialization01</definedTerm>
                <definition>
                  <para>Mostra como examinar uma classe .NET existente e certificar-se de que as informações de propriedades públicas selecionadas dessa classe são preservadas em serialização/desserialização.</para>
                </definition>
                <definedTerm>Serialization02</definedTerm>
                <definition>
                  <para>Mostra como examinar uma classe .NET existente e certificar-se de que informações de instância dessa classe são preservadas em serialização/desserialização quando as informações não estiverem disponíveis nas propriedades públicas da classe.</para>
                </definition>
                <definedTerm>Serialization03</definedTerm>
                <definition>
                  <para>Mostra como examinar uma classe .NET existente e certifique-se de que instâncias dessa classe e de classes derivadas são desserializadas (reidratadas) em objetos do .NET em tempo real.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>Exemplos de eventos</title>
            <content>
              <definitionTable>
                <definedTerm>Event01</definedTerm>
                <definition>
                  <para>Mostra como criar um cmdlet de registro de eventos derivando de ObjectEventRegistrationBase.</para>
                </definition>
                <definedTerm>Event02</definedTerm>
                <definition>
                  <para>Mostra como receber notificações de eventos <token>mshshort</token> que são gerados em computadores remotos. Ele usa o evento PSEventReceived exposto por meio da classe <codeEntityReference>T:System.Management.Automation.Runspaces.Runspace</codeEntityReference>.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>Exemplos de aplicativo de hospedagem</title>
            <content>
              <definitionTable>
                <definedTerm>Runspace01</definedTerm>
                <definition>
                  <para>Mostra como usar a classe <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> para executar o cmdlet <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> sincronicamente. O cmdlet <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> retorna objetos de <codeEntityReference>t: System.Diagnostics.Process</codeEntityReference> para cada processo em execução no computador local.</para>
                </definition>
                <definedTerm>Runspace02</definedTerm>
                <definition>
                  <para>Mostra como usar a classe <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> para executar os cmdlets <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> e <externalLink><linkText>Sort-Object</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkID=113403</linkUri></externalLink> sincronicamente. O cmdlet <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> retorna objetos de <codeEntityReference>T:System.Diagnostics.Process</codeEntityReference> para cada processo em execução no computador local e o Sort-Object classifica os objetos com base em sua propriedade <codeEntityReference>P:System.Diagnostics.Process.Id</codeEntityReference>. Os resultados desses comandos são exibidos usando um controle <codeEntityReference>T:System.Windows.Forms.DataGridView</codeEntityReference>.</para>
                </definition>
                <definedTerm>Runspace03</definedTerm>
                <definition>
                  <para>Mostra como usar a classe <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> para executar um script de forma síncrona e como tratar erros de não encerramento. O script recebe uma lista de nomes de processo e, em seguida, recupera tais processos. Os resultados do script, incluindo erros de não encerramento que foram gerados durante a execução do script, são exibidos em uma janela de console.</para>
                </definition>
                <definedTerm>Runspace04</definedTerm>
                <definition>
                  <para>Mostra como usar a classe <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> para executar comandos e como obter erros de encerramento que são gerados durante a execução de comandos. Dois comandos são executados e o último comando é passado um argumento de parâmetro que não é válido. Como resultado, não há objetos são retornados e um erro de encerramento é lançado.</para>
                </definition>
                <definedTerm>Runspace05</definedTerm>
                <definition>
                  <para>Mostra como adicionar um snap-in a um objeto <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference> para que o cmdlet do snap-in esteja disponível quando o espaço de execução for aberto. O snap-in fornece um cmdlet Get-Proc (definido pelo <legacyLink xlink:href="7b48bf80-cbf0-4cb1-8d5b-3b8d06196598">Exemplo GetProcessSample01</legacyLink>) que é executado de forma síncrona usando um objeto <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference>.</para>
                </definition>
                <definedTerm>Runspace06</definedTerm>
                <definition>
                  <para>Mostra como adicionar um módulo a um objeto <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference> para que o módulo seja carregado quando o espaço de execução for aberto. O módulo fornece um cmdlet Get-Proc (definido pelo <legacyLink xlink:href="481f557d-3344-4d33-b2da-4736a0165181">Exemplo GetProcessSample02</legacyLink>) que é executado de forma síncrona usando um objeto <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference>.</para>
                </definition>
                <definedTerm>Runspace07</definedTerm>
                <definition>
                  <para>Mostra como criar um espaço de execução e, em seguida, usar esse espaço de execução para executar dois cmdlets de forma síncrona usando um objeto <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference>.</para>
                </definition>
                <definedTerm>Runspace08</definedTerm>
                <definition>
                  <para>Mostra como adicionar comandos e argumentos ao pipeline de um objeto <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> e como executar os comandos de forma síncrona.</para>
                </definition>
                <definedTerm>Runspace09</definedTerm>
                <definition>
                  <para>Mostra como adicionar um script para o pipeline de um objeto <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> e como executar o script de forma assíncrona. Eventos são usados para tratar a saída do script.</para>
                </definition>
                <definedTerm>Runspace10</definedTerm>
                <definition>
                  <para>Mostra como criar um estado de sessão inicial padrão, como adicionar um cmdlet a <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference>, como criar um espaço de execução que usa o estado de sessão inicial e como executar o comando usando um objeto <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference>.</para>
                </definition>
                <definedTerm>Runspace11</definedTerm>
                <definition>
                  <para>Mostra como usar a classe <codeEntityReference>T:System.Management.Automation.ProxyCommand</codeEntityReference> para criar um comando de proxy que chama um cmdlet existente, mas restringe o conjunto de parâmetros disponíveis. O comando de proxy é adicionado a um estado de sessão inicial que é usado para criar um espaço de execução restrito. Isso significa que o usuário pode acessar a funcionalidade do cmdlet apenas através do comando de proxy.</para>
                </definition>
                <definedTerm>PowerShell01</definedTerm>
                <definition>
                  <para>Mostra como criar um espaço de execução restrito usando um objeto <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference>.</para>
                </definition>
                <definedTerm>PowerShell02</definedTerm>
                <definition>
                  <para>Mostra como usar um pool de espaço de execução para executar vários comandos simultaneamente.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>Exemplos de host</title>
            <content>
              <definitionTable>
                <definedTerm>Host01</definedTerm>
                <definition>
                  <para>Mostra como implementar um aplicativo host que usa um host personalizado. Neste exemplo é criado um espaço de execução que usa o host personalizado, e, em seguida, a API <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> é usada para executar um script que chama "sair". Em seguida, o aplicativo host analisa a saída do script e imprime os resultados.</para>
                </definition>
                <definedTerm>Host02</definedTerm>
                <definition>
                  <para>Mostra como escrever um aplicativo host que usa o tempo de execução <token>mshshort</token> com uma implementação de host personalizado. O aplicativo host define a cultura do host para o alemão, executa o cmdlet <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> e exibe os resultados como você os veria usando pwrsh.exe e, em seguida, imprime a data atual e a hora em alemão.</para>
                </definition>
                <definedTerm>Host03</definedTerm>
                <definition>
                  <para>Mostra como compilar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, exibe os resultados para o console.</para>
                </definition>
                <definedTerm>Host04</definedTerm>
                <definition>
                  <para>Mostra como compilar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, exibe os resultados para o console. Este aplicativo de host também dá suporte a solicitações de exibição que permitem ao usuário especificar várias opções.</para>
                </definition>
                <definedTerm>Host05</definedTerm>
                <definition>
                  <para>Mostra como compilar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, exibe os resultados para o console. Este aplicativo host também dá suporte a chamadas para computadores remotos usando os cmdlets <externalLink><linkText>Enter-PsSession</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=135210</linkUri></externalLink> e <externalLink><linkText>Exit-PsSession</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=135212</linkUri></externalLink>.</para>
                </definition>
                <definedTerm>Host06</definedTerm>
                <definition>
                  <para>Mostra como compilar um aplicativo host baseado em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, exibe os resultados para o console. Além disso, este exemplo usa as APIs do Criador de Token para especificar a cor do texto inserido pelo usuário.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>Exemplos de provedor</title>
            <content>
              <definitionTable>
                <definedTerm>AccessDBProviderSample01</definedTerm>
                <definition>
                  <para>Mostra como declarar uma classe de provedor que deriva diretamente da classe <codeEntityReference>T:System.Management.Automation.Provider.CmdletProvider</codeEntityReference>. Ele é incluído aqui apenas para fins de exatidão.</para>
                </definition>
                <definedTerm>AccessDBProviderSample02</definedTerm>
                <definition>
                  <para>Mostra como substituir os métodos <codeEntityReference>M:System.Management.Automation.Provider.DriveCmdletProvider.NewDrive(System.Management.Automation.PSDriveInfo)</codeEntityReference> e <codeEntityReference>M:System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive(System.Management.Automation.PSDriveInfo)</codeEntityReference> para dar suporte a chamadas para os cmdlets New-PSDrive e Remove-PSDrive. A classe de provedor neste exemplo deriva da classe <codeEntityReference>T:System.Management.Automation.Provider.DriveCmdletProvider</codeEntityReference>.</para>
                </definition>
                <definedTerm>AccessDBProviderSample03</definedTerm>
                <definition>
                  <para>Mostra como substituir os métodos <codeEntityReference>M:System.Management.Automation.Provider.ItemCmdletProvider.GetItem(System.String)</codeEntityReference> e <codeEntityReference>M:System.Management.Automation.Provider.ItemCmdletProvider.SetItem(System.String,System.Object)</codeEntityReference> para dar suporte a chamadas para os cmdlets Get-Item e Set-Item. A classe de provedor neste exemplo deriva da classe <codeEntityReference>T:System.Management.Automation.Provider.ItemCmdletProvider</codeEntityReference>.</para>
                </definition>
                <definedTerm>AccessDBProviderSample04</definedTerm>
                <definition>
                  <para>Mostra como substituir os métodos de contêiner para dar suporte a chamadas para os cmdlets Copy-Item, Get-ChildItem, New-Item e Remove-Item. Esses métodos devem ser implementados quando o armazenamento de dados contiver itens que são contêineres. Um contêiner é um grupo de itens filho em um item pai comum. A classe de provedor neste exemplo deriva da classe <codeEntityReference>T:System.Management.Automation.Provider.ItemCmdletProvider</codeEntityReference>.</para>
                </definition>
                <definedTerm>AccessDBProviderSample05</definedTerm>
                <definition>
                  <para>Mostra como substituir os métodos de contêiner para dar suporte a chamadas para os cmdlets Move-Item e Join-Path. Esses métodos deverão ser implementados quando o usuário precisar mover itens dentro de um contêiner e se o armazenamento de dados contiver contêineres aninhados. A classe de provedor neste exemplo deriva da classe <codeEntityReference>T:System.Management.Automation.Provider.NavigationCmdletProvider</codeEntityReference>. </para>
                </definition>
                <definedTerm>AccessDBProviderSample06</definedTerm>
                <definition>
                  <para>Mostra como substituir os métodos de conteúdo para dar suporte a chamadas para os cmdlets Clear-Content, Get-Content e Set-Content. Esses métodos devem ser implementados quando o usuário precisa gerenciar o conteúdo dos itens no armazenamento de dados. A classe de provedor neste exemplo deriva da classe <codeEntityReference>T:System.Management.Automation.Provider.NavigationCmdletProvider</codeEntityReference> e implementa a interface <codeEntityReference>T:System.Management.Automation.Provider.IContentCmdletProvider</codeEntityReference>.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
        </sections>
      </section>
    </sections>
  </section>
  <relatedTopics />
</developerConceptualDocument>




<!--HONumber=Jun16_HO4-->


