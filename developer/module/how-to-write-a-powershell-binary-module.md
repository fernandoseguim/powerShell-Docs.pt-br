---
title: Como escrever um módulo do PowerShell binário | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: 9ddb3bc172c66314603d2be4df5192a76c92e05d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856482"
---
# <a name="how-to-write-a-powershell-binary-module"></a><span data-ttu-id="872f6-102">Como escrever um módulo binário do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="872f6-102">How to Write a PowerShell Binary Module</span></span>

<span data-ttu-id="872f6-103">Um módulo binário pode ser qualquer assembly (. dll) que contém as classes de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="872f6-103">A binary module can be any assembly (.dll) that contains cmdlet classes.</span></span> <span data-ttu-id="872f6-104">Por padrão, todos os cmdlets no assembly são importados quando o módulo binário é importado.</span><span class="sxs-lookup"><span data-stu-id="872f6-104">By default, all the cmdlets in the assembly are imported when the binary module is imported.</span></span> <span data-ttu-id="872f6-105">No entanto, você pode restringir os cmdlets que são importados com a criação de um manifesto de módulo cuja raiz é o assembly.</span><span class="sxs-lookup"><span data-stu-id="872f6-105">However, you can restrict the cmdlets that are imported by creating a module manifest whose root module is the assembly.</span></span> <span data-ttu-id="872f6-106">(Por exemplo, a chave de CmdletsToExport do manifesto pode ser usada para exportar apenas os cmdlets que são necessários.) Além disso, um módulo binário pode conter arquivos adicionais, uma estrutura de diretório e outras partes de informação de gerenciamento bastante úteis que um único cmdlet não pode.</span><span class="sxs-lookup"><span data-stu-id="872f6-106">(For example, the CmdletsToExport key of the manifest can be used to export only those cmdlets that are needed.) In addition, a binary module can contain additional files, a directory structure, and other pieces of useful management information that a single cmdlet cannot.</span></span>

<span data-ttu-id="872f6-107">O procedimento a seguir descreve como criar e instalar um módulo binário do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="872f6-107">The following procedure describes how to create and install a PowerShell binary module.</span></span>

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a><span data-ttu-id="872f6-108">Como criar e instalar um módulo binário do PowerShell</span><span class="sxs-lookup"><span data-stu-id="872f6-108">How to create and install a PowerShell binary module</span></span>

1. <span data-ttu-id="872f6-109">Criar uma solução binária do PowerShell (como um cmdlet escrito em C#), com os recursos de que necessita e certifique-se de que ele seja executado corretamente.</span><span class="sxs-lookup"><span data-stu-id="872f6-109">Create a binary PowerShell solution (such as a cmdlet written in C#), with the capabilities you need, and ensure that it runs properly.</span></span>

   <span data-ttu-id="872f6-110">De uma perspectiva de código, o núcleo de um módulo binário é simplesmente um conjunto de módulos do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="872f6-110">From a code perspective, the core of a binary module is simply a cmdlet assembly.</span></span> <span data-ttu-id="872f6-111">Na verdade, o PowerShell tratará um assembly único cmdlet como um módulo, em termos de carregamento e descarregamento, sem esforço adicional por parte do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="872f6-111">In fact, PowerShell will treat a single cmdlet assembly as a module, in terms of loading and unloading, with no additional effort on the part of the developer.</span></span> <span data-ttu-id="872f6-112">Para obter mais informações sobre como escrever um cmdlet, consulte [escrevendo um Cmdlet do Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="872f6-112">For more information about writing a cmdlet, see [Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span></span>

2. <span data-ttu-id="872f6-113">Se necessário, crie o restante de sua solução: (cmdlets adicionais, arquivos XML e assim por diante) e descrevê-los com um manifesto de módulo.</span><span class="sxs-lookup"><span data-stu-id="872f6-113">If necessary, create the rest of your solution: (additional cmdlets, XML files, and so on) and describe them with a module manifest.</span></span>

   <span data-ttu-id="872f6-114">Além de descrever os assemblies de cmdlet em sua solução, um manifesto de módulo pode descrever como você deseja que seu módulo exportados e importados, quais cmdlets serão expostas e o que irá arquivos adicionais no módulo.</span><span class="sxs-lookup"><span data-stu-id="872f6-114">In addition to describing the cmdlet assemblies in your solution, a module manifest can describe how you want your module exported and imported, what cmdlets will be exposed, and what additional files will go into the module.</span></span> <span data-ttu-id="872f6-115">Conforme mencionado anteriormente no entanto, o PowerShell pode tratar um cmdlet binário como um módulo sem esforço adicional.</span><span class="sxs-lookup"><span data-stu-id="872f6-115">As stated previously however, PowerShell can treat a binary cmdlet like a module with no additional effort.</span></span> <span data-ttu-id="872f6-116">Como tal, um manifesto de módulo é útil principalmente para combinar vários arquivos em um único pacote, ou para controlar explicitamente a publicação para um determinado assembly.</span><span class="sxs-lookup"><span data-stu-id="872f6-116">As such, a module manifest is useful mainly for combining multiple files into a single package, or for explicitly controlling publication for a given assembly.</span></span> <span data-ttu-id="872f6-117">Para obter mais informações, consulte [como escrever um manifesto de módulo do PowerShell](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).</span><span class="sxs-lookup"><span data-stu-id="872f6-117">For more information, see [How to Write a PowerShell Module Manifest](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).</span></span>

   <span data-ttu-id="872f6-118">O código a seguir é extremamente simples C# bloco de código que contém três cmdlets no mesmo arquivo que pode ser usado como um módulo.</span><span class="sxs-lookup"><span data-stu-id="872f6-118">The following code is an extremely simple C# code block that contains three cmdlets in the same file that can be used as a module.</span></span>

   ```csharp
   using System.Management.Automation;           // Windows PowerShell namespace.

   namespace ModuleCmdlets
   {
     [Cmdlet(VerbsDiagnostic.Test,"BinaryModuleCmdlet1")]
     public class TestBinaryModuleCmdlet1Command : Cmdlet
     {
       protected override void BeginProcessing()
       {
         WriteObject("BinaryModuleCmdlet1 exported by the ModuleCmdlets module.");
       }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet2")]
     public class TestBinaryModuleCmdlet2Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet2 exported by the ModuleCmdlets module.");
         }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet3")]
     public class TestBinaryModuleCmdlet3Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet3 exported by the ModuleCmdlets module.");
         }
     }

   }
   ```

3. <span data-ttu-id="872f6-119">Empacotar sua solução e salvar o pacote em algum lugar no caminho do módulo do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="872f6-119">Package your solution, and save the package to somewhere in the PowerShell module path.</span></span>

   <span data-ttu-id="872f6-120">O `PSModulePath` variável de ambiente global descreve os caminhos padrão que o PowerShell usará para localizar seu módulo.</span><span class="sxs-lookup"><span data-stu-id="872f6-120">The `PSModulePath` global environment variable describes the default paths that PowerShell will use to locate your module.</span></span> <span data-ttu-id="872f6-121">Por exemplo, um caminho comum para salvar um módulo em um sistema seria `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="872f6-121">For example, a common path to save a module on a system would be `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span></span> <span data-ttu-id="872f6-122">Se você não usar os caminhos padrão, você precisará declarar explicitamente o local do seu módulo durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="872f6-122">If you do not use the default paths, you will need to explicitly state the location of your module during installation.</span></span> <span data-ttu-id="872f6-123">Certifique-se de criar uma pasta para salvar o módulo, pois você talvez tenha a pasta para armazenar vários assemblies e arquivos para sua solução.</span><span class="sxs-lookup"><span data-stu-id="872f6-123">Be sure to create a folder to save your module in, as you may need the folder to store multiple assemblies and files for your solution.</span></span>

   <span data-ttu-id="872f6-124">Observe que tecnicamente você não precisa instalar o módulo em qualquer lugar no `PSModulePath` -esses são simplesmente os locais padrão que irá procurar o módulo PowerShell.</span><span class="sxs-lookup"><span data-stu-id="872f6-124">Note that technically you do not need to install your module anywhere on the `PSModulePath` - those are simply the default locations that PowerShell will look for your module.</span></span> <span data-ttu-id="872f6-125">No entanto, ele é considerado uma prática recomendada para fazer isso, a menos que você tenha uma boa razão para armazenar seu módulo em outro lugar.</span><span class="sxs-lookup"><span data-stu-id="872f6-125">However, it is considered best practice to do so, unless you have a good reason for storing your module somewhere else.</span></span> <span data-ttu-id="872f6-126">Para obter mais informações, consulte [instalando um módulo do PowerShell](./installing-a-powershell-module.md) e [modificando o caminho de instalação do módulo do PowerShell](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="872f6-126">For more information, see [Installing a PowerShell Module](./installing-a-powershell-module.md) and [Modifying the PowerShell Module Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

4. <span data-ttu-id="872f6-127">Importar o módulo do PowerShell com uma chamada para [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span><span class="sxs-lookup"><span data-stu-id="872f6-127">Import your module into PowerShell with a call to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span>

   <span data-ttu-id="872f6-128">Chamada para [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) carregará seu módulo na memória ativa.</span><span class="sxs-lookup"><span data-stu-id="872f6-128">Calling to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) will load your module into active memory.</span></span> <span data-ttu-id="872f6-129">Se você estiver usando o PowerShell 3.0 e posterior, basta chamar o nome do seu módulo de código também serão importados Para obter mais informações, consulte [importação de um módulo do PowerShell](./importing-a-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="872f6-129">If you are using PowerShell 3.0 and later, simply calling the name of your module in code will also import it; for more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="importing-snap-in-assemblies-as-modules"></a><span data-ttu-id="872f6-130">Importando Assemblies Snap-in como módulos</span><span class="sxs-lookup"><span data-stu-id="872f6-130">Importing Snap-in Assemblies as Modules</span></span>

<span data-ttu-id="872f6-131">Cmdlets e provedores que existem no snap-in de assemblies carregados como módulos binários.</span><span class="sxs-lookup"><span data-stu-id="872f6-131">Cmdlets and providers that exist in snap-in assemblies can be loaded as binary modules.</span></span> <span data-ttu-id="872f6-132">Quando os snap-in de assemblies são carregados como módulos binários, os cmdlets e provedores do snap-in estão disponíveis para o usuário, mas a classe de snap-in no assembly será ignorada e o snap-in não está registrado.</span><span class="sxs-lookup"><span data-stu-id="872f6-132">When the snap-in assemblies are loaded as binary modules, the cmdlets and providers in the snap-in are available to the user, but the snap-in class in the assembly is ignored, and the snap-in is not registered.</span></span> <span data-ttu-id="872f6-133">Como resultado, os cmdlets do snap-in fornecidos pelo Windows PowerShell não pode detectar o snap-in, mesmo que os cmdlets e provedores estão disponíveis para a sessão.</span><span class="sxs-lookup"><span data-stu-id="872f6-133">As a result, the snap-in cmdlets provided by Windows PowerShell cannot detect the snap-in even though the cmdlets and providers are available to the session.</span></span>

<span data-ttu-id="872f6-134">Além disso, qualquer formatação ou tipos de arquivos que são referenciados pelo snap-in não podem ser importados como parte de um módulo binário.</span><span class="sxs-lookup"><span data-stu-id="872f6-134">In addition, any formatting or types files that are referenced by the snap-in cannot be imported as part of a binary module.</span></span> <span data-ttu-id="872f6-135">Para importar os arquivos de formatação e tipos, você deve criar um manifesto de módulo.</span><span class="sxs-lookup"><span data-stu-id="872f6-135">To import the formatting and types files you must create a module manifest.</span></span> <span data-ttu-id="872f6-136">Consulte, [como escrever um manifesto de módulo do PowerShell](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).</span><span class="sxs-lookup"><span data-stu-id="872f6-136">See, [How to Write a PowerShell Module Manifest](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).</span></span>

## <a name="see-also"></a><span data-ttu-id="872f6-137">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="872f6-137">See Also</span></span>

[<span data-ttu-id="872f6-138">Escrevendo um módulo do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="872f6-138">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
