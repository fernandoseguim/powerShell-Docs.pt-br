---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: "Obtendo informações de ajuda detalhadas"
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: c786ce089073abccdf186dc1d9e8ee383f83655d
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2017
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="c8c51-103">Obtendo informações de ajuda detalhadas</span><span class="sxs-lookup"><span data-stu-id="c8c51-103">Getting Detailed Help Information</span></span>
<span data-ttu-id="c8c51-104">O Windows PowerShell inclui tópicos detalhados que explicam os conceitos do Windows PowerShell e a linguagem do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8c51-104">Windows PowerShell includes detailed Help topics that explain Windows PowerShell concepts and the Windows PowerShell language.</span></span> <span data-ttu-id="c8c51-105">Também há tópicos da Ajuda para cada cmdlet e tópicos de provedor e de Ajuda para muitas funções e scripts.</span><span class="sxs-lookup"><span data-stu-id="c8c51-105">There are also Help topics for each cmdlet and provider and Help topics for many functions and scripts.</span></span>

<span data-ttu-id="c8c51-106">Você pode exibir esses tópicos da Ajuda no prompt de comando ou exibir as versões mais atualizadas dos seguintes tópicos na Biblioteca do Microsoft TechNet.</span><span class="sxs-lookup"><span data-stu-id="c8c51-106">You can display these Help topics at the command prompt or view the most recently updated versions of these topics in the Microsoft TechNet Library.</span></span> <span data-ttu-id="c8c51-107">Muitos programas que hospedam o Windows PowerShell, como o Ambiente de Script Integrado do Windows PowerShell, fornecem recursos adicionais de Ajuda, como a Ajuda contextual e o arquivo de Ajuda compilado (.chm).</span><span class="sxs-lookup"><span data-stu-id="c8c51-107">Many programs that host Windows PowerShell, such as Windows PowerShell Integrated Scripting Environment, provide additional Help features, such as context-sensitive Help and compiled Help file (.chm).</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="c8c51-108">Obtendo Ajuda para os cmdlets</span><span class="sxs-lookup"><span data-stu-id="c8c51-108">Getting Help for Cmdlets</span></span>
<span data-ttu-id="c8c51-109">Para obter Ajuda para cmdlets do Windows PowerShell, use o cmdlet [Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2).</span><span class="sxs-lookup"><span data-stu-id="c8c51-109">To get Help about Windows PowerShell cmdlets, use the [Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) cmdlet.</span></span> <span data-ttu-id="c8c51-110">Por exemplo, para obter Ajuda para o cmdlet [Get-ChildItem [m2]](https://technet.microsoft.com/en-us/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc), digite:</span><span class="sxs-lookup"><span data-stu-id="c8c51-110">For example, to get Help for the [Get-ChildItem [m2]](https://technet.microsoft.com/en-us/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) cmdlet, type:</span></span>

```
get-help get-childitem
```

<span data-ttu-id="c8c51-111">ou</span><span class="sxs-lookup"><span data-stu-id="c8c51-111">or</span></span>

```
get-childitem -?
```

<span data-ttu-id="c8c51-112">Você pode até mesmo obter ajuda para o cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="c8c51-112">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="c8c51-113">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c8c51-113">For example:</span></span>

```
get-help get-help
```

<span data-ttu-id="c8c51-114">Para obter uma lista de todos os tópicos de Ajuda de cmdlet na sua sessão, digite:</span><span class="sxs-lookup"><span data-stu-id="c8c51-114">To get a list of all the cmdlet Help topics in your session, type:</span></span>

```
get-help -category cmdlet
```

<span data-ttu-id="c8c51-115">Para exibir uma página de cada tópico da Ajuda por vez, use a função **help** ou seu alias **man**.</span><span class="sxs-lookup"><span data-stu-id="c8c51-115">To display one page of each Help topic at a time, use the **help** function or its alias **man**.</span></span> <span data-ttu-id="c8c51-116">Por exemplo, para exibir a Ajuda do cmdlet Get-ChildItem, digite</span><span class="sxs-lookup"><span data-stu-id="c8c51-116">For example, to display Help for the Get-ChildItem cmdlet, type</span></span>

```
man get-childitem
```

<span data-ttu-id="c8c51-117">ou</span><span class="sxs-lookup"><span data-stu-id="c8c51-117">or</span></span>

```
help get-childitem
```

<span data-ttu-id="c8c51-118">Para exibir informações detalhadas sobre um cmdlet, uma função ou um script, incluindo descrições de seus parâmetros e exemplos de uso, use o parâmetro *Detailed* do cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="c8c51-118">To display detailed information about a cmdlet, function, or script, including descriptions of its parameters and examples of its use, use the *Detailed* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="c8c51-119">Por exemplo, para obter informações detalhadas sobre o cmdlet Get-ChildItem, digite:</span><span class="sxs-lookup"><span data-stu-id="c8c51-119">For example, to get detailed information about the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -detailed
```

<span data-ttu-id="c8c51-120">Para exibir todo o conteúdo do tópico da Ajuda, use o parâmetro *Full* do cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="c8c51-120">To display all content in the Help topic, use the *Full* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="c8c51-121">Por exemplo, para exibir todo o conteúdo do tópico de Ajuda para o cmdlet Get-ChildItem, digite:</span><span class="sxs-lookup"><span data-stu-id="c8c51-121">For example, to display all content in the Help topic for the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -full
```

<span data-ttu-id="c8c51-122">Para obter Ajuda detalhada sobre os parâmetros de um cmdlet, use o parâmetro *Parameter* do cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="c8c51-122">To get detailed Help about the parameters of a cmdlet, use the *Parameter* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="c8c51-123">Por exemplo, para obter Ajuda detalhada para todos os parâmetros do cmdlet Get-ChildItem, digite:</span><span class="sxs-lookup"><span data-stu-id="c8c51-123">For example, to get detailed Help for all of the parameters of the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -parameter *
```

<span data-ttu-id="c8c51-124">Para exibir apenas os exemplos em um tópico da Ajuda, use o parâmetro *Example* do Get-Help.</span><span class="sxs-lookup"><span data-stu-id="c8c51-124">To display only the examples in a Help topic, use the *Example* parameter of the Get-Help.</span></span> <span data-ttu-id="c8c51-125">Por exemplo, para exibir apenas os exemplos do tópico de Ajuda para o cmdlet Get-ChildItem, digite:</span><span class="sxs-lookup"><span data-stu-id="c8c51-125">For example, to display only the examples in the Help topic for the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -examples
```

<span data-ttu-id="c8c51-126">Para obter informações de como escrever tópicos de Ajuda para os cmdlets que você escreve, consulte [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) (Como escrever a ajuda do cmdlet) na biblioteca MSDN.</span><span class="sxs-lookup"><span data-stu-id="c8c51-126">For information about how to write Help topics for the cmdlets that you write, see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="c8c51-127">Obtendo Ajuda conceitual</span><span class="sxs-lookup"><span data-stu-id="c8c51-127">Getting Conceptual Help</span></span>
<span data-ttu-id="c8c51-128">O cmdlet Get-Help exibe também informações sobre tópicos conceituais no Windows PowerShell, incluindo tópicos sobre a linguagem do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8c51-128">The Get-Help cmdlet also displays information about conceptual topics in Windows PowerShell, including topics about the Windows PowerShell language.</span></span> <span data-ttu-id="c8c51-129">Tópicos de Ajuda conceituais começam com o prefixo "about_", como about_line_editing.</span><span class="sxs-lookup"><span data-stu-id="c8c51-129">Conceptual Help topics begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="c8c51-130">(O nome do tópico conceitual deve ser inserido em inglês, mesmo em versões do Windows PowerShell em idiomas diferentes do inglês.)</span><span class="sxs-lookup"><span data-stu-id="c8c51-130">(The name of the conceptual topic must be entered in English even on non-English versions of Windows PowerShell.)</span></span>

<span data-ttu-id="c8c51-131">Para exibir uma lista de tópicos conceituais, digite:</span><span class="sxs-lookup"><span data-stu-id="c8c51-131">To display a list of conceptual topics, type:</span></span>

```
get-help about_*
```

<span data-ttu-id="c8c51-132">Para exibir um tópico de Ajuda específico, digite o nome do tópico, como por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c8c51-132">To display a particular Help topic, type the topic name, for example:</span></span>

```
get-help about_command_syntax
```

<span data-ttu-id="c8c51-133">Os parâmetros de Get-Help, como *Detailed*, *Parameter* e *Examples*, não têm efeito sobre a exibição dos tópicos de Ajuda conceitual.</span><span class="sxs-lookup"><span data-stu-id="c8c51-133">The parameters of Get-Help, such as *Detailed*, *Parameter*, and *Examples*, have no effect on the display of conceptual Help topics.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="c8c51-134">Obtendo Ajuda para provedores</span><span class="sxs-lookup"><span data-stu-id="c8c51-134">Getting Help About Providers</span></span>
<span data-ttu-id="c8c51-135">O cmdlet Get-Help exibe informações sobre provedores do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8c51-135">The Get-Help cmdlet displays information about Windows PowerShell providers.</span></span> <span data-ttu-id="c8c51-136">Para obter Ajuda sobre um provedor, digite "Get-Help" seguido do nome do provedor.</span><span class="sxs-lookup"><span data-stu-id="c8c51-136">To get Help for a provider, type "Get-Help" followed by the provider name.</span></span> <span data-ttu-id="c8c51-137">Por exemplo, para obter Ajuda para o provedor de Registro, digite:</span><span class="sxs-lookup"><span data-stu-id="c8c51-137">For example, to get Help for the Registry provider, type:</span></span>

```
get-help registry
```

<span data-ttu-id="c8c51-138">Para obter uma lista de todos os tópicos de Ajuda de provedor na sua sessão, digite</span><span class="sxs-lookup"><span data-stu-id="c8c51-138">To get a list of all the provider Help topics in your session, type</span></span>

```
get-help -category provider
```

<span data-ttu-id="c8c51-139">Os parâmetros de Get-Help, como *Detailed*, *Parameter* e *Examples*, não têm efeito sobre a exibição dos tópicos de Ajuda de provedor.</span><span class="sxs-lookup"><span data-stu-id="c8c51-139">The parameters of Get-Help, such as *Detailed*, *Parameter*, and *Examples*, have no effect on the display of provider Help topics.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="c8c51-140">Obtendo Ajuda para scripts e funções</span><span class="sxs-lookup"><span data-stu-id="c8c51-140">Getting Help About Scripts and Functions</span></span>
<span data-ttu-id="c8c51-141">Muitos scripts e funções no Windows PowerShell têm tópicos da Ajuda.</span><span class="sxs-lookup"><span data-stu-id="c8c51-141">Many scripts and functions in Windows PowerShell have Help topics.</span></span> <span data-ttu-id="c8c51-142">Use o cmdlet Get-Help para exibir tópicos da Ajuda para scripts e funções.</span><span class="sxs-lookup"><span data-stu-id="c8c51-142">Use the Get-Help cmdlet to display the Help topics for scripts and functions.</span></span>

<span data-ttu-id="c8c51-143">Para exibir a Ajuda para uma função, digite "get-help" seguido pelo nome da função.</span><span class="sxs-lookup"><span data-stu-id="c8c51-143">To display the Help for a function, type "get-help" followed by the function name.</span></span> <span data-ttu-id="c8c51-144">Por exemplo, para obter Ajuda para a função Disable-PSRemoting, digite:</span><span class="sxs-lookup"><span data-stu-id="c8c51-144">For example, to get Help for the Disable-PSRemoting function, type:</span></span>

```
get-help disable-psremoting
```

<span data-ttu-id="c8c51-145">Para exibir a Ajuda para um script, digite o caminho totalmente qualificado para o arquivo de script.</span><span class="sxs-lookup"><span data-stu-id="c8c51-145">To display the Help for a script, type the fully qualified path to the script file.</span></span> <span data-ttu-id="c8c51-146">Se o script estiver em um caminho listado na variável de ambiente Path, você poderá omitir o caminho do comando.</span><span class="sxs-lookup"><span data-stu-id="c8c51-146">If the script is in a path that is listed in the Path environment variable, you can omit the path from the command.</span></span>

<span data-ttu-id="c8c51-147">Por exemplo, se você tiver um script chamado "TestScript.ps1" no diretório C:\\PS-Test, para exibir o tópico da Ajuda do script, digite:</span><span class="sxs-lookup"><span data-stu-id="c8c51-147">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help topic for the script, type:</span></span>

```
get-help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="c8c51-148">Os parâmetros que foram projetados para exibir o cmdlet Help, como *Detailed*, *Full*, *Examples* e *Parameter* funcionam tanto para o script quanto para a função Help.</span><span class="sxs-lookup"><span data-stu-id="c8c51-148">The parameters that were designed for displaying cmdlet Help, such as *Detailed*, *Full*, *Examples*, and *Parameter*, work for script Help and function Help, too.</span></span> <span data-ttu-id="c8c51-149">No entanto, ao exibir toda a Ajuda digitando "get-help \*", a Ajuda de funções e scripts não é exibida.</span><span class="sxs-lookup"><span data-stu-id="c8c51-149">However, when you display all Help, by typing "get-help \*", Help for functions and scripts does not appear.</span></span>

<span data-ttu-id="c8c51-150">Para obter informações sobre como criar Ajuda para suas funções e scripts, consulte [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af) e [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).</span><span class="sxs-lookup"><span data-stu-id="c8c51-150">For information about writing Help topics for your functions and scripts, see [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af), and [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).</span></span>

## <a name="getting-help-online"></a><span data-ttu-id="c8c51-151">Obtendo Ajuda online</span><span class="sxs-lookup"><span data-stu-id="c8c51-151">Getting Help Online</span></span>
<span data-ttu-id="c8c51-152">Se você estiver conectado à Internet, uma das melhores maneiras de obter Ajuda será exibir os tópicos da Ajuda online.</span><span class="sxs-lookup"><span data-stu-id="c8c51-152">If you are connected to the Internet, one of the best ways to get Help is to view the Help topics online.</span></span> <span data-ttu-id="c8c51-153">Como tópicos online são fáceis de atualizar, eles provavelmente fornecerão o conteúdo mais atual.</span><span class="sxs-lookup"><span data-stu-id="c8c51-153">Because online topics are easy to update, they are likely to provide the most current content.</span></span>

<span data-ttu-id="c8c51-154">Para obter Ajuda online, experimente o parâmetro *Online* do cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="c8c51-154">To get Help online, try the *Online* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="c8c51-155">O parâmetro *Online* do cmdlet Get-Help funciona somente para Ajuda de cmdlet, Ajuda de função e Ajuda de script.</span><span class="sxs-lookup"><span data-stu-id="c8c51-155">The *Online* parameter of the Get-Help cmdlet works only for cmdlet Help, function Help, and script Help.</span></span> <span data-ttu-id="c8c51-156">Não é possível usar o parâmetro *Online* com tópicos de Ajuda conceitual (About) ou de provedor.</span><span class="sxs-lookup"><span data-stu-id="c8c51-156">You cannot use the *Online* parameter with conceptual (About) topics or provider Help topics.</span></span> <span data-ttu-id="c8c51-157">Além disso, como esse recurso é opcional, ele não funciona para o tópico de Ajuda de todos os cmdlets, funções ou scripts.</span><span class="sxs-lookup"><span data-stu-id="c8c51-157">Also, because this feature is optional, it does not work for every cmdlet, function, or script Help topic.</span></span>

<span data-ttu-id="c8c51-158">No entanto, todos os tópicos de Ajuda que acompanham o Windows PowerShell, incluindo tópicos de Ajuda de provedor e conceitual (About), estão disponíveis online na seção [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) da Biblioteca do Microsoft TechNet.</span><span class="sxs-lookup"><span data-stu-id="c8c51-158">However, all the Help topics that come with Windows PowerShell, including provider Help and conceptual (About) Help topics, are available online in the [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) section of the Microsoft TechNet Library.</span></span>

<span data-ttu-id="c8c51-159">Para usar o parâmetro *Online* do cmdlet Get-Help, use o seguinte formato de comando.</span><span class="sxs-lookup"><span data-stu-id="c8c51-159">To use the *Online* parameter of the Get-Help cmdlet, use the following command format.</span></span>

```
get-help <command-name> -online
```

<span data-ttu-id="c8c51-160">Por exemplo, para obter a versão online do tópico da Ajuda para o cmdlet Get-ChildItem, digite:</span><span class="sxs-lookup"><span data-stu-id="c8c51-160">For example, to get the online version of the Help topic about the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -online
```

<span data-ttu-id="c8c51-161">Se uma versão online do tópico da Ajuda estiver disponível, ela será aberta no navegador padrão.</span><span class="sxs-lookup"><span data-stu-id="c8c51-161">If an online version of the Help topic is available, it will open in your default browser.</span></span>

<span data-ttu-id="c8c51-162">Se a Ajuda online tiver suporte em um tópico da Ajuda, você também poderá exibir a URL (o endereço de Internet) do tópico da Ajuda.</span><span class="sxs-lookup"><span data-stu-id="c8c51-162">If online Help is supported for a Help topic, you can also view the Internet address (URL) of the Help topic.</span></span> <span data-ttu-id="c8c51-163">O endereço de Internet é exibido na seção Links Relacionados de um tópico da Ajuda.</span><span class="sxs-lookup"><span data-stu-id="c8c51-163">The Internet address appears in the Related Links section of a Help topic.</span></span>

<span data-ttu-id="c8c51-164">Por exemplo, para ver a URL da versão online do cmdlet Add-Computer, digite:</span><span class="sxs-lookup"><span data-stu-id="c8c51-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```
get-help add-computer
```

<span data-ttu-id="c8c51-165">A primeira linha na seção Links Relacionados do tópico é mostrada abaixo.</span><span class="sxs-lookup"><span data-stu-id="c8c51-165">The first line in the Related Links section of the topic is shown below.</span></span>

```
Online version: http://go.microsoft.com/fwlink/?LinkID=135194
```

<span data-ttu-id="c8c51-166">Para obter informações de como dar suporte online aos seus tópicos da Ajuda, consulte [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf) e [Como escrever a ajuda do Cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415) na biblioteca MSDN.</span><span class="sxs-lookup"><span data-stu-id="c8c51-166">For information about how to provide online support for your Help topics, see [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf), and see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8c51-167">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="c8c51-167">See Also</span></span>
- [<span data-ttu-id="c8c51-168">about_Functions [m2]</span><span class="sxs-lookup"><span data-stu-id="c8c51-168">about_Functions [m2]</span></span>](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)
- [<span data-ttu-id="c8c51-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="c8c51-169">about_Scripts</span></span>](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af)
- [<span data-ttu-id="c8c51-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="c8c51-170">about_Comment_Based_Help</span></span>](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)
- [<span data-ttu-id="c8c51-171">Get-Help [m2]</span><span class="sxs-lookup"><span data-stu-id="c8c51-171">Get-Help [m2]</span></span>](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)

