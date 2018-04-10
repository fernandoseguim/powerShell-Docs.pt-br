---
ms.date: 09/26/2017
contributor: keithb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: PrereleaseModule
ms.openlocfilehash: 1fc08cbba90e3eb8ca7d280e4d279af1d8aa279f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="prerelease-module-versions"></a>Versões de pré-lançamento do módulo
Começando com a versão 1.6.0, o PowerShellGet e a Galeria do PowerShell são compatíveis com versões de marcação superiores a 1.0.0 como um pré-lançamento. Antes desse recurso, os itens de pré-lançamento eram limitados a ter uma versão que começasse com 0. A meta desses recursos é oferecer maior compatibilidade com a convenção de versão [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html), sem perder a compatibilidade com o PowerShell versão 3 e superiores ou com as versões existentes do PowerShellGet. Este tópico se concentra nos recursos específicos do módulo. Os recursos equivalentes para scripts estão no tópico [Versões de pré-lançamento dos scripts](../script/PrereleaseScript.md). Ao usar esses recursos, os editores podem identificar um módulo ou um script como a versão 2.5.0-alpha e, então, lançar uma versão 2.5.0 pronta para produção, que substitui a versão de pré-lançamento.

Em um nível alto, os recursos de pré-lançamento do módulo incluem:

* A adição de uma cadeia de caracteres de pré-lançamento na seção PSData do manifesto do módulo identifica o módulo como uma versão de pré-lançamento.
Quando o módulo é publicado na Galeria do PowerShell, esses dados são extraídos do manifesto e usados para identificar os itens de pré-lançamento.
* A aquisição dos itens de pré-lançamento requer a adição do sinalizador -AllowPrerelease aos comandos Find-Module, Install-Module, Update-Module e Save-Module do PowerShellGet.
Se o sinalizador não for especificado, os itens de pré-lançamento não serão exibidos.
* As versões de módulo exibidas pelos comandos Find-Module, Get-InstalledModule e na Galeria do PowerShell serão exibidas como uma única cadeia de caracteres com a cadeia de caracteres de pré-lançamento anexada, como em 2.5.0-alpha.

Os detalhes para os recursos estão incluídos abaixo.

Essas alterações não afetam o suporte de versão do módulo que é criado no PowerShell, e são compatíveis com o PowerShell 3.0, 4.0 e 5.

## <a name="identifying-a-module-version-as-a-prerelease"></a>Identificação de uma versão de módulo como uma versão de pré-lançamento

O suporte para as versões de pré-lançamento do PowerShellGet exige o uso de dois campos no manifesto de módulo:

* O ModuleVersion incluído no manifesto de módulo deverá ser uma versão de três partes se uma versão de pré-lançamento for usada, e deverá estar em conformidade com o controle de versão existente do PowerShell. O formato da versão seria A.B.C, em que A, B e C são todos os números inteiros.
* A cadeia de caracteres de pré-lançamento é especificada no manifesto de módulo, na seção PSData de PrivateData.
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

* A cadeia de caracteres de pré-lançamento só poderá ser especificada quando o ModuleVersion tiver três segmentos para Major.Minor.Build. Ela é alinhada ao SemVer v1.0.0.
* Um hífen é o delimitador entre o número de build e a cadeia de caracteres de pré-lançamento. Um hífen pode ser incluído na cadeia de pré-lançamento apenas como o primeiro caractere.
* A cadeia de caracteres de pré-lançamento pode conter somente ASCII alfanuméricos [0-9A-Za-z-]. Uma prática recomendada é iniciar a cadeia de caracteres de pré-lançamento com um caractere alfabético, pois será mais fácil de identificar que se trata de uma versão de pré-lançamento ao examinar uma lista de itens.
* Somente as cadeias de caracteres SemVer v1.0.0 são compatíveis no momento. A cadeia de caracteres de pré-lançamento __não deve__ conter um ponto ou + [.+], que é permitido no SemVer 2.0.
* Alguns exemplos de cadeias de caracteres de pré-lançamento compatíveis são: -alpha, -alpha1, -BETA, -update20171020

__Impacto na versão de pré-lançamento sobre a ordem de classificação e nas pastas de instalação__

A ordem de classificação é alterada ao usar uma versão de pré-lançamento, que é importante ao publicar na Galeria do PowerShell e ao instalar módulos usando comandos do PowerShellGet.
Se a cadeia de caracteres de pré-lançamento for especificada para dois módulos, a ordem de classificação será baseada na parte da cadeia de caracteres após o hífen. Portanto, a versão 2.5.0-alpha é menor que a versão 2.5.0-beta, que é menor que a versão 2.5.0-gamma.
Se dois módulos tiverem o mesmo ModuleVersion e somente um tiver uma cadeia de caracteres de pré-lançamento, o módulo sem a cadeia de caracteres de pré-lançamento será considerado como a versão pronta para produção e será classificado como uma versão maior do que a versão de pré-lançamento (que inclui a cadeia de caracteres de pré-lançamento).
Por exemplo, ao comparar as versões 2.5.0 e 2.5.0-beta, a versão 2.5.0 será considerada a maior das duas.

Ao publicar na Galeria do PowerShell, por padrão a versão do módulo que está sendo publicado deverá ter uma versão maior do que qualquer versão previamente publicada na Galeria do PowerShell.

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a>Localização e aquisição de itens de pré-lançamento usando os comandos do PowerShellGet

Para lidar com os itens de pré-lançamento usando os comandos PowerShellGet Find-Module, Install-Module, Update-Module e Save-Module, é necessário adicionar o sinalizador -AllowPrerelease.
Se -AllowPrerelease for especificado, os itens de pré-lançamento serão incluídos se estiverem presentes.
Se o sinalizador -AllowPrerelease não for especificado, os itens de pré-lançamento não serão exibidos.

As únicas exceções a isso nos comandos do módulo PowerShellGet são Get-InstalledModule e alguns casos com Uninstall-Module.

* Get-InstalledModule sempre mostrará as informações de pré-lançamento automaticamente na cadeia de caracteres de versão para os módulos.
* Por padrão, o Uninstall-Module desinstalará a versão mais recente de um módulo se __nenhuma versão__ for especificada. Esse comportamento não mudou. No entanto, se uma versão de pré-lançamento for especificada usando -RequiredVersion, -AllowPrerelease será necessário.

## <a name="examples"></a>Exemplos
```powershell
# Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha. If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> find-module TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

# To install a prerelease, always specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

Não há compatibilidade para a instalação lado a lado das versões de um módulo que diferem apenas devido à versão de pré-lançamento especificada.
Ao instalar um módulo usando o PowerShellGet, versões diferentes do mesmo módulo serão instaladas lado a lado com a criação de um nome de pasta usando o ModuleVersion.
O ModuleVersion, sem a cadeia de caracteres de pré-lançamento, é usado para o nome da pasta.
Se um usuário instalar MyModule versão 2.5.0-alpha, ele será instalado na pasta MyModule\2.5.0.
Se o usuário instalar a versão 2.5.0-beta, ela __substituirá__ o conteúdo da pasta MyModule\2.5.0.
Uma vantagem dessa abordagem é que não é necessário desinstalar a versão de pré-lançamento depois de instalar a versão pronta para produção.
O exemplo a seguir mostra o que esperar:


``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-beta     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

O Uninstall-Module removerá a versão mais recente de um módulo quando -RequiredVersion não for fornecido.
Se -RequiredVersion for especificado e for uma versão de pré-lançamento, -AllowPrerelease deverá ser adicionado ao comando.

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-Module



C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...


```



## <a name="more-details"></a>Mais detalhes
### <a name="prerelease-script-versionsscriptprereleasescriptmd"></a>[Versões de pré-lançamento do Script](../script/PrereleaseScript.md)
### <a name="find-modulepsgetfind-modulemd"></a>[Find-Module](./psget_find-module.md)
### <a name="install-modulepsgetinstall-modulemd"></a>[Install-Module](./psget_install-module.md)
### <a name="save-modulepsgetsave-modulemd"></a>[Save-Module](./psget_save-module.md)
### <a name="update-modulepsgetupdate-modulemd"></a>[Update-Module](./psget_update-module.md)
### <a name="get-installedmodulepsgetget-installedmodulemd"></a>[Get-InstalledModule](./psget_get-installedmodule.md)
### <a name="uninstall-modulepsgetuninstall-modulemd"></a>[UnInstall-Module](./psget_uninstall-module.md)