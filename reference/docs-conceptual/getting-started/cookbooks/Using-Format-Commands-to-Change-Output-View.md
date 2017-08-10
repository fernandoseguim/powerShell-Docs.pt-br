---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: "Usando comandos de formatação para alterar a exibição de saída"
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
ms.openlocfilehash: 0163fcb21d586fc98902d9bdcfab6fe4eb97c225
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2017
---
# <a name="using-format-commands-to-change-output-view"></a><span data-ttu-id="22bca-103">Usando comandos de formatação para alterar a exibição de saída</span><span class="sxs-lookup"><span data-stu-id="22bca-103">Using Format Commands to Change Output View</span></span>
<span data-ttu-id="22bca-104">O Windows PowerShell tem um conjunto de cmdlets que permite controlar quais propriedades são exibidas para objetos específicos.</span><span class="sxs-lookup"><span data-stu-id="22bca-104">Windows PowerShell has a set of cmdlets that allow you to control which properties are displayed for particular objects.</span></span> <span data-ttu-id="22bca-105">Os nomes de todos os cmdlets começam com o verbo **Format**.</span><span class="sxs-lookup"><span data-stu-id="22bca-105">The names of all the cmdlets begin with the verb **Format**.</span></span> <span data-ttu-id="22bca-106">Eles permitem selecionar uma ou mais propriedades para mostrar.</span><span class="sxs-lookup"><span data-stu-id="22bca-106">They let you select one or more properties to show.</span></span>

<span data-ttu-id="22bca-107">Os cmdlets **Format** são **Format-Wide**, **Format-List**, **Format-Table** e **Format-Custom**.</span><span class="sxs-lookup"><span data-stu-id="22bca-107">The **Format** cmdlets are **Format-Wide**, **Format-List**, **Format-Table**, and **Format-Custom**.</span></span> <span data-ttu-id="22bca-108">Descreveremos apenas os cmdlets **Format-Wide**, **Format-List** e **Format-Table** neste guia do usuário.</span><span class="sxs-lookup"><span data-stu-id="22bca-108">We will only describe the **Format-Wide**, **Format-List**, and **Format-Table** cmdlets in this user's guide.</span></span>

<span data-ttu-id="22bca-109">Cada cmdlet de formato tem propriedades padrão que serão usadas se você não definir propriedades específicas a serem exibidas.</span><span class="sxs-lookup"><span data-stu-id="22bca-109">Each format cmdlet has default properties that will be used if you do not specify specific properties to display.</span></span> <span data-ttu-id="22bca-110">Cada cmdlet também usa o mesmo nome de parâmetro, **Property**, para especificar quais propriedades você deseja exibir.</span><span class="sxs-lookup"><span data-stu-id="22bca-110">Each cmdlet also uses the same parameter name, **Property**, to specify which properties you want to display.</span></span> <span data-ttu-id="22bca-111">Como **Format-Wide** mostra apenas uma única propriedade, seu parâmetro **Property** tem apenas um único valor, mas os parâmetros de propriedade de **Format-List** e **Format-Table** aceitarão uma lista de nomes de propriedade.</span><span class="sxs-lookup"><span data-stu-id="22bca-111">Because **Format-Wide** only shows a single property, its **Property** parameter only takes a single value, but the property parameters of **Format-List** and **Format-Table** will accept a list of property names.</span></span>

<span data-ttu-id="22bca-112">Usando o comando **Get-Process -Name powershell** com duas instâncias do Windows PowerShell em execução, você obterá uma saída parecida com esta:</span><span class="sxs-lookup"><span data-stu-id="22bca-112">If you use the command **Get-Process -Name powershell** with two instances of Windows PowerShell running, you get output that looks like this:</span></span>

```
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

<span data-ttu-id="22bca-113">No restante desta seção, exploraremos como usar cmdlets **Format** para alterar a maneira como a saída desse comando é exibida.</span><span class="sxs-lookup"><span data-stu-id="22bca-113">In the rest of this section, we will explore how to use **Format** cmdlets to change the way the output of this command is displayed.</span></span>

### <a name="using-format-wide-for-single-item-output"></a><span data-ttu-id="22bca-114">Usando Format-Wide para saída Single-Item</span><span class="sxs-lookup"><span data-stu-id="22bca-114">Using Format-Wide for Single-Item Output</span></span>
<span data-ttu-id="22bca-115">O cmdlet **Format-Wide**, por padrão, exibe apenas a propriedade padrão de um objeto.</span><span class="sxs-lookup"><span data-stu-id="22bca-115">The **Format-Wide** cmdlet, by default, displays only the default property of an object.</span></span> <span data-ttu-id="22bca-116">As informações associadas a cada objeto são exibidas em uma única coluna:</span><span class="sxs-lookup"><span data-stu-id="22bca-116">The information associated with each object is displayed in a single column:</span></span>

```
PS> Get-Process -Name powershell | Format-Wide

powershell                              powershell
```

<span data-ttu-id="22bca-117">Você também pode especificar uma propriedade não padrão:</span><span class="sxs-lookup"><span data-stu-id="22bca-117">You can also specify a non-default property:</span></span>

```
PS> Get-Process -Name powershell | Format-Wide -Property Id

2760                                    3448
```

#### <a name="controlling-format-wide-display-with-column"></a><span data-ttu-id="22bca-118">Controlando a exibição Format-Wide com Column</span><span class="sxs-lookup"><span data-stu-id="22bca-118">Controlling Format-Wide Display with Column</span></span>
<span data-ttu-id="22bca-119">Com o cmdlet **Format-Wide**, é possível exibir apenas uma única propriedade por vez.</span><span class="sxs-lookup"><span data-stu-id="22bca-119">With the **Format-Wide** cmdlet, you can only display a single property at a time.</span></span> <span data-ttu-id="22bca-120">Isso é útil para exibir listas simples que mostram apenas um elemento por linha.</span><span class="sxs-lookup"><span data-stu-id="22bca-120">This makes it useful for displaying simple lists that show only one element per line.</span></span> <span data-ttu-id="22bca-121">Para obter uma lista simples, defina o valor do parâmetro **Column** para 1 digitando:</span><span class="sxs-lookup"><span data-stu-id="22bca-121">To get a simple listing, set the value of the **Column** parameter to 1 by typing:</span></span>

```
Get-Command Format-Wide -Property Name -Column 1
```

### <a name="using-format-list-for-a-list-view"></a><span data-ttu-id="22bca-122">Usando Format-List para uma exibição de lista</span><span class="sxs-lookup"><span data-stu-id="22bca-122">Using Format-List for a List View</span></span>
<span data-ttu-id="22bca-123">O cmdlet **Format-List** exibe um objeto em forma de uma lista, com cada propriedade rotulada e exibida em uma linha separada:</span><span class="sxs-lookup"><span data-stu-id="22bca-123">The **Format-List** cmdlet displays an object in the form of a listing, with each property labeled and displayed on a separate line:</span></span>

```
PS> Get-Process -Name powershell | Format-List

Id      : 2760
Handles : 1242
CPU     : 3.03125
Name    : powershell

Id      : 3448
Handles : 328
CPU     : 1.0625
Name    : powershell
```

<span data-ttu-id="22bca-124">Você pode especificar quantas propriedades quiser:</span><span class="sxs-lookup"><span data-stu-id="22bca-124">You can specify as many properties as you want:</span></span>

```
PS> Get-Process -Name powershell | Format-List -Property ProcessName,FileVersion
,StartTime,Id

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:42:00
Id          : 2760

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:54:28
Id          : 3448
```

#### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a><span data-ttu-id="22bca-125">Obtendo informações detalhadas usando Format-List com curingas</span><span class="sxs-lookup"><span data-stu-id="22bca-125">Getting Detailed Information by Using Format-List with Wildcards</span></span>
<span data-ttu-id="22bca-126">O cmdlet **Format-List** permite usar um caractere curinga como o valor do seu parâmetro **Property**.</span><span class="sxs-lookup"><span data-stu-id="22bca-126">The **Format-List** cmdlet lets you use a wildcard as the value of its **Property** parameter.</span></span> <span data-ttu-id="22bca-127">Isso permite exibir informações detalhadas.</span><span class="sxs-lookup"><span data-stu-id="22bca-127">This lets you display detailed information.</span></span> <span data-ttu-id="22bca-128">Geralmente, os objetos incluem mais informações do que você precisa, por isso, o Windows PowerShell não mostra todos os valores de propriedade por padrão.</span><span class="sxs-lookup"><span data-stu-id="22bca-128">Often, objects include more information than you need, which is why Windows PowerShell does not show all property values by default.</span></span> <span data-ttu-id="22bca-129">Para mostrar todas as propriedades de um objeto, use o comando **Format-List -Property \&#42;**.</span><span class="sxs-lookup"><span data-stu-id="22bca-129">To show all of properties of an object, use the **Format-List -Property \&#42;** command.</span></span> <span data-ttu-id="22bca-130">O comando a seguir gera mais de 60 linhas de saída para um único processo:</span><span class="sxs-lookup"><span data-stu-id="22bca-130">The following command generates over 60 lines of output for a single process:</span></span>

```
Get-Process -Name powershell | Format-List -Property *
```

<span data-ttu-id="22bca-131">Embora o comando **Format-List** seja útil para mostrar os detalhes, se você quiser obter uma visão geral de saída que inclui muitos itens, uma exibição tabular simples geralmente será mais útil.</span><span class="sxs-lookup"><span data-stu-id="22bca-131">Although the **Format-List** command is useful for showing detail, if you want an overview of output that includes many items, a simpler tabular view is often more useful.</span></span>

### <a name="using-format-table-for-tabular-output"></a><span data-ttu-id="22bca-132">Usando Format-Table para saída tabular</span><span class="sxs-lookup"><span data-stu-id="22bca-132">Using Format-Table for Tabular Output</span></span>
<span data-ttu-id="22bca-133">Caso use o cmdlet **Format-Table** sem nenhum nome de propriedade especificado para formatar a saída do comando **Get-Process**, você obterá exatamente a mesma saída que receberia sem executar qualquer formatação de saída.</span><span class="sxs-lookup"><span data-stu-id="22bca-133">If you use the **Format-Table** cmdlet with no property names specified to format the output of the **Get-Process** command, you get exactly the same output as you do without performing any formatting.</span></span> <span data-ttu-id="22bca-134">O motivo disso é que os processos normalmente são exibidos em um formato tabular, assim como a maioria dos objetos do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22bca-134">The reason is that processes are usually displayed in a tabular format, as are most Windows PowerShell objects.</span></span>

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

#### <a name="improving-format-table-output-autosize"></a><span data-ttu-id="22bca-135">Melhorando a saída do Format-Table (AutoSize)</span><span class="sxs-lookup"><span data-stu-id="22bca-135">Improving Format-Table Output (AutoSize)</span></span>
<span data-ttu-id="22bca-136">Embora uma exibição tabular seja útil para exibir muitas informações comparáveis, ela poderá ser difícil de interpretar se a exibição for muito estreita para os dados.</span><span class="sxs-lookup"><span data-stu-id="22bca-136">Although a tabular view is useful for displaying a lot of comparable information, it may be difficult to interpret if the display is too narrow for the data.</span></span> <span data-ttu-id="22bca-137">Por exemplo, se você tentar exibir o caminho do processo, ID, nome e empresa, você receberá uma saída truncada para o caminho do processo e a coluna da empresa:</span><span class="sxs-lookup"><span data-stu-id="22bca-137">For example, if you try to display process path, ID, name, and company, you get truncated output for the process path and the company column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

<span data-ttu-id="22bca-138">Se você especificar o parâmetro **AutoSize** ao executar o comando **Format-Table**, o Windows PowerShell calculará as larguras das colunas com base nos dados reais que serão exibidos.</span><span class="sxs-lookup"><span data-stu-id="22bca-138">If you specify the **AutoSize** parameter when you run the **Format-Table** command, Windows PowerShell will calculate column widths based on the actual data you are going to display.</span></span> <span data-ttu-id="22bca-139">Isso torna a coluna **Path** legível, mas a coluna de empresa permanece truncada:</span><span class="sxs-lookup"><span data-stu-id="22bca-139">This makes the **Path** column readable, but the company column remains truncated:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

<span data-ttu-id="22bca-140">O cmdlet **Format-Table** ainda pode truncar os dados, mas ele só fará isso no fim da tela.</span><span class="sxs-lookup"><span data-stu-id="22bca-140">The **Format-Table** cmdlet might still truncate data, but it will only do so at the end of the screen.</span></span> <span data-ttu-id="22bca-141">Propriedades, além da última exibida, recebem o tamanho correspondente ao que precisam para seu elemento de dados mais longo ser exibido corretamente.</span><span class="sxs-lookup"><span data-stu-id="22bca-141">Properties, other than the last one displayed, are given as much size as they need for their longest data element to display correctly.</span></span> <span data-ttu-id="22bca-142">Você pode ver que o nome da empresa estará visível e o caminho ficará truncado se você trocar os locais de **Path** e **Company** na lista de valores **Property**:</span><span class="sxs-lookup"><span data-stu-id="22bca-142">You can see that company name is visible but path is truncated if you swap the locations of **Path** and **Company** in the **Property** value list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

<span data-ttu-id="22bca-143">O comando **Format-Table** supõe que quanto mais próxima uma propriedade estiver do início da lista de propriedades, mais importante ela será.</span><span class="sxs-lookup"><span data-stu-id="22bca-143">The **Format-Table** command assumes that the nearer a property is to the beginning of the property list, the more important it is.</span></span> <span data-ttu-id="22bca-144">Portanto, ele tenta exibir as propriedades mais próximo ao início completamente.</span><span class="sxs-lookup"><span data-stu-id="22bca-144">So it attempts to display the properties nearest the beginning completely.</span></span> <span data-ttu-id="22bca-145">Se o comando **Format-Table** não conseguir exibir todas as propriedades, ele removerá algumas colunas da exibição e fornecerá um aviso.</span><span class="sxs-lookup"><span data-stu-id="22bca-145">If the **Format-Table** command cannot display all the properties, it will remove some columns from the display and provide a warning.</span></span> <span data-ttu-id="22bca-146">Você pode ver esse comportamento se colocar a propriedade **Name** por último na lista:</span><span class="sxs-lookup"><span data-stu-id="22bca-146">You can see this behavior if you make **Name** the last property in the list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

<span data-ttu-id="22bca-147">Na saída acima, a coluna ID é truncada para ajustá-la para a listagem e os cabeçalhos de coluna são empilhados.</span><span class="sxs-lookup"><span data-stu-id="22bca-147">In the output above, the ID column is truncated to make it fit into the listing, and the column headings are stacked up.</span></span> <span data-ttu-id="22bca-148">Redimensionar automaticamente as colunas nem sempre produz o resultado desejado.</span><span class="sxs-lookup"><span data-stu-id="22bca-148">Automatically resizing the columns does not always do what you want.</span></span>

#### <a name="wrapping-format-table-output-in-columns-wrap"></a><span data-ttu-id="22bca-149">Quebra automática de linha na saída de Format-Table em colunas (Wrap)</span><span class="sxs-lookup"><span data-stu-id="22bca-149">Wrapping Format-Table Output in Columns (Wrap)</span></span>
<span data-ttu-id="22bca-150">Você pode forçar dados do **Format-Table** longos a serem exibidos com encapsulamento em sua coluna de exibição usando o parâmetro **Wrap**.</span><span class="sxs-lookup"><span data-stu-id="22bca-150">You can force lengthy **Format-Table** data to wrap within its display column by using the **Wrap** parameter.</span></span> <span data-ttu-id="22bca-151">Usar o parâmetro **Wrap** sozinho não necessariamente fará o que você espera, já que ele usará as configurações padrão se você não especificar **AutoSize**:</span><span class="sxs-lookup"><span data-stu-id="22bca-151">Using the **Wrap** parameter alone will not necessarily do what you expect, since it uses default settings if you do not also specify **AutoSize**:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

<span data-ttu-id="22bca-152">Uma vantagem de usar o parâmetro **Wrap** sozinho é que ele não retarda muito o processamento.</span><span class="sxs-lookup"><span data-stu-id="22bca-152">An advantage of using the **Wrap** parameter by itself is that it does not slow down processing very much.</span></span> <span data-ttu-id="22bca-153">Se você realizar uma listagem recursiva dos arquivos de um sistema de diretório, isso poderá levar muito tempo e usar muita memória antes de exibir os primeiros itens de saída se você usar **AutoSize**.</span><span class="sxs-lookup"><span data-stu-id="22bca-153">If you perform a recursive file listing of a large directory system, it might take a very long time and use a lot of memory before displaying the first output items if you use **AutoSize**.</span></span>

<span data-ttu-id="22bca-154">Se você não estiver preocupado com a carga do sistema, **AutoSize** funcionará bem com o parâmetro **Wrap**.</span><span class="sxs-lookup"><span data-stu-id="22bca-154">If you are not concerned about system load, then **AutoSize** works well with the **Wrap** parameter.</span></span> <span data-ttu-id="22bca-155">As colunas iniciais sempre são alocadas com o máximo de largura necessário para exibir os itens em uma linha, da mesma forma que ao especificar **AutoSize** sem o parâmetro **Wrap**.</span><span class="sxs-lookup"><span data-stu-id="22bca-155">The initial columns are always allotted as much width as they need to display items on one line, just as when you specify **AutoSize** without the **Wrap** parameter.</span></span> <span data-ttu-id="22bca-156">A única diferença é que a coluna final terá quebra de linha se necessário:</span><span class="sxs-lookup"><span data-stu-id="22bca-156">The only difference is that the final column will be wrapped if necessary:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

<span data-ttu-id="22bca-157">Algumas colunas poderão não ser exibidas se você especificar as colunas mais amplas primeiro, portanto, é mais seguro especificar os elementos com menos dados primeiro.</span><span class="sxs-lookup"><span data-stu-id="22bca-157">Some columns might not be displayed if you specify the widest columns first, so it is safest to specify the smallest data elements first.</span></span> <span data-ttu-id="22bca-158">No exemplo a seguir, especificamos o elemento de caminho do elemento extremamente amplo primeiro e, até mesmo com quebra automática, ainda perdemos a coluna final **Name**:</span><span class="sxs-lookup"><span data-stu-id="22bca-158">In the following example, we specify the extremely wide path element first, and even with wrapping, we still lose the final **Name** column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

#### <a name="organizing-table-output--groupby"></a><span data-ttu-id="22bca-159">Organizando a saída da tabela (-GroupBy)</span><span class="sxs-lookup"><span data-stu-id="22bca-159">Organizing Table Output (-GroupBy)</span></span>
<span data-ttu-id="22bca-160">Outro parâmetro útil para controlar a saída tabular é **GroupBy**.</span><span class="sxs-lookup"><span data-stu-id="22bca-160">Another useful parameter for tabular output control is **GroupBy**.</span></span> <span data-ttu-id="22bca-161">Listagens de tabela mais longas podem ser especialmente difíceis de comparar.</span><span class="sxs-lookup"><span data-stu-id="22bca-161">Longer tabular listings in particular may be hard to compare.</span></span> <span data-ttu-id="22bca-162">O parâmetro **GroupBy** agrupa a saída com base em um valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="22bca-162">The **GroupBy** parameter groups output based on a property value.</span></span> <span data-ttu-id="22bca-163">Por exemplo, é possível agrupar processos pela empresa para inspeção mais fácil, omitindo o valor da empresa na lista de propriedade:</span><span class="sxs-lookup"><span data-stu-id="22bca-163">For example, we can group processes by company for easier inspection, omitting the company value from the property listing:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```

