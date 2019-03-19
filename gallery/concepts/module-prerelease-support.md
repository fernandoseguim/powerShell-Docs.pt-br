---
ms.date: 09/26/2017
contributor: keithb
keywords: galeria,powershell,cmdlet,psget
title: Versões de pré-lançamento do módulo
ms.openlocfilehash: eced067dd21082de0db653daf3b838217154f1dd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58056236"
---
# <a name="prerelease-module-versions"></a>Versões de pré-lançamento do módulo

Começando com a versão 1.6.0, o PowerShellGet e a Galeria do PowerShell são compatíveis com versões de marcação superiores a 1.0.0 como um pré-lançamento. Antes desse recurso, os pacotes de pré-lançamento eram limitados a ter uma versão que começasse com 0. A meta desses recursos é oferecer maior compatibilidade com a convenção de versão [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html), sem perder a compatibilidade com o PowerShell versão 3 e superiores ou com as versões existentes do PowerShellGet. Este tópico se concentra nos recursos específicos do módulo. Os recursos equivalentes para scripts estão no tópico [Versões de pré-lançamento dos scripts](script-prerelease-support.md). Ao usar esses recursos, os editores podem identificar um módulo ou um script como a versão 2.5.0-alpha e, então, lançar uma versão 2.5.0 pronta para produção, que substitui a versão de pré-lançamento.

Em um nível alto, os recursos de pré-lançamento do módulo incluem:

- A adição de uma cadeia de caracteres de pré-lançamento na seção PSData do manifesto do módulo identifica o módulo como uma versão de pré-lançamento. Quando o módulo é publicado na Galeria do PowerShell, esses dados são extraídos do manifesto e usados para identificar os pacotes de pré-lançamento.
- A aquisição de pacotes de pré-lançamento exige a adição do sinalizador `-AllowPrerelease` aos comandos do PowerShellGet `Find-Module`, `Install-Module`, `Update-Module` e `Save-Module`. Se o sinalizador não for especificado, os pacotes de pré-lançamento não serão exibidos.
- As versões de módulo exibidas pelos comandos `Find-Module`, `Get-InstalledModule` e na Galeria do PowerShell serão exibidas como uma única cadeia de caracteres com a cadeia de caracteres de pré-lançamento anexada, como em 2.5.0-alpha.

Os detalhes para os recursos estão incluídos abaixo.

Essas alterações não afetam o suporte de versão do módulo que é criado no PowerShell, e são compatíveis com o PowerShell 3.0, 4.0 e 5.

## <a name="identifying-a-module-version-as-a-prerelease"></a>Identificação de uma versão de módulo como uma versão de pré-lançamento

O suporte para as versões de pré-lançamento do PowerShellGet exige o uso de dois campos no manifesto de módulo:

- O ModuleVersion incluído no manifesto de módulo deverá ser uma versão de três partes se uma versão de pré-lançamento for usada, e deverá estar em conformidade com o controle de versão existente do PowerShell. O formato da versão seria A.B.C, em que A, B e C são todos os números inteiros.
- A cadeia de caracteres de pré-lançamento é especificada no manifesto de módulo, na seção PSData de PrivateData.

A seguir estão os requisitos detalhados na cadeia de pré-lançamento.

Uma seção de exemplo de um manifesto de módulo que define um módulo como uma versão de pré-lançamento seria semelhante ao seguinte:

```powershell
@{
    ModuleVersion = '2.5.0'
    #---
    PrivateData = @{
        PSData = @{
            Prerelease = 'alpha'
        }
    }
}
```

Os requisitos detalhados para a cadeia de caracteres de pré-lançamento são:

- A cadeia de caracteres de pré-lançamento só poderá ser especificada quando o ModuleVersion tiver três segmentos para Major.Minor.Build. Ela é alinhada ao SemVer v1.0.0.
- Um hífen é o delimitador entre o número de build e a cadeia de caracteres de pré-lançamento. Um hífen pode ser incluído na cadeia de pré-lançamento apenas como o primeiro caractere.
- A cadeia de caracteres de pré-lançamento pode conter somente ASCII alfanuméricos [0-9A-Za-z-]. Uma prática recomendada é iniciar a cadeia de caracteres de pré-lançamento com um caractere alfabético, pois será mais fácil de identificar que se trata de uma versão de pré-lançamento ao examinar uma lista de pacotes.
- Somente as cadeias de caracteres SemVer v1.0.0 são compatíveis no momento. A cadeia de caracteres de pré-lançamento **não deve** conter um ponto ou + [.+], que é permitido no SemVer 2.0.
- Alguns exemplos de cadeias de caracteres de pré-lançamento compatíveis são: -alpha, -alpha1, -BETA, -update20171020

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a>Impacto na versão de pré-lançamento sobre a ordem de classificação e nas pastas de instalação

A ordem de classificação é alterada ao usar uma versão de pré-lançamento, que é importante ao publicar na Galeria do PowerShell e ao instalar módulos usando comandos do PowerShellGet. Se a cadeia de caracteres de pré-lançamento for especificada para dois módulos, a ordem de classificação será baseada na parte da cadeia de caracteres após o hífen. Portanto, a versão 2.5.0-alpha é menor que a versão 2.5.0-beta, que é menor que a versão 2.5.0-gamma. Se dois módulos tiverem o mesmo ModuleVersion e somente um tiver uma cadeia de caracteres de pré-lançamento, o módulo sem a cadeia de caracteres de pré-lançamento será considerado como a versão pronta para produção e será classificado como uma versão maior do que a versão de pré-lançamento (que inclui a cadeia de caracteres de pré-lançamento). Por exemplo, ao comparar as versões 2.5.0 e 2.5.0-beta, a versão 2.5.0 será considerada a maior das duas.

Ao publicar na Galeria do PowerShell, por padrão a versão do módulo que está sendo publicado deverá ter uma versão maior do que qualquer versão previamente publicada na Galeria do PowerShell.

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a>Localização e aquisição de pacotes de pré-lançamento usando os comandos do PowerShellGet

Para lidar com os pacotes de pré-lançamento, usando os comandos PowerShellGet Find-Module, Install-Module, Update-Module e Save-Module, é necessário adicionar o sinalizador -AllowPrerelease. Se -AllowPrerelease for especificado, os pacotes de pré-lançamento serão incluídos se estiverem presentes. Se o sinalizador -AllowPrerelease não for especificado, os pacotes de pré-lançamento não serão exibidos.

As únicas exceções a isso nos comandos do módulo PowerShellGet são Get-InstalledModule e alguns casos com Uninstall-Module.

- Get-InstalledModule sempre mostrará as informações de pré-lançamento automaticamente na cadeia de caracteres de versão para os módulos.
- Por padrão, o Uninstall-Module desinstalará a versão mais recente de um módulo se __nenhuma versão__ for especificada. Esse comportamento não mudou. No entanto, se uma versão de pré-lançamento for especificada usando -RequiredVersion, -AllowPrerelease será necessário.

## <a name="examples"></a>Exemplos

Vamos supor que a Galeria do PowerShell tenha as versões do módulo TestPackage 1.8.0 e 1.9.0-alpha. Se `-AllowPrerelease` não for especificado, somente a versão 1.8.0 retornará.

```powershell
find-module TestPackage
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.8.0          TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

```powershell
find-module TestPackage -AllowPrerelease
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.9.0-alpha    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

Para instalar uma versão de pré-lançamento, sempre especifique -AllowPrerelease. Não basta especificar uma cadeia de caracteres de versão de pré-lançamento.

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha
```

```output
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exception
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage
```

O comando anterior falhou porque -AllowPrerelease não foi especificado. A adição de `-AllowPrerelease` resultará em sucesso.

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

Não há compatibilidade para a instalação lado a lado das versões de um módulo que diferem apenas devido à versão de pré-lançamento especificada. Ao instalar um módulo usando o PowerShellGet, versões diferentes do mesmo módulo serão instaladas lado a lado com a criação de um nome de pasta usando o ModuleVersion. O ModuleVersion, sem a cadeia de caracteres de pré-lançamento, é usado para o nome da pasta. Se um usuário instalar MyModule versão 2.5.0-alpha, ele será instalado na pasta `MyModule\2.5.0`. Se o usuário instalar a versão 2.5.0-beta, ela **substituirá** o conteúdo da pasta `MyModule\2.5.0`. Uma vantagem dessa abordagem é que não é necessário desinstalar a versão de pré-lançamento depois de instalar a versão pronta para produção. O exemplo a seguir mostra o que esperar:

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-alpha     TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name            Repository  Description
-------        ----            ----------  -----------
1.9.0-beta     TestPackage     PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

```

O Uninstall-Module removerá a versão mais recente de um módulo quando -RequiredVersion não for fornecido.
Se -RequiredVersion for especificado e for uma versão de pré-lançamento, -AllowPrerelease deverá ser adicionado ao comando.

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
2.0.0-alpha1    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta

Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninstall-Module

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
2.0.0-alpha1    TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...
```

## <a name="more-details"></a>Mais detalhes

- [Versões de pré-lançamento do Script](script-prerelease-support.md)
- [Find-Module](/powershell/module/powershellget/find-module)
- [Install-Module](/powershell/module/powershellget/install-module)
- [Save-Module](/powershell/module/powershellget/save-module)
- [Update-Module](/powershell/module/powershellget/Update-Module)
- [Get-InstalledModule](/powershell/module/powershellget/get-installedmodule)
- [UnInstall-Module](/powershell/module/powershellget/uninstall-module)
