---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Redirecionamento de dados com cmdlets Out
ms.assetid: 2a4acd33-041d-43a5-a3e9-9608a4c52b0c
ms.openlocfilehash: f08879f436ce751b176af020aba21e90f09aa61f
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52321002"
---
# <a name="redirecting-data-with-out--cmdlets"></a><span data-ttu-id="05486-103">Redirecionamento de dados com cmdlets Out-\*</span><span class="sxs-lookup"><span data-stu-id="05486-103">Redirecting Data with Out-\* Cmdlets</span></span>

<span data-ttu-id="05486-104">O Windows PowerShell oferece vários cmdlets que permitem controlar os dados de saída diretamente.</span><span class="sxs-lookup"><span data-stu-id="05486-104">Windows PowerShell provides several cmdlets that let you control data output directly.</span></span> <span data-ttu-id="05486-105">Esses cmdlets compartilham duas importantes características.</span><span class="sxs-lookup"><span data-stu-id="05486-105">These cmdlets share two important characteristics.</span></span>

<span data-ttu-id="05486-106">Primeiramente, eles geralmente transformam dados em alguma forma de texto.</span><span class="sxs-lookup"><span data-stu-id="05486-106">First, they generally transform data to some form of text.</span></span> <span data-ttu-id="05486-107">Eles fazem isso porque geram saída de dados para os componentes do sistema que exigem entrada de texto.</span><span class="sxs-lookup"><span data-stu-id="05486-107">They do this because they output the data to system components that require text input.</span></span> <span data-ttu-id="05486-108">Isso significa que eles precisam para representar os objetos como texto.</span><span class="sxs-lookup"><span data-stu-id="05486-108">This means they need to represent the objects as text.</span></span> <span data-ttu-id="05486-109">Portanto, o texto é formatado como visto na janela do console do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="05486-109">Therefore, the text is formatted as you see it in the Windows PowerShell console window.</span></span>

<span data-ttu-id="05486-110">Em segundo lugar, esses cmdlets usam o verbo do Windows PowerShell **Out** porque eles enviam informações do Windows PowerShell para outro lugar.</span><span class="sxs-lookup"><span data-stu-id="05486-110">Second, these cmdlets use the Windows PowerShell verb **Out** because they send information out from Windows PowerShell to somewhere else.</span></span> <span data-ttu-id="05486-111">O cmdlet **Out-Host** não é uma exceção: a exibição da janela do host está fora do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="05486-111">The **Out-Host** cmdlet is no exception: the host window display is outside of Windows PowerShell.</span></span> <span data-ttu-id="05486-112">Isso é importante porque, quando os dados são enviados do Windows PowerShell, eles realmente são removidos.</span><span class="sxs-lookup"><span data-stu-id="05486-112">This is important because when data is sent out of Windows PowerShell, it is actually removed.</span></span> <span data-ttu-id="05486-113">Você poderá ver isso se tentar criar um pipeline de dados que realiza a paginação de dados para a janela do host e, em seguida, tentar formatá-los como uma lista, conforme mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="05486-113">You can see this if you try to create a pipeline that pages data to the host window, and then attempt to format it as a list, as shown here:</span></span>

```powershell
Get-Process | Out-Host -Paging | Format-List
```

<span data-ttu-id="05486-114">Você pode esperar que o comando exiba páginas de informações do processo em formato de lista.</span><span class="sxs-lookup"><span data-stu-id="05486-114">You might expect the command to display pages of process information in list format.</span></span> <span data-ttu-id="05486-115">Em vez disso, ele exibe a lista tabular padrão:</span><span class="sxs-lookup"><span data-stu-id="05486-115">Instead, it displays the default tabular list:</span></span>

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    101       5     1076       3316    32     0.05   2888 alg
...
    618      18    39348      51108   143   211.20    740 explorer
    257       8     9752      16828    79     3.02   2560 explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="05486-116">O cmdlet **Out-Host** envia os dados diretamente para o console, por isso o comando **Format-List** nunca recebe nada para formatar.</span><span class="sxs-lookup"><span data-stu-id="05486-116">The **Out-Host** cmdlet sends the data directly to the console, so the **Format-List** command never receives anything to format.</span></span>

<span data-ttu-id="05486-117">A maneira correta de estruturar esse comando é colocar o cmdlet **Out-Host** no final do pipeline, conforme mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="05486-117">The correct way to structure this command is to put the **Out-Host** cmdlet at the end of the pipeline as shown below.</span></span> <span data-ttu-id="05486-118">Isso faz com que os dados do processo sejam formatados em uma lista antes de serem paginados e exibidos.</span><span class="sxs-lookup"><span data-stu-id="05486-118">This causes the process data to be formatted in a list before being paged and displayed.</span></span>

```
PS> Get-Process | Format-List | Out-Host -Paging

Id      : 2888
Handles : 101
CPU     : 0.046875
Name    : alg
...

Id      : 740
Handles : 612
CPU     : 211.703125
Name    : explorer

Id      : 2560
Handles : 257
CPU     : 3.015625
Name    : explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="05486-119">Isso se aplica a todos os cmdlets **Out**.</span><span class="sxs-lookup"><span data-stu-id="05486-119">This applies to all of the **Out** cmdlets.</span></span> <span data-ttu-id="05486-120">Um cmdlet **Out** sempre deve aparecer no final do pipeline.</span><span class="sxs-lookup"><span data-stu-id="05486-120">An **Out** cmdlet should always appear at the end of the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="05486-121">Todos os cmdlets **Out** renderizam a saída como texto, usando a formatação em vigor para a janela de console, incluindo os limites de tamanho da linha.</span><span class="sxs-lookup"><span data-stu-id="05486-121">All the **Out** cmdlets render output as text, using the formatting in effect for the console window, including line length limits.</span></span>

#### <a name="paging-console-output-out-host"></a><span data-ttu-id="05486-122">Paginando a saída do console (Out-Host)</span><span class="sxs-lookup"><span data-stu-id="05486-122">Paging Console Output (Out-Host)</span></span>

<span data-ttu-id="05486-123">Por padrão, o Windows PowerShell envia dados para a janela do host, que é exatamente o que o cmdlet Out-Host faz.</span><span class="sxs-lookup"><span data-stu-id="05486-123">By default, Windows PowerShell sends data to the host window, which is exactly what the Out-Host cmdlet does.</span></span> <span data-ttu-id="05486-124">O principal uso do cmdlet Out-Host é paginar os dados conforme abordado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="05486-124">The primary use for the Out-Host cmdlet is paging data as we discussed earlier.</span></span> <span data-ttu-id="05486-125">Por exemplo, o comando a seguir usa Out-Host para paginar a saída do cmdlet Get-Command:</span><span class="sxs-lookup"><span data-stu-id="05486-125">For example, the following command uses Out-Host to page the output of the Get-Command cmdlet:</span></span>

```powershell
Get-Command | Out-Host -Paging
```

<span data-ttu-id="05486-126">Você também pode usar a função **more** para paginar os dados.</span><span class="sxs-lookup"><span data-stu-id="05486-126">You can also use the **more** function to page data.</span></span> <span data-ttu-id="05486-127">No Windows PowerShell, **more** é uma função que chama **Out-Host -Paging**.</span><span class="sxs-lookup"><span data-stu-id="05486-127">In Windows PowerShell, **more** is a function that calls **Out-Host -Paging**.</span></span> <span data-ttu-id="05486-128">O comando a seguir demonstra como usar a função **more** para paginar a saída de Get-Command:</span><span class="sxs-lookup"><span data-stu-id="05486-128">The following command demonstrates using the **more** function to page the output of Get-Command:</span></span>

```powershell
Get-Command | more
```

<span data-ttu-id="05486-129">Se você incluir um ou mais nomes de arquivo como argumentos para a função more, ela lerá os arquivos especificados e paginará o conteúdo para o host:</span><span class="sxs-lookup"><span data-stu-id="05486-129">If you include one or more filenames as arguments to the more function, the function will read the specified files and page their contents to the host:</span></span>

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

#### <a name="discarding-output-out-null"></a><span data-ttu-id="05486-130">Descartando a saída (Out-Null)</span><span class="sxs-lookup"><span data-stu-id="05486-130">Discarding Output (Out-Null)</span></span>

<span data-ttu-id="05486-131">O cmdlet **Out-Null** é projetado para descartar imediatamente qualquer entrada que receber.</span><span class="sxs-lookup"><span data-stu-id="05486-131">The **Out-Null** cmdlet is designed to immediately discard any input it receives.</span></span> <span data-ttu-id="05486-132">Isso é útil para descartar dados desnecessários obtidos como efeito colateral da execução de um comando.</span><span class="sxs-lookup"><span data-stu-id="05486-132">This is useful for discarding unnecessary data that you get as a side-effect of running a command.</span></span> <span data-ttu-id="05486-133">Ao digitar o comando a seguir, você não receberá nenhuma saída dele:</span><span class="sxs-lookup"><span data-stu-id="05486-133">When type the following command, you do not get anything back from the command:</span></span>

```powershell
Get-Command | Out-Null
```

<span data-ttu-id="05486-134">O cmdlet **Out-Null** não descarta a saída de erro.</span><span class="sxs-lookup"><span data-stu-id="05486-134">The **Out-Null** cmdlet does not discard error output.</span></span> <span data-ttu-id="05486-135">Por exemplo, se você digitar o comando a seguir, uma mensagem será exibida informando que o Windows PowerShell não reconhece 'Is -NotACommand':</span><span class="sxs-lookup"><span data-stu-id="05486-135">For example, if you enter the following command, a message is displayed informing you that Windows PowerShell does not recognize 'Is-NotACommand':</span></span>

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

#### <a name="printing-data-out-printer"></a><span data-ttu-id="05486-136">Imprimindo dados (Out-Printer)</span><span class="sxs-lookup"><span data-stu-id="05486-136">Printing Data (Out-Printer)</span></span>

<span data-ttu-id="05486-137">Você pode imprimir dados usando o cmdlet **Out-Printer**.</span><span class="sxs-lookup"><span data-stu-id="05486-137">You can print data by using the **Out-Printer** cmdlet.</span></span> <span data-ttu-id="05486-138">O cmdlet **Out-Printer** usará sua impressora padrão se você não fornecer um nome de impressora.</span><span class="sxs-lookup"><span data-stu-id="05486-138">The **Out-Printer** cmdlet will use your default printer if you do not provide a printer name.</span></span> <span data-ttu-id="05486-139">Você pode usar qualquer impressora baseada em Windows especificando seu nome de exibição.</span><span class="sxs-lookup"><span data-stu-id="05486-139">You can use any Windows-based printer by specifying its display name.</span></span> <span data-ttu-id="05486-140">Não é necessário nenhum tipo de mapeamento de porta de impressora nem mesmo uma impressora física real.</span><span class="sxs-lookup"><span data-stu-id="05486-140">There is no need for any kind of printer port mapping or even a real physical printer.</span></span> <span data-ttu-id="05486-141">Por exemplo, se você tiver as ferramentas de geração de imagens de documento do Microsoft Office instaladas, poderá enviar os dados para um arquivo de imagem digitando:</span><span class="sxs-lookup"><span data-stu-id="05486-141">For example, if you have the Microsoft Office document imaging tools installed, you can send the data to an image file by typing:</span></span>

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

#### <a name="saving-data-out-file"></a><span data-ttu-id="05486-142">Salvando dados (Out-File)</span><span class="sxs-lookup"><span data-stu-id="05486-142">Saving Data (Out-File)</span></span>

<span data-ttu-id="05486-143">Você pode enviar a saída para um arquivo em vez da janela de console usando o cmdlet **Out-File**.</span><span class="sxs-lookup"><span data-stu-id="05486-143">You can send output to a file instead of the console window by using the **Out-File** cmdlet.</span></span> <span data-ttu-id="05486-144">A linha de comando a seguir envia uma lista de processos para o arquivo **C:\\temp\\processlist.txt**:</span><span class="sxs-lookup"><span data-stu-id="05486-144">The following command line sends a list of processes to the file **C:\\temp\\processlist.txt**:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

<span data-ttu-id="05486-145">Os resultados do uso do cmdlet **Out-File** poderão não ser o esperado se você estiver acostumado com o redirecionamento de saída tradicional.</span><span class="sxs-lookup"><span data-stu-id="05486-145">The results of using the **Out-File** cmdlet may not be what you expect if you are used to traditional output redirection.</span></span> <span data-ttu-id="05486-146">Para entender seu comportamento, você deve estar ciente do contexto no qual o cmdlet **Out-File** opera.</span><span class="sxs-lookup"><span data-stu-id="05486-146">To understand its behavior, you must be aware of the context in which the **Out-File** cmdlet operates.</span></span>

<span data-ttu-id="05486-147">Por padrão, o cmdlet **Out-File** cria um arquivo Unicode.</span><span class="sxs-lookup"><span data-stu-id="05486-147">By default, the **Out-File** cmdlet creates a Unicode file.</span></span> <span data-ttu-id="05486-148">Esse é o melhor padrão a longo prazo, porém significa que ferramentas que esperam arquivos ASCII não funcionarão corretamente com o formato de saída padrão.</span><span class="sxs-lookup"><span data-stu-id="05486-148">This is the best default in the long run, but it means that tools that expect ASCII files will not work correctly with the default output format.</span></span> <span data-ttu-id="05486-149">Você pode alterar o formato de saída padrão para ASCII usando o parâmetro **Encoding**:</span><span class="sxs-lookup"><span data-stu-id="05486-149">You can change the default output format to ASCII by using the **Encoding** parameter:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

<span data-ttu-id="05486-150">**Out-File** formata o conteúdo do arquivo para se parecer com a saída do console.</span><span class="sxs-lookup"><span data-stu-id="05486-150">**Out-file** formats file contents to look like console output.</span></span> <span data-ttu-id="05486-151">Isso faz com que a saída seja truncada da mesma forma que na janela do console na maioria das circunstâncias.</span><span class="sxs-lookup"><span data-stu-id="05486-151">This causes the output to be truncated just as it is in a console window in most circumstances.</span></span> <span data-ttu-id="05486-152">Por exemplo, se você executar o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="05486-152">For example, if you run the following command:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

<span data-ttu-id="05486-153">A saída será assim:</span><span class="sxs-lookup"><span data-stu-id="05486-153">The output will look like this:</span></span>

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

<span data-ttu-id="05486-154">Para obter uma saída que não força quebras de linha para corresponder à largura da tela, você pode usar o parâmetro **Width** para especificar a largura da linha.</span><span class="sxs-lookup"><span data-stu-id="05486-154">To get output that does not force line wraps to match the screen width, you can use the **Width** parameter to specify line width.</span></span> <span data-ttu-id="05486-155">Como a **Width** é um parâmetro de número inteiro de 32 bits, o valor máximo que ele pode ter é 2147483647.</span><span class="sxs-lookup"><span data-stu-id="05486-155">Because **Width** is a 32-bit integer parameter, the maximum value it can have is 2147483647.</span></span> <span data-ttu-id="05486-156">Digite o seguinte para definir a largura da linha para esse valor máximo:</span><span class="sxs-lookup"><span data-stu-id="05486-156">Type the following to set the line width to this maximum value:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

<span data-ttu-id="05486-157">O cmdlet **Out-File** é mais útil quando você deseja salvar a saída da mesma forma que ela seria exibida no console.</span><span class="sxs-lookup"><span data-stu-id="05486-157">The **Out-File** cmdlet is most useful when you want to save output as it would have displayed on the console.</span></span> <span data-ttu-id="05486-158">Para ter maior controle sobre o formato de saída, você precisa de ferramentas mais avançadas.</span><span class="sxs-lookup"><span data-stu-id="05486-158">For finer control over output format, you need more advanced tools.</span></span> <span data-ttu-id="05486-159">Elas serão abordadas no próximo capítulo, juntamente com alguns detalhes sobre a manipulação de objetos.</span><span class="sxs-lookup"><span data-stu-id="05486-159">We will look at those in the next chapter, along with some details about object manipulation.</span></span>