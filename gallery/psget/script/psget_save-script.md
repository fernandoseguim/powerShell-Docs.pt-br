---
ms.date: 10/17/2017
contributor: keithb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: Save-Script
ms.openlocfilehash: 67697fc0e70fb31cad9ad5ae7ce01debef160b81
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="save-script"></a><span data-ttu-id="3251e-103">Save-Script</span><span class="sxs-lookup"><span data-stu-id="3251e-103">Save-Script</span></span>

<span data-ttu-id="3251e-104">O cmdlet Save-Script permite examinar o arquivo de script salvando-o em um local especificado.</span><span class="sxs-lookup"><span data-stu-id="3251e-104">Save-Script cmdlet lets you to review the script file by saving it to a specified location.</span></span>

## <a name="description"></a><span data-ttu-id="3251e-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="3251e-105">Description</span></span>

<span data-ttu-id="3251e-106">O cmdlet Save-Script salva o script especificado.</span><span class="sxs-lookup"><span data-stu-id="3251e-106">The Save-Script cmdlet saves the specified script.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="3251e-107">Sintaxe do cmdlet</span><span class="sxs-lookup"><span data-stu-id="3251e-107">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="3251e-108">Referência da ajuda online sobre cmdlets</span><span class="sxs-lookup"><span data-stu-id="3251e-108">Cmdlet online help reference</span></span>

[<span data-ttu-id="3251e-109">Save-Script</span><span class="sxs-lookup"><span data-stu-id="3251e-109">Save-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a><span data-ttu-id="3251e-110">Comandos de exemplo</span><span class="sxs-lookup"><span data-stu-id="3251e-110">Example commands</span></span>

### <a name="example-1-save-a-script-from-a-repository"></a><span data-ttu-id="3251e-111">Exemplo 1: Salvar um script de um repositório</span><span class="sxs-lookup"><span data-stu-id="3251e-111">Example 1: Save a script from a repository</span></span>
<span data-ttu-id="3251e-112">Este comando salva a versão mais recente do script Fabrikam-ClientScript do repositório GalleryINT na pasta local C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="3251e-112">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a><span data-ttu-id="3251e-113">Exemplo 2: Salvar uma versão de um script por tubulação do cmdlet Find-Script</span><span class="sxs-lookup"><span data-stu-id="3251e-113">Example 2: Save a version of a script by piping from the Find-Script cmdlet</span></span>

<span data-ttu-id="3251e-114">O primeiro comando localiza a versão 1.5 de Fabrikam-ClientScript do repositório GalleryINT e a salva na pasta C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="3251e-114">The first command finds version 1.5 of Fabrikam-ClientScript from the repository GalleryINT and saves it to the folder C:\ScriptSharingDemo</span></span>

<span data-ttu-id="3251e-115">O segundo comando valida os metadados do script salvo.</span><span class="sxs-lookup"><span data-stu-id="3251e-115">The second command validates the saved script metadata.</span></span>

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

### <a name="example-3-save-a-prerelease-version-of-a-script-from-a-repository"></a><span data-ttu-id="3251e-116">Exemplo 3: salvar uma versão de pré-lançamento de um script de um repositório</span><span class="sxs-lookup"><span data-stu-id="3251e-116">Example 3: Save a prerelease version of a script from a repository</span></span>
<span data-ttu-id="3251e-117">Este comando salva a versão mais recente do script Fabrikam-ClientScript do repositório GalleryINT na pasta local C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="3251e-117">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Path C:\ScriptSharingDemo -AllowPrerelease
```