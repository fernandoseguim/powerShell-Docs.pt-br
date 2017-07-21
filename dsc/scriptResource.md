---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: Recurso Script de DSC
ms.openlocfilehash: 81718de0b0c8463189e33e565dc9ff39692dbe8b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-script-resource"></a><span data-ttu-id="ee657-103">Recurso Script de DSC</span><span class="sxs-lookup"><span data-stu-id="ee657-103">DSC Script Resource</span></span>

 
> <span data-ttu-id="ee657-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ee657-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="ee657-105">O recurso **Script** na Configuração de Estado Desejado (DSC) do Windows PowerShell fornece um mecanismo para executar blocos de script do Windows PowerShell em nós de destino.</span><span class="sxs-lookup"><span data-stu-id="ee657-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="ee657-106">O recurso `Script` tem as propriedades `GetScript`, `SetScript` e `TestScript`.</span><span class="sxs-lookup"><span data-stu-id="ee657-106">The `Script` resource has `GetScript`, `SetScript`, and `TestScript` properties.</span></span> <span data-ttu-id="ee657-107">Essas propriedades devem ser definidas em blocos de script que serão executado em cada nó de destino.</span><span class="sxs-lookup"><span data-stu-id="ee657-107">These properties should be set to script blocks that will run on each target node.</span></span> 

<span data-ttu-id="ee657-108">O bloco de script `GetScript` deve retornar uma tabela de hash que representa o estado do nó atual.</span><span class="sxs-lookup"><span data-stu-id="ee657-108">The `GetScript` script block should return a hashtable representing the state of the current node.</span></span> <span data-ttu-id="ee657-109">A tabela de hash deve conter somente uma chave `Result` e o valor deve ser do tipo `String`.</span><span class="sxs-lookup"><span data-stu-id="ee657-109">The hashtable must only contain one key `Result` and the value must be of type `String`.</span></span> <span data-ttu-id="ee657-110">Ele não precisa retornar nada.</span><span class="sxs-lookup"><span data-stu-id="ee657-110">It is not required to return anything.</span></span> <span data-ttu-id="ee657-111">O DSC não faz nada com a saída desse bloco de script.</span><span class="sxs-lookup"><span data-stu-id="ee657-111">DSC doesn't do anything with the output of this script block.</span></span>

<span data-ttu-id="ee657-112">O bloco de script `TestScript` deve determinar se o nó atual precisa ser modificado.</span><span class="sxs-lookup"><span data-stu-id="ee657-112">The `TestScript` script block should determine if the current node needs to be modified.</span></span> <span data-ttu-id="ee657-113">Ele deverá retornar `$true` se o nó for atualizado.</span><span class="sxs-lookup"><span data-stu-id="ee657-113">It should return `$true` if the node is up-to-date.</span></span> <span data-ttu-id="ee657-114">Ele deverá retornar `$false` se a configuração do nó estiver desatualizada e deverá ser atualizada pelo bloco de script `SetScript`.</span><span class="sxs-lookup"><span data-stu-id="ee657-114">It should return `$false` if the node's configuration is out-of-date and should be updated by the `SetScript` script block.</span></span> <span data-ttu-id="ee657-115">O bloco de script `TestScript` é chamado pelo DSC.</span><span class="sxs-lookup"><span data-stu-id="ee657-115">The `TestScript` script block is called by DSC.</span></span>

<span data-ttu-id="ee657-116">O bloco de script `SetScript` deve modificar o nó.</span><span class="sxs-lookup"><span data-stu-id="ee657-116">The `SetScript` script block should modify the node.</span></span> <span data-ttu-id="ee657-117">Ele será chamado pelo DSC, se o bloco `TestScript` retornar `$false`.</span><span class="sxs-lookup"><span data-stu-id="ee657-117">It is called by DSC if the `TestScript` block return `$false`.</span></span>

<span data-ttu-id="ee657-118">Se você precisa usar variáveis do seu script de configuração nos blocos de script `GetScript`, `TestScript` ou `SetScript`, use o escopo `$using:` (consulte abaixo para obter um exemplo).</span><span class="sxs-lookup"><span data-stu-id="ee657-118">If you need to use variables from your configuration script in the `GetScript`, `TestScript`, or `SetScript` script blocks, use the `$using:` scope (see below for an example).</span></span>


## <a name="syntax"></a><span data-ttu-id="ee657-119">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ee657-119">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="ee657-120">Propriedades</span><span class="sxs-lookup"><span data-stu-id="ee657-120">Properties</span></span>

|  <span data-ttu-id="ee657-121">Propriedade</span><span class="sxs-lookup"><span data-stu-id="ee657-121">Property</span></span>  |  <span data-ttu-id="ee657-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="ee657-122">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="ee657-123">GetScript</span><span class="sxs-lookup"><span data-stu-id="ee657-123">GetScript</span></span>| <span data-ttu-id="ee657-124">Fornece um bloco de script do Windows PowerShell que é executado quando você invoca o cmdlet [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx).</span><span class="sxs-lookup"><span data-stu-id="ee657-124">Provides a block of Windows PowerShell script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) cmdlet.</span></span> <span data-ttu-id="ee657-125">Esse bloco deve retornar uma tabela de hash.</span><span class="sxs-lookup"><span data-stu-id="ee657-125">This block must return a hashtable.</span></span> <span data-ttu-id="ee657-126">A tabela de hash deve conter somente uma chave **Resultado** e o valor deve ser do tipo **cadeia de caracteres**.</span><span class="sxs-lookup"><span data-stu-id="ee657-126">The hashtable must only contain one key **Result** and the value must be of type **String**.</span></span>| 
| <span data-ttu-id="ee657-127">SetScript</span><span class="sxs-lookup"><span data-stu-id="ee657-127">SetScript</span></span>| <span data-ttu-id="ee657-128">Fornece um bloco de script do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ee657-128">Provides a block of Windows PowerShell script.</span></span> <span data-ttu-id="ee657-129">Quando você invoca o cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), o bloco **TestScript** é executado primeiro.</span><span class="sxs-lookup"><span data-stu-id="ee657-129">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, the **TestScript** block runs first.</span></span> <span data-ttu-id="ee657-130">Se o bloco **TestScript** gerar **$false**, o bloco **SetScript** será executado.</span><span class="sxs-lookup"><span data-stu-id="ee657-130">If the **TestScript** block returns **$false**, the **SetScript** block will run.</span></span> <span data-ttu-id="ee657-131">Se o bloco **TestScript** gerar **$true**, o bloco **SetScript** não será executado.</span><span class="sxs-lookup"><span data-stu-id="ee657-131">If the **TestScript** block returns **$true**, the **SetScript** block will not run.</span></span>| 
| <span data-ttu-id="ee657-132">TestScript</span><span class="sxs-lookup"><span data-stu-id="ee657-132">TestScript</span></span>| <span data-ttu-id="ee657-133">Fornece um bloco de script do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ee657-133">Provides a block of Windows PowerShell script.</span></span> <span data-ttu-id="ee657-134">Quando você invoca o cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), esse bloco é executado.</span><span class="sxs-lookup"><span data-stu-id="ee657-134">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, this block runs.</span></span> <span data-ttu-id="ee657-135">Se gerar **$false**, o bloco SetScript será executado.</span><span class="sxs-lookup"><span data-stu-id="ee657-135">If it returns **$false**, the SetScript block will run.</span></span> <span data-ttu-id="ee657-136">Se gerar **$true**, o bloco SetScript não será executado.</span><span class="sxs-lookup"><span data-stu-id="ee657-136">If it returns **$true**, the SetScript block will not run.</span></span> <span data-ttu-id="ee657-137">O bloco **TestScript** também é executado quando você invoca o cmdlet [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx).</span><span class="sxs-lookup"><span data-stu-id="ee657-137">The **TestScript** block also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="ee657-138">No entanto, nesse caso, o bloco **SetScript** não será executado, independentemente do valor gerado pelo bloco TestScript.</span><span class="sxs-lookup"><span data-stu-id="ee657-138">However, in this case, the **SetScript** block will not run, no matter what value the TestScript block returns.</span></span> <span data-ttu-id="ee657-139">O bloco **TestScript** precisará gerar True se a configuração real corresponder à configuração atual de estado desejado e False se não corresponder.</span><span class="sxs-lookup"><span data-stu-id="ee657-139">The **TestScript** block must return True if the actual configuration matches the current desired state configuration, and False if it does not match.</span></span> <span data-ttu-id="ee657-140">(A configuração atual de estado desejado é a última configuração aplicada no nó que está usando a DSC.)</span><span class="sxs-lookup"><span data-stu-id="ee657-140">(The current desired state configuration is the last configuration enacted on the node that is using DSC.)</span></span>| 
| <span data-ttu-id="ee657-141">Credential</span><span class="sxs-lookup"><span data-stu-id="ee657-141">Credential</span></span>| <span data-ttu-id="ee657-142">Indica as credenciais que devem ser usadas para executar esse script, caso sejam necessárias.</span><span class="sxs-lookup"><span data-stu-id="ee657-142">Indicates the credentials to use for running this script, if credentials are required.</span></span>| 
| <span data-ttu-id="ee657-143">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ee657-143">DependsOn</span></span>| <span data-ttu-id="ee657-144">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="ee657-144">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ee657-145">Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="ee657-145">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>

## <a name="example-1"></a><span data-ttu-id="ee657-146">Exemplo 1</span><span class="sxs-lookup"><span data-stu-id="ee657-146">Example 1</span></span>
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script ScriptExample
    {
        SetScript = 
        { 
            $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
            $sw.WriteLine("Some sample string")
            $sw.Close()
        }
        TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
        GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }          
    }
}
```

## <a name="example-2"></a><span data-ttu-id="ee657-147">Exemplo 2</span><span class="sxs-lookup"><span data-stu-id="ee657-147">Example 2</span></span>
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script UpdateConfigurationVersion
    {
        GetScript = { 
            $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            return @{ 'Version' = "$currentVersion" }
        }          
        TestScript = { 
            $state = $GetScript
            if( $state['Version'] -eq $using:version )
            {
                Write-Verbose -Message ('{0} -eq {1}' -f $state['Version'],$using:version)
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
```

<span data-ttu-id="ee657-148">Este recurso está gravando a versão da configuração em um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="ee657-148">This resource is writing the configuration's version to a text file.</span></span> <span data-ttu-id="ee657-149">Esta versão está disponível no computador cliente, mas não está em nenhum dos nós, por isso deve ser passada para cada um dos blocos de script do recurso `Script` com o escopo `using` do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ee657-149">This version is available on the client computer, but isn't on any of the nodes, so it has to be passed to each of the `Script` resource's script blocks with PowerShell's `using` scope.</span></span> <span data-ttu-id="ee657-150">Quando gera o arquivo MOF do nó, o valor da variável `$version` é lido de um arquivo de texto no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="ee657-150">When generating the node's MOF file, the value of the `$version` variable is read from a text file on the client computer.</span></span> <span data-ttu-id="ee657-151">O DSC substitui as variáveis `$using:version` em cada bloco de script pelo valor da variável `$version`.</span><span class="sxs-lookup"><span data-stu-id="ee657-151">DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span>

