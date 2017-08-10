---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: "Outros objetos de script úteis"
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 8334d0b346e59dea3643a93bf52b780b361d1945
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2017
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="efa29-103">Outros objetos de script úteis</span><span class="sxs-lookup"><span data-stu-id="efa29-103">Other Useful Scripting Objects</span></span>
  <span data-ttu-id="efa29-104">Os seguintes objetos fornecem funcionalidade adicional de script no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="efa29-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="efa29-105">Eles não fazem parte da hierarquia **$psISE**.</span><span class="sxs-lookup"><span data-stu-id="efa29-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="efa29-106">Objetos de scripts úteis</span><span class="sxs-lookup"><span data-stu-id="efa29-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="efa29-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="efa29-107">$psUnsupportedConsoleApplications</span></span>
 <span data-ttu-id="efa29-108">Existem algumas limitações sobre como o ISE do Windows PowerShell interage com os aplicativos do console.</span><span class="sxs-lookup"><span data-stu-id="efa29-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="efa29-109">Um comando ou um script de automação que requer a intervenção do usuário pode não funcionar da maneira que funciona no console do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="efa29-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="efa29-110">Você pode impedir que esses comandos ou scripts sejam executados no painel de comando ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="efa29-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="efa29-111">O objeto **$psUnsupportedConsoleApplications** mantém uma lista de tais comandos.</span><span class="sxs-lookup"><span data-stu-id="efa29-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="efa29-112">Se você tentar executar os comandos nesta lista, receberá uma mensagem de que eles não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="efa29-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="efa29-113">O script a seguir adiciona uma entrada à lista.</span><span class="sxs-lookup"><span data-stu-id="efa29-113">The following script adds an entry to the list.</span></span>

```
# List the unsupported commands
psUnsupportedConsoleApplications
# Add a command to this list
psUnsupportedConsoleApplications.Add(“Mycommand”)
#Show the augmented list of commands
psUnsupportedConsoleApplications

```

### <a name="pslocalhelp"></a><span data-ttu-id="efa29-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="efa29-114">$psLocalHelp</span></span>
 <span data-ttu-id="efa29-115">Esse é um objeto de dicionário que mantém um mapeamento contextual entre os tópicos da Ajuda e seus links associados no arquivo de ajuda local HTML compilado.</span><span class="sxs-lookup"><span data-stu-id="efa29-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="efa29-116">Ele é usado para localizar a Ajuda local para determinado tópico.</span><span class="sxs-lookup"><span data-stu-id="efa29-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="efa29-117">Você pode adicionar ou excluir tópicos desta lista.</span><span class="sxs-lookup"><span data-stu-id="efa29-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="efa29-118">O exemplo de código a seguir mostra alguns exemplos de pares de chave-valor contidos em **$psLocalHelp**.</span><span class="sxs-lookup"><span data-stu-id="efa29-118">The following code example shows some example key-value pairs that are contained in **$psLocalHelp**.</span></span>

```
# See the local help map
$psLocalHelp | Format-List

```

### <a name="sample-output"></a><span data-ttu-id="efa29-119">Saída de exemplo</span><span class="sxs-lookup"><span data-stu-id="efa29-119">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="efa29-120">Chave: Add-Computer</span><span class="sxs-lookup"><span data-stu-id="efa29-120">Key : Add-Computer</span></span>|<span data-ttu-id="efa29-121">Valor: WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span><span class="sxs-lookup"><span data-stu-id="efa29-121">Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span></span>|
|<span data-ttu-id="efa29-122">Chave: Add-Content</span><span class="sxs-lookup"><span data-stu-id="efa29-122">Key : Add-Content</span></span>|<span data-ttu-id="efa29-123">Valor: WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span><span class="sxs-lookup"><span data-stu-id="efa29-123">Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span></span>|

 <span data-ttu-id="efa29-124">O script a seguir adiciona uma entrada à lista.</span><span class="sxs-lookup"><span data-stu-id="efa29-124">The following script adds an entry to the list.</span></span>

```
$psLocalHelp.Add("get-myNoun","c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="efa29-125">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="efa29-125">$psOnlineHelp</span></span>
 <span data-ttu-id="efa29-126">Este é um objeto de dicionário que mantém um mapeamento contextual entre títulos de tópicos dos tópicos de ajuda e suas URLs externas associadas.</span><span class="sxs-lookup"><span data-stu-id="efa29-126">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="efa29-127">Ele é usado para localizar a ajuda para um tópico específico na Web.</span><span class="sxs-lookup"><span data-stu-id="efa29-127">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="efa29-128">Você pode adicionar ou excluir tópicos desta lista.</span><span class="sxs-lookup"><span data-stu-id="efa29-128">You can add or delete topics from this list.</span></span>

```
$psOnlineHelp | Format-List

```

### <a name="sample-output"></a><span data-ttu-id="efa29-129">Saída de exemplo</span><span class="sxs-lookup"><span data-stu-id="efa29-129">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="efa29-130">Chave: Add-Computer</span><span class="sxs-lookup"><span data-stu-id="efa29-130">Key : Add-Computer</span></span>|<span data-ttu-id="efa29-131">Valor : http://go.microsoft.com/fwlink/p/?LinkID=135194</span><span class="sxs-lookup"><span data-stu-id="efa29-131">Value : http://go.microsoft.com/fwlink/p/?LinkID=135194</span></span>|
|<span data-ttu-id="efa29-132">Chave: Add-Content</span><span class="sxs-lookup"><span data-stu-id="efa29-132">Key : Add-Content</span></span>|<span data-ttu-id="efa29-133">Valor: http://go.microsoft.com/fwlink/p/?LinkID=113278</span><span class="sxs-lookup"><span data-stu-id="efa29-133">Value : http://go.microsoft.com/fwlink/p/?LinkID=113278</span></span>|

 <span data-ttu-id="efa29-134">O script a seguir adiciona uma entrada à lista.</span><span class="sxs-lookup"><span data-stu-id="efa29-134">The following script adds an entry to the list.</span></span>

```
$psOnlineHelp.Add("get-myNoun","http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="efa29-135">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="efa29-135">See Also</span></span>
- [<span data-ttu-id="efa29-136">O modelo de objeto de script do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="efa29-136">The Windows PowerShell ISE Scripting Object Model</span></span>](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
