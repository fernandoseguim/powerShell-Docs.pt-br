---
ms.date: 12/14/2018
keywords: powershell, cmdlet
title: Gravação de módulos portáteis
ms.openlocfilehash: 38a93b5b030d58784b91292e2cd060b3a2c19a00
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676401"
---
# <a name="portable-modules"></a>Módulos portátil

Windows PowerShell foi criado para [.NET Framework][] enquanto o PowerShell Core é gravado para [.NET Core][]. Módulos portáteis são módulos que funcionam no Windows PowerShell e o PowerShell Core. Embora o .NET Framework e .NET Core são altamente compatíveis, há diferenças nas APIs disponíveis entre os dois. Também há diferenças nas APIs disponíveis no Windows PowerShell e o PowerShell Core. Módulos que se destina a ser usado em ambos os ambientes precisam estar ciente dessas diferenças.

## <a name="porting-an-existing-module"></a>Portabilidade de um módulo existente

### <a name="porting-a-pssnapin"></a>Portando um PSSnapIn

PowerShell SnapIns (PSSnapIn) não têm suporte no PowerShell Core. No entanto, é trivial para converter um PSSnapIn em um módulo do PowerShell. Normalmente, o código de registro PSSnapIn é em um único arquivo de origem de uma classe que deriva de [PSSnapIn][]. Remover esse arquivo de origem da compilação; ele não é mais necessário.

Use [New-ModuleManifest][] para criar um novo manifesto de módulo que substitui a necessidade do código de registro de PSSnapIn. Alguns dos valores da PSSnapIn (como descrição) podem ser reutilizados no manifesto do módulo.

O `RootModule` propriedade no manifesto do módulo deve ser definida como o nome do assembly (dll) que implementa os cmdlets.

### <a name="the-net-portability-analyzer-aka-apiport"></a>O .NET Portability Analyzer (também conhecido como APIPort)

Para módulos de porta escritos para o Windows PowerShell trabalhar com o PowerShell Core, inicie com o [.NET Portability Analyzer][]. Execute essa ferramenta em seu assembly compilado para determinar se as APIs do .NET usado no módulo são compatíveis com o .NET Framework, .NET Core e outros tempos de execução do .NET. A ferramenta sugere APIs alternativas se eles existirem. Caso contrário, você talvez precise adicionar [verificações de tempo de execução][] e restringir os recursos não disponíveis em tempos de execução específicos.

## <a name="creating-a-new-module"></a>Criar um novo módulo

Se criar um novo módulo, a recomendação é usar o [.NET CLI][].

### <a name="installing-the-powershell-standard-module-template"></a>Instalando o modelo de módulo do PowerShell padrão

Depois que a CLI do .NET está instalada, instale uma biblioteca de modelos para gerar um módulo do PowerShell simple.
O módulo será compatível com o Windows PowerShell, o PowerShell Core, Windows, Linux e macOS.

O exemplo a seguir mostra como instalar o modelo:

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

### <a name="creating-a-new-module-project"></a>Criar um novo projeto de módulo

Depois que o modelo for instalado, você pode criar um novo projeto de módulo do PowerShell com base nesse modelo. Neste exemplo, o módulo de exemplo é chamado 'myModule'.

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

### <a name="building-the-module"></a>Criar o módulo

Use comandos de CLI do .NET padrão para compilar o projeto.

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

### <a name="testing-the-module"></a>Teste do módulo

Depois de criar o módulo, você pode importá-lo e execute o cmdlet de exemplo.

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

As seções a seguir descrevem em detalhes algumas das tecnologias usadas por este modelo.

## <a name="net-standard-library"></a>.NET standard Library

[.NET standard][] é uma especificação formal de APIs .NET que estão disponíveis em todas as implementações do .NET. Direcionamento do .NET Standard funciona com as versões do .NET Framework e .NET Core são compatíveis com a versão do .NET Standard de código gerenciado.

> [!NOTE]
> Embora uma API pode existir no .NET Standard, a implementação da API no .NET Core pode lançar um `PlatformNotSupportedException` em tempo de execução, portanto, para verificar a compatibilidade com o Windows PowerShell e o PowerShell Core, a prática recomendada é executar testes para o seu módulo dentro de ambos os ambientes.
> Também execute testes no Linux e macOS, se seu módulo deve ser de plataforma cruzada.

Direcionamento para .NET Standard ajuda a garantir que, à medida que o módulo evolui, APIs incompatíveis não acidentalmente obter introduzidas no módulo. Incompatibilidades são descobertas em tempo de compilação em vez de tempo de execução.

No entanto, ele não é necessário para direcionar .NET Standard para um módulo para trabalhar com o Windows PowerShell e o PowerShell Core, desde que você use APIs compatíveis. A linguagem intermediária (IL) é compatível entre os dois tempos de execução. Você pode direcionar o .NET Framework 4.6.1, que é compatível com o .NET Standard 2.0. Se você não usar APIs fora do .NET Standard 2.0, em seguida, o módulo funciona com o PowerShell Core 6 sem recompilação.

## <a name="powershell-standard-library"></a>Biblioteca padrão do PowerShell

O [Padrão do PowerShell][] library é uma especificação formal das APIs do PowerShell disponíveis em todas as versões do PowerShell maiores que ou iguais à versão esse padrão.

Por exemplo, [PowerShell Standard 5.1][] é compatível com o Windows PowerShell 5.1 e o PowerShell Core 6.0 ou mais recente.

É recomendável que você compilar o módulo usando a biblioteca padrão do PowerShell. A biblioteca garante que as APIs estão disponíveis e implementados no Windows PowerShell e o PowerShell Core 6.
PowerShell padrão destina-se a ser sempre encaminhamentos compatível. Um módulo compilado usando o PowerShell 5.1 de biblioteca padrão sempre será compatível com versões futuras do PowerShell.

## <a name="module-manifest"></a>Manifesto de módulo

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a>Que indica a compatibilidade com o Windows PowerShell e o PowerShell Core

Após validar que o módulo funciona com o Windows PowerShell e o PowerShell Core, o manifesto de módulo deve indicar explicitamente compatibilidade usando o [CompatiblePSEditions][] propriedade. Um valor de `Desktop` significa que o módulo é compatível com o Windows PowerShell, enquanto um valor de `Core` significa que o módulo é compatível com o PowerShell Core. Incluindo ambos `Desktop` e `Core` significa que o módulo é compatível com o Windows PowerShell e o PowerShell Core.

> [!NOTE]
> `Core` não automaticamente significa que o módulo é compatível com Windows, Linux e macOS.
> O **CompatiblePSEditions** propriedade foi introduzida no PowerShell v5. Manifestos de módulo que usam o **CompatiblePSEditions** propriedade falhar ao serem carregados em versões anteriores do PowerShell v5.

### <a name="indicating-os-compatibility"></a>Que indica a compatibilidade de SO

Primeiro, valide que o módulo funciona no Linux e macOS. Em seguida, indique a compatibilidade com esses sistemas operacionais no manifesto de módulo. Isso torna mais fácil para os usuários encontrem seu módulo para seu sistema operacional quando publicado para o [Galeria do PowerShell][].

No manifesto do módulo, o `PrivateData` propriedade tem um `PSData` subpropriedade. Opcional `Tags` propriedade de `PSData` pega uma matriz de valores que aparecem na Galeria do PowerShell. A Galeria do PowerShell suporta os seguintes valores de compatibilidade:

| Tag               | Descrição                                |
|-------------------|--------------------------------------------|
| PSEdition_Core    | Compatível com o PowerShell Core 6          |
| PSEdition_Desktop | Compatível com o Windows PowerShell         |
| Windows           | Compatível com Windows                    |
| Linux             | Compatível com Linux (nenhuma distribuição específica) |
| macOS             | Compatível com macOS                      |

Exemplo:

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
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[Padrão do PowerShell]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[Galeria do PowerShell]: https://www.powershellgallery.com
[.NET portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
