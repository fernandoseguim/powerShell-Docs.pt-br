---
ms.date: 08/24/2018
keywords: DSC,powershell,configuração,instalação
title: Recurso Script de DSC
ms.openlocfilehash: 86dfb74bf52d8907686bb955fd722f4fb8b9131b
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58054740"
---
# <a name="dsc-script-resource"></a><span data-ttu-id="b1701-103">Recurso Script de DSC</span><span class="sxs-lookup"><span data-stu-id="b1701-103">DSC Script Resource</span></span>

> <span data-ttu-id="b1701-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="b1701-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="b1701-105">O recurso **Script** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para executar blocos de script do Windows PowerShell em nós de destino.</span><span class="sxs-lookup"><span data-stu-id="b1701-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="b1701-106">O recurso **Script** usa as propriedades `GetScript`, `SetScript` e `TestScript` que contém blocos de script definidos para executar as operações de estado de DSC correspondentes.</span><span class="sxs-lookup"><span data-stu-id="b1701-106">The **Script** resource uses `GetScript`, `SetScript`, and `TestScript` properties that contain script blocks you define to perform the corresponding DSC state operations.</span></span>

## <a name="syntax"></a><span data-ttu-id="b1701-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1701-107">Syntax</span></span>

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> <span data-ttu-id="b1701-108">O blocos `GetScript`, `TestScript` e `SetScript` são armazenados como cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b1701-108">The `GetScript`, `TestScript`, and `SetScript` blocks are stored as strings.</span></span>

## <a name="properties"></a><span data-ttu-id="b1701-109">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b1701-109">Properties</span></span>

|<span data-ttu-id="b1701-110">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b1701-110">Property</span></span>|<span data-ttu-id="b1701-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1701-111">Description</span></span>|
|--------|-----------|
|<span data-ttu-id="b1701-112">GetScript</span><span class="sxs-lookup"><span data-stu-id="b1701-112">GetScript</span></span>|<span data-ttu-id="b1701-113">Um bloco de script que retorna o estado atual do Node.</span><span class="sxs-lookup"><span data-stu-id="b1701-113">A script block that returns the current state of the Node.</span></span>|
|<span data-ttu-id="b1701-114">SetScript</span><span class="sxs-lookup"><span data-stu-id="b1701-114">SetScript</span></span>|<span data-ttu-id="b1701-115">Um bloco de script usado pelo DSC para impor a conformidade quando o Node não estiver no estado desejado.</span><span class="sxs-lookup"><span data-stu-id="b1701-115">A script block that DSC uses to enforce compliance when the Node is not in the desired state.</span></span>|
|<span data-ttu-id="b1701-116">TestScript</span><span class="sxs-lookup"><span data-stu-id="b1701-116">TestScript</span></span>|<span data-ttu-id="b1701-117">Um bloco de script que determina se o Node está no estado desejado.</span><span class="sxs-lookup"><span data-stu-id="b1701-117">A script block that determines if the Node is in the desired state.</span></span>|
|<span data-ttu-id="b1701-118">Credential</span><span class="sxs-lookup"><span data-stu-id="b1701-118">Credential</span></span>| <span data-ttu-id="b1701-119">Indica as credenciais que devem ser usadas para executar esse script, caso sejam necessárias.</span><span class="sxs-lookup"><span data-stu-id="b1701-119">Indicates the credentials to use for running this script, if credentials are required.</span></span>|
|<span data-ttu-id="b1701-120">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b1701-120">DependsOn</span></span>| <span data-ttu-id="b1701-121">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="b1701-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b1701-122">Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="b1701-122">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>

### <a name="getscript"></a><span data-ttu-id="b1701-123">GetScript</span><span class="sxs-lookup"><span data-stu-id="b1701-123">GetScript</span></span>

<span data-ttu-id="b1701-124">DSC não usa a saída do `GetScript`.</span><span class="sxs-lookup"><span data-stu-id="b1701-124">DSC does not use the output from `GetScript`.</span></span> <span data-ttu-id="b1701-125">O cmdlet [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) executa o `GetScript` para recuperar o estado atual do nó.</span><span class="sxs-lookup"><span data-stu-id="b1701-125">The [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet executes the `GetScript` to retrieve a node's current state.</span></span> <span data-ttu-id="b1701-126">`GetScript` não exige um valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="b1701-126">A return value is not required from `GetScript`.</span></span> <span data-ttu-id="b1701-127">Se você especificar um valor de retorno, ele deverá ser um `hashtable` que contenha uma chave **Resultado** cujo valor seja um `String`.</span><span class="sxs-lookup"><span data-stu-id="b1701-127">If you specify a return value, it must be a `hashtable` containing a **Result** key whose value is a `String`.</span></span>

### <a name="testscript"></a><span data-ttu-id="b1701-128">TestScript</span><span class="sxs-lookup"><span data-stu-id="b1701-128">TestScript</span></span>

<span data-ttu-id="b1701-129">O `TestScript` é executado pelo DSC para determinar se o `SetScript` deve ser executado.</span><span class="sxs-lookup"><span data-stu-id="b1701-129">The `TestScript` is executed by DSC to determine if the `SetScript` should be run.</span></span> <span data-ttu-id="b1701-130">Se o `TestScript` retornar `$false`, o DSC executará o `SetScript` para colocar o nó de volta no estado desejado.</span><span class="sxs-lookup"><span data-stu-id="b1701-130">If the `TestScript` returns `$false`, DSC executes the `SetScript` to bring the node back to the desired state.</span></span> <span data-ttu-id="b1701-131">Ele deve retornar um valor `boolean`.</span><span class="sxs-lookup"><span data-stu-id="b1701-131">It must return a `boolean` value.</span></span> <span data-ttu-id="b1701-132">Um resultado de `$true` indica que o nó está em conformidade, e `SetScript` não deve ser executado.</span><span class="sxs-lookup"><span data-stu-id="b1701-132">A result of `$true` indicates that the node is compliant and `SetScript` should not executed.</span></span>

<span data-ttu-id="b1701-133">O cmdlet [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration), executa o `TestScript` para recuperar a conformidade de nós com os recursos de **Script**.</span><span class="sxs-lookup"><span data-stu-id="b1701-133">The [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, executes the `TestScript` to retrieve the nodes compliance with the  **Script** resources.</span></span> <span data-ttu-id="b1701-134">No entanto, nesse caso, o `SetScript` não é executado, não importa o que o bloco `TestScript` retorna.</span><span class="sxs-lookup"><span data-stu-id="b1701-134">However, in this case, the `SetScript` does not run, no matter what the `TestScript` block returns.</span></span>

> [!NOTE]
> <span data-ttu-id="b1701-135">Toda a saída do seu `TestScript` faz parte de seu valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="b1701-135">All output from your `TestScript` is part of its return value.</span></span> <span data-ttu-id="b1701-136">O PowerShell interpreta a saída não suprimida como diferente de zero, o que significa que seu `TestScript` retornará `$true` independentemente do estado do seu nó.</span><span class="sxs-lookup"><span data-stu-id="b1701-136">PowerShell interprets unsuppressed output as non-zero, which means that your `TestScript` will return `$true` regardless of your node's state.</span></span>
> <span data-ttu-id="b1701-137">Isso resulta em resultados imprevisíveis, falsos positivos e causa dificuldades durante a solução de problemas.</span><span class="sxs-lookup"><span data-stu-id="b1701-137">This results in unpredictable results, false positives, and causes difficulty during troubleshooting.</span></span>

### <a name="setscript"></a><span data-ttu-id="b1701-138">SetScript</span><span class="sxs-lookup"><span data-stu-id="b1701-138">SetScript</span></span>

<span data-ttu-id="b1701-139">O `SetScript` modifica o nó para impor o estado desejado.</span><span class="sxs-lookup"><span data-stu-id="b1701-139">The `SetScript` modifies the node to enforce the desired state.</span></span> <span data-ttu-id="b1701-140">Ele será chamado pelo DSC se o bloco de script `TestScript` retornar `$false`.</span><span class="sxs-lookup"><span data-stu-id="b1701-140">It is called by DSC if the `TestScript` script block returns `$false`.</span></span> <span data-ttu-id="b1701-141">O `SetScript` não deve ter nenhum valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="b1701-141">The `SetScript` should have no return value.</span></span>

## <a name="examples"></a><span data-ttu-id="b1701-142">Exemplos</span><span class="sxs-lookup"><span data-stu-id="b1701-142">Examples</span></span>

### <a name="example-1-write-sample-text-using-a-script-resource"></a><span data-ttu-id="b1701-143">Exemplo 1: Escrever texto de exemplo usando um recurso de Script</span><span class="sxs-lookup"><span data-stu-id="b1701-143">Example 1: Write sample text using a Script resource</span></span>

<span data-ttu-id="b1701-144">Este exemplo testa a existência de `C:\TempFolder\TestFile.txt` em cada nó.</span><span class="sxs-lookup"><span data-stu-id="b1701-144">This example tests for the existence of `C:\TempFolder\TestFile.txt` on each node.</span></span> <span data-ttu-id="b1701-145">Se não existir, ele o criará usando o `SetScript`.</span><span class="sxs-lookup"><span data-stu-id="b1701-145">If it does not exist, it creates it using the `SetScript`.</span></span> <span data-ttu-id="b1701-146">O `GetScript` retorna o conteúdo do arquivo, e seu valor de retorno não é usado.</span><span class="sxs-lookup"><span data-stu-id="b1701-146">The `GetScript` returns the contents of the file, and its return value is not used.</span></span>

```powershell
Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script ScriptExample
        {
            SetScript = {
                $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
                $sw.WriteLine("Some sample string")
                $sw.Close()
            }
            TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
            GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
        }
    }
}
```

### <a name="example-2-compare-version-information-using-a-script-resource"></a><span data-ttu-id="b1701-147">Exemplo 2: Comparar informações de versão usando um recurso de Script</span><span class="sxs-lookup"><span data-stu-id="b1701-147">Example 2: Compare version information using a Script resource</span></span>

<span data-ttu-id="b1701-148">Este exemplo recupera as informações da versão *compatível* de um arquivo de texto no computador de criação e as armazenam na variável `$version`.</span><span class="sxs-lookup"><span data-stu-id="b1701-148">This example retrieves the *compliant* version information from a text file on the authoring computer and stores it in the `$version` variable.</span></span> <span data-ttu-id="b1701-149">Ao gerar o arquivo MOF do nó, o DSC substitui as variáveis `$using:version` em cada bloco de script pelo valor da variável `$version`.</span><span class="sxs-lookup"><span data-stu-id="b1701-149">When generating the node's MOF file, DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span> <span data-ttu-id="b1701-150">Durante a execução, a versão *compatível* é armazenada em um arquivo de texto em cada Node, comparada e atualizada em execuções subsequentes.</span><span class="sxs-lookup"><span data-stu-id="b1701-150">During execution, the *compliant* version is stored in a text file on each Node and compared and updated on subsequent executions.</span></span>

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

                if( $state['Result'] -eq $using:version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                    return $true
                }
                Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
                return $false
            }
            SetScript = {
                $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            }
        }
    }
}
```