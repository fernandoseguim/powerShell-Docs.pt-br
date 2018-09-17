---
ms.date: 08/27/2018
keywords: powershell, cmdlet
title: Usando nomes familiares de comando
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: c5665f64fd832eb9c807f413a8e879f63db7f8c6
ms.sourcegitcommit: c170a1608d20d3c925d79c35fa208f650d014146
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43353242"
---
# <a name="using-familiar-command-names"></a><span data-ttu-id="e3781-103">Usando nomes de comando familiares</span><span class="sxs-lookup"><span data-stu-id="e3781-103">Using familiar command names</span></span>

<span data-ttu-id="e3781-104">O PowerShell dá suporte a aliases para se referir aos comandos por nomes alternativos.</span><span class="sxs-lookup"><span data-stu-id="e3781-104">PowerShell supports aliases to refer to commands by alternate names.</span></span> <span data-ttu-id="e3781-105">Usar alias permite que usuários com experiência em outros shells utilizem nomes de comando comuns que já conhecem para operações semelhantes no PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3781-105">Aliasing allows users with experience in other shells to use common command names that they already know for similar operations in PowerShell.</span></span>

<span data-ttu-id="e3781-106">O alias associa um novo nome a outro comando.</span><span class="sxs-lookup"><span data-stu-id="e3781-106">Aliasing associates a new name with another command.</span></span> <span data-ttu-id="e3781-107">Por exemplo, o PowerShell tem uma função interna denominada `Clear-Host` que limpa a janela de saída.</span><span class="sxs-lookup"><span data-stu-id="e3781-107">For example, PowerShell has an internal function named `Clear-Host` that clears the output window.</span></span> <span data-ttu-id="e3781-108">Você pode digitar o alias `cls` ou `clear` em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="e3781-108">You can type either the `cls` or `clear` alias at a command prompt.</span></span> <span data-ttu-id="e3781-109">O PowerShell interpreta esses aliases e executa a função `Clear-Host`.</span><span class="sxs-lookup"><span data-stu-id="e3781-109">PowerShell interprets these aliases and runs the `Clear-Host` function.</span></span>

<span data-ttu-id="e3781-110">Esse recurso ajuda os usuários a aprender sobre o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3781-110">This feature helps users to learn PowerShell.</span></span> <span data-ttu-id="e3781-111">Primeiro, a maioria dos usuários de **cmd.exe** e do Unix conhece um grande repertório de comandos por nome.</span><span class="sxs-lookup"><span data-stu-id="e3781-111">First, most **cmd.exe** and Unix users have a large repertoire of commands that users already know by name.</span></span> <span data-ttu-id="e3781-112">Talvez os equivalentes do PowerShell não produzam resultados idênticos.</span><span class="sxs-lookup"><span data-stu-id="e3781-112">The PowerShell equivalents may not produce identical results.</span></span> <span data-ttu-id="e3781-113">No entanto, os resultados são bem parecidos, e os usuários podem fazer o trabalho sem conhecer o nome de comando do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3781-113">However, the results are close enough that users can do work without knowing the PowerShell command name.</span></span> <span data-ttu-id="e3781-114">"Memória dos dedos" é outra grande fonte de frustração ao aprender um novo shell de comando.</span><span class="sxs-lookup"><span data-stu-id="e3781-114">"Finger memory" is another major source of frustration when learning a new command shell.</span></span> <span data-ttu-id="e3781-115">Se você tiver usado o **cmd.exe** durante anos, talvez digite de forma reflexiva o comando `cls` para limpar a tela.</span><span class="sxs-lookup"><span data-stu-id="e3781-115">If you have used **cmd.exe** for years, you might reflexively type the `cls` command to clear the screen.</span></span> <span data-ttu-id="e3781-116">Sem o alias para `Clear-Host`, você receberá uma mensagem de erro e não saberá o que fazer para limpar a saída.</span><span class="sxs-lookup"><span data-stu-id="e3781-116">Without the alias for `Clear-Host`, you receive an error message and won't know what to do to clear the output.</span></span>

<span data-ttu-id="e3781-117">A lista a seguir mostra alguns comandos comuns do **cmd.exe** e Unix que podem ser usados no PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e3781-117">The following list shows a few of the common **cmd.exe** and Unix commands that you can use in PowerShell:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="e3781-118">cat</span><span class="sxs-lookup"><span data-stu-id="e3781-118">cat</span></span>|<span data-ttu-id="e3781-119">dir</span><span class="sxs-lookup"><span data-stu-id="e3781-119">dir</span></span>|<span data-ttu-id="e3781-120">montagem</span><span class="sxs-lookup"><span data-stu-id="e3781-120">mount</span></span>|<span data-ttu-id="e3781-121">rm</span><span class="sxs-lookup"><span data-stu-id="e3781-121">rm</span></span>|
|<span data-ttu-id="e3781-122">cd</span><span class="sxs-lookup"><span data-stu-id="e3781-122">cd</span></span>|<span data-ttu-id="e3781-123">echo</span><span class="sxs-lookup"><span data-stu-id="e3781-123">echo</span></span>|<span data-ttu-id="e3781-124">move</span><span class="sxs-lookup"><span data-stu-id="e3781-124">move</span></span>|<span data-ttu-id="e3781-125">rmdir</span><span class="sxs-lookup"><span data-stu-id="e3781-125">rmdir</span></span>|
|<span data-ttu-id="e3781-126">chdir</span><span class="sxs-lookup"><span data-stu-id="e3781-126">chdir</span></span>|<span data-ttu-id="e3781-127">erase</span><span class="sxs-lookup"><span data-stu-id="e3781-127">erase</span></span>|<span data-ttu-id="e3781-128">popd</span><span class="sxs-lookup"><span data-stu-id="e3781-128">popd</span></span>|<span data-ttu-id="e3781-129">sleep</span><span class="sxs-lookup"><span data-stu-id="e3781-129">sleep</span></span>|
|<span data-ttu-id="e3781-130">clear</span><span class="sxs-lookup"><span data-stu-id="e3781-130">clear</span></span>|<span data-ttu-id="e3781-131">h</span><span class="sxs-lookup"><span data-stu-id="e3781-131">h</span></span>|<span data-ttu-id="e3781-132">ps</span><span class="sxs-lookup"><span data-stu-id="e3781-132">ps</span></span>|<span data-ttu-id="e3781-133">sort</span><span class="sxs-lookup"><span data-stu-id="e3781-133">sort</span></span>|
|<span data-ttu-id="e3781-134">cls</span><span class="sxs-lookup"><span data-stu-id="e3781-134">cls</span></span>|<span data-ttu-id="e3781-135">history</span><span class="sxs-lookup"><span data-stu-id="e3781-135">history</span></span>|<span data-ttu-id="e3781-136">pushd</span><span class="sxs-lookup"><span data-stu-id="e3781-136">pushd</span></span>|<span data-ttu-id="e3781-137">tee</span><span class="sxs-lookup"><span data-stu-id="e3781-137">tee</span></span>|
|<span data-ttu-id="e3781-138">copy</span><span class="sxs-lookup"><span data-stu-id="e3781-138">copy</span></span>|<span data-ttu-id="e3781-139">kill</span><span class="sxs-lookup"><span data-stu-id="e3781-139">kill</span></span>|<span data-ttu-id="e3781-140">pwd</span><span class="sxs-lookup"><span data-stu-id="e3781-140">pwd</span></span>|<span data-ttu-id="e3781-141">tipo</span><span class="sxs-lookup"><span data-stu-id="e3781-141">type</span></span>|
|<span data-ttu-id="e3781-142">del</span><span class="sxs-lookup"><span data-stu-id="e3781-142">del</span></span>|<span data-ttu-id="e3781-143">lp</span><span class="sxs-lookup"><span data-stu-id="e3781-143">lp</span></span>|<span data-ttu-id="e3781-144">r</span><span class="sxs-lookup"><span data-stu-id="e3781-144">r</span></span>|<span data-ttu-id="e3781-145">write</span><span class="sxs-lookup"><span data-stu-id="e3781-145">write</span></span>|
|<span data-ttu-id="e3781-146">diff</span><span class="sxs-lookup"><span data-stu-id="e3781-146">diff</span></span>|<span data-ttu-id="e3781-147">ls</span><span class="sxs-lookup"><span data-stu-id="e3781-147">ls</span></span>|<span data-ttu-id="e3781-148">ren</span><span class="sxs-lookup"><span data-stu-id="e3781-148">ren</span></span>||

<span data-ttu-id="e3781-149">O cmdlet `Get-Alias` mostra o nome real do comando nativo do PowerShell associado a um alias.</span><span class="sxs-lookup"><span data-stu-id="e3781-149">The `Get-Alias` cmdlet shows you the real name of the native PowerShell command associated with an alias.</span></span>

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a><span data-ttu-id="e3781-150">Interpretar aliases padrão</span><span class="sxs-lookup"><span data-stu-id="e3781-150">Interpreting standard aliases</span></span>

<span data-ttu-id="e3781-151">Os aliases que descrevemos antes foram projetados para compatibilidade de nome com outros shells de comando.</span><span class="sxs-lookup"><span data-stu-id="e3781-151">The aliases we described previous were designed for name-compatibility with other command shells.</span></span>
<span data-ttu-id="e3781-152">A maioria dos aliases criados no PowerShell é projetada para manter a brevidade.</span><span class="sxs-lookup"><span data-stu-id="e3781-152">Most aliases built into PowerShell are designed for brevity.</span></span> <span data-ttu-id="e3781-153">Os nomes mais curtos são mais fáceis de digitar, mas são difíceis de ler se você não souber a que se referem.</span><span class="sxs-lookup"><span data-stu-id="e3781-153">Shorter names are easier to type, but are difficult to read if you don't know what they refer to.</span></span>

<span data-ttu-id="e3781-154">Os aliases do PowerShell tentam equilibrar a clareza e a brevidade.</span><span class="sxs-lookup"><span data-stu-id="e3781-154">PowerShell aliases try to compromise between clarity and brevity.</span></span> <span data-ttu-id="e3781-155">O PowerShell usa um conjunto padrão de aliases para substantivos e verbos comum.</span><span class="sxs-lookup"><span data-stu-id="e3781-155">PowerShell uses a standard set of aliases for common nouns and verbs.</span></span>

<span data-ttu-id="e3781-156">Exemplo de abreviações:</span><span class="sxs-lookup"><span data-stu-id="e3781-156">Example abbreviations:</span></span>

| <span data-ttu-id="e3781-157">Substantivo ou verbo</span><span class="sxs-lookup"><span data-stu-id="e3781-157">Noun or Verb</span></span> | <span data-ttu-id="e3781-158">Abreviação</span><span class="sxs-lookup"><span data-stu-id="e3781-158">Abbreviation</span></span> |
|--------------|--------------|
| <span data-ttu-id="e3781-159">Get</span><span class="sxs-lookup"><span data-stu-id="e3781-159">Get</span></span>          | <span data-ttu-id="e3781-160">g</span><span class="sxs-lookup"><span data-stu-id="e3781-160">g</span></span>            |
| <span data-ttu-id="e3781-161">Set</span><span class="sxs-lookup"><span data-stu-id="e3781-161">Set</span></span>          | <span data-ttu-id="e3781-162">s</span><span class="sxs-lookup"><span data-stu-id="e3781-162">s</span></span>            |
| <span data-ttu-id="e3781-163">Item</span><span class="sxs-lookup"><span data-stu-id="e3781-163">Item</span></span>         | <span data-ttu-id="e3781-164">i</span><span class="sxs-lookup"><span data-stu-id="e3781-164">i</span></span>            |
| <span data-ttu-id="e3781-165">Local</span><span class="sxs-lookup"><span data-stu-id="e3781-165">Location</span></span>     | <span data-ttu-id="e3781-166">l</span><span class="sxs-lookup"><span data-stu-id="e3781-166">l</span></span>            |
| <span data-ttu-id="e3781-167">Comando</span><span class="sxs-lookup"><span data-stu-id="e3781-167">Command</span></span>      | <span data-ttu-id="e3781-168">cm</span><span class="sxs-lookup"><span data-stu-id="e3781-168">cm</span></span>           |
| <span data-ttu-id="e3781-169">Alias</span><span class="sxs-lookup"><span data-stu-id="e3781-169">Alias</span></span>        | <span data-ttu-id="e3781-170">al</span><span class="sxs-lookup"><span data-stu-id="e3781-170">al</span></span>           |

<span data-ttu-id="e3781-171">Esses aliases são compreensíveis quando você conhece os nomes abreviados.</span><span class="sxs-lookup"><span data-stu-id="e3781-171">These aliases are understandable when you know the shorthand names.</span></span>

| <span data-ttu-id="e3781-172">Nome do cmdlet</span><span class="sxs-lookup"><span data-stu-id="e3781-172">Cmdlet name</span></span>    | <span data-ttu-id="e3781-173">Alias</span><span class="sxs-lookup"><span data-stu-id="e3781-173">Alias</span></span> |
|----------------|-------|
| `Get-Item `    | <span data-ttu-id="e3781-174">gi</span><span class="sxs-lookup"><span data-stu-id="e3781-174">gi</span></span>    |
| `Set-Item`     | <span data-ttu-id="e3781-175">si</span><span class="sxs-lookup"><span data-stu-id="e3781-175">si</span></span>    |
| `Get-Location` | <span data-ttu-id="e3781-176">gl</span><span class="sxs-lookup"><span data-stu-id="e3781-176">gl</span></span>    |
| `Set-Location` | <span data-ttu-id="e3781-177">sl</span><span class="sxs-lookup"><span data-stu-id="e3781-177">sl</span></span>    |
| `Get-Command`  | <span data-ttu-id="e3781-178">gcm</span><span class="sxs-lookup"><span data-stu-id="e3781-178">gcm</span></span>   |
| `Get-Alias`    | <span data-ttu-id="e3781-179">gal</span><span class="sxs-lookup"><span data-stu-id="e3781-179">gal</span></span>   |

<span data-ttu-id="e3781-180">Quando você estiver familiarizado com o alias do PowerShell, será fácil imaginar que o alias **sal** se refere a `Set-Alias`.</span><span class="sxs-lookup"><span data-stu-id="e3781-180">Once you're familiar with PowerShell aliasing, it's easy to guess that the **sal** alias refers to `Set-Alias`.</span></span>

## <a name="creating-new-aliases"></a><span data-ttu-id="e3781-181">Criar um novo alias</span><span class="sxs-lookup"><span data-stu-id="e3781-181">Creating new aliases</span></span>

<span data-ttu-id="e3781-182">Você pode criar seus próprios aliases usando o cmdlet `Set-Alias`.</span><span class="sxs-lookup"><span data-stu-id="e3781-182">You can create your own aliases using the `Set-Alias` cmdlet.</span></span> <span data-ttu-id="e3781-183">Por exemplo, as instruções a seguir criam os aliases de cmdlet padrão discutidos anteriormente:</span><span class="sxs-lookup"><span data-stu-id="e3781-183">For example, the following statements create the standard cmdlet aliases previously discussed:</span></span>

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

<span data-ttu-id="e3781-184">Internamente, o PowerShell usa comandos parecidos com esses durante a inicialização, mas esses aliases não são mutáveis.</span><span class="sxs-lookup"><span data-stu-id="e3781-184">Internally, PowerShell uses similar commands during startup, but these aliases are not changeable.</span></span>
<span data-ttu-id="e3781-185">Se você tentar executar um desses comandos, receberá um erro explicando que o alias não pode ser modificado.</span><span class="sxs-lookup"><span data-stu-id="e3781-185">If you try to execute one of these commands, you get an error explaining that the alias can't be modified.</span></span> <span data-ttu-id="e3781-186">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e3781-186">For example:</span></span>

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```