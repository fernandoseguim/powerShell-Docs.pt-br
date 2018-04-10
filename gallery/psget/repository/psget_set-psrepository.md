---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: Set-PSRepository
ms.openlocfilehash: 0b555f31241bad15c5e99f3db0136d88ff7ab717
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="set-psrepository"></a>Set-PSRepository

Set-PSRepository define valores para um repositório registrado.

## <a name="description"></a>Descrição

O cmdlet Set-PSRepository define valores para um repositório de módulo registrado.

## <a name="cmdlet-syntax"></a>Sintaxe do cmdlet

```powershell
Get-Command -Name Set-PSRepository -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Referência da ajuda online sobre cmdlets

[Set-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517128)

## <a name="example-commands"></a>Comandos de exemplo

```powershell
PS C:\> Register-PSRepository -Name myRepository -SourceLocation "https://www.myget.org/F/powershellgetdemo/api/v2" -InstallationPolicy Trusted
PS C:\> Get-PSRepository
Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
myRepository              Trusted              https://www.myget.org/F/powershellgetdemo/api/v2

# Set installation Policy for a repository
PS C:\> Set-PSRepository -Name myRepository -InstallationPolicy Untrusted
PS C:\> Get-PSRepository

Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
myRepository              Untrusted            https://www.myget.org/F/powershellgetdemo/api/v2
```


### <a name="set-psrepository-cmdlet-with-script-sharing-support"></a>Cmdlet Set-PSRepository com suporte de compartilhamento de script

Use o cmdlet Set-PSRepository para adicionar **ScriptSourceLocation** e **ScriptPublishLocation** ao PSRepository.
```powershell
# Add script sharing locations to an existing PSRepository using Set-PSRepository object.
Set-PSRepository -Name MyGallery `
                 -ScriptSourceLocation https://MyGallery.com/api/v2/items/psscript/ `
                 -ScriptPublishLocation https://MyGallery.com/api/v2/package/

Get-PSRepository -Name GalleryINT | Format-List * -Force

Name : GalleryINT
SourceLocation : https://MyGallery.com/api/v2/
Trusted : True
Registered : True
InstallationPolicy : Trusted
PackageManagementProvider : NuGet
PublishLocation : https://MyGallery.com/api/v2/package/
ScriptSourceLocation : https://MyGallery.com/api/v2/items/psscript/
ScriptPublishLocation : https://MyGallery.com/api/v2/package/
ProviderOptions : {}

```