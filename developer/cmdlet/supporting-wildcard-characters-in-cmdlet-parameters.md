---
title: Suporte a caracteres curinga em parâmetros do Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wildcards [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide], wildcards
ms.assetid: 9b26e1e9-9350-4a5a-aad5-ddcece658d93
caps.latest.revision: 12
ms.openlocfilehash: 6c762d3889bc4b649252390625525db4735f4c1d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059602"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a><span data-ttu-id="76c84-102">Suporte a caracteres curinga em parâmetros de cmdlet</span><span class="sxs-lookup"><span data-stu-id="76c84-102">Supporting Wildcard Characters in Cmdlet Parameters</span></span>

<span data-ttu-id="76c84-103">Muitas vezes, você precisará de um cmdlet para executar em relação a um grupo de recursos, em vez de em relação a um único recurso de design.</span><span class="sxs-lookup"><span data-stu-id="76c84-103">Often, you will have to design a cmdlet to run against a group of resources rather than against a single resource.</span></span> <span data-ttu-id="76c84-104">Por exemplo, um cmdlet, talvez seja necessário localizar todos os arquivos em um repositório de dados que têm o mesmo nome ou a extensão.</span><span class="sxs-lookup"><span data-stu-id="76c84-104">For example, a cmdlet might need to locate all the files in a data store that have the same name or extension.</span></span> <span data-ttu-id="76c84-105">Você deve fornecer suporte para caracteres curinga, quando você projeta um cmdlet que será executado em relação a um grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="76c84-105">You must provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

> [!NOTE]
> <span data-ttu-id="76c84-106">Usando caracteres curinga é, às vezes, conhecido como *recurso de curinga*.</span><span class="sxs-lookup"><span data-stu-id="76c84-106">Using wildcard characters is sometimes referred to as *globbing*.</span></span>

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a><span data-ttu-id="76c84-107">Cmdlets do Windows PowerShell que usam curingas</span><span class="sxs-lookup"><span data-stu-id="76c84-107">Windows PowerShell Cmdlets That Use Wildcards</span></span>

 <span data-ttu-id="76c84-108">Muitos cmdlets do Windows PowerShell dão suporte a caracteres curinga para seus valores de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="76c84-108">Many Windows PowerShell cmdlets support wildcard characters for their parameter values.</span></span> <span data-ttu-id="76c84-109">Por exemplo, quase todos os cmdlets que tem um `Name` ou `Path` parâmetro dá suporte a caracteres curinga para esses parâmetros.</span><span class="sxs-lookup"><span data-stu-id="76c84-109">For example, almost every cmdlet that has a `Name` or `Path` parameter supports wildcard characters for these parameters.</span></span> <span data-ttu-id="76c84-110">(Embora a maioria dos cmdlets que têm uma `Path` parâmetro também têm um `LiteralPath` parâmetro que não oferece suporte a caracteres curinga.) O comando a seguir mostra como um caractere curinga é usado para retornar todos os cmdlets na sessão atual, cujo nome contém o verbo Get.</span><span class="sxs-lookup"><span data-stu-id="76c84-110">(Although most cmdlets that have a `Path` parameter also have a `LiteralPath` parameter that does not support wildcard characters.) The following command shows how a wildcard character is used to return all the cmdlets in the current session whose name contains the Get verb.</span></span>

 <span data-ttu-id="76c84-111">**PS > get-command get -\***</span><span class="sxs-lookup"><span data-stu-id="76c84-111">**PS>get-command get-\***</span></span>

## <a name="supported-wildcard-characters"></a><span data-ttu-id="76c84-112">Caracteres curinga suportados</span><span class="sxs-lookup"><span data-stu-id="76c84-112">Supported Wildcard Characters</span></span>

<span data-ttu-id="76c84-113">Windows PowerShell suporta os seguintes caracteres curinga.</span><span class="sxs-lookup"><span data-stu-id="76c84-113">Windows PowerShell supports the following wildcard characters.</span></span>

|<span data-ttu-id="76c84-114">caractere curinga</span><span class="sxs-lookup"><span data-stu-id="76c84-114">Wildcard character</span></span>|<span data-ttu-id="76c84-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="76c84-115">Description</span></span>|<span data-ttu-id="76c84-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="76c84-116">Example</span></span>|<span data-ttu-id="76c84-117">Correspondências</span><span class="sxs-lookup"><span data-stu-id="76c84-117">Matches</span></span>|<span data-ttu-id="76c84-118">Não corresponde</span><span class="sxs-lookup"><span data-stu-id="76c84-118">Does not match</span></span>|
|------------------------|-----------------|-------------|-------------|--------------------|
|*|<span data-ttu-id="76c84-119">Corresponde a zero ou mais caracteres, começando na posição especificada</span><span class="sxs-lookup"><span data-stu-id="76c84-119">Matches zero or more characters, starting at the specified position</span></span>|<span data-ttu-id="76c84-120">a\*</span><span class="sxs-lookup"><span data-stu-id="76c84-120">a\*</span></span>|<span data-ttu-id="76c84-121">Um, ag, Apple</span><span class="sxs-lookup"><span data-stu-id="76c84-121">A, ag, Apple</span></span>||
|<span data-ttu-id="76c84-122">?</span><span class="sxs-lookup"><span data-stu-id="76c84-122">?</span></span>|<span data-ttu-id="76c84-123">Anycharacter correspondências na posição especificada</span><span class="sxs-lookup"><span data-stu-id="76c84-123">Matches anycharacter at the specified position</span></span>|<span data-ttu-id="76c84-124">?n</span><span class="sxs-lookup"><span data-stu-id="76c84-124">?n</span></span>|<span data-ttu-id="76c84-125">Um, no, no</span><span class="sxs-lookup"><span data-stu-id="76c84-125">An, in, on</span></span>|<span data-ttu-id="76c84-126">ran</span><span class="sxs-lookup"><span data-stu-id="76c84-126">ran</span></span>|
|<span data-ttu-id="76c84-127">[ ]</span><span class="sxs-lookup"><span data-stu-id="76c84-127">[ ]</span></span>|<span data-ttu-id="76c84-128">Corresponde a um intervalo de caracteres</span><span class="sxs-lookup"><span data-stu-id="76c84-128">Matches a range of characters</span></span>|<span data-ttu-id="76c84-129">[a-l]ook</span><span class="sxs-lookup"><span data-stu-id="76c84-129">[a-l]ook</span></span>|<span data-ttu-id="76c84-130">catálogo, cook, aparência</span><span class="sxs-lookup"><span data-stu-id="76c84-130">book, cook, look</span></span>|<span data-ttu-id="76c84-131">levou</span><span class="sxs-lookup"><span data-stu-id="76c84-131">took</span></span>|
|<span data-ttu-id="76c84-132">[ ]</span><span class="sxs-lookup"><span data-stu-id="76c84-132">[ ]</span></span>|<span data-ttu-id="76c84-133">Corresponde a caracteres especificados</span><span class="sxs-lookup"><span data-stu-id="76c84-133">Matches the specified characters</span></span>|<span data-ttu-id="76c84-134">[bc]ook</span><span class="sxs-lookup"><span data-stu-id="76c84-134">[bc]ook</span></span>|<span data-ttu-id="76c84-135">catálogo, cook</span><span class="sxs-lookup"><span data-stu-id="76c84-135">book, cook</span></span>|<span data-ttu-id="76c84-136">aparência</span><span class="sxs-lookup"><span data-stu-id="76c84-136">look</span></span>|

<span data-ttu-id="76c84-137">Quando você projeta cmdlets que oferecem suporte a caracteres curinga, permitir combinações de caracteres curinga.</span><span class="sxs-lookup"><span data-stu-id="76c84-137">When you design cmdlets that support wildcard characters, allow for combinations of wildcard characters.</span></span> <span data-ttu-id="76c84-138">Por exemplo, o comando a seguir usa o `Get-ChildItem` cmdlet para recuperar todos os arquivos. txt que estão na pasta c:\Techdocs e que começam com as letras "a" "l" por meio.</span><span class="sxs-lookup"><span data-stu-id="76c84-138">For example, the following command uses the `Get-ChildItem` cmdlet to retrieve all the .txt files that are in the c:\Techdocs folder and that begin with the letters "a" through "l."</span></span>

<span data-ttu-id="76c84-139">**get-childitem c:\techdocs\\[a-l]\*.txt**</span><span class="sxs-lookup"><span data-stu-id="76c84-139">**get-childitem c:\techdocs\\[a-l]\*.txt**</span></span>

<span data-ttu-id="76c84-140">O comando anterior usa o curinga de intervalo **[a-l]** para especificar o nome do arquivo deve começar com os caracteres "a" "l" por meio.</span><span class="sxs-lookup"><span data-stu-id="76c84-140">The previous command uses the range wildcard **[a-l]** to specify that the file name should begin with the characters "a" through "l."</span></span> <span data-ttu-id="76c84-141">O comando, em seguida, usa o \* caractere curinga como um espaço reservado para todos os caracteres entre a primeira letra do nome do arquivo e a extensão. txt.</span><span class="sxs-lookup"><span data-stu-id="76c84-141">The command then uses the \* wildcard character as a placeholder for any characters between the first letter of the file name and the .txt extension.</span></span>

<span data-ttu-id="76c84-142">O exemplo a seguir usa um padrão de curinga de intervalo que exclui a letra "d", mas inclui todas as outras letras de "a" a "f."</span><span class="sxs-lookup"><span data-stu-id="76c84-142">The following example uses a range wildcard pattern that excludes the letter "d" but includes all the other letters from "a" through "f."</span></span>

<span data-ttu-id="76c84-143">**get-childitem c:\techdocs\\[a-cef]\*.txt**</span><span class="sxs-lookup"><span data-stu-id="76c84-143">**get-childitem c:\techdocs\\[a-cef]\*.txt**</span></span>

## <a name="handling-literal-characters-in-wildcard-patterns"></a><span data-ttu-id="76c84-144">Tratamento de caracteres literais em padrões de curinga</span><span class="sxs-lookup"><span data-stu-id="76c84-144">Handling Literal Characters in Wildcard Patterns</span></span>

<span data-ttu-id="76c84-145">Se o padrão de curinga especificado contém caracteres literais, use o caractere de acento grave (') como um caractere de escape.</span><span class="sxs-lookup"><span data-stu-id="76c84-145">If the wildcard pattern you specify contains literal characters, use the backtick character (\`) as an escape character.</span></span> <span data-ttu-id="76c84-146">Quando você especificar caracteres literais programaticamente, use um acento grave único.</span><span class="sxs-lookup"><span data-stu-id="76c84-146">When you specify literal characters programmatically, use a single backtick.</span></span> <span data-ttu-id="76c84-147">Quando você especifica os caracteres literais no prompt de comando, use dois backticks.</span><span class="sxs-lookup"><span data-stu-id="76c84-147">When you specify literal characters at the command prompt, use two backticks.</span></span> <span data-ttu-id="76c84-148">Por exemplo, o padrão a seguir contém dois colchetes que devem ser interpretadas literalmente.</span><span class="sxs-lookup"><span data-stu-id="76c84-148">For example, the following pattern contains two brackets that must be taken literally.</span></span>

<span data-ttu-id="76c84-149">"John Smith \`[\*']" (especificado por meio de programação)</span><span class="sxs-lookup"><span data-stu-id="76c84-149">"John Smith \`[\*\`]" (specified programmatically)</span></span>

<span data-ttu-id="76c84-150">"John Smith \` \`[\*\`']" (especificado no prompt de comando)</span><span class="sxs-lookup"><span data-stu-id="76c84-150">"John Smith \`\`[\*\`\`]"  (specified at the command prompt)</span></span>

<span data-ttu-id="76c84-151">Este padrão corresponde a "John Smith [Marketing]" ou "John Smith [desenvolvimento do]".</span><span class="sxs-lookup"><span data-stu-id="76c84-151">This pattern matches "John Smith [Marketing]" or "John Smith [Development]".</span></span>

## <a name="cmdlet-output-and-wildcard-characters"></a><span data-ttu-id="76c84-152">Saída do cmdlet e caracteres curinga</span><span class="sxs-lookup"><span data-stu-id="76c84-152">Cmdlet Output and Wildcard Characters</span></span>

<span data-ttu-id="76c84-153">Quando os parâmetros de cmdlet dá suporte a caracteres curinga, uma operação do cmdlet normalmente gera uma saída de matriz.</span><span class="sxs-lookup"><span data-stu-id="76c84-153">When cmdlet parameters support wildcard characters, a cmdlet operation usually generates an array output.</span></span> <span data-ttu-id="76c84-154">Ocasionalmente, ele não faz sentido para dar suporte a uma matriz de saída porque o usuário pode usar apenas um único item por vez.</span><span class="sxs-lookup"><span data-stu-id="76c84-154">Occasionally, it makes no sense to support an array output because the user might use only a single item at a time.</span></span> <span data-ttu-id="76c84-155">Por exemplo, o `Set-Location` cmdlet oferece suporte a uma matriz de saída porque o usuário define apenas um único local.</span><span class="sxs-lookup"><span data-stu-id="76c84-155">For example, the `Set-Location` cmdlet does support an array output because the user sets only a single location.</span></span> <span data-ttu-id="76c84-156">Nesse caso, o cmdlet ainda ofereça suporte a caracteres curinga, mas ele força a resolução para um único local.</span><span class="sxs-lookup"><span data-stu-id="76c84-156">In this instance, the cmdlet still supports wildcard characters, but it forces resolution to a single location.</span></span>

## <a name="see-also"></a><span data-ttu-id="76c84-157">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="76c84-157">See Also</span></span>

<span data-ttu-id="76c84-158">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="76c84-158">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

[<span data-ttu-id="76c84-159">Classe WildcardPattern</span><span class="sxs-lookup"><span data-stu-id="76c84-159">WildcardPattern Class</span></span>](/dotnet/api/system.management.automation.wildcardpattern)
