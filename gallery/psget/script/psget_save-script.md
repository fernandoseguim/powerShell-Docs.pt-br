---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: Save-Script
ms.openlocfilehash: 7b692d33e3f86a89505b8d37c0da4177f3dff2c2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="save-script"></a><span data-ttu-id="253d0-103">Save-Script</span><span class="sxs-lookup"><span data-stu-id="253d0-103">Save-Script</span></span>

<span data-ttu-id="253d0-104">O cmdlet Save-Script permite examinar o arquivo de script salvando-o em um local especificado.</span><span class="sxs-lookup"><span data-stu-id="253d0-104">Save-Script cmdlet lets you to review the script file by saving it to a specified location.</span></span>

## <a name="description"></a><span data-ttu-id="253d0-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="253d0-105">Description</span></span>

<span data-ttu-id="253d0-106">O cmdlet Save-Script salva o script especificado.</span><span class="sxs-lookup"><span data-stu-id="253d0-106">The Save-Script cmdlet saves the specified script.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="253d0-107">Sintaxe do cmdlet</span><span class="sxs-lookup"><span data-stu-id="253d0-107">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="253d0-108">Referência da ajuda online sobre cmdlets</span><span class="sxs-lookup"><span data-stu-id="253d0-108">Cmdlet online help reference</span></span>

[<span data-ttu-id="253d0-109">Save-Script</span><span class="sxs-lookup"><span data-stu-id="253d0-109">Save-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a><span data-ttu-id="253d0-110">Comandos de exemplo</span><span class="sxs-lookup"><span data-stu-id="253d0-110">Example commands</span></span>

### <a name="example-1-save-a-script-from-a-repository"></a><span data-ttu-id="253d0-111">Exemplo 1: Salvar um script de um repositório</span><span class="sxs-lookup"><span data-stu-id="253d0-111">Example 1: Save a script from a repository</span></span>
<span data-ttu-id="253d0-112">Este comando salva a versão mais recente do script Fabrikam-ClientScript do repositório GalleryINT na pasta local C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="253d0-112">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a><span data-ttu-id="253d0-113">Exemplo 2: Salvar uma versão de um script por tubulação do cmdlet Find-Script</span><span class="sxs-lookup"><span data-stu-id="253d0-113">Example 2: Save a version of a script by piping from the Find-Script cmdlet</span></span>

<span data-ttu-id="253d0-114">O primeiro comando localiza a versão 1.5 de Fabrikam-ClientScript do repositório GalleryINT e a salva na pasta C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="253d0-114">The first command finds version 1.5 of Fabrikam-ClientScript from the repository GalleryINT and saves it to the folder C:\ScriptSharingDemo</span></span>

<span data-ttu-id="253d0-115">O segundo comando valida os metadados do script salvo.</span><span class="sxs-lookup"><span data-stu-id="253d0-115">The second command validates the saved script metadata.</span></span>

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

