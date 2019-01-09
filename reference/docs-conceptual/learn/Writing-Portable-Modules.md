---
ms.date: 12/14/2018
keywords: powershell, cmdlet
title: Gravação de módulos portáteis
ms.openlocfilehash: 38a93b5b030d58784b91292e2cd060b3a2c19a00
ms.sourcegitcommit: d396d0e4cfe3d279f399c17e7337380a31d373ac
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2018
ms.locfileid: "53747714"
---
# <a name="portable-modules"></a><span data-ttu-id="e7ca5-103">Módulos portátil</span><span class="sxs-lookup"><span data-stu-id="e7ca5-103">Portable Modules</span></span>

<span data-ttu-id="e7ca5-104">Windows PowerShell foi criado para [.NET Framework][] enquanto o PowerShell Core é gravado para [.NET Core][].</span><span class="sxs-lookup"><span data-stu-id="e7ca5-104">Windows PowerShell is written for [.NET Framework][] while PowerShell Core is written for [.NET Core][].</span></span> <span data-ttu-id="e7ca5-105">Módulos portáteis são módulos que funcionam no Windows PowerShell e o PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-105">Portable modules are modules that work in both Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="e7ca5-106">Embora o .NET Framework e .NET Core são altamente compatíveis, há diferenças nas APIs disponíveis entre os dois.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-106">While .NET Framework and .NET Core are highly compatible, there are differences in the available APIs between the two.</span></span> <span data-ttu-id="e7ca5-107">Também há diferenças nas APIs disponíveis no Windows PowerShell e o PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-107">There are also differences in the APIs available in Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="e7ca5-108">Módulos que se destina a ser usado em ambos os ambientes precisam estar ciente dessas diferenças.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-108">Modules intended to be used in both environments need to be aware of these differences.</span></span>

## <a name="porting-an-existing-module"></a><span data-ttu-id="e7ca5-109">Portabilidade de um módulo existente</span><span class="sxs-lookup"><span data-stu-id="e7ca5-109">Porting an Existing Module</span></span>

### <a name="porting-a-pssnapin"></a><span data-ttu-id="e7ca5-110">Portando um PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="e7ca5-110">Porting a PSSnapIn</span></span>

<span data-ttu-id="e7ca5-111">PowerShell SnapIns (PSSnapIn) não têm suporte no PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-111">PowerShell SnapIns (PSSnapIn) aren't supported in PowerShell Core.</span></span> <span data-ttu-id="e7ca5-112">No entanto, é trivial para converter um PSSnapIn em um módulo do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-112">However, it's trivial to convert a PSSnapIn to a PowerShell module.</span></span> <span data-ttu-id="e7ca5-113">Normalmente, o código de registro PSSnapIn é em um único arquivo de origem de uma classe que deriva de [PSSnapIn][].</span><span class="sxs-lookup"><span data-stu-id="e7ca5-113">Typically, the PSSnapIn registration code is in a single source file of a class that derives from [PSSnapIn][].</span></span> <span data-ttu-id="e7ca5-114">Remover esse arquivo de origem da compilação; ele não é mais necessário.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-114">Remove this source file from the build; it's no longer needed.</span></span>

<span data-ttu-id="e7ca5-115">Use [New-ModuleManifest][] para criar um novo manifesto de módulo que substitui a necessidade do código de registro de PSSnapIn.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-115">Use [New-ModuleManifest][] to create a new module manifest that replaces the need for the PSSnapIn registration code.</span></span> <span data-ttu-id="e7ca5-116">Alguns dos valores da PSSnapIn (como descrição) podem ser reutilizados no manifesto do módulo.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-116">Some of the values from the PSSnapIn (such as Description) can be reused within the module manifest.</span></span>

<span data-ttu-id="e7ca5-117">O `RootModule` propriedade no manifesto do módulo deve ser definida como o nome do assembly (dll) que implementa os cmdlets.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-117">The `RootModule` property in the module manifest should be set to the name of the assembly (dll) implementing the cmdlets.</span></span>

### <a name="the-net-portability-analyzer-aka-apiport"></a><span data-ttu-id="e7ca5-118">O .NET Portability Analyzer (também conhecido como APIPort)</span><span class="sxs-lookup"><span data-stu-id="e7ca5-118">The .NET Portability Analyzer (aka APIPort)</span></span>

<span data-ttu-id="e7ca5-119">Para módulos de porta escritos para o Windows PowerShell trabalhar com o PowerShell Core, inicie com o [.NET Portability Analyzer][].</span><span class="sxs-lookup"><span data-stu-id="e7ca5-119">To port modules written for Windows PowerShell to work with PowerShell Core, start with the [.NET Portability Analyzer][].</span></span> <span data-ttu-id="e7ca5-120">Execute essa ferramenta em seu assembly compilado para determinar se as APIs do .NET usado no módulo são compatíveis com o .NET Framework, .NET Core e outros tempos de execução do .NET.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-120">Run this tool against your compiled assembly to determine if the .NET APIs used in the module are compatible with .NET Framework, .NET Core, and other .NET runtimes.</span></span> <span data-ttu-id="e7ca5-121">A ferramenta sugere APIs alternativas se eles existirem.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-121">The tool suggests alternate APIs if they exist.</span></span> <span data-ttu-id="e7ca5-122">Caso contrário, você talvez precise adicionar [verificações de tempo de execução][] e restringir os recursos não disponíveis em tempos de execução específicos.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-122">Otherwise, you may need to add [runtime checks][] and restrict capabilities not available in specific runtimes.</span></span>

## <a name="creating-a-new-module"></a><span data-ttu-id="e7ca5-123">Criar um novo módulo</span><span class="sxs-lookup"><span data-stu-id="e7ca5-123">Creating a New Module</span></span>

<span data-ttu-id="e7ca5-124">Se criar um novo módulo, a recomendação é usar o [CLI DO .NET][].</span><span class="sxs-lookup"><span data-stu-id="e7ca5-124">If creating a new module, the recommendation is to use the [.NET CLI][].</span></span>

### <a name="installing-the-powershell-standard-module-template"></a><span data-ttu-id="e7ca5-125">Instalando o modelo de módulo do PowerShell padrão</span><span class="sxs-lookup"><span data-stu-id="e7ca5-125">Installing the PowerShell Standard Module Template</span></span>

<span data-ttu-id="e7ca5-126">Depois que a CLI do .NET está instalada, instale uma biblioteca de modelos para gerar um módulo do PowerShell simple.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-126">Once the .NET CLI is installed, install a template library to generate a simple PowerShell module.</span></span>
<span data-ttu-id="e7ca5-127">O módulo será compatível com o Windows PowerShell, o PowerShell Core, Windows, Linux e macOS.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-127">The module will be compatible with Windows PowerShell, PowerShell Core, Windows, Linux, and macOS.</span></span>

<span data-ttu-id="e7ca5-128">O exemplo a seguir mostra como instalar o modelo:</span><span class="sxs-lookup"><span data-stu-id="e7ca5-128">The following example shows how to install the template:</span></span>

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
```

```output
  Restoring packages for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj...
  Installing Microsoft.PowerShell.Standard.Module.Template 0.1.3.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.targets.
  Restore completed in 1.66 sec for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj.

Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.
  -n, --name          The name for the output being created. If no name is specified, the name of the current directory is used.
  -o, --output        Location to place the generated output.
  -i, --install       Installs a source or a template pack.
  -u, --uninstall     Uninstalls a source or a template pack.
  --nuget-source      Specifies a NuGet source to use during install.
  --type              Filters templates based on available types. Predefined values are "project", "item" or "other".
  --force             Forces content to be generated even if it would change existing files.
  -lang, --language   Filters templates based on language and specifies the language of the template to create.


Templates                                         Short Name         Language          Tags
----------------------------------------------------------------------------------------------------------------------------
Console Application                               console            [C#], F#, VB      Common/Console
Class library                                     classlib           [C#], F#, VB      Common/Library
PowerShell Standard Module                        psmodule           [C#]              Library/PowerShell/Module
...
```

### <a name="creating-a-new-module-project"></a><span data-ttu-id="e7ca5-129">Criar um novo projeto de módulo</span><span class="sxs-lookup"><span data-stu-id="e7ca5-129">Creating a New Module Project</span></span>

<span data-ttu-id="e7ca5-130">Depois que o modelo for instalado, você pode criar um novo projeto de módulo do PowerShell com base nesse modelo.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-130">After the template is installed, you can create a new PowerShell module project using that template.</span></span> <span data-ttu-id="e7ca5-131">Neste exemplo, o módulo de exemplo é chamado 'myModule'.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-131">In this example, the sample module is called 'myModule'.</span></span>

```
PS> mkdir myModule

    Directory: C:\Users\Steve

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 8/3/2018 2:41 PM myModule

PS> cd myModule
PS C:\Users\Steve\myModule> dotnet new psmodule

The template "PowerShell Standard Module" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\Users\Steve\myModule\myModule.csproj...
  Restoring packages for C:\Users\Steve\myModule\myModule.csproj...
  Installing PowerShellStandard.Library 5.1.0.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.targets.
  Restore completed in 1.76 sec for C:\Users\Steve\myModule\myModule.csproj.

Restore succeeded.
```

### <a name="building-the-module"></a><span data-ttu-id="e7ca5-132">Criar o módulo</span><span class="sxs-lookup"><span data-stu-id="e7ca5-132">Building the Module</span></span>

<span data-ttu-id="e7ca5-133">Use comandos de CLI do .NET padrão para compilar o projeto.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-133">Use standard .NET CLI commands to build the project.</span></span>

```powershell
dotnet build
```

```output
PS C:\Users\Steve\myModule> dotnet build
Microsoft (R) Build Engine version 15.7.179.6572 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 76.85 ms for C:\Users\Steve\myModule\myModule.csproj.
  myModule -> C:\Users\Steve\myModule\bin\Debug\netstandard2.0\myModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:05.40
```

### <a name="testing-the-module"></a><span data-ttu-id="e7ca5-134">Teste do módulo</span><span class="sxs-lookup"><span data-stu-id="e7ca5-134">Testing the Module</span></span>

<span data-ttu-id="e7ca5-135">Depois de criar o módulo, você pode importá-lo e execute o cmdlet de exemplo.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-135">After building the module, you can import it and execute the sample cmdlet.</span></span>

```powershell
ipmo .\bin\Debug\netstandard2.0\myModule.dll
Test-SampleCmdlet -?
Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat
```

```output
PS C:\Users\Steve\myModule> ipmo .\bin\Debug\netstandard2.0\myModule.dll
PS C:\Users\Steve\myModule> Test-SampleCmdlet -?

NAME
    Test-SampleCmdlet

SYNTAX
    Test-SampleCmdlet [-FavoriteNumber] <int> [[-FavoritePet] {Cat | Dog | Horse}] [<CommonParameters>]


ALIASES
    None


REMARKS
    None


PS C:\Users\Steve\myModule> Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat

FavoriteNumber FavoritePet
-------------- -----------
             7 Cat
```

<span data-ttu-id="e7ca5-136">As seções a seguir descrevem em detalhes algumas das tecnologias usadas por este modelo.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-136">The following sections describe in detail some of the technologies used by this template.</span></span>

## <a name="net-standard-library"></a><span data-ttu-id="e7ca5-137">.NET standard Library</span><span class="sxs-lookup"><span data-stu-id="e7ca5-137">.NET Standard Library</span></span>

<span data-ttu-id="e7ca5-138">[.NET standard][] é uma especificação formal de APIs .NET que estão disponíveis em todas as implementações do .NET.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-138">[.NET Standard][] is a formal specification of .NET APIs that are available in all .NET implementations.</span></span> <span data-ttu-id="e7ca5-139">Direcionamento do .NET Standard funciona com as versões do .NET Framework e .NET Core são compatíveis com a versão do .NET Standard de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-139">Managed code targeting .NET Standard works with the .NET Framework and .NET Core versions that are compatible with that version of the .NET Standard.</span></span>

> [!NOTE]
> <span data-ttu-id="e7ca5-140">Embora uma API pode existir no .NET Standard, a implementação da API no .NET Core pode lançar um `PlatformNotSupportedException` em tempo de execução, portanto, para verificar a compatibilidade com o Windows PowerShell e o PowerShell Core, a prática recomendada é executar testes para o seu módulo dentro de ambos os ambientes.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-140">Although an API may exist in .NET Standard, the API implementation in .NET Core may throw a `PlatformNotSupportedException` at runtime, so to verify compatibility with Windows PowerShell and PowerShell Core, the best practice is to run tests for your module within both environments.</span></span>
> <span data-ttu-id="e7ca5-141">Também execute testes no Linux e macOS, se seu módulo deve ser de plataforma cruzada.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-141">Also run tests on Linux and macOS if your module is intended to be cross-platform.</span></span>

<span data-ttu-id="e7ca5-142">Direcionamento para .NET Standard ajuda a garantir que, à medida que o módulo evolui, APIs incompatíveis não acidentalmente obter introduzidas no módulo.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-142">Targeting .NET Standard helps ensure that, as the module evolves, incompatible APIs don't accidentally get introduced into the module.</span></span> <span data-ttu-id="e7ca5-143">Incompatibilidades são descobertas em tempo de compilação em vez de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-143">Incompatibilities are discovered at compile time instead of runtime.</span></span>

<span data-ttu-id="e7ca5-144">No entanto, ele não é necessário para direcionar .NET Standard para um módulo para trabalhar com o Windows PowerShell e o PowerShell Core, desde que você use APIs compatíveis.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-144">However, it isn't required to target .NET Standard for a module to work with both Windows PowerShell and PowerShell Core, as long as you use compatible APIs.</span></span> <span data-ttu-id="e7ca5-145">A linguagem intermediária (IL) é compatível entre os dois tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-145">The Intermediate Language (IL) is compatible between the two runtimes.</span></span> <span data-ttu-id="e7ca5-146">Você pode direcionar o .NET Framework 4.6.1, que é compatível com o .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-146">You can target .NET Framework 4.6.1, which is compatible with .NET Standard 2.0.</span></span> <span data-ttu-id="e7ca5-147">Se você não usar APIs fora do .NET Standard 2.0, em seguida, o módulo funciona com o PowerShell Core 6 sem recompilação.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-147">If you don't use APIs outside of .NET Standard 2.0, then your module works with PowerShell Core 6 without recompilation.</span></span>

## <a name="powershell-standard-library"></a><span data-ttu-id="e7ca5-148">Biblioteca padrão do PowerShell</span><span class="sxs-lookup"><span data-stu-id="e7ca5-148">PowerShell Standard Library</span></span>

<span data-ttu-id="e7ca5-149">O [Padrão do PowerShell][] library é uma especificação formal das APIs do PowerShell disponíveis em todas as versões do PowerShell maiores que ou iguais à versão esse padrão.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-149">The [PowerShell Standard][] library is a formal specification of PowerShell APIs available in all PowerShell versions greater than or equal to the version of that standard.</span></span>

<span data-ttu-id="e7ca5-150">Por exemplo, [Padrão de PowerShell 5.1][] é compatível com o Windows PowerShell 5.1 e o PowerShell Core 6.0 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-150">For example, [PowerShell Standard 5.1][] is compatible with both Windows PowerShell 5.1 and PowerShell Core 6.0 or newer.</span></span>

<span data-ttu-id="e7ca5-151">É recomendável que você compilar o módulo usando a biblioteca padrão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-151">We recommend you compile your module using PowerShell Standard Library.</span></span> <span data-ttu-id="e7ca5-152">A biblioteca garante que as APIs estão disponíveis e implementados no Windows PowerShell e o PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-152">The library ensures the APIs are available and implemented in both Windows PowerShell and PowerShell Core 6.</span></span>
<span data-ttu-id="e7ca5-153">PowerShell padrão destina-se a ser sempre encaminhamentos compatível.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-153">PowerShell Standard is intended to always be forwards-compatible.</span></span> <span data-ttu-id="e7ca5-154">Um módulo compilado usando o PowerShell 5.1 de biblioteca padrão sempre será compatível com versões futuras do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-154">A module built using PowerShell Standard Library 5.1 will always be compatible with future versions of PowerShell.</span></span>

## <a name="module-manifest"></a><span data-ttu-id="e7ca5-155">Manifesto de módulo</span><span class="sxs-lookup"><span data-stu-id="e7ca5-155">Module Manifest</span></span>

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a><span data-ttu-id="e7ca5-156">Que indica a compatibilidade com o Windows PowerShell e o PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="e7ca5-156">Indicating Compatibility With Windows PowerShell and PowerShell Core</span></span>

<span data-ttu-id="e7ca5-157">Após validar que o módulo funciona com o Windows PowerShell e o PowerShell Core, o manifesto de módulo deve indicar explicitamente compatibilidade usando o [CompatiblePSEditions][] propriedade.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-157">After validating that your module works with both Windows PowerShell and PowerShell Core, the module manifest should explicitly indicate compatibility by using the [CompatiblePSEditions][] property.</span></span> <span data-ttu-id="e7ca5-158">Um valor de `Desktop` significa que o módulo é compatível com o Windows PowerShell, enquanto um valor de `Core` significa que o módulo é compatível com o PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-158">A value of `Desktop` means that the module is compatible with Windows PowerShell, while a value of `Core` means that the module is compatible with PowerShell Core.</span></span> <span data-ttu-id="e7ca5-159">Incluindo ambos `Desktop` e `Core` significa que o módulo é compatível com o Windows PowerShell e o PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-159">Including both `Desktop` and `Core` means that the module is compatible with both Windows PowerShell and PowerShell Core.</span></span>

> [!NOTE]
> <span data-ttu-id="e7ca5-160">`Core` não automaticamente significa que o módulo é compatível com Windows, Linux e macOS.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-160">`Core` does not automatically mean that the module is compatible with Windows, Linux, and macOS.</span></span>
> <span data-ttu-id="e7ca5-161">O **CompatiblePSEditions** propriedade foi introduzida no PowerShell v5.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-161">The **CompatiblePSEditions** property was introduced in PowerShell v5.</span></span> <span data-ttu-id="e7ca5-162">Manifestos de módulo que usam o **CompatiblePSEditions** propriedade falhar ao serem carregados em versões anteriores do PowerShell v5.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-162">Module manifests that use the **CompatiblePSEditions** property fail to load in versions prior to PowerShell v5.</span></span>

### <a name="indicating-os-compatibility"></a><span data-ttu-id="e7ca5-163">Que indica a compatibilidade de SO</span><span class="sxs-lookup"><span data-stu-id="e7ca5-163">Indicating OS Compatibility</span></span>

<span data-ttu-id="e7ca5-164">Primeiro, valide que o módulo funciona no Linux e macOS.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-164">First, validate that your module works on Linux and macOS.</span></span> <span data-ttu-id="e7ca5-165">Em seguida, indique a compatibilidade com esses sistemas operacionais no manifesto de módulo.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-165">Next, indicate compatibility with those operating systems in the module manifest.</span></span> <span data-ttu-id="e7ca5-166">Isso torna mais fácil para os usuários encontrem seu módulo para seu sistema operacional quando publicado para o [Galeria do PowerShell][].</span><span class="sxs-lookup"><span data-stu-id="e7ca5-166">This makes it easier for users to find your module for their operating system when published to the [PowerShell Gallery][].</span></span>

<span data-ttu-id="e7ca5-167">No manifesto do módulo, o `PrivateData` propriedade tem um `PSData` subpropriedade.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-167">Within the module manifest, the `PrivateData` property has a `PSData` sub-property.</span></span> <span data-ttu-id="e7ca5-168">Opcional `Tags` propriedade de `PSData` pega uma matriz de valores que aparecem na Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-168">The optional `Tags` property of `PSData` takes an array of values that show up in PowerShell Gallery.</span></span> <span data-ttu-id="e7ca5-169">A Galeria do PowerShell suporta os seguintes valores de compatibilidade:</span><span class="sxs-lookup"><span data-stu-id="e7ca5-169">The PowerShell Gallery supports the following compatibility values:</span></span>

| <span data-ttu-id="e7ca5-170">Tag</span><span class="sxs-lookup"><span data-stu-id="e7ca5-170">Tag</span></span>               | <span data-ttu-id="e7ca5-171">Descrição</span><span class="sxs-lookup"><span data-stu-id="e7ca5-171">Description</span></span>                                |
|-------------------|--------------------------------------------|
| <span data-ttu-id="e7ca5-172">PSEdition_Core</span><span class="sxs-lookup"><span data-stu-id="e7ca5-172">PSEdition_Core</span></span>    | <span data-ttu-id="e7ca5-173">Compatível com o PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="e7ca5-173">Compatible with PowerShell Core 6</span></span>          |
| <span data-ttu-id="e7ca5-174">PSEdition_Desktop</span><span class="sxs-lookup"><span data-stu-id="e7ca5-174">PSEdition_Desktop</span></span> | <span data-ttu-id="e7ca5-175">Compatível com o Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e7ca5-175">Compatible with Windows PowerShell</span></span>         |
| <span data-ttu-id="e7ca5-176">Windows</span><span class="sxs-lookup"><span data-stu-id="e7ca5-176">Windows</span></span>           | <span data-ttu-id="e7ca5-177">Compatível com Windows</span><span class="sxs-lookup"><span data-stu-id="e7ca5-177">Compatible with Windows</span></span>                    |
| <span data-ttu-id="e7ca5-178">Linux</span><span class="sxs-lookup"><span data-stu-id="e7ca5-178">Linux</span></span>             | <span data-ttu-id="e7ca5-179">Compatível com Linux (nenhuma distribuição específica)</span><span class="sxs-lookup"><span data-stu-id="e7ca5-179">Compatible with Linux (no specific distro)</span></span> |
| <span data-ttu-id="e7ca5-180">macOS</span><span class="sxs-lookup"><span data-stu-id="e7ca5-180">macOS</span></span>             | <span data-ttu-id="e7ca5-181">Compatível com macOS</span><span class="sxs-lookup"><span data-stu-id="e7ca5-181">Compatible with macOS</span></span>                      |

<span data-ttu-id="e7ca5-182">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="e7ca5-182">Example:</span></span>

```powershell
@{
    GUID = "4ae9fd46-338a-459c-8186-07f910774cb8"
    Author = "Microsoft Corporation"
    CompanyName = "Microsoft Corporation"
    Copyright = "(C) Microsoft Corporation. All rights reserved."
    HelpInfoUri = "https://go.microsoft.com/fwlink/?linkid=855962"
    ModuleVersion = "1.2.4"
    PowerShellVersion = "3.0"
    ClrVersion = "4.0"
    RootModule = "PackageManagement.psm1"
    Description = 'PackageManagement (a.k.a. OneGet) is a new way to discover and install software packages from around the web.
 It is a manager or multiplexer of existing package managers (also called package providers) that unifies Windows package management with a single Windows PowerShell interface. With PackageManagement, you can do the following.
  - Manage a list of software repositories in which packages can be searched, acquired and installed
  - Discover software packages
  - Seamlessly install, uninstall, and inventory packages from one or more software repositories'

    CmdletsToExport = @(
        'Find-Package',
        'Get-Package',
        'Get-PackageProvider',
        'Get-PackageSource',
        'Install-Package',
        'Import-PackageProvider'
        'Find-PackageProvider'
        'Install-PackageProvider'
        'Register-PackageSource',
        'Set-PackageSource',
        'Unregister-PackageSource',
        'Uninstall-Package'
        'Save-Package'
    )

    FormatsToProcess  = @('PackageManagement.format.ps1xml')

    PrivateData = @{
        PSData = @{
            Tags = @('PackageManagement', 'PSEdition_Core', 'PSEdition_Desktop', 'Windows', 'Linux', 'macOS')
            ProjectUri = 'https://oneget.org'
        }
    }
}
```

<!-- reference links -->
[.NET Framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[verificações de tempo de execução]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[runtime checks]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[CLI DO .NET]: /dotnet/core/tools/?tabs=netcore2x
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[Padrão do PowerShell]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[Padrão de PowerShell 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[Galeria do PowerShell]: https://www.powershellgallery.com
[PowerShell Gallery]: https://www.powershellgallery.com
[.NET portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[.NET Portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
