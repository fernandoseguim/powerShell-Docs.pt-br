---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Criando objetos .NET e COM New Object
ms.assetid: 2057b113-efeb-465e-8b44-da2f20dbf603
ms.openlocfilehash: 1ffd8d4afa419ec0c24321e44aa4a2f41a9bee44
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400589"
---
# <a name="creating-net-and-com-objects-new-object"></a><span data-ttu-id="b8e3d-103">Criando objetos .NET e COM (New-Object)</span><span class="sxs-lookup"><span data-stu-id="b8e3d-103">Creating .NET and COM Objects (New-Object)</span></span>

<span data-ttu-id="b8e3d-104">Existem componentes de software com as interfaces .NET Framework e COM que permitem executar muitas tarefas de administração do sistema.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-104">There are software components with .NET Framework and COM interfaces that enable you to perform many system administration tasks.</span></span> <span data-ttu-id="b8e3d-105">O Windows PowerShell permite usar esses componentes para que você não fique limitado a tarefas que podem ser executadas usando cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-105">Windows PowerShell lets you use these components, so you are not limited to the tasks that can be performed by using cmdlets.</span></span> <span data-ttu-id="b8e3d-106">Muitos dos cmdlets na versão inicial do Windows PowerShell não funcionam em computadores remotos.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-106">Many of the cmdlets in the initial release of Windows PowerShell do not work against remote computers.</span></span> <span data-ttu-id="b8e3d-107">Demonstraremos como contornar essa limitação gerenciando logs de eventos usando a classe **System.Diagnostics.EventLog** do .NET Framework diretamente do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-107">We will demonstrate how to get around this limitation when managing event logs by using the .NET Framework **System.Diagnostics.EventLog** class directly from Windows PowerShell.</span></span>

### <a name="using-new-object-for-event-log-access"></a><span data-ttu-id="b8e3d-108">Usando New-Object para acesso ao Log de Eventos</span><span class="sxs-lookup"><span data-stu-id="b8e3d-108">Using New-Object for Event Log Access</span></span>

<span data-ttu-id="b8e3d-109">A Biblioteca de Classes do .NET Framework inclui uma classe chamada **System.Diagnostics.EventLog** que pode ser usada para gerenciar logs de eventos.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-109">The .NET Framework Class Library includes a class named **System.Diagnostics.EventLog** that can be used to manage event logs.</span></span> <span data-ttu-id="b8e3d-110">Você pode criar uma nova instância de uma classe do .NET Framework usando o cmdlet **New-Object** com o parâmetro **TypeName**.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-110">You can create a new instance of a .NET Framework class by using the **New-Object** cmdlet with the **TypeName** parameter.</span></span> <span data-ttu-id="b8e3d-111">Por exemplo, o comando a seguir cria uma referência de log de eventos:</span><span class="sxs-lookup"><span data-stu-id="b8e3d-111">For example, the following command creates an event log reference:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

<span data-ttu-id="b8e3d-112">Embora o comando tenha criado uma instância da classe EventLog, ela não inclui nenhum dado.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-112">Although the command has created an instance of the EventLog class, the instance does not include any data.</span></span> <span data-ttu-id="b8e3d-113">Isso ocorre porque não especificamos um log de eventos específico.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-113">That is because we did not specify a particular event log.</span></span> <span data-ttu-id="b8e3d-114">Como obter um log de eventos real?</span><span class="sxs-lookup"><span data-stu-id="b8e3d-114">How do you get a real event log?</span></span>

#### <a name="using-constructors-with-new-object"></a><span data-ttu-id="b8e3d-115">Usando construtores com New-Object</span><span class="sxs-lookup"><span data-stu-id="b8e3d-115">Using Constructors with New-Object</span></span>

<span data-ttu-id="b8e3d-116">Para consultar um log de eventos específico, é necessário especificar o nome do log.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-116">To refer to a specific event log, you need to specify the name of the log.</span></span> <span data-ttu-id="b8e3d-117">**New-Object** tem um parâmetro **ArgumentList**.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-117">**New-Object** has an **ArgumentList** parameter.</span></span> <span data-ttu-id="b8e3d-118">Os argumentos que você passa como valores para esse parâmetro são usados por um método especial de inicialização do objeto.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-118">The arguments you pass as values to this parameter are used by a special startup method of the object.</span></span> <span data-ttu-id="b8e3d-119">O método é chamado de *construtor* porque ele é usado para construir o objeto.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-119">The method is called a *constructor* because it is used to construct the object.</span></span> <span data-ttu-id="b8e3d-120">Por exemplo, para obter uma referência para o Log do aplicativo, especifique a cadeia de caracteres “Application” (Aplicativo) como um argumento:</span><span class="sxs-lookup"><span data-stu-id="b8e3d-120">For example, to get a reference to the Application log, you specify the string 'Application' as an argument:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> <span data-ttu-id="b8e3d-121">Uma vez que a maioria das classes principais do .NET Framework está contida no namespace System, o Windows PowerShell tentará localizar automaticamente as classes que você especificar no namespace System se ele não encontrar uma correspondência para o typename especificado.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-121">Since most of the .NET Framework core classes are contained in the System namespace, Windows PowerShell will automatically attempt to find classes you specify in the System namespace if it cannot find a match for the typename you specify.</span></span> <span data-ttu-id="b8e3d-122">Isso significa que você pode especificar Diagnostics.EventLog em vez de System.Diagnostics.EventLog.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-122">This means that you can specify Diagnostics.EventLog instead of System.Diagnostics.EventLog.</span></span>

#### <a name="storing-objects-in-variables"></a><span data-ttu-id="b8e3d-123">Armazenar objetos em variáveis</span><span class="sxs-lookup"><span data-stu-id="b8e3d-123">Storing Objects in Variables</span></span>

<span data-ttu-id="b8e3d-124">Pode ser útil armazenar uma referência a um objeto para que você pode usá-lo no shell atual.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-124">You might want to store a reference to an object, so you can use it in the current shell.</span></span> <span data-ttu-id="b8e3d-125">Embora o Windows PowerShell permita fazer grande parte do trabalho com pipelines, reduzindo a necessidade de variáveis, às vezes armazenar as referências a objetos em variáveis torna mais conveniente a tarefa de manipular esses objetos.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-125">Although Windows PowerShell lets you do a lot of work with pipelines, lessening the need for variables, sometimes storing references to objects in variables makes it more convenient to manipulate those objects.</span></span>

<span data-ttu-id="b8e3d-126">O Windows PowerShell permite criar variáveis que são basicamente objetos nomeados.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-126">Windows PowerShell lets you create variables that are essentially named objects.</span></span> <span data-ttu-id="b8e3d-127">A saída de qualquer comando válido do Windows PowerShell pode ser armazenada em uma variável.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-127">The output from any valid Windows PowerShell command can be stored in a variable.</span></span> <span data-ttu-id="b8e3d-128">Nomes de variáveis sempre começam com $.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-128">Variable names always begin with $.</span></span> <span data-ttu-id="b8e3d-129">Se você deseja armazenar a referência de log do aplicativo em uma variável chamada $AppLog, digite o nome da variável, seguido por um sinal de igual e, em seguida, digite o comando usado para criar o objeto do log do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="b8e3d-129">If you want to store the Application log reference in a variable named $AppLog, type the name of the variable, followed by an equal sign and then type the command used to create the Application log object:</span></span>

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

<span data-ttu-id="b8e3d-130">Se você digitar $AppLog, poderá ver que ele contém o log do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="b8e3d-130">If you then type $AppLog, you can see that it contains the Application log:</span></span>

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

#### <a name="accessing-a-remote-event-log-with-new-object"></a><span data-ttu-id="b8e3d-131">Acessando um Log de Eventos Remoto com New-Object</span><span class="sxs-lookup"><span data-stu-id="b8e3d-131">Accessing a Remote Event Log with New-Object</span></span>

<span data-ttu-id="b8e3d-132">Os comandos usados na seção anterior destinam-se ao computador local. O cmdlet **Get-EventLog** pode fazer isso.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-132">The commands used in the preceding section target the local computer; the **Get-EventLog** cmdlet can do that.</span></span> <span data-ttu-id="b8e3d-133">Para acessar o log do aplicativo em um computador remoto, você deve fornecer tanto o nome do log quanto um nome do computador (ou endereço IP) como argumentos.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-133">To access the Application log on a remote computer, you must supply both the log name and a computer name (or IP address) as arguments.</span></span>

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

<span data-ttu-id="b8e3d-134">Agora que temos uma referência a um log de eventos armazenado na variável $RemoteAppLog, quais tarefas que podemos realizar nela?</span><span class="sxs-lookup"><span data-stu-id="b8e3d-134">Now that we have a reference to an event log stored in the $RemoteAppLog variable, what tasks can we perform on it?</span></span>

#### <a name="clearing-an-event-log-with-object-methods"></a><span data-ttu-id="b8e3d-135">Limpar um Log de Eventos com métodos de objeto</span><span class="sxs-lookup"><span data-stu-id="b8e3d-135">Clearing an Event Log with Object Methods</span></span>

<span data-ttu-id="b8e3d-136">Objetos geralmente têm métodos que podem ser chamados para executar tarefas.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-136">Objects often have methods that can be called to perform tasks.</span></span> <span data-ttu-id="b8e3d-137">Você pode usar **Get-Member** para exibir os métodos associados a um objeto.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-137">You can use **Get-Member** to display the methods associated with an object.</span></span> <span data-ttu-id="b8e3d-138">O seguinte comando e a saída selecionada mostram alguns métodos da classe EventLog:</span><span class="sxs-lookup"><span data-stu-id="b8e3d-138">The following command and selected output show some the methods of the EventLog class:</span></span>

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

<span data-ttu-id="b8e3d-139">O método **Clear()** pode ser usado para limpar o log de eventos.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-139">The **Clear()** method can be used to clear the event log.</span></span> <span data-ttu-id="b8e3d-140">Ao chamar um método, você sempre deverá acrescentar parênteses ao fim do nome do método, mesmo se ele não exigir argumentos.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-140">When calling a method, you must always follow the method name by parentheses, even if the method does not require arguments.</span></span> <span data-ttu-id="b8e3d-141">Isso permite que o Windows PowerShell faça distinção entre o método e uma propriedade em potencial com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-141">This lets Windows PowerShell distinguish between the method and a potential property with the same name.</span></span> <span data-ttu-id="b8e3d-142">Digite o seguinte para chamar o método **Clear**:</span><span class="sxs-lookup"><span data-stu-id="b8e3d-142">Type the following to call the **Clear** method:</span></span>

```
PS> $RemoteAppLog.Clear()
```

<span data-ttu-id="b8e3d-143">Digite o seguinte para exibir o log.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-143">Type the following to display the log.</span></span> <span data-ttu-id="b8e3d-144">Você verá que o log de eventos foi limpo e agora tem 0 entradas em vez de 262:</span><span class="sxs-lookup"><span data-stu-id="b8e3d-144">You will see that the event log was cleared, and now has 0 entries instead of 262:</span></span>

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

### <a name="creating-com-objects-with-new-object"></a><span data-ttu-id="b8e3d-145">Criação de objetos COM usando New-Object</span><span class="sxs-lookup"><span data-stu-id="b8e3d-145">Creating COM Objects with New-Object</span></span>
<span data-ttu-id="b8e3d-146">Você pode usar **New-Object** para trabalhar com componentes COM (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="b8e3d-146">You can use **New-Object** to work with Component Object Model (COM) components.</span></span> <span data-ttu-id="b8e3d-147">Os componentes variam desde as várias bibliotecas incluídas no WSH (Windows Script Host) até aplicativos de ActiveX como o Internet Explorer que estão instalados na maioria dos sistemas.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-147">Components range from the various libraries included with Windows Script Host (WSH) to ActiveX applications such as Internet Explorer that are installed on most systems.</span></span>

<span data-ttu-id="b8e3d-148">**New-Object** usa Runtime Callable Wrappers do .NET Framework para criar objetos COM, portanto, ele tem as mesmas limitações que o .NET Framework ao chamar objetos COM.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-148">**New-Object** uses .NET Framework Runtime-Callable Wrappers to create COM objects, so it has the same limitations that .NET Framework does when calling COM objects.</span></span> <span data-ttu-id="b8e3d-149">Para criar um objeto COM, você precisa especificar o parâmetro **ComObject** com o identificador programático ou *ProgId* da classe COM que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-149">To create a COM object, you need to specify the **ComObject** parameter with the Programmatic Identifier or *ProgId* of the COM class you want to use.</span></span> <span data-ttu-id="b8e3d-150">Uma discussão completa sobre as limitações de uso de COM e como determinar quais ProgIds estão disponíveis em um sistema está além do escopo deste guia do usuário, mas a maioria dos objetos bem conhecidos de ambientes como WSH podem ser usados no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-150">A complete discussion of the limitations of COM use and determining what ProgIds are available on a system is beyond the scope of this user's guide, but most well-known objects from environments such as WSH can be used within Windows PowerShell.</span></span>

<span data-ttu-id="b8e3d-151">Você pode criar objetos WSH especificando essas progids: **WScript. Shell**, **Wscript. Network**, **Dictionary**, e **Scripting. FileSystemObject**.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-151">You can create the WSH objects by specifying these progids: **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary**, and **Scripting.FileSystemObject**.</span></span> <span data-ttu-id="b8e3d-152">Os comandos a seguir criam esses objetos:</span><span class="sxs-lookup"><span data-stu-id="b8e3d-152">The following commands create these objects:</span></span>

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

<span data-ttu-id="b8e3d-153">Embora a maioria das funcionalidades dessas classes seja disponibilizada de outras maneiras no Windows PowerShell, algumas tarefas, como a criação de atalhos, são ainda mais fáceis de executar usando as classes WSH.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-153">Although most of the functionality of these classes is made available in other ways in Windows PowerShell, a few tasks such as shortcut creation are still easier to do using the WSH classes.</span></span>

### <a name="creating-a-desktop-shortcut-with-wscriptshell"></a><span data-ttu-id="b8e3d-154">Criar um atalho da área de trabalho com WScript.Shell</span><span class="sxs-lookup"><span data-stu-id="b8e3d-154">Creating a Desktop Shortcut with WScript.Shell</span></span>

<span data-ttu-id="b8e3d-155">Uma tarefa que pode ser executada rapidamente um objeto COM é a criação de um atalho.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-155">One task that can be performed quickly with a COM object is creating a shortcut.</span></span> <span data-ttu-id="b8e3d-156">Suponha que você deseja criar um atalho na área de trabalho que a vincula a pasta base ao Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-156">Suppose you want to create a shortcut on your desktop that links to the home folder for Windows PowerShell.</span></span> <span data-ttu-id="b8e3d-157">Você precisa primeiro criar uma referência a **WScript.Shell**, que armazenaremos em uma variável chamada **$WshShell**:</span><span class="sxs-lookup"><span data-stu-id="b8e3d-157">You first need to create a reference to **WScript.Shell**, which we will store in a variable named **$WshShell**:</span></span>

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

<span data-ttu-id="b8e3d-158">Get-Member trabalha com objetos COM, por isso você pode explorar os membros do objeto digitando:</span><span class="sxs-lookup"><span data-stu-id="b8e3d-158">Get-Member works with COM objects, so you can explore the members of the object by typing:</span></span>

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

<span data-ttu-id="b8e3d-159">**Get-Member** tem um parâmetro **InputObject** opcional que você pode usar em vez de redirecionar para fornecer entrada para **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-159">**Get-Member** has an optional **InputObject** parameter you can use instead of piping to provide input to **Get-Member**.</span></span> <span data-ttu-id="b8e3d-160">Você deverá obter a mesma saída mostrada acima se usar o comando **Get-Member -InputObject $WshShell**.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-160">You would get the same output as shown above if you instead used the command **Get-Member -InputObject $WshShell**.</span></span> <span data-ttu-id="b8e3d-161">Se você usar **InputObject**, ele tratará seu argumento como um único item.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-161">If you use **InputObject**, it treats its argument as a single item.</span></span> <span data-ttu-id="b8e3d-162">Isso significa que, se você tiver vários objetos em uma variável, **Get-Member** os tratará como uma matriz de objetos.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-162">This means that if you have several objects in a variable, **Get-Member** treats them as an array of objects.</span></span> <span data-ttu-id="b8e3d-163">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b8e3d-163">For example:</span></span>

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

<span data-ttu-id="b8e3d-164">O método **WScript.Shell CreateShortcut** aceita um único argumento, o caminho para o arquivo de atalho a ser criado.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-164">The **WScript.Shell CreateShortcut** method accepts a single argument, the path to the shortcut file to create.</span></span> <span data-ttu-id="b8e3d-165">Podemos pode digitar o caminho completo para a área de trabalho, mas há uma maneira mais fácil.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-165">We could type in the full path to the desktop, but there is an easier way.</span></span> <span data-ttu-id="b8e3d-166">A área de trabalho normalmente é representada por uma pasta chamada Área de Trabalho dentro da pasta base do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-166">The desktop is normally represented by a folder named Desktop inside the home folder of the current user.</span></span> <span data-ttu-id="b8e3d-167">O Windows PowerShell tem uma variável **$Home** que contém o caminho para esta pasta.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-167">Windows PowerShell has a variable **$Home** that contains the path to this folder.</span></span> <span data-ttu-id="b8e3d-168">Podemos especificar o caminho para a pasta base usando essa variável e, em seguida, adicione o nome da pasta da Área de Trabalho e o nome do atalho a ser criado digitando:</span><span class="sxs-lookup"><span data-stu-id="b8e3d-168">We can specify the path to the home folder by using this variable, and then add the name of the Desktop folder and the name for the shortcut to create by typing:</span></span>

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

<span data-ttu-id="b8e3d-169">Quando você usa algo parecido com um nome de variável entre aspas duplas, o Windows PowerShell tenta substituir por um valor correspondente.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-169">When you use something that looks like a variable name inside double-quotes, Windows PowerShell tries to substitute a matching value.</span></span> <span data-ttu-id="b8e3d-170">Se você usar aspas simples, o Windows PowerShell não tentará substituir o valor da variável.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-170">If you use single-quotes, Windows PowerShell does not try to substitute the variable value.</span></span> <span data-ttu-id="b8e3d-171">Por exemplo, tente digitar os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="b8e3d-171">For example, try typing the following commands:</span></span>

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

<span data-ttu-id="b8e3d-172">Agora temos uma variável chamada **$lnk** que contém uma nova referência de atalho.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-172">We now have a variable named **$lnk** that contains a new shortcut reference.</span></span> <span data-ttu-id="b8e3d-173">Se quiser ver seus membros, você poderá direcioná-lo para **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-173">If you want to see its members, you can pipe it to **Get-Member**.</span></span> <span data-ttu-id="b8e3d-174">A saída abaixo mostra os membros que precisamos usar para terminar de criar o atalho:</span><span class="sxs-lookup"><span data-stu-id="b8e3d-174">The output below shows the members we need to use to finish creating our shortcut:</span></span>

```
PS> $lnk | Get-Member
TypeName: System.__ComObject#{f935dc23-1cf0-11d0-adb9-00c04fd58a0b}
Name             MemberType   Definition
----             ----------   ----------
...
Save             Method       void Save ()
...
TargetPath       Property     string TargetPath () {get} {set}
```

<span data-ttu-id="b8e3d-175">É necessário especificar o **TargetPath**, que é a pasta do aplicativo para o Windows PowerShell e salvar o atalho **$lnk** chamando o método **Save**.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-175">We need to specify the **TargetPath**, which is the application folder for Windows PowerShell, and then save the shortcut **$lnk** by calling the **Save** method.</span></span> <span data-ttu-id="b8e3d-176">O caminho da pasta de aplicativo do Windows PowerShell é armazenado na variável **$PSHome**, por isso podemos fazer isso digitando:</span><span class="sxs-lookup"><span data-stu-id="b8e3d-176">The Windows PowerShell application folder path is stored in the variable **$PSHome**, so we can do this by typing:</span></span>

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

### <a name="using-internet-explorer-from-windows-powershell"></a><span data-ttu-id="b8e3d-177">Usando o Internet Explorer do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8e3d-177">Using Internet Explorer from Windows PowerShell</span></span>

<span data-ttu-id="b8e3d-178">Muitos aplicativos (incluindo a família de aplicativos Microsoft Office e o Internet Explorer) podem ser automatizados usando COM.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-178">Many applications (including the Microsoft Office family of applications and Internet Explorer) can be automated by using COM.</span></span> <span data-ttu-id="b8e3d-179">O Internet Explorer ilustra algumas das técnicas e problemas típicos envolvidos ao trabalhar com aplicativos baseados em COM.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-179">Internet Explorer illustrates some of the typical techniques and issues involved in working with COM-based applications.</span></span>

<span data-ttu-id="b8e3d-180">Você pode criar uma instância do Internet Explorer especificando a ProgId do Internet Explorer, **InternetExplorer.Application**:</span><span class="sxs-lookup"><span data-stu-id="b8e3d-180">You create an Internet Explorer instance by specifying the Internet Explorer ProgId, **InternetExplorer.Application**:</span></span>

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

<span data-ttu-id="b8e3d-181">Esse comando inicia o Internet Explorer, mas não o torna visível.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-181">This command starts Internet Explorer, but does not make it visible.</span></span> <span data-ttu-id="b8e3d-182">Se digitar Get-Process, você poderá ver que um processo chamado iexplore está em execução.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-182">If you type Get-Process, you can see that a process named iexplore is running.</span></span> <span data-ttu-id="b8e3d-183">Na verdade, se você sair do Windows PowerShell, este processo continuará em execução.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-183">In fact, if you exit Windows PowerShell, the process will continue to run.</span></span> <span data-ttu-id="b8e3d-184">Você deve reinicializar o computador ou usar uma ferramenta como o Gerenciador de Tarefas para encerrar o processo iexplore.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-184">You must reboot the computer or use a tool like Task Manager to end the iexplore process.</span></span>

> [!NOTE]
> <span data-ttu-id="b8e3d-185">Objetos COM que iniciam como processos separados, normalmente chamados de *executáveis do ActiveX*, podem ou não exibir uma janela de interface do usuário quando são iniciados.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-185">COM objects that start as separate processes, commonly called *ActiveX executables*, may or may not display a user interface window when they start up.</span></span> <span data-ttu-id="b8e3d-186">Se eles criarem uma janela, mas não a tornarem visível, como no caso do Internet Explorer, o foco geralmente moverá para a área de trabalho do Windows e você deverá deixar a janela visível para interagir com ela.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-186">If they create a window but do not make it visible, like Internet Explorer, the focus will generally move to the Windows desktop and you must make the window visible to interact with it.</span></span>

<span data-ttu-id="b8e3d-187">Digitando **$ie | Get-Member**, você pode exibir as propriedades e os métodos do Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-187">By typing **$ie | Get-Member**, you can view properties and methods for Internet Explorer.</span></span> <span data-ttu-id="b8e3d-188">Para ver a janela do Internet Explorer, defina a propriedade Visible para $true digitando:</span><span class="sxs-lookup"><span data-stu-id="b8e3d-188">To see the Internet Explorer window, set the Visible property to $true by typing:</span></span>

```powershell
$ie.Visible = $true
```

<span data-ttu-id="b8e3d-189">Em seguida, você pode navegar para um endereço Web específico usando o método Navigate:</span><span class="sxs-lookup"><span data-stu-id="b8e3d-189">You can then navigate to a specific Web address by using the Navigate method:</span></span>

```powershell
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

<span data-ttu-id="b8e3d-190">Usando outros membros do modelo de objeto do Internet Explorer, é possível recuperar o conteúdo de texto da página da Web.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-190">Using other members of the Internet Explorer object model, it is possible to retrieve text content from the Web page.</span></span> <span data-ttu-id="b8e3d-191">O comando a seguir exibirá o texto HTML no corpo da página da Web atual:</span><span class="sxs-lookup"><span data-stu-id="b8e3d-191">The following command will display the HTML text in the body of the current Web page:</span></span>

```powershell
$ie.Document.Body.InnerText
```

<span data-ttu-id="b8e3d-192">Para fechar o Internet Explorer de dentro do PowerShell, chame o método Quit():</span><span class="sxs-lookup"><span data-stu-id="b8e3d-192">To close Internet Explorer from within PowerShell, call its Quit() method:</span></span>

```powershell
$ie.Quit()
```

<span data-ttu-id="b8e3d-193">Isso o forçará a fechar.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-193">This will force it to close.</span></span> <span data-ttu-id="b8e3d-194">A variável $ie não contém uma referência válida, mesmo parecendo ser um objeto COM.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-194">The $ie variable no longer contains a valid reference even though it still appears to be a COM object.</span></span> <span data-ttu-id="b8e3d-195">Se você tentar usá-la, obterá um erro de automação:</span><span class="sxs-lookup"><span data-stu-id="b8e3d-195">If you attempt to use it, you will get an automation error:</span></span>

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

<span data-ttu-id="b8e3d-196">É possível remover a referência restante com um comando como $ie = $null ou remover por completo a variável digitando:</span><span class="sxs-lookup"><span data-stu-id="b8e3d-196">You can either remove the remaining reference with a command like $ie = $null, or completely remove the variable by typing:</span></span>

```powershell
Remove-Variable ie
```

> [!NOTE]
> <span data-ttu-id="b8e3d-197">não há um padrão comum para se executáveis do ActiveX fecham ou continuam em execução quando você remove uma referência deles.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-197">There is no common standard for whether ActiveX executables exit or continue to run when you remove a reference to one.</span></span> <span data-ttu-id="b8e3d-198">Dependendo das circunstâncias, tal como se o aplicativo estiver visível, se um documento editado está em execução e até mesmo se o Windows PowerShell ainda está em execução, o aplicativo pode ser encerrado ou não.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-198">Depending on circumstances such as whether the application is visible, whether an edited document is running in it, and even whether Windows PowerShell is still running, the application may or may not exit.</span></span> <span data-ttu-id="b8e3d-199">Por esse motivo, você deve testar o comportamento de encerramento para cada executável do ActiveX que você deseja usar no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-199">For this reason, you should test termination behavior for each ActiveX executable you want to use in Windows PowerShell.</span></span>

### <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a><span data-ttu-id="b8e3d-200">Obtendo avisos sobre objetos COM Wrapped do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b8e3d-200">Getting Warnings About .NET Framework-Wrapped COM Objects</span></span>

<span data-ttu-id="b8e3d-201">Em alguns casos, um objeto COM pode ter um *Runtime Callable Wrapper* ou RCW do .NET Framework associado, e este será usado pelo **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-201">In some cases, a COM object might have an associated .NET Framework *Runtime-Callable Wrapper* or RCW, and this will be used by **New-Object**.</span></span> <span data-ttu-id="b8e3d-202">Como o comportamento do RCW pode ser diferente do comportamento do objeto COM normal, **New-Object** tem um parâmetro **Strict** para avisar sobre o acesso ao RCW.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-202">Since the behavior of the RCW may be different from the behavior of the normal COM object, **New-Object** has a **Strict** parameter to warn you about RCW access.</span></span> <span data-ttu-id="b8e3d-203">Se você especificar o parâmetro **Strict** e criar um objeto COM que usa um RCW, receberá uma mensagem de aviso:</span><span class="sxs-lookup"><span data-stu-id="b8e3d-203">If you specify the **Strict** parameter and then create a COM object that uses an RCW, you get a warning message:</span></span>

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

<span data-ttu-id="b8e3d-204">Embora o objeto ainda seja criado, você será avisado de que este não é um objeto COM padrão.</span><span class="sxs-lookup"><span data-stu-id="b8e3d-204">Although the object is still created, you are warned that it is not a standard COM object.</span></span>