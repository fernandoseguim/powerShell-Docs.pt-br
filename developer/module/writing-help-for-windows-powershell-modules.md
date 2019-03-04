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
# <a name="writing-help-for-windows-powershell-modules"></a><span data-ttu-id="199bb-102">Escrever ajuda para módulos do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="199bb-102">Writing Help for Windows PowerShell Modules</span></span>

<span data-ttu-id="199bb-103">Módulos do Windows PowerShell podem incluir tópicos da Ajuda sobre o módulo e sobre os membros do módulo, como cmdlets, provedores, funções e scripts.</span><span class="sxs-lookup"><span data-stu-id="199bb-103">Windows PowerShell modules can include Help topics about the module and about the module members, such as cmdlets, providers, functions and scripts.</span></span> <span data-ttu-id="199bb-104">O `Get-Help` cmdlet exibe os tópicos de Ajuda do módulo no mesmo formato que exibe a Ajuda para outros itens do Windows PowerShell e os usuários usam o padrão `Get-Help` comandos para obter os tópicos da Ajuda.</span><span class="sxs-lookup"><span data-stu-id="199bb-104">The `Get-Help` cmdlet displays the module Help topics in the same format as it displays Help for other Windows PowerShell items, and users use standard `Get-Help` commands to get the Help topics.</span></span>

<span data-ttu-id="199bb-105">Este documento explica o formato e o posicionamento correto dos tópicos de Ajuda do módulo e sugere as diretrizes para o conteúdo da Ajuda de módulo.</span><span class="sxs-lookup"><span data-stu-id="199bb-105">This document explains the format and correct placement of module Help topics, and it suggests guidelines for module Help content.</span></span>

## <a name="types-of-module-help"></a><span data-ttu-id="199bb-106">Tipos de Ajuda do módulo</span><span class="sxs-lookup"><span data-stu-id="199bb-106">Types of Module Help</span></span>

<span data-ttu-id="199bb-107">Um módulo pode incluir os seguintes tipos de Ajuda.</span><span class="sxs-lookup"><span data-stu-id="199bb-107">A module can include the following types of Help.</span></span>

- <span data-ttu-id="199bb-108">**A Ajuda do cmdlet**.</span><span class="sxs-lookup"><span data-stu-id="199bb-108">**Cmdlet Help**.</span></span> <span data-ttu-id="199bb-109">Os tópicos da Ajuda que descrevem os cmdlets em um módulo são arquivos XML que usam o comando ajudam do esquema</span><span class="sxs-lookup"><span data-stu-id="199bb-109">The Help topics that describe cmdlets in a module are XML files that use the command help schema</span></span>

- <span data-ttu-id="199bb-110">**Ajuda do provedor**.</span><span class="sxs-lookup"><span data-stu-id="199bb-110">**Provider Help**.</span></span> <span data-ttu-id="199bb-111">Os tópicos da Ajuda que descrevem os provedores em um módulo são arquivos XML que usam o provedor de ajudam do esquema.</span><span class="sxs-lookup"><span data-stu-id="199bb-111">The Help topics that describe providers in a module are XML files that use the provider help schema.</span></span>

- <span data-ttu-id="199bb-112">**Ajuda de função**.</span><span class="sxs-lookup"><span data-stu-id="199bb-112">**Function Help**.</span></span> <span data-ttu-id="199bb-113">Os tópicos da Ajuda que descrevem as funções em um módulo pode ser arquivos XML que usam o comando ajudam do esquema ou os tópicos da Ajuda baseada em comentário em função, ou o script ou módulo de script</span><span class="sxs-lookup"><span data-stu-id="199bb-113">The Help topics that describe functions in a module can be XML files that use the command help schema or comment-based Help topics within the function, or the script or script module</span></span>

- <span data-ttu-id="199bb-114">**Script Help**.</span><span class="sxs-lookup"><span data-stu-id="199bb-114">**Script Help**.</span></span> <span data-ttu-id="199bb-115">Os tópicos da Ajuda que descrevem os scripts em um módulo pode ser arquivos XML que usam o comando ajudam tópicos de ajuda baseados em comentário no script ou módulo de script ou de esquema.</span><span class="sxs-lookup"><span data-stu-id="199bb-115">The Help topics that describe scripts in a module can be XML files that use the command help schema or comment-based Help topics in the script or script module.</span></span>

- <span data-ttu-id="199bb-116">**Ajuda ("sobre")**.</span><span class="sxs-lookup"><span data-stu-id="199bb-116">**Conceptual ("About") Help**.</span></span> <span data-ttu-id="199bb-117">Você pode usar um tópico da Ajuda ("sobre") conceitual para descrever o módulo e seus membros e explicar como os membros podem ser usados juntos para executar tarefas.</span><span class="sxs-lookup"><span data-stu-id="199bb-117">You can use a conceptual ("about") Help topic to describe the module and its members and to explain how the members can be used together to perform tasks.</span></span> <span data-ttu-id="199bb-118">Tópicos de ajuda conceituais são arquivos de texto com a codificação Unicode (UTF-8).</span><span class="sxs-lookup"><span data-stu-id="199bb-118">Conceptual Help topics are text files with Unicode (UTF-8) encoding.</span></span> <span data-ttu-id="199bb-119">O nome do arquivo deve usar o `about_<name>.help.txt` formato, como about_MyModule.help.txt.</span><span class="sxs-lookup"><span data-stu-id="199bb-119">The file name must use the `about_<name>.help.txt` format, such as about_MyModule.help.txt.</span></span> <span data-ttu-id="199bb-120">Por padrão, Windows PowerShell inclui mais de 100 destes tópicos conceituais sobre da Ajuda, e eles são formatados como o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="199bb-120">By default, Windows PowerShell includes over 100 of these conceptual About Help topics, and they are formatted like the following example.</span></span>

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

## <a name="placement-of-module-help"></a><span data-ttu-id="199bb-121">Posicionamento de Ajuda do módulo</span><span class="sxs-lookup"><span data-stu-id="199bb-121">Placement of Module Help</span></span>

<span data-ttu-id="199bb-122">O `Get-Help` cmdlet procura arquivos de tópico da Ajuda de módulo em subdiretórios específicos do idioma do diretório do módulo.</span><span class="sxs-lookup"><span data-stu-id="199bb-122">The `Get-Help` cmdlet looks for module Help topic files in language-specific subdirectories of the module directory.</span></span>

<span data-ttu-id="199bb-123">Por exemplo, o diagrama de estrutura de diretório a seguir mostra o local dos tópicos da Ajuda para o módulo SampleModule.</span><span class="sxs-lookup"><span data-stu-id="199bb-123">For example, the following directory structure diagram shows the location of the Help topics for the SampleModule module.</span></span>

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
> <span data-ttu-id="199bb-124">No exemplo, o  *\<ModulePath >* espaço reservado representa um dos caminhos no `PSModulePath` variável de ambiente, como home\Documents\Modules $, $pshome\Modules ou um caminho personalizado que especifica o usuário.</span><span class="sxs-lookup"><span data-stu-id="199bb-124">In the example, the *\<ModulePath>* placeholder represents one of the paths in the `PSModulePath` environment variable, such as $home\Documents\Modules, $pshome\Modules, or a custom path that the user specifies.</span></span>

## <a name="getting-module-help"></a><span data-ttu-id="199bb-125">Obtendo Ajuda do módulo</span><span class="sxs-lookup"><span data-stu-id="199bb-125">Getting Module Help</span></span>

<span data-ttu-id="199bb-126">Quando um usuário importa um módulo em uma sessão, os tópicos da Ajuda do módulo são importados para a sessão, juntamente com o módulo.</span><span class="sxs-lookup"><span data-stu-id="199bb-126">When a user imports a module into a session, the Help topics for that module are imported into the session along with the module.</span></span> <span data-ttu-id="199bb-127">Você pode listar os arquivos de tópico da Ajuda no valor da chave FileList no manifesto do módulo, mas os tópicos da Ajuda não são afetados pelo `Export-ModuleMember` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="199bb-127">You can list the Help topic files in the value of the FileList key in the module manifest, but Help topics are not affected by the `Export-ModuleMember` cmdlet.</span></span>

<span data-ttu-id="199bb-128">Você pode fornecer os tópicos de ajuda de módulo em idiomas diferentes.</span><span class="sxs-lookup"><span data-stu-id="199bb-128">You can provide module Help topics in different languages.</span></span> <span data-ttu-id="199bb-129">O `Get-Help` cmdlet exibe automaticamente os tópicos de Ajuda do módulo no idioma especificado para o usuário atual no item no painel de controle Opções regionais e idiomas.</span><span class="sxs-lookup"><span data-stu-id="199bb-129">The `Get-Help` cmdlet automatically displays module Help topics in the language that is specified for the current user in the Regional and Language Options item in Control Panel.</span></span> <span data-ttu-id="199bb-130">No Windows Vista e versões posteriores do Windows, `Get-Help` procura os tópicos da Ajuda em subdiretórios específicos do idioma do diretório do módulo de acordo com os padrões de fallback de idioma estabelecidas para Windows.</span><span class="sxs-lookup"><span data-stu-id="199bb-130">In Windows Vista and later versions of Windows, `Get-Help` searches for the Help topics in language-specific subdirectories of the module directory in accordance with the language fallback standards established for Windows.</span></span>

<span data-ttu-id="199bb-131">A partir do Windows PowerShell 3.0, executando um `Get-Help` comando para um cmdlet ou função dispara a importação automática do módulo.</span><span class="sxs-lookup"><span data-stu-id="199bb-131">Beginning in Windows PowerShell 3.0, running a `Get-Help` command for a cmdlet or function triggers automatic importing of the module.</span></span> <span data-ttu-id="199bb-132">O `Get-Help` imediatamente, o cmdlet exibe o conteúdo dos tópicos da Ajuda no módulo.</span><span class="sxs-lookup"><span data-stu-id="199bb-132">The `Get-Help` cmdlet immediately displays the contents of the help topics in the module.</span></span>

<span data-ttu-id="199bb-133">Se o módulo não contém tópicos da Ajuda e não há nenhum tópicos da Ajuda para os comandos no módulo no computador do usuário, `Get-Help` exibe a Ajuda gerada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="199bb-133">If the module does not contain help topics and there are no help topics for the commands in the module on the user's computer, `Get-Help` displays auto-generated help.</span></span> <span data-ttu-id="199bb-134">A Ajuda gerada automaticamente inclui a sintaxe de comando, parâmetros e tipos de entrada e saída, mas não inclui todas as descrições.</span><span class="sxs-lookup"><span data-stu-id="199bb-134">The auto-generated help includes the command syntax, parameters, and input and output types, but does not include any descriptions.</span></span> <span data-ttu-id="199bb-135">A Ajuda gerada automaticamente inclui o texto que direciona o usuário a tentar usar o `Update-Help` cmdlet para baixar a Ajuda para o comando da Internet ou de um compartilhamento de arquivos.</span><span class="sxs-lookup"><span data-stu-id="199bb-135">The auto-generated help includes text that directs the user to try to use the `Update-Help` cmdlet to download help for the command from the Internet or a file share.</span></span> <span data-ttu-id="199bb-136">Ele também recomenda o uso de **Online** parâmetro do `Get-Help` para obter a versão online do tópico da Ajuda.</span><span class="sxs-lookup"><span data-stu-id="199bb-136">It also recommends using the **Online** parameter of the `Get-Help` cmdlet to get the online version of the help topic.</span></span>

## <a name="supporting-updatable-help"></a><span data-ttu-id="199bb-137">Suporte à ajuda atualizável</span><span class="sxs-lookup"><span data-stu-id="199bb-137">Supporting Updatable Help</span></span>

<span data-ttu-id="199bb-138">Os usuários do Windows PowerShell 3.0 e versões posteriores do Windows PowerShell podem baixar e instalar arquivos de Ajuda atualizados para um módulo da Internet ou de um compartilhamento de arquivos local.</span><span class="sxs-lookup"><span data-stu-id="199bb-138">Users of Windows PowerShell 3.0 and later versions of Windows PowerShell can download and install updated help files for a module from the Internet or from a local file share.</span></span> <span data-ttu-id="199bb-139">O `Update-Help` e `Save-Help` cmdlets ocultar os detalhes de gerenciamento do usuário.</span><span class="sxs-lookup"><span data-stu-id="199bb-139">The `Update-Help` and `Save-Help` cmdlets hide the management details from the user.</span></span> <span data-ttu-id="199bb-140">Os usuários executem o `Update-Help` cmdlet e, em seguida, use o `Get-Help` cmdlet para ler os arquivos de ajuda mais recentes para o módulo no prompt de comando do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="199bb-140">Users run the `Update-Help` cmdlet and then use the `Get-Help` cmdlet to read the newest help files for the module at the Windows PowerShell command prompt.</span></span> <span data-ttu-id="199bb-141">Os usuários não é necessário reiniciar o Windows ou Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="199bb-141">Users do not need to restart Windows or Windows PowerShell.</span></span>

<span data-ttu-id="199bb-142">Os usuários por trás de firewalls e aqueles sem acesso à Internet podem usar a Ajuda atualizável, também.</span><span class="sxs-lookup"><span data-stu-id="199bb-142">Users behind firewalls and those without Internet access can use Updatable Help, as well.</span></span> <span data-ttu-id="199bb-143">Acessam a administradores com a Internet usem o `Save-Help` cmdlet para baixar e instalar os arquivos de ajuda mais recentes para um compartilhamento de arquivos.</span><span class="sxs-lookup"><span data-stu-id="199bb-143">Administrators with Internet access use the `Save-Help` cmdlet to download and install the newest help files to a file share.</span></span> <span data-ttu-id="199bb-144">Em seguida, os usuários usam o **caminho** parâmetro do `Update-Help` para obter os arquivos de ajuda mais recentes do compartilhamento de arquivos.</span><span class="sxs-lookup"><span data-stu-id="199bb-144">Then, users use the **Path** parameter of the `Update-Help` cmdlet to get the newest help files from the file share.</span></span>

<span data-ttu-id="199bb-145">Os autores de módulo podem incluir arquivos de Ajuda no módulo e usar a Ajuda atualizável para atualizar os arquivos de Ajuda ou omitir os arquivos de Ajuda do módulo e usar a Ajuda atualizável para instalar e atualizá-los.</span><span class="sxs-lookup"><span data-stu-id="199bb-145">Module authors can include help files in the module and use Updatable Help to update the help files, or omit help files from the module and use Updatable Help both to install and to update them.</span></span>

<span data-ttu-id="199bb-146">Para obter mais informações sobre a Ajuda atualizável, consulte [suporte à Ajuda atualizável](./supporting-updatable-help.md).</span><span class="sxs-lookup"><span data-stu-id="199bb-146">For more information about Updatable Help, see [Supporting Updatable Help](./supporting-updatable-help.md).</span></span>

## <a name="supporting-online-help"></a><span data-ttu-id="199bb-147">Suporte à ajuda online</span><span class="sxs-lookup"><span data-stu-id="199bb-147">Supporting Online Help</span></span>

<span data-ttu-id="199bb-148">Os usuários que não é possível ou não instalam atualizavam ajuda arquivos em seus computadores frequentemente contam com a versão online dos tópicos de Ajuda do módulo.</span><span class="sxs-lookup"><span data-stu-id="199bb-148">Users who cannot or do not install updated help files on their computers often rely on the online version of module help topics.</span></span> <span data-ttu-id="199bb-149">O **Online** parâmetro do `Get-Help` cmdlet abre a versão online de um cmdlet ou função avançada de tópico de ajuda para o usuário no seu navegador de Internet padrão.</span><span class="sxs-lookup"><span data-stu-id="199bb-149">The **Online** parameter of the `Get-Help` cmdlet opens the online version of a cmdlet or advanced function help topic for the user in their default Internet browser.</span></span>

<span data-ttu-id="199bb-150">O `Get-Help` cmdlet usa o valor de **HelpUri** propriedade do cmdlet ou função para localizar a versão online do tópico da Ajuda.</span><span class="sxs-lookup"><span data-stu-id="199bb-150">The `Get-Help` cmdlet uses the value of the **HelpUri** property of the cmdlet or function to find the online version of the help topic.</span></span>

<span data-ttu-id="199bb-151">Começando no Windows PowerShell 3.0, você pode ajudar os usuários a localizar a versão online dos tópicos de ajuda de cmdlet e a função definindo o atributo HelpUri na classe do cmdlet ou o **HelpUri** propriedade do **CmdletBinding** atributo.</span><span class="sxs-lookup"><span data-stu-id="199bb-151">Beginning in Windows PowerShell 3.0, you can help users find the online version of cmdlet and function help topics by defining the HelpUri attribute on the cmdlet class or the **HelpUri** property of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="199bb-152">O valor do atributo é o valor da **HelpUri** propriedade do cmdlet ou função.</span><span class="sxs-lookup"><span data-stu-id="199bb-152">The value of the attribute is the value of the **HelpUri** property of the cmdlet or function.</span></span>

<span data-ttu-id="199bb-153">Para obter mais informações, consulte [suporte à Ajuda Online](./supporting-online-help.md).</span><span class="sxs-lookup"><span data-stu-id="199bb-153">For more information, see [Supporting Online Help](./supporting-online-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="199bb-154">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="199bb-154">See Also</span></span>

[<span data-ttu-id="199bb-155">Escrevendo um módulo do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="199bb-155">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="199bb-156">Suporte à Ajuda atualizável</span><span class="sxs-lookup"><span data-stu-id="199bb-156">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)

[<span data-ttu-id="199bb-157">Suporte à Ajuda Online</span><span class="sxs-lookup"><span data-stu-id="199bb-157">Supporting Online Help</span></span>](./supporting-online-help.md)