---
title:  Criando objetos .NET e COM New Object 
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  2057b113-efeb-465e-8b44-da2f20dbf603
---

# Criando objetos .NET e COM (New-Object)
Existem componentes de software com as interfaces .NET Framework e COM que permitem executar muitas tarefas de administração do sistema. O Windows PowerShell permite usar esses componentes para que você não fique limitado a tarefas que podem ser executadas usando cmdlets. Muitos dos cmdlets na versão inicial do Windows PowerShell não funcionam em computadores remotos. Demonstraremos como contornar essa limitação gerenciando logs de eventos usando a classe **System.Diagnostics.EventLog** do .NET Framework diretamente do Windows PowerShell.

### Usar New-Object para acesso ao Log de Eventos
A Biblioteca de Classes do .NET Framework inclui uma classe chamada **System.Diagnostics.EventLog** que pode ser usada para gerenciar logs de eventos. Você pode criar uma nova instância de uma classe do .NET Framework usando o cmdlet **New-Object** com o parâmetro **TypeName**. Por exemplo, o comando a seguir cria uma referência de log de eventos:

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

Embora o comando tenha criado uma instância da classe EventLog, ela não inclui nenhum dado. Isso ocorre porque não especificamos um log de eventos específico. Como obter um log de eventos real?

#### Usar construtores com New-Object
Para consultar um log de eventos específico, é necessário especificar o nome do log. **New-Object** tem um parâmetro **ArgumentList**. Os argumentos que você passa como valores para esse parâmetro são usados por um método especial de inicialização do objeto. O método é chamado de *construtor* porque ele é usado para construir o objeto. Por exemplo, para obter uma referência para o Log do aplicativo, especifique a cadeia de caracteres “Application” (Aplicativo) como um argumento:

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> Uma vez que a maioria das classes principais do .NET Framework está contida no namespace System, o Windows PowerShell tentará localizar automaticamente as classes que você especificar no namespace System se ele não encontrar uma correspondência para o typename especificado. Isso significa que você pode especificar Diagnostics.EventLog em vez de System.Diagnostics.EventLog.

#### Armazenar objetos em variáveis
Pode ser útil armazenar uma referência a um objeto para que você pode usá-lo no shell atual. Embora o Windows PowerShell permita fazer grande parte do trabalho com pipelines, reduzindo a necessidade de variáveis, às vezes armazenar as referências a objetos em variáveis torna mais conveniente a tarefa de manipular esses objetos.

O Windows PowerShell permite criar variáveis que são basicamente objetos nomeados. A saída de qualquer comando válido do Windows PowerShell pode ser armazenada em uma variável. Nomes de variáveis sempre começam com $. Se você deseja armazenar a referência de log do aplicativo em uma variável chamada $AppLog, digite o nome da variável, seguido por um sinal de igual e, em seguida, digite o comando usado para criar o objeto do log do aplicativo:

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

Se você digitar $AppLog, poderá ver que ele contém o log do aplicativo:

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

#### Acessar um Log de Eventos Remoto com New-Object
Os comandos usados na seção anterior destinam-se ao computador local. O cmdlet **Get-EventLog** pode fazer isso. Para acessar o log do aplicativo em um computador remoto, você deve fornecer tanto o nome do log quanto um nome do computador (ou endereço IP) como argumentos.

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

Agora que temos uma referência a um log de eventos armazenado na variável $RemoteAppLog, quais tarefas que podemos realizar nela?

#### Limpar um Log de Eventos com métodos de objeto
Objetos geralmente têm métodos que podem ser chamados para executar tarefas. Você pode usar **Get-Member** para exibir os métodos associados a um objeto. O seguinte comando e a saída selecionada mostram alguns métodos da classe EventLog:

```
PS> $RemoteAppLog | Get-Member -MemberType Method

   TypeName: System.Diagnostics.EventLog

Name                      MemberType Definition
----                      ---------- ----------
...
Clear                     Method     System.Void Clear()
Close                     Method     System.Void Close()
...
GetType                   Method     System.Type GetType()
...
ModifyOverflowPolicy      Method     System.Void ModifyOverflowPolicy(Overfl...
RegisterDisplayName       Method     System.Void RegisterDisplayName(String ...
...
ToString                  Method     System.String ToString()
WriteEntry                Method     System.Void WriteEntry(String message),...
WriteEvent                Method     System.Void WriteEvent(EventInstance in...
```

O método **Clear()** pode ser usado para limpar o log de eventos. Ao chamar um método, você sempre deverá acrescentar parênteses ao fim do nome do método, mesmo se ele não exigir argumentos. Isso permite que o Windows PowerShell faça distinção entre o método e uma propriedade em potencial com o mesmo nome. Digite o seguinte para chamar o método **Clear**:

```
PS> $RemoteAppLog.Clear()
```

Digite o seguinte para exibir o log. Você verá que o log de eventos foi limpo e agora tem 0 entradas em vez de 262:

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

### Criar objetos COM o New-Object
Você pode usar **New-Object** para trabalhar com componentes COM (Component Object Model). Os componentes variam desde as várias bibliotecas incluídas no WSH (Windows Script Host) até aplicativos de ActiveX como o Internet Explorer que estão instalados na maioria dos sistemas.

**New-Object** usa Runtime Callable Wrappers do .NET Framework para criar objetos COM, portanto ele tem as mesmas limitações que o .NET Framework ao chamar objetos COM. Para criar um objeto COM, você precisa especificar o parâmetro **ComObject** com o identificador programático ou *ProgId* da classe COM que você deseja usar. Uma discussão completa sobre as limitações de uso de COM e como determinar quais ProgIds estão disponíveis em um sistema está além do escopo deste guia do usuário, mas a maioria dos objetos bem conhecidos de ambientes como WSH podem ser usados no Windows PowerShell.

Você pode criar objetos WSH especificando essas ProgIDs: **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary** e **Scripting.FileSystemObject**. Os comandos a seguir criam esses objetos:

```
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

Embora a maioria das funcionalidades dessas classes seja disponibilizada de outras maneiras no Windows PowerShell, algumas tarefas, como a criação de atalhos, são ainda mais fáceis de executar usando as classes WSH.

### Criar um atalho da área de trabalho com WScript.Shell
Uma tarefa que pode ser executada rapidamente um objeto COM é a criação de um atalho. Suponha que você deseja criar um atalho na área de trabalho que a vincula a pasta base ao Windows PowerShell. Você precisa primeiro criar uma referência a **WScript.Shell**, que armazenaremos em uma variável chamada **$WshShell**:

```
$WshShell = New-Object -ComObject WScript.Shell
```

Get-Member trabalha com objetos COM, por isso você pode explorar os membros do objeto digitando:

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

**Get-Member** tem um parâmetro **InputObject** opcional que você pode usar em vez de redirecionar para fornecer entrada para **Get-Member**. Você deverá obter a mesma saída mostrada acima se usar o comando **Get-Member -InputObject $WshShell**. Se você usar **InputObject**, ele tratará seu argumento como um único item. Isso significa que, se você tiver vários objetos em uma variável, **Get-Member** os tratará como uma matriz de objetos. Por exemplo:

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

O método **WScript.Shell CreateShortcut** aceita um único argumento, o caminho para o arquivo de atalho a ser criado. Podemos pode digitar o caminho completo para a área de trabalho, mas há uma maneira mais fácil. A área de trabalho normalmente é representada por uma pasta chamada Área de Trabalho dentro da pasta base do usuário atual. O Windows PowerShell tem uma variável **$Home** que contém o caminho para esta pasta. Podemos especificar o caminho para a pasta base usando essa variável e, em seguida, adicione o nome da pasta da Área de Trabalho e o nome do atalho a ser criado digitando:

```
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

Quando você usa algo parecido com um nome de variável entre aspas duplas, o Windows PowerShell tenta substituir por um valor correspondente. Se você usar aspas únicas, o Windows PowerShell não tentará substituir o valor da variável. Por exemplo, tente digitar os seguintes comandos:

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

Agora temos uma variável chamada **$lnk** que contém uma nova referência de atalho. Se você quiser ver seus membros, poderá direcioná-lo para **Get-Member**. A saída abaixo mostra os membros que precisamos usar para terminar de criar o atalho:

<pre>PS> $lnk | Get-Member TypeName: System.__ComObject#{f935dc23-1cf0-11d0-adb9-00c04fd58a0b} Name             MemberType   Definition ----             ----------   ---------- ... Save             Method       void Save () ... TargetPath       Property     string TargetPath () {get} {set} ...</pre>

É necessário especificar o **TargetPath**, que é a pasta do aplicativo para o Windows PowerShell e salvar o atalho **$lnk** chamando o método **Save**. O caminho da pasta de aplicativo do Windows PowerShell é armazenado na variável **$PSHome**, por isso podemos fazer isso digitando:

<pre>$lnk.TargetPath = $PSHome $lnk.Save()</pre>

### Usando o Internet Explorer do Windows PowerShell
Muitos aplicativos (incluindo a família de aplicativos Microsoft Office e o Internet Explorer) podem ser automatizados usando COM. O Internet Explorer ilustra algumas das técnicas e problemas típicos envolvidos ao trabalhar com aplicativos baseados em COM.

Você pode criar uma instância do Internet Explorer especificando a ProgId do Internet Explorer, **InternetExplorer.Application**:

```
$ie = New-Object -ComObject InternetExplorer.Application
```

Esse comando inicia o Internet Explorer, mas não o torna visível. Se você digitar Get-Process, verá que um processo chamado iexplore está em execução. Na verdade, se você sair do Windows PowerShell, este processo continuará em execução. Você deve reinicializar o computador ou usar uma ferramenta como o Gerenciador de Tarefas para encerrar o processo iexplore.

> [!NOTE]
> Objetos COM que iniciam como processos separados, normalmente chamados de *executáveis do ActiveX*, podem ou não exibir uma janela de interface do usuário quando são iniciados. Se eles criarem uma janela, mas não a tornarem visível, como no caso do Internet Explorer, o foco geralmente moverá para a área de trabalho do Windows e você deverá deixar a janela visível para interagir com ela.

Digitando **$ie | Get\-Member**, você pode exibir as propriedades e métodos para o Internet Explorer. Para ver a janela do Internet Explorer, defina a propriedade Visible para $true digitando:

```
$ie.Visible = $true
```

Em seguida, você pode navegar para um endereço Web específico usando o método Navigate:

```
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

Usando outros membros do modelo de objeto do Internet Explorer, é possível recuperar o conteúdo de texto da página da Web. O comando a seguir exibirá o texto HTML no corpo da página da Web atual:

```
$ie.Document.Body.InnerText
```

Para fechar o Internet Explorer de dentro do PowerShell, chame o método Quit():

```
$ie.Quit()
```

Isso o forçará a fechar. A variável $ie não contém uma referência válida, mesmo parecendo ser um objeto COM. Se você tentar usá-la, obterá um erro de automação:

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

Você pode remover a referência restante com um comando como $ie = $null ou remover completamente a variável digitando:

```
Remove-Variable ie
```

> [!NOTE]
> não há um padrão comum para se executáveis do ActiveX fecham ou continuam em execução quando você remove uma referência deles. Dependendo das circunstâncias, tal como se o aplicativo estiver visível, se um documento editado está em execução e até mesmo se o Windows PowerShell ainda está em execução, o aplicativo pode ser encerrado ou não. Por esse motivo, você deve testar o comportamento de encerramento para cada executável do ActiveX que você deseja usar no Windows PowerShell.

### Obtendo avisos sobre objetos COM Wrapped do .NET Framework
Em alguns casos, um objeto COM pode ter um *Runtime Callable Wrapper* ou RCW do .NET Framework associado, e este será usado pelo **New-Object**. Como o comportamento do RCW pode ser diferente do comportamento do objeto COM normal, **New-Object** tem um parâmetro **Strict** para avisar sobre acesso ao RCW. Se você especificar o parâmetro **Strict** e criar um objeto COM que usa um RCW, receberá uma mensagem de aviso:

```
PS> $xl = New-Object -ComObject Excel.Application -Strict
New-Object : The object written to the pipeline is an instance of the type "Mic
rosoft.Office.Interop.Excel.ApplicationClass" from the component's primary inte
rop assembly. If this type exposes different members than the IDispatch members
, scripts written to work with this object might not work if the primary intero
p assembly is not installed.
At line:1 char:17
+ $xl = New-Object  <<<< -ComObject Excel.Application -Strict
```

Embora o objeto ainda seja criado, você será avisado de que este não é um objeto COM padrão.



<!--HONumber=May16_HO2-->


