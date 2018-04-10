---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
title: Correções de Bug no WMF 5.1
ms.openlocfilehash: dfd9ead447edfe9b7bdae23be14785df4b182bbc
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="bug-fixes-in-wmf-51"></a><span data-ttu-id="10e0d-103">Correções de bug no WMF 5.1#</span><span class="sxs-lookup"><span data-stu-id="10e0d-103">Bug Fixes in WMF 5.1#</span></span>

## <a name="bug-fixes"></a><span data-ttu-id="10e0d-104">Correções de bug</span><span class="sxs-lookup"><span data-stu-id="10e0d-104">Bug fixes</span></span> ##

<span data-ttu-id="10e0d-105">Os seguintes bugs importantes foram corrigidos no WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="10e0d-105">The following notable bugs are fixed in WMF 5.1:</span></span>

### <a name="module-auto-discovery-fully-honors-envpsmodulepath"></a><span data-ttu-id="10e0d-106">A descoberta automática do módulo honra totalmente `$env:PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="10e0d-106">Module auto-discovery fully honors `$env:PSModulePath`</span></span> ###

<span data-ttu-id="10e0d-107">A descoberta automática do módulo (carregando módulos automaticamente sem um Import-Module explícito ao chamar um comando) foi introduzida no WMF 3.</span><span class="sxs-lookup"><span data-stu-id="10e0d-107">Module auto-discovery (loading modules automatically without an explicit Import-Module when calling a command) was introduced in WMF 3.</span></span>
<span data-ttu-id="10e0d-108">Quando introduzido, o PowerShell verificava comandos no `$PSHome\Modules` antes de usar `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="10e0d-108">When introduced, PowerShell checked for commands in `$PSHome\Modules` before using `$env:PSModulePath`.</span></span>

<span data-ttu-id="10e0d-109">O WMF 5.1 altera esse comportamento para honrar `$env:PSModulePath` completamente.</span><span class="sxs-lookup"><span data-stu-id="10e0d-109">WMF 5.1 changes this behavior to honor `$env:PSModulePath` completely.</span></span>
<span data-ttu-id="10e0d-110">Isso permite que um módulo de autoria do usuário que define comandos fornecidos pelo PowerShell (por exemplo, `Get-ChildItem`) seja carregado automaticamente, substituindo corretamente o comando interno.</span><span class="sxs-lookup"><span data-stu-id="10e0d-110">This allows for a user-authored module that defines commands provided by PowerShell (e.g. `Get-ChildItem`) to be auto-loaded and correctly overriding the built-in command.</span></span>

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a><span data-ttu-id="10e0d-111">Redirecionamento de arquivos não embute mais `-Encoding Unicode`</span><span class="sxs-lookup"><span data-stu-id="10e0d-111">File redirection no longer hard-codes `-Encoding Unicode`</span></span> ###

<span data-ttu-id="10e0d-112">Em versões anteriores do PowerShell, era impossível controlar a codificação do arquivo usada pelo operador de redirecionamento de arquivo, por exemplo, `Get-ChildItem > out.txt`, porque o PowerShell adicionava `-Encoding Unicode`.</span><span class="sxs-lookup"><span data-stu-id="10e0d-112">In all previous versions of PowerShell, it was impossible to control the file encoding used by the file redirection operator, e.g. `Get-ChildItem > out.txt` because PowerShell added `-Encoding Unicode`.</span></span>

<span data-ttu-id="10e0d-113">Do WMF 5.1 em diante, agora é possível alterar a codificação do arquivo de redirecionamento configurando `$PSDefaultParameterValues`:</span><span class="sxs-lookup"><span data-stu-id="10e0d-113">Starting with WMF 5.1, you can now change the file encoding of redirection by setting `$PSDefaultParameterValues`:</span></span>

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a><span data-ttu-id="10e0d-114">Corrigida uma regressão no acesso a membros do `System.Reflection.TypeInfo`</span><span class="sxs-lookup"><span data-stu-id="10e0d-114">Fixed a regression in accessing members of `System.Reflection.TypeInfo`</span></span> ###

<span data-ttu-id="10e0d-115">Uma regressão introduzida no WMF 5.0 se rompeu ao acessar membros de `System.Reflection.RuntimeType`, por exemplo, `[int].ImplementedInterfaces`.</span><span class="sxs-lookup"><span data-stu-id="10e0d-115">A regression introduced in WMF 5.0 broke accessing members of `System.Reflection.RuntimeType`, e.g. `[int].ImplementedInterfaces`.</span></span>
<span data-ttu-id="10e0d-116">Esse bug foi corrigido no WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="10e0d-116">This bug has been fixed in WMF 5.1.</span></span>


### <a name="fixed-some-issues-with-com-objects"></a><span data-ttu-id="10e0d-117">Corrigidos alguns problemas com objetos COM</span><span class="sxs-lookup"><span data-stu-id="10e0d-117">Fixed some issues with COM objects</span></span> ###

<span data-ttu-id="10e0d-118">O WMF 5.0 introduziu um novo associador de COM para chamar métodos em objetos COM e o acesso às propriedades de objetos COM.</span><span class="sxs-lookup"><span data-stu-id="10e0d-118">WMF 5.0 introduced a new COM binder for invoking methods on COM objects and accessing properties of COM objects.</span></span>
<span data-ttu-id="10e0d-119">Esse novo associador melhorou consideravelmente o desempenho, mas também introduziu alguns bugs que foram corrigidos no WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="10e0d-119">This new binder improved performance significantly but also introduced some bugs which have been fixed in WMF 5.1.</span></span>

#### <a name="argument-conversions-were-not-always-performed-correctly"></a><span data-ttu-id="10e0d-120">Conversões de argumento não eram sempre executadas corretamente</span><span class="sxs-lookup"><span data-stu-id="10e0d-120">Argument conversions were not always performed correctly</span></span> ####

<span data-ttu-id="10e0d-121">No exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="10e0d-121">In the following example:</span></span>

```
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

<span data-ttu-id="10e0d-122">O método SendKeys espera uma cadeia de caracteres, mas o PowerShell não converteu o caractere para uma cadeia de caracteres, adiando a conversão para IDispatch::Invoke, que usa VariantChangeType para fazer a conversão, que, neste exemplo, resultou em enviar as chaves “1”, “7” e “3”, em vez da chave Volume.Mute esperada.</span><span class="sxs-lookup"><span data-stu-id="10e0d-122">The SendKeys method expects a string, but PowerShell did not convert the char to a string, deferring the conversion to IDispatch::Invoke, which uses VariantChangeType to do the conversion, which in this example resulted in sending the keys '1', '7', and '3' instead of the expected Volume.Mute key.</span></span>

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a><span data-ttu-id="10e0d-123">Objetos COM enumeráveis nem sempre eram tratados corretamente</span><span class="sxs-lookup"><span data-stu-id="10e0d-123">Enumerable COM objects not always handled correctly</span></span> ####

<span data-ttu-id="10e0d-124">O PowerShell normalmente enumera a maioria dos objetos enumeráveis, mas uma regressão introduzida no WMF 5.0 impedia a enumeração de objetos COM que implementam IEnumerable.</span><span class="sxs-lookup"><span data-stu-id="10e0d-124">PowerShell normally enumerates most enumerable objects, but a regression introduced in WMF 5.0 prevented the enumeration of COM objects that implement IEnumerable.</span></span>  <span data-ttu-id="10e0d-125">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="10e0d-125">For example:</span></span>

```
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

<span data-ttu-id="10e0d-126">No exemplo acima, o WMF 5.0 gravou incorretamente Scripting.Dictionary no pipeline, em vez de enumerar os pares chave-valor.</span><span class="sxs-lookup"><span data-stu-id="10e0d-126">In the above example, WMF 5.0 incorrectly wrote the Scripting.Dictionary to the pipeline instead of enumerating the key/value pairs.</span></span>

<span data-ttu-id="10e0d-127">Esta alteração também aborda o [problema 1752224 no Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)</span><span class="sxs-lookup"><span data-stu-id="10e0d-127">This change also addresses [issue 1752224 on Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)</span></span>

### <a name="ordered-was-not-allowed-inside-classes"></a><span data-ttu-id="10e0d-128">`[ordered]` não era permitido dentro de classes</span><span class="sxs-lookup"><span data-stu-id="10e0d-128">`[ordered]` was not allowed inside classes</span></span> ###

<span data-ttu-id="10e0d-129">O WMF 5.0 introduziu classes com validação de literais de tipo usados em classes.</span><span class="sxs-lookup"><span data-stu-id="10e0d-129">WMF 5.0 introduced classes with validation of type literals used in classes.</span></span>
<span data-ttu-id="10e0d-130">`[ordered]` parece um literal de tipo, mas não é um tipo .NET verdadeiro.</span><span class="sxs-lookup"><span data-stu-id="10e0d-130">`[ordered]` looks like a type literal but is not a true .NET type.</span></span>
<span data-ttu-id="10e0d-131">O WMF 5.0 relatou incorretamente um erro no `[ordered]` dentro de uma classe:</span><span class="sxs-lookup"><span data-stu-id="10e0d-131">WMF 5.0 incorrectly reported an error on `[ordered]` inside a class:</span></span>

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a><span data-ttu-id="10e0d-132">A ajuda em tópicos “Sobre” com várias versões não funciona</span><span class="sxs-lookup"><span data-stu-id="10e0d-132">Help on About topics with multiple versions does not work</span></span> ###

<span data-ttu-id="10e0d-133">Antes do WMF 5.1, se houvesse várias versões de um módulo instaladas e elas compartilhassem um tópico de ajuda, por exemplo, about_PSReadline, `help about_PSReadline` retornaria vários tópicos sem uma maneira óbvia de exibir a ajuda real.</span><span class="sxs-lookup"><span data-stu-id="10e0d-133">Before WMF 5.1, if you had multiple versions of a module installed and they all shared a help topic, for example, about_PSReadline, `help about_PSReadline` would return multiple topics with no obvious way to view the real help.</span></span>

<span data-ttu-id="10e0d-134">O WMF 5.1 corrige isso retornando a ajuda para a versão mais recente do tópico.</span><span class="sxs-lookup"><span data-stu-id="10e0d-134">WMF 5.1 fixes this by returning the help for the latest version of the topic.</span></span>

<span data-ttu-id="10e0d-135">`Get-Help` não oferece uma maneira de especificar para qual versão você quer obter ajuda.</span><span class="sxs-lookup"><span data-stu-id="10e0d-135">`Get-Help` does not provide a way to specify which version you want help for.</span></span>
<span data-ttu-id="10e0d-136">Para solucionar esse problema, navegue até o diretório de módulos e exibir a ajuda diretamente com uma ferramenta como seu editor favorito.</span><span class="sxs-lookup"><span data-stu-id="10e0d-136">To work around this, navigate to the modules directory and view the help directly with a tool like your favorite editor.</span></span>

### <a name="powershellexe-reading-from-stdin-stopped-working"></a><span data-ttu-id="10e0d-137">A leitura do powershell.exe do STDIN parou de funcionar</span><span class="sxs-lookup"><span data-stu-id="10e0d-137">powershell.exe reading from STDIN stopped working</span></span>

<span data-ttu-id="10e0d-138">Os clientes usam o `powershell -command -` de aplicativos nativos para executar o PowerShell passando o script por meio do STDIN, mas infelizmente isso não está funcionando devido a outras alterações no host do console.</span><span class="sxs-lookup"><span data-stu-id="10e0d-138">Customers use `powershell -command -` from native apps to execute PowerShell passing in the script via STDIN unfortunately this was broken due to other changes it the console host.</span></span>

https://windowsserver.uservoice.com/forums/301869-powershell/suggestions/15854689-powershell-exe-command-is-broken-on-windows-10

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a><span data-ttu-id="10e0d-139">O powershell.exe cria um pico no uso da CPU durante a inicialização</span><span class="sxs-lookup"><span data-stu-id="10e0d-139">powershell.exe creates spike in CPU usage on startup</span></span>

<span data-ttu-id="10e0d-140">O PowerShell usa uma consulta de WMI para verificar se ele foi iniciado por meio de Política de Grupo para evitar um atraso no logon.</span><span class="sxs-lookup"><span data-stu-id="10e0d-140">PowerShell uses a WMI query to check if it was started via Group Policy to avoid causing delay in login.</span></span>
<span data-ttu-id="10e0d-141">A consulta de WMI acaba injetando o tzres.mui.dll em cada processo no sistema, uma vez que a classe Win32_Process de WMI tenta recuperar informações do fuso horário local.</span><span class="sxs-lookup"><span data-stu-id="10e0d-141">The WMI query ends up injecting tzres.mui.dll into every process on the system since the WMI Win32_Process class attempts to retrieve local timezone information.</span></span>
<span data-ttu-id="10e0d-142">Isso resulta em um grande aumento no uso da CPU no wmiprvse (o host de provedor de WMI).</span><span class="sxs-lookup"><span data-stu-id="10e0d-142">This results in a large CPU spike in wmiprvse (the WMI provider host).</span></span>
<span data-ttu-id="10e0d-143">A correção é usar chamadas de API do Win32 para obter as mesmas informações em vez de usar o WMI.</span><span class="sxs-lookup"><span data-stu-id="10e0d-143">Fix is to use Win32 API calls to get the same information instead of using WMI.</span></span>