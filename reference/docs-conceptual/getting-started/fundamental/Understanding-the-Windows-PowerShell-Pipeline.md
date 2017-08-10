---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: Compreendendo o Pipeline do Windows PowerShell
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: 6d152e52d2fcfb9dd592eb9ac40500615f2186cb
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2017
---
# <a name="understanding-the-windows-powershell-pipeline"></a><span data-ttu-id="ceb00-103">Compreendendo o Pipeline do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ceb00-103">Understanding the Windows PowerShell Pipeline</span></span>
<span data-ttu-id="ceb00-104">O redirecionamento funciona praticamente em qualquer lugar no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ceb00-104">Piping works virtually everywhere in Windows PowerShell.</span></span> <span data-ttu-id="ceb00-105">Embora você veja o texto na tela, o Windows PowerShell não redireciona o texto entre comandos.</span><span class="sxs-lookup"><span data-stu-id="ceb00-105">Although you see text on the screen, Windows PowerShell does not pipe text between commands.</span></span> <span data-ttu-id="ceb00-106">Em vez disso, ele redireciona os objetos.</span><span class="sxs-lookup"><span data-stu-id="ceb00-106">Instead, it pipes objects.</span></span>

<span data-ttu-id="ceb00-107">A notação usada para as pipelines é semelhante àquela usada em outros shells, então à primeira vista, pode não ser aparente que o Windows PowerShell apresenta algo novo.</span><span class="sxs-lookup"><span data-stu-id="ceb00-107">The notation used for pipelines is similar to that used in other shells, so at first glance, it may not be apparent that Windows PowerShell introduces something new.</span></span> <span data-ttu-id="ceb00-108">Por exemplo, se você usar o cmdlet **Out-Host** para forçar uma exibição de página a página da saída de outro comando, a saída parecerá ser apenas o texto normal exibido na tela, dividida em páginas:</span><span class="sxs-lookup"><span data-stu-id="ceb00-108">For example, if you use the **Out-Host** cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\system32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2005-10-22  11:04 PM        315 $winnt$.inf
-a---        2004-08-04   8:00 AM      68608 access.cpl
-a---        2004-08-04   8:00 AM      64512 acctres.dll
-a---        2004-08-04   8:00 AM     183808 accwiz.exe
-a---        2004-08-04   8:00 AM      61952 acelpdec.ax
-a---        2004-08-04   8:00 AM     129536 acledit.dll
-a---        2004-08-04   8:00 AM     114688 aclui.dll
-a---        2004-08-04   8:00 AM     194048 activeds.dll
-a---        2004-08-04   8:00 AM     111104 activeds.tlb
-a---        2004-08-04   8:00 AM       4096 actmovie.exe
-a---        2004-08-04   8:00 AM     101888 actxprxy.dll
-a---        2003-02-21   6:50 PM     143150 admgmt.msc
-a---        2006-01-25   3:35 PM      53760 admparse.dll
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="ceb00-109">O comando Out-Host -Paging será um elemento de pipeline útil sempre que houver uma saída longa que você gostaria de exibir lentamente.</span><span class="sxs-lookup"><span data-stu-id="ceb00-109">The Out-Host -Paging command is a useful pipeline element whenever you have lengthy output that you would like to display slowly.</span></span> <span data-ttu-id="ceb00-110">Ele será especialmente útil se a operação for utilizar muita CPU.</span><span class="sxs-lookup"><span data-stu-id="ceb00-110">It is especially useful if the operation is very CPU-intensive.</span></span> <span data-ttu-id="ceb00-111">Como o processamento é transferido para o cmdlet Out-Host, quando ele tem uma página completa pronta para ser exibida, os cmdlets que o precedem no pipeline interrompem a operação até que a próxima página de saída esteja disponível.</span><span class="sxs-lookup"><span data-stu-id="ceb00-111">Because processing is transferred to the Out-Host cmdlet when it has a complete page ready to display, cmdlets that precede it in the pipeline halt operation until the next page of output is available.</span></span> <span data-ttu-id="ceb00-112">Você poderá ver isso se usar o Gerenciador de Tarefas do Windows para monitorar o uso de CPU e memória do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ceb00-112">You can see this if you use the Windows Task Manager to monitor CPU and memory use by Windows PowerShell.</span></span>

<span data-ttu-id="ceb00-113">Execute o seguinte comando: **Get-ChildItem C:\\Windows -Recurse**.</span><span class="sxs-lookup"><span data-stu-id="ceb00-113">Run the following command: **Get-ChildItem C:\\Windows -Recurse**.</span></span> <span data-ttu-id="ceb00-114">Compare o uso de CPU e de memória ao deste comando: **Get-ChildItem C:\\Windows -Recurse | Out-Host -Paging**.</span><span class="sxs-lookup"><span data-stu-id="ceb00-114">Compare the CPU and memory usage to this command: **Get-ChildItem C:\\Windows -Recurse | Out-Host -Paging**.</span></span> <span data-ttu-id="ceb00-115">O que você vê na tela é texto, mas isso é porque é necessário representar objetos como texto em uma janela de console.</span><span class="sxs-lookup"><span data-stu-id="ceb00-115">What you see on the screen is text, but that is because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="ceb00-116">Isso é apenas uma representação do que é realmente ocorre dentro do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ceb00-116">This is just a representation of what is really going on inside Windows PowerShell.</span></span> <span data-ttu-id="ceb00-117">Por exemplo, considere o cmdlet Get-Location.</span><span class="sxs-lookup"><span data-stu-id="ceb00-117">For example, consider the Get-Location cmdlet.</span></span> <span data-ttu-id="ceb00-118">Se você digitar **Get-Location** enquanto seu local atual for a raiz da unidade C, a seguinte saída será exibida:</span><span class="sxs-lookup"><span data-stu-id="ceb00-118">If you type **Get-Location** while your current location is the root of the C drive, you would see the following output:</span></span>

```
PS> Get-Location

Path
----
C:\
```

<span data-ttu-id="ceb00-119">Se o Windows PowerShell redirecionasse o texto, emitir um comando como **Get-Location | Out-Host** passaria de **Get-Location** para **Out-Host** um conjunto de caracteres na ordem em que eles são exibidos na tela.</span><span class="sxs-lookup"><span data-stu-id="ceb00-119">If Windows PowerShell pipelined text, issuing a command such as **Get-Location | Out-Host**, would pass from **Get-Location** to **Out-Host** a set of characters in the order they are displayed onscreen.</span></span> <span data-ttu-id="ceb00-120">Em outras palavras, se você ignorar as informações de cabeçalho, **Out-Host** receberá primeiro o caractere '**C'**, em seguida, o caractere '**:'** e depois o caractere '**\\'**.</span><span class="sxs-lookup"><span data-stu-id="ceb00-120">In other words, if you were to ignore the heading information, **Out-Host** would first receive the character '**C'**, then the character '**:'**, then the character '**\\'**.</span></span> <span data-ttu-id="ceb00-121">O cmdlet **Out-Host** não pôde determinar qual significado associar à saída de caracteres do cmdlet **Get-Location**.</span><span class="sxs-lookup"><span data-stu-id="ceb00-121">The **Out-Host** cmdlet could not determine what meaning to associate with the characters output by the **Get-Location** cmdlet.</span></span>

<span data-ttu-id="ceb00-122">Em vez de usar o texto para permitir que os comandos em um pipeline se comuniquem, o Windows PowerShell usa objetos.</span><span class="sxs-lookup"><span data-stu-id="ceb00-122">Instead of using text to let commands in a pipeline communicate, Windows PowerShell uses objects.</span></span> <span data-ttu-id="ceb00-123">Do ponto de vista de um usuário, os objetos empacotam informações relacionadas em um formulário que torna mais fácil manipular as informações como uma unidade e extrair itens específicos que você precisa.</span><span class="sxs-lookup"><span data-stu-id="ceb00-123">From the standpoint of a user, objects package related information into a form that makes it easier to manipulate the information as a unit, and extract specific items that you need.</span></span>

<span data-ttu-id="ceb00-124">O comando **Get-Location** não retorna o texto que contém o caminho atual.</span><span class="sxs-lookup"><span data-stu-id="ceb00-124">The **Get-Location** command does not return text that contains the current path.</span></span> <span data-ttu-id="ceb00-125">Ele retorna um pacote de informações chamado de um objeto **PathInfo** que contém o caminho atual juntamente com outras informações.</span><span class="sxs-lookup"><span data-stu-id="ceb00-125">It returns a package of information called a **PathInfo** object that contains the current path along with some other information.</span></span> <span data-ttu-id="ceb00-126">O cmdlet **Out-Host** envia então esse objeto **PathInfo** para a tela e o Windows PowerShell decide quais informações exibir e como exibi-las com base em suas regras de formatação.</span><span class="sxs-lookup"><span data-stu-id="ceb00-126">The **Out-Host** cmdlet then sends this **PathInfo** object to the screen, and Windows PowerShell decides what information to display and how to display it based on its formatting rules.</span></span>

<span data-ttu-id="ceb00-127">Na verdade, a saída das informações de cabeçalho do cmdlet **Get-Location** é adicionada somente no fim do processo, como parte do processo de formatação de dados para exibição na tela.</span><span class="sxs-lookup"><span data-stu-id="ceb00-127">In fact, the heading information output by the **Get-Location** cmdlet is added only at the end of the process, as part of the process of formatting the data for onscreen display.</span></span> <span data-ttu-id="ceb00-128">O que você vê na tela é um resumo das informações e não uma representação completa do objeto de saída.</span><span class="sxs-lookup"><span data-stu-id="ceb00-128">What you see onscreen is a summary of information, and not a complete representation of the output object.</span></span>

<span data-ttu-id="ceb00-129">Considerando que pode haver mais saída de informações de um comando do Windows PowerShell do que é exibido na janela do console, como podemos recuperar os elementos não visíveis?</span><span class="sxs-lookup"><span data-stu-id="ceb00-129">Given that there may be more information output from a Windows PowerShell command than what we see displayed in the console window, how can you retrieve the non-visible elements?</span></span> <span data-ttu-id="ceb00-130">Como exibir os dados extras?</span><span class="sxs-lookup"><span data-stu-id="ceb00-130">How do you view the extra data?</span></span> <span data-ttu-id="ceb00-131">E se você desejar exibir os dados em um formato diferente do que o Windows PowerShell normalmente usa?</span><span class="sxs-lookup"><span data-stu-id="ceb00-131">And what if you want to view the data in a format different than the one Windows PowerShell normally uses?</span></span>

<span data-ttu-id="ceb00-132">O restante deste capítulo discute como é possível pode descobrir a estrutura de objetos específicos do Windows PowerShell selecionando itens específicos e formatando-os para exibição mais fácil, bem como enviar essas informações para locais de saída alternativos, como arquivos e impressoras.</span><span class="sxs-lookup"><span data-stu-id="ceb00-132">The rest of this chapter discusses how you can discover the structure of specific Windows PowerShell objects, selecting specific items and formatting them for easier display, and how to send this information to alternative output locations such as files and printers.</span></span>

