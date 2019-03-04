---
title: Noções básicas sobre um módulo do Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4e38235-9987-4347-afd2-0f7d1dc8f64a
caps.latest.revision: 19
ms.openlocfilehash: 77d328bc1cb8cb42d5a10f107a149c05ab270ce3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862732"
---
# <a name="understanding-a-windows-powershell-module"></a><span data-ttu-id="b6aea-102">Noções básicas sobre um módulo do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b6aea-102">Understanding a Windows PowerShell Module</span></span>

<span data-ttu-id="b6aea-103">Um *módulo* é um conjunto de funcionalidades relacionadas do Windows PowerShell, agrupados juntos como uma unidade conveniente (normalmente, salva em um único diretório).</span><span class="sxs-lookup"><span data-stu-id="b6aea-103">A *module* is a set of related Windows PowerShell functionalities, grouped together as a convenient unit (usually saved in a single directory).</span></span> <span data-ttu-id="b6aea-104">Definindo um conjunto de arquivos de script relacionadas, assemblies e recursos relacionados como um módulo, você pode fazer referência, carregar, persistir e compartilhar seu código mais fácil do que você precisaria de outra forma.</span><span class="sxs-lookup"><span data-stu-id="b6aea-104">By defining a set of related script files, assemblies, and related resources as a module, you can reference, load, persist, and share your code much easier than you would otherwise.</span></span>

<span data-ttu-id="b6aea-105">O objetivo principal de um módulo é permitir que a modularização (ou seja, reutilização e abstração) de código do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b6aea-105">The main purpose of a module is to allow the modularization (ie, reuse and abstraction) of Windows PowerShell code.</span></span> <span data-ttu-id="b6aea-106">Por exemplo, a maneira mais básica de criação de um módulo é simplesmente salvar um script do Windows PowerShell como um arquivo. psm1.</span><span class="sxs-lookup"><span data-stu-id="b6aea-106">For example, the most basic way of creating a module is to simply save a Windows PowerShell script as a .psm1 file.</span></span> <span data-ttu-id="b6aea-107">Fazer então permite que você controle (ou seja, tornar público ou privado) as funções e variáveis contidas no script.</span><span class="sxs-lookup"><span data-stu-id="b6aea-107">Doing so allows you to control (ie, make public or private) the functions and variables contained in the script.</span></span> <span data-ttu-id="b6aea-108">Salvando o script como um arquivo. psm1 também permite que você controle o escopo de certas variáveis.</span><span class="sxs-lookup"><span data-stu-id="b6aea-108">Saving the script as a .psm1 file also allows you to control the scope of certain variables.</span></span> <span data-ttu-id="b6aea-109">Por fim, você também pode usar cmdlets como [Install-Module](/powershell/module/PowershellGet/Install-Module) para organizar, instalar e usar o script como blocos de construção para soluções maiores.</span><span class="sxs-lookup"><span data-stu-id="b6aea-109">Finally, you can also use cmdlets such as [Install-Module](/powershell/module/PowershellGet/Install-Module) to organize, install, and use your script as building blocks for larger solutions.</span></span>

## <a name="module-components-and-types"></a><span data-ttu-id="b6aea-110">Tipos e os componentes de módulo</span><span class="sxs-lookup"><span data-stu-id="b6aea-110">Module Components and Types</span></span>

<span data-ttu-id="b6aea-111">Um módulo é composto por quatro componentes básicos:</span><span class="sxs-lookup"><span data-stu-id="b6aea-111">A module is made up of four basic components:</span></span>

1. <span data-ttu-id="b6aea-112">Algum tipo de arquivo de código, normalmente, um script do PowerShell ou um assembly de cmdlet gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="b6aea-112">Some sort of code file - usually either a PowerShell script or a managed cmdlet assembly.</span></span>

2. <span data-ttu-id="b6aea-113">Qualquer outra coisa que o arquivo de código acima pode precisa, como assemblies adicionais, ajudar a arquivos ou scripts.</span><span class="sxs-lookup"><span data-stu-id="b6aea-113">Anything else that the above code file may need, such as additional assemblies, help files, or scripts.</span></span>

3. <span data-ttu-id="b6aea-114">Um arquivo de manifesto que descreve os arquivos acima, bem como armazena metadados, como informações de autor e controle de versão...</span><span class="sxs-lookup"><span data-stu-id="b6aea-114">A manifest file that describes the above files, as well as stores metadada such as author and versioning information..</span></span>

4. <span data-ttu-id="b6aea-115">Um diretório que contém todo o conteúdo acima e está localizado onde PowerShell razoavelmente pode encontrá-lo.</span><span class="sxs-lookup"><span data-stu-id="b6aea-115">A directory that contains all of the above content, and is located where PowerShell can reasonably find it.</span></span>

   <span data-ttu-id="b6aea-116">Observe que nenhum desses componentes, por si só, é realmente necessário.</span><span class="sxs-lookup"><span data-stu-id="b6aea-116">Note that none of these components, by themselves, are actually necessary.</span></span> <span data-ttu-id="b6aea-117">Por exemplo, um módulo pode tecnicamente ser somente um script armazenado em um arquivo. psm1.</span><span class="sxs-lookup"><span data-stu-id="b6aea-117">For example, a module can technically be only a script stored in a .psm1 file.</span></span> <span data-ttu-id="b6aea-118">Você também pode ter um módulo que é nada além de um arquivo de manifesto, que é usado principalmente para fins de organização.</span><span class="sxs-lookup"><span data-stu-id="b6aea-118">You can also have a module that is nothing but a manifest file, which is used mainly for organizational purposes.</span></span> <span data-ttu-id="b6aea-119">Você também pode escrever um script que cria dinamicamente um módulo e, assim, não precisa realmente um diretório para armazenar qualquer coisa no.</span><span class="sxs-lookup"><span data-stu-id="b6aea-119">You can also write a script that dynamically creates a module, and as such doesn't actually need a directory to store anything in.</span></span> <span data-ttu-id="b6aea-120">As seções a seguir descrevem os tipos de módulos, que você pode obter ao misturar e combinar as diferentes partes possíveis de um módulo juntos.</span><span class="sxs-lookup"><span data-stu-id="b6aea-120">The following sections describe the types of modules you can get by mixing and matching the different possible parts of a module together.</span></span>

### <a name="script-modules"></a><span data-ttu-id="b6aea-121">Módulos de script</span><span class="sxs-lookup"><span data-stu-id="b6aea-121">Script Modules</span></span>

<span data-ttu-id="b6aea-122">Como o nome implica, uma *módulo de script* é um arquivo (. psm1) que contém qualquer código válido do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b6aea-122">As the name implies, a *script module* is a file (.psm1) that contains any valid Windows PowerShell code.</span></span> <span data-ttu-id="b6aea-123">Os administradores e desenvolvedores de script podem usar esse tipo de módulo para criar módulos cujos membros incluem funções, variáveis e muito mais.</span><span class="sxs-lookup"><span data-stu-id="b6aea-123">Script developers and administrators can use this type of module to create modules whose members include functions, variables, and more.</span></span> <span data-ttu-id="b6aea-124">Em essência, um módulo de script é simplesmente um script do Windows PowerShell com uma extensão diferente, que permite aos administradores usar funções de gerenciamento, exportação e importação nele.</span><span class="sxs-lookup"><span data-stu-id="b6aea-124">At heart, a script module is simply a Windows PowerShell script with a different extension, which allows administrators to use import, export, and management functions on it.</span></span>

<span data-ttu-id="b6aea-125">Além disso, você pode usar um arquivo de manifesto para incluir outros recursos em seu módulo, como arquivos de dados, outros módulos dependentes ou scripts de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b6aea-125">In addition, you can use a manifest file to include other resources in your module, such as data files, other dependent modules, or runtime scripts.</span></span> <span data-ttu-id="b6aea-126">Arquivos de manifesto também são úteis para metadados, como informações de criação e controle de versão de controle.</span><span class="sxs-lookup"><span data-stu-id="b6aea-126">Manifest files are also useful for tracking metadata such as authoring and versioning information.</span></span>

<span data-ttu-id="b6aea-127">Por fim, um módulo de script, como qualquer outro módulo que não será criado dinamicamente, precisa ser salvo em uma pasta que o PowerShell razoavelmente pode descobrir.</span><span class="sxs-lookup"><span data-stu-id="b6aea-127">Finally, a script module, like any other module that isn't dynamically created, needs to be saved in a folder that PowerShell can reasonably discover.</span></span> <span data-ttu-id="b6aea-128">Geralmente, isso é no caminho do módulo do PowerShell; mas, se necessário você pode descrever explicitamente onde o módulo está instalado.</span><span class="sxs-lookup"><span data-stu-id="b6aea-128">Usually, this is on the PowerShell module path; but if necessary you can explicitly describe where your module is installed.</span></span> <span data-ttu-id="b6aea-129">Para obter mais informações, consulte [como escrever um módulo de Script do PowerShell](./how-to-write-a-powershell-script-module.md).</span><span class="sxs-lookup"><span data-stu-id="b6aea-129">For more information, see [How to Write a PowerShell Script Module](./how-to-write-a-powershell-script-module.md).</span></span>

### <a name="binary-modules"></a><span data-ttu-id="b6aea-130">Módulos binários</span><span class="sxs-lookup"><span data-stu-id="b6aea-130">Binary Modules</span></span>

<span data-ttu-id="b6aea-131">Um *módulo binário* é um assembly do .NET Framework (. dll) que contém o código compilado, como C#.</span><span class="sxs-lookup"><span data-stu-id="b6aea-131">A *binary module* is a .NET Framework assembly (.dll) that contains compiled code, such as C#.</span></span> <span data-ttu-id="b6aea-132">Os desenvolvedores de cmdlet podem usar esse tipo de módulo para compartilhar cmdlets, provedores e muito mais.</span><span class="sxs-lookup"><span data-stu-id="b6aea-132">Cmdlet developers can use this type of module to share cmdlets, providers, and more.</span></span> <span data-ttu-id="b6aea-133">(Os snap-ins existentes também pode ser usados como módulos binários.) Em comparação com um módulo de script, um módulo binário permite que você crie cmdlets que são mais rápidos ou usar os recursos (como multithreading) que não são tão fácil de codificar em scripts do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b6aea-133">(Existing snap-ins can also be used as binary modules.) Compared to a script module, a binary module allows you to create cmdlets that are faster or use features (such as multithreading) that are not as easy to code in Windows PowerShell scripts.</span></span>

<span data-ttu-id="b6aea-134">Como com módulos de script, você pode incluir um arquivo de manifesto para descrever os recursos adicionais que usa seu módulo e para controlar metadados sobre seu módulo.</span><span class="sxs-lookup"><span data-stu-id="b6aea-134">As with script modules, you can include a manifest file to describe additional resources that your module uses, and to track metadata about your module.</span></span> <span data-ttu-id="b6aea-135">Da mesma forma, você provavelmente deve instalar o módulo binário em uma pasta em algum lugar no caminho do módulo do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b6aea-135">Similarly, you probably should install your binary module in a folder somewhere along the PowerShell module path.</span></span> <span data-ttu-id="b6aea-136">Para obter mais informações, consulte como [como escrever um módulo binário do PowerShell](./how-to-write-a-powershell-binary-module.md).</span><span class="sxs-lookup"><span data-stu-id="b6aea-136">For more information, see How to [How to Write a PowerShell Binary Module](./how-to-write-a-powershell-binary-module.md).</span></span>

### <a name="manifest-modules"></a><span data-ttu-id="b6aea-137">Módulos de manifesto</span><span class="sxs-lookup"><span data-stu-id="b6aea-137">Manifest Modules</span></span>

<span data-ttu-id="b6aea-138">Um *módulo de manifesto* é um módulo que usa um arquivo de manifesto para descrever todos os seus componentes, mas não tem qualquer tipo de assembly principal ou script.</span><span class="sxs-lookup"><span data-stu-id="b6aea-138">A *manifest module* is a module that uses a manifest file to describe all of its components, but doesn't have any sort of core assembly or script.</span></span> <span data-ttu-id="b6aea-139">(Formalmente, o módulo de manifesto deixa o `ModuleToProcess` ou `RootModule` elemento do manifesto vazio.) No entanto, você ainda pode usar outros recursos de um módulo, como a capacidade de carregar assemblies de dependente ou executar certos scripts de pré-processando automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b6aea-139">(Formally, a manifest module leaves the `ModuleToProcess` or `RootModule` element of the manifest empty.) However, you can still use the other features of a module, such as the ability to load up dependent assemblies or automatically run certain pre-processing scripts.</span></span> <span data-ttu-id="b6aea-140">Você também pode usar um módulo de manifesto como uma maneira conveniente de empacotar os recursos que outros módulos serão usadas, como módulos aninhados, assemblies, tipos ou formatos.</span><span class="sxs-lookup"><span data-stu-id="b6aea-140">You can also use a manifest module as a convenient way to package up resources that other modules will use, such as nested modules, assemblies, types, or formats.</span></span> <span data-ttu-id="b6aea-141">Para obter mais informações, consulte [como escrever um manifesto de módulo do PowerShell](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="b6aea-141">For more information, see [How to Write a PowerShell Module Manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

### <a name="dynamic-modules"></a><span data-ttu-id="b6aea-142">Módulos dinâmicos</span><span class="sxs-lookup"><span data-stu-id="b6aea-142">Dynamic Modules</span></span>

<span data-ttu-id="b6aea-143">Um *módulo dinâmico* é um módulo não foi carregado ou salvo em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="b6aea-143">A *dynamic module* is a module is not loaded from, or saved to, a file.</span></span> <span data-ttu-id="b6aea-144">Em vez disso, eles são criados dinamicamente por um script, usando o [New-Module](/powershell/module/Microsoft.PowerShell.Core/New-Module) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b6aea-144">Instead, they are created dynamically by a script, using the [New-Module](/powershell/module/Microsoft.PowerShell.Core/New-Module) cmdlet.</span></span> <span data-ttu-id="b6aea-145">Esse tipo de módulo permite que um script criar um módulo sob demanda que não precisam ser carregados ou salvos no armazenamento persistente.</span><span class="sxs-lookup"><span data-stu-id="b6aea-145">This type of module enables a script to create a module on demand that does not need to be loaded or saved to persistent storage.</span></span> <span data-ttu-id="b6aea-146">Por sua natureza, um módulo dinâmico se destina a ser de curta duração e, portanto, não pode ser acessado pelo `Get-Module` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b6aea-146">By its nature, a dynamic module is intended to be short-lived, and therefore cannot be accessed by the `Get-Module` cmdlet.</span></span> <span data-ttu-id="b6aea-147">Da mesma forma, eles geralmente não precisam de manifestos de módulo, nem fazem que provavelmente precisarão permanentes pastas para armazenar seus assemblies relacionados.</span><span class="sxs-lookup"><span data-stu-id="b6aea-147">Similarly, they usually do not need module manifests, nor do they likely need permanent folders to store their related assemblies.</span></span>

## <a name="module-manifests"></a><span data-ttu-id="b6aea-148">Manifestos de módulo</span><span class="sxs-lookup"><span data-stu-id="b6aea-148">Module Manifests</span></span>

<span data-ttu-id="b6aea-149">Um *manifesto de módulo* é um arquivo. psd1 que contém uma tabela de hash.</span><span class="sxs-lookup"><span data-stu-id="b6aea-149">A *module manifest* is a .psd1 file that contains a hash table.</span></span> <span data-ttu-id="b6aea-150">As chaves e valores na tabela de hash fazem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b6aea-150">The keys and values in the hash table do the following things:</span></span>

- <span data-ttu-id="b6aea-151">Descreva o conteúdo e os atributos do módulo.</span><span class="sxs-lookup"><span data-stu-id="b6aea-151">Describe the contents and attributes of the module.</span></span>

- <span data-ttu-id="b6aea-152">Defina os pré-requisitos.</span><span class="sxs-lookup"><span data-stu-id="b6aea-152">Define the prerequisites.</span></span>

- <span data-ttu-id="b6aea-153">Determine como os componentes são processados.</span><span class="sxs-lookup"><span data-stu-id="b6aea-153">Determine how the components are processed.</span></span>

  <span data-ttu-id="b6aea-154">Manifestos não são necessários para um módulo.</span><span class="sxs-lookup"><span data-stu-id="b6aea-154">Manifests are not required for a module.</span></span> <span data-ttu-id="b6aea-155">Módulos podem fazer referência a arquivos de script (. ps1), arquivos de módulo (. psm1), arquivos de manifesto (. psd1), formatação de script e digite arquivos (. ps1xml), conjuntos de módulos de cmdlet e o provedor (. dll), arquivos de recurso, arquivos de Ajuda, arquivos de localização ou qualquer outro tipo de arquivo ou recurso que é fornecido como parte do módulo.</span><span class="sxs-lookup"><span data-stu-id="b6aea-155">Modules can reference script files (.ps1), script module files (.psm1), manifest files (.psd1), formatting and type files (.ps1xml), cmdlet and provider assemblies (.dll), resource files, Help files, localization files, or any other type of file or resource that is bundled as part of the module.</span></span> <span data-ttu-id="b6aea-156">Para obter um script internacionalizado, a pasta de módulo também contém um conjunto de arquivos de catálogo de mensagens.</span><span class="sxs-lookup"><span data-stu-id="b6aea-156">For an internationalized script, the module folder also contains a set of message catalog files.</span></span> <span data-ttu-id="b6aea-157">Se você adicionar um arquivo de manifesto para a pasta de módulo, você pode fazer referência os vários arquivos como uma única unidade referenciando o manifesto.</span><span class="sxs-lookup"><span data-stu-id="b6aea-157">If you add a manifest file to the module folder, you can reference the multiple files as a single unit by referencing the manifest.</span></span>

  <span data-ttu-id="b6aea-158">O manifesto do próprio descreve categorias de informações a seguir:</span><span class="sxs-lookup"><span data-stu-id="b6aea-158">The manifest itself describes the following categories of information:</span></span>

- <span data-ttu-id="b6aea-159">Metadados sobre o módulo, como o número de versão do módulo, o autor e a descrição.</span><span class="sxs-lookup"><span data-stu-id="b6aea-159">Metadata about the module, such as the module version number, the author, and the description.</span></span>

- <span data-ttu-id="b6aea-160">Pré-requisitos necessários para importar o módulo, como a versão do Windows PowerShell, a versão do common language runtime (CLR) e os módulos necessários.</span><span class="sxs-lookup"><span data-stu-id="b6aea-160">Prerequisites needed to import the module, such as the Windows PowerShell version, the common language runtime (CLR) version, and the required modules.</span></span>

- <span data-ttu-id="b6aea-161">Diretivas de processamento, como os scripts, formatos e tipos para processar.</span><span class="sxs-lookup"><span data-stu-id="b6aea-161">Processing directives, such as the scripts, formats, and types to process.</span></span>

- <span data-ttu-id="b6aea-162">Restrições sobre os membros do módulo para exportar, como os aliases, funções, variáveis e cmdlets para exportar.</span><span class="sxs-lookup"><span data-stu-id="b6aea-162">Restrictions on the members of the module to export, such as the aliases, functions, variables, and cmdlets to export.</span></span>

  <span data-ttu-id="b6aea-163">Para obter mais informações, consulte [como escrever um manifesto de módulo do PowerShell](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="b6aea-163">For more information, see [How to Write a PowerShell Module Manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

## <a name="storing-and-installing-a-module"></a><span data-ttu-id="b6aea-164">Armazenando e instalando um módulo</span><span class="sxs-lookup"><span data-stu-id="b6aea-164">Storing and Installing a Module</span></span>

<span data-ttu-id="b6aea-165">Depois de criar um script, o módulo binário ou manifesto, você pode salvar seu trabalho em um local que outras pessoas possam acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="b6aea-165">Once you have created a script, binary, or manifest module, you can save your work in a location that others may access it.</span></span> <span data-ttu-id="b6aea-166">Por exemplo, o módulo pode ser armazenado na pasta do sistema onde o Windows PowerShell está instalado, ou ele pode ser armazenado em uma pasta de usuário.</span><span class="sxs-lookup"><span data-stu-id="b6aea-166">For example, your module can be stored in the system folder where Windows PowerShell is installed, or it can be stored in a user folder.</span></span>

<span data-ttu-id="b6aea-167">Em termos gerais, você pode determinar onde você deve instalar o módulo usando um dos caminhos armazenados no `$ENV:PSModulePath` variável.</span><span class="sxs-lookup"><span data-stu-id="b6aea-167">Generally speaking, you can determine where you should install your module by using one of the paths stored in the `$ENV:PSModulePath` variable.</span></span> <span data-ttu-id="b6aea-168">Usar um desses caminhos significa PowerShell pode localizar e carregar o módulo quando um usuário faz uma chamada a ele em seu código automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b6aea-168">Using one of these paths means that PowerShell can automatically find and load your module when a user makes a call to it in their code.</span></span> <span data-ttu-id="b6aea-169">Se você armazenar seu módulo em outro lugar, você pode explicitamente informar PowerShell passando o local do seu módulo como um parâmetro ao chamar `Install-Module`.</span><span class="sxs-lookup"><span data-stu-id="b6aea-169">If you store your module somewhere else, you can explicitly let PowerShell know by passing in the location of your module as a parameter when you call `Install-Module`.</span></span>

<span data-ttu-id="b6aea-170">Independentemente disso, o caminho da pasta é conhecido como o *base* do módulo (ModuleBase) e o nome do script, o arquivo de módulo binário ou de manifesto deve ser o mesmo que o nome da pasta de módulo, com as seguintes exceções:</span><span class="sxs-lookup"><span data-stu-id="b6aea-170">Regardless, the path of the folder is referred to as the *base* of the module (ModuleBase), and the name of the script, binary, or manifest module file should be the same as the module folder name, with the following exceptions:</span></span>

- <span data-ttu-id="b6aea-171">Módulos dinâmicos que são criados pela `New-Module` cmdlet pode ser nomeado usando o `Name` parâmetro do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b6aea-171">Dynamic modules that are created by the `New-Module` cmdlet can be named using the `Name` parameter of the cmdlet.</span></span>

- <span data-ttu-id="b6aea-172">Módulos importados de objetos de assembly, o  **`Import-Module` -Assembly** comando são nomeados de acordo com a seguinte sintaxe: `"dynamic_code_module_" + assembly.GetName()`.</span><span class="sxs-lookup"><span data-stu-id="b6aea-172">Modules imported from assembly objects by the **`Import-Module` -Assembly** command are named according to the following syntax: `"dynamic_code_module_" + assembly.GetName()`.</span></span>

  <span data-ttu-id="b6aea-173">Para obter mais informações, consulte [instalando um módulo do PowerShell](./installing-a-powershell-module.md) e [modificando o caminho de instalação do PSModulePath](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="b6aea-173">For more information, see [Installing a PowerShell Module](./installing-a-powershell-module.md) and [Modifying the PSModulePath Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

## <a name="module-cmdlets-and-variables"></a><span data-ttu-id="b6aea-174">Variáveis e os Cmdlets do módulo</span><span class="sxs-lookup"><span data-stu-id="b6aea-174">Module Cmdlets and Variables</span></span>

<span data-ttu-id="b6aea-175">As variáveis e os cmdlets a seguir são fornecidas pelo Windows PowerShell para a criação e gerenciamento de módulos.</span><span class="sxs-lookup"><span data-stu-id="b6aea-175">The following cmdlets and variables are provided by Windows PowerShell for the creation and management of modules.</span></span>

<span data-ttu-id="b6aea-176">[Novo módulo](/powershell/module/Microsoft.PowerShell.Core/New-Module) cmdlet esse cmdlet cria um novo módulo dinâmico que existe apenas na memória.</span><span class="sxs-lookup"><span data-stu-id="b6aea-176">[New-Module](/powershell/module/Microsoft.PowerShell.Core/New-Module) cmdlet This cmdlet creates a new dynamic module that exists only in memory.</span></span> <span data-ttu-id="b6aea-177">O módulo é criado a partir de um bloco de script e seus membros exportados, como suas funções e variáveis, ficam imediatamente disponíveis na sessão e permanecem disponíveis até que a sessão é fechada.</span><span class="sxs-lookup"><span data-stu-id="b6aea-177">The module is created from a script block, and its exported members, such as its functions and variables, are immediately available in the session and remain available until the session is closed.</span></span>

<span data-ttu-id="b6aea-178">[New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet esse cmdlet cria um novo arquivo de manifesto (. psd1) do módulo, preenche os valores e salva o arquivo de manifesto no caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="b6aea-178">[New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet This cmdlet creates a new module manifest (.psd1) file, populates its values, and saves the manifest file to the specified path.</span></span> <span data-ttu-id="b6aea-179">Esse cmdlet também pode ser usado para criar um modelo de manifesto de módulo que pode ser preenchido manualmente.</span><span class="sxs-lookup"><span data-stu-id="b6aea-179">This cmdlet can also be used to create a module manifest template that can be filled in manually.</span></span>

<span data-ttu-id="b6aea-180">[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet esse cmdlet adiciona um ou mais módulos à sessão atual.</span><span class="sxs-lookup"><span data-stu-id="b6aea-180">[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet This cmdlet adds one or more modules to the current session.</span></span>

<span data-ttu-id="b6aea-181">[Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet este cmdlet recupera informações sobre os módulos que foram ou que podem ser importados para a sessão atual.</span><span class="sxs-lookup"><span data-stu-id="b6aea-181">[Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet This cmdlet retrieves information about the modules that have been or that can be imported into the current session.</span></span>

<span data-ttu-id="b6aea-182">[Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) cmdlet esse cmdlet especifica os membros do módulo (como cmdlets, funções, variáveis e aliases) que são exportados a partir de um arquivo de módulo (. psm1) de script ou um módulo dinâmico criado usando o `New-Module` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b6aea-182">[Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) cmdlet This cmdlet specifies the module members (such as cmdlets, functions, variables, and aliases) that are exported from a script module (.psm1) file or from a dynamic module created by using the `New-Module` cmdlet.</span></span>

<span data-ttu-id="b6aea-183">[Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) cmdlet esse cmdlet remove módulos da sessão atual.</span><span class="sxs-lookup"><span data-stu-id="b6aea-183">[Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) cmdlet This cmdlet removes modules from the current session.</span></span>

<span data-ttu-id="b6aea-184">[Test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) cmdlet esse cmdlet verifica se um manifesto de módulo descreve com precisão os componentes de um módulo, verificando se os arquivos que estão listados no arquivo de manifesto de módulo (. psd1) realmente existem nos caminhos especificados.</span><span class="sxs-lookup"><span data-stu-id="b6aea-184">[Test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) cmdlet This cmdlet verifies that a module manifest accurately describes the components of a module by verifying that the files that are listed in the module manifest file (.psd1) actually exist in the specified paths.</span></span>

<span data-ttu-id="b6aea-185">$PSScriptRoot essa variável contém o diretório do qual o módulo de script está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="b6aea-185">$PSScriptRoot This variable contains the directory from which the script module is being executed.</span></span> <span data-ttu-id="b6aea-186">Ele permite que os scripts usar o caminho do módulo para acessar outros recursos.</span><span class="sxs-lookup"><span data-stu-id="b6aea-186">It enables scripts to use the module path to access other resources.</span></span>

<span data-ttu-id="b6aea-187">$env: PSModulePath essa variável de ambiente contém uma lista dos diretórios nos quais Windows PowerShell módulos são armazenados.</span><span class="sxs-lookup"><span data-stu-id="b6aea-187">$env:PSModulePath This environment variable contains a list of the directories in which Windows PowerShell modules are stored.</span></span> <span data-ttu-id="b6aea-188">Windows PowerShell usa o valor dessa variável ao importar módulos automaticamente e atualizando os tópicos de ajuda para módulos.</span><span class="sxs-lookup"><span data-stu-id="b6aea-188">Windows PowerShell uses the value of this variable when importing modules automatically and updating Help topics for modules.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6aea-189">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="b6aea-189">See Also</span></span>

[<span data-ttu-id="b6aea-190">Escrevendo um módulo do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b6aea-190">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)