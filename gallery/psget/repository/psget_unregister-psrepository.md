---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: Unregister-PSRepository
ms.openlocfilehash: 7847e223ae7edd9ec2417d104e5e8130f92a59cf
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="unregister-psrepository"></a>Unregister-PSRepository

Cancela o registro de um repositório.

## <a name="description"></a>Descrição

O cmdlet Unregister-PSRepository cancela o registro de um repositório para o usuário atual.
- O cancelamento de registros e a realização de novos registros do repositório PSGallery são permitidos para cenários empresariais e desconectados.
- Os usuários podem registrar novamente a PSGallery apenas executando `Register-PSRepository -Default`
- Como PSGallery é o repositório de publicação padrão nos cmdlets Publish-Module e Publish-Script, um erro será gerado se PSGallery não estiver disponível na lista de repositórios registrados.

## <a name="cmdlet-syntax"></a>Sintaxe do cmdlet

```powershell
Get-Command -Name Unregister-PSRepository -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Referência da ajuda online sobre cmdlets

[Unregister-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517130)

## <a name="example-commands"></a>Comandos de exemplo

```powershell
Unregister-PSRepository -Name "MyPrivateGallery"

Get-PSRepository exp | Unregister-PSRepository
```

### <a name="unregistration-and-re-registration-of-the-psgallery-repository-is-allowed-for-an-enterprise-and-disconnected-scenarios"></a>O cancelamento de registros e a realização de novos registros do repositório PSGallery são permitidos para cenários empresariais e desconectados.
```powershell

# Unregister PSGallery repository
Unregister-PSRepository PSGallery

# Publish-Module throws an error when PSGallery is not a registered repository
Publish-Module -Name MyModule
publish-module : Unable to find repository 'PSGallery'. Use Get-PSRepository to see all available repositories. Try again after specifying a valid repository name. You can use 'Register-PSRepository -Default' to register the PSGallery repository.
At line:1 char:1
+ publish-module -name mymodule
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (PSGallery:String) [Publish-Module], ArgumentException
    + FullyQualifiedErrorId : PSGalleryNotFound,Publish-Module

# Re-register PSGallery repository
Register-PSRepository -Default
```