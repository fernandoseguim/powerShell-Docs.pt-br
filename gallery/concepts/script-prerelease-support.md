---
ms.date: 10/17/2017
contributor: keithb
keywords: galeria,powershell,cmdlet,psget
title: Versões de pré-lançamento de scripts
ms.openlocfilehash: 5b93da418b836d537491d3f1e4e29fa2e61f2f77
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="prerelease-versions-of-scripts"></a>Versões de pré-lançamento de scripts

Começando com a versão 1.6.0, o PowerShellGet e a Galeria do PowerShell são compatíveis com versões de marcação superiores a 1.0.0 como um pré-lançamento. Antes desse recurso, os itens de pré-lançamento eram limitados a ter uma versão que começasse com 0. A meta desses recursos é oferecer maior compatibilidade com a convenção de versão [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html), sem perder a compatibilidade com o PowerShell versão 3 e superiores ou com as versões existentes do PowerShellGet. Este tópico se concentra os recursos específicos do script. Os recursos equivalentes para módulos estão no tópico [Versões de pré-lançamento do módulo](module-prerelease-support.md). Ao usar esses recursos, os editores podem identificar um script como a versão 2.5.0-alpha e, então, lançar uma versão 2.5.0 pronta para produção que substitui a versão de pré-lançamento.

Em um nível alto, os recursos de pré-lançamento do script incluem:

- Adição de um sufixo PrereleaseString na cadeia de caracteres de versão no manifesto do script. Quando os scripts são publicados na Galeria do PowerShell, esses dados são extraídos do manifesto e usados para identificar os itens de pré-lançamento.
- A aquisição dos itens de pré-lançamento exige a adição do sinalizador -AllowPrerelease aos comandos Find-Script, Install-Script, Update-Script e Save-Script do PowerShellGet. Se o sinalizador não for especificado, os itens de pré-lançamento não serão exibidos.
- As versões de script exibidas pelo Find-Script, pelo Get-InstalledScript e na Galeria do PowerShell serão exibidas com o PrereleaseString, como 2.5.0-alpha.

Os detalhes para os recursos estão incluídos abaixo.

## <a name="identifying-a-script-version-as-a-prerelease"></a>Identificação de uma versão de script como um pré-lançamento

O suporte do PowerShellGet para as versões de pré-lançamento é mais simples para os scripts do que para os módulos. O controle de versão do script é compatível apenas com o PowerShellGet. Portanto, não há nenhum problema de compatibilidade causado ao adicionar a cadeia de caracteres de pré-lançamento. Para identificar um script na Galeria do PowerShell como uma versão de pré-lançamento, adicione um sufixo de pré-lançamento a uma cadeia de caracteres de versão formatada adequadamente nos metadados do script.

Uma seção de exemplo de um manifesto de script com uma versão de pré-lançamento seria semelhante ao seguinte:

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>

```

Para usar um sufixo de pré-lançamento, a cadeia de caracteres de versão deve atender aos seguintes requisitos:

- Um sufixo de pré-lançamento só poderá ser especificado quando a versão tiver três segmentos para Major.Minor.Build.
  Ela é alinhada ao SemVer v1.0.0
- O sufixo de pré-lançamento é uma cadeia de caracteres que começa com um hífen e pode conter ASCII alfanuméricos [0-9A-Za-z-]
- Somente as cadeias de caracteres de pré-lançamento SemVer v1.0.0 são compatíveis no momento, portanto o sufixo de pré-lançamento __não deve__ conter um ponto ou + [. +], que é permitido no SemVer 2.0
- Alguns exemplos de cadeias de caracteres PrereleaseString compatíveis são: -alpha, -alpha1, -BETA, -update20171020

__Impacto na versão de pré-lançamento sobre a ordem de classificação e nas pastas de instalação__

A ordem de classificação é alterada ao usar uma versão de pré-lançamento, que é importante ao publicar na Galeria do PowerShell e ao instalar scripts usando comandos do PowerShellGet. Se duas versões de scripts com o número de versão existirem, a ordem de classificação será baseada na parte da cadeia de caracteres após o hífen. Portanto, a versão 2.5.0-alpha é menor que a versão 2.5.0-beta, que é menor que a versão 2.5.0-gamma. Se dois scripts tiverem o mesmo número de versão e somente um tiver um PrereleaseString, o script __sem__ o sufixo de pré-lançamento será considerado como a versão pronta para produção e será classificado como uma versão maior do que a versão de pré-lançamento. Por exemplo, ao comparar as versões 2.5.0 e 2.5.0-beta, a versão 2.5.0 será considerada a maior das duas.

Ao publicar na Galeria do PowerShell, por padrão, a versão do script que está sendo publicado deverá ter uma versão maior do que qualquer versão previamente publicada na Galeria do PowerShell. Um editor pode atualizar a versão 2.5.0-alpha com 2.5.0-beta, ou com 2.5.0 (sem nenhum sufixo de pré-lançamento).

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a>Localização e aquisição de itens de pré-lançamento usando os comandos do PowerShellGet

Para lidar com os itens de pré-lançamento usando os comandos PowerShellGet Find-Script, Install-Script, Update-Script e Save-Script, é necessário adicionar o sinalizador -AllowPrerelease. Se -AllowPrerelease for especificado, os itens de pré-lançamento serão incluídos se estiverem presentes. Se o sinalizador -AllowPrerelease não for especificado, os itens de pré-lançamento não serão exibidos.

As únicas exceções a isso nos comandos do script PowerShellGet são Get-InstalledScript, e alguns casos com Uninstall-Script.

- Get-InstalledScript sempre mostrará as informações de pré-lançamento automaticamente na cadeia de caracteres de versão, se estiver presente.
- Por padrão, o Uninstall-Script desinstalará a versão mais recente de um script se __nenhuma versão__ for especificada. Esse comportamento não mudou. No entanto, se uma versão de pré-lançamento for especificada usando -RequiredVersion, -AllowPrerelease será necessário.

## <a name="examples"></a>Exemplos

```powershell
# Assume the PowerShell Gallery has TestPackage versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> Find-Script TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Find-Script TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# To install a prerelease, you must specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and script name 'TestPackage'.
Try Get-PSRepository to see all available registered script repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# Note that Get-InstalledScript shows the prerelease version.
# If -RequiredVersion is not specified, all installed scripts will be displayed by Get-InstalledScript
```

Uninstall-Script removerá a versão atual de um script quando -RequiredVersion não for fornecido.
Se -RequiredVersion for especificado e for uma versão de pré-lançamento, -AllowPrerelease deverá ser adicionado ao comando.

``` powershell
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha
Uninstall-Script: The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Script TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Script], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-script


C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
# Since script versions are not installed side-by-side, the above could be simply "Uninstall-Script TestPackage"

C:\windows\system32> Get-Installedscript TestPackage
PackageManagement\Get-Package : No match was found for the specified search criteria and script names 'testpackage'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.5.0.0\PSModule.psm1:4088 char:9
+         PackageManagement\Get-Package @PSBoundParameters | Microsoft. ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...lets.GetPackage:GetPackage) [Get-Package], Exception
    + FullyQualifiedErrorId : NoMatchFound,Microsoft.PowerShell.PackageManagement.Cmdlets.GetPackage
```

## <a name="more-details"></a>Mais detalhes

- [Versões de pré-lançamento do módulo](module-prerelease-support.md)
- [Find-script](/powershell/module/powershellget/find-script)
- [Install-script](/powershell/module/powershellget/install-script)
- [Save-script](/powershell/module/powershellget/save-script)
- [Update-script](/powershell/module/powershellget/update-script)
- [Get-Installedscript](/powershell/module/powershellget/get-installedscript)
- [UnInstall-script](/powershell/module/powershellget/uninstall-script)