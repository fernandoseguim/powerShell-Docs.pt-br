---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC,powershell,configuração,instalação
title: Escrevendo um recurso de DSC de instância única (melhor prática)
ms.openlocfilehash: fc118fd8b0d91d2001030769ac7e3c6321972905
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a><span data-ttu-id="fb003-103">Escrevendo um recurso de DSC de instância única (melhor prática)</span><span class="sxs-lookup"><span data-stu-id="fb003-103">Writing a single-instance DSC resource (best practice)</span></span>

><span data-ttu-id="fb003-104">**Observação:** este tópico descreve a melhor prática para a definição de um recurso de DSC que permite apenas uma única instância em uma configuração.</span><span class="sxs-lookup"><span data-stu-id="fb003-104">**Note:** This topic describes a best practice for defining a DSC resource that allows only a single instance in a configuration.</span></span> <span data-ttu-id="fb003-105">Atualmente, não há nenhum recurso interno do DSC para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="fb003-105">Currently, there is no built-in DSC feature to do this.</span></span> <span data-ttu-id="fb003-106">Isso pode mudar no futuro.</span><span class="sxs-lookup"><span data-stu-id="fb003-106">That might change in the future.</span></span>

<span data-ttu-id="fb003-107">Há situações em que você não deseja permitir que um recurso seja usado várias vezes em uma configuração.</span><span class="sxs-lookup"><span data-stu-id="fb003-107">There are situations where you don't want to allow a resource to be used multiple times in a configuration.</span></span> <span data-ttu-id="fb003-108">Por exemplo, um uma implementação anterior do recurso [xTimeZone](https://github.com/PowerShell/xTimeZone), uma configuração poderia chamar o recurso várias vezes, configurando o fuso horário para uma definição diferente em cada bloco de recurso:</span><span class="sxs-lookup"><span data-stu-id="fb003-108">For example, in a previous implementation of the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource, a configuration could call the resource multiple times, setting the time zone to a different setting in each resource block:</span></span>

```powershell
Configuration SetTimeZone
{
    Param
    (
        [String[]]$NodeName = $env:COMPUTERNAME

    )

    Import-DSCResource -ModuleName xTimeZone


    Node $NodeName
    {
         xTimeZone TimeZoneExample
         {

            TimeZone = 'Eastern Standard Time'
         }

         xTimeZone TimeZoneExample2
         {

            TimeZone = 'Pacific Standard Time'

         }

    }
}
```

<span data-ttu-id="fb003-109">Isso ocorre devido à forma como as chaves de recurso de DSC funcionam.</span><span class="sxs-lookup"><span data-stu-id="fb003-109">This is because of the way DSC resource keys work.</span></span> <span data-ttu-id="fb003-110">Um recurso deve ter pelo menos uma propriedade de chave.</span><span class="sxs-lookup"><span data-stu-id="fb003-110">A resource must have at least one key property.</span></span> <span data-ttu-id="fb003-111">Uma instância do recurso é considerada exclusiva se a combinação de valores de todas as suas propriedades de chave for exclusiva.</span><span class="sxs-lookup"><span data-stu-id="fb003-111">A resource instance is considered unique if the combination of the values of all of its key properties is unique.</span></span> <span data-ttu-id="fb003-112">Em sua implementação anterior, o recurso [xTimeZone](https://github.com/PowerShell/xTimeZone) apresentava apenas uma propriedade --**TimeZone**, que obrigatoriamente tinha que ser uma chave.</span><span class="sxs-lookup"><span data-stu-id="fb003-112">In its previous implementation, the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource had only one property--**TimeZone**, which was required to be a key.</span></span> <span data-ttu-id="fb003-113">Por isso, uma configuração, como mostrado acima seria compilada e executada sem aviso.</span><span class="sxs-lookup"><span data-stu-id="fb003-113">Because of this, a configuration such as the one above would compile and run without warning.</span></span> <span data-ttu-id="fb003-114">Cada um do blocos de recurso de **xTimeZone** é considerado exclusivo.</span><span class="sxs-lookup"><span data-stu-id="fb003-114">Each of the **xTimeZone** resource blocks is considered unique.</span></span> <span data-ttu-id="fb003-115">Isso faria com que a configuração fosse aplicada várias vezes ao nó, alternando o fuso horário.</span><span class="sxs-lookup"><span data-stu-id="fb003-115">This would cause the configuration to be repeatedly applied to the node, cycling the timezone back and forth.</span></span>

<span data-ttu-id="fb003-116">Para garantir que uma configuração possa definir o fuso horário para um nó de destino somente uma vez, o recurso foi atualizado para adicionar uma segunda propriedade, **IsSingleInstance**, que se tornou a propriedade principal.</span><span class="sxs-lookup"><span data-stu-id="fb003-116">To ensure that a configuration could set the time zone for a target node only once, the resource was updated to add a second property, **IsSingleInstance**, that became the key property.</span></span>
<span data-ttu-id="fb003-117">O **IsSingleInstance** foi limitado a um único valor, "Yes" (Sim) usando um **ValueMap**.</span><span class="sxs-lookup"><span data-stu-id="fb003-117">The **IsSingleInstance** was limited to a single value, "Yes" by using a **ValueMap**.</span></span> <span data-ttu-id="fb003-118">O esquema MOF antigo para o recurso foi:</span><span class="sxs-lookup"><span data-stu-id="fb003-118">The old MOF schema for the resource was:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="fb003-119">O esquema MOF atualizado para o recurso é:</span><span class="sxs-lookup"><span data-stu-id="fb003-119">The updated MOF schema for the resource is:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="fb003-120">O script de recurso também foi atualizado para usar o novo parâmetro.</span><span class="sxs-lookup"><span data-stu-id="fb003-120">The resource script was also updated to use the new parameter.</span></span> <span data-ttu-id="fb003-121">Aqui está o script de recurso antigo:</span><span class="sxs-lookup"><span data-stu-id="fb003-121">Here is the old resource script:</span></span>

```powershell
function Get-TargetResource
{
    [CmdletBinding()]
    [OutputType([Hashtable])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Get the current TimeZone
    $CurrentTimeZone = Get-TimeZone

    $returnValue = @{
        TimeZone = $CurrentTimeZone
        IsSingleInstance = 'Yes'
    }

    #Output the target resource
    $returnValue
}


function Set-TargetResource
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output the result of Get-TargetResource function.
    $CurrentTimeZone = Get-TimeZone

    if($PSCmdlet.ShouldProcess("'$TimeZone'","Replace the System Time Zone"))
    {
        try
        {
            if($CurrentTimeZone -ne $TimeZone)
            {
                Write-Verbose -Verbose "Setting the TimeZone"
                Set-TimeZone -TimeZone $TimeZone}
            else
            {
                Write-Verbose -Verbose "TimeZone already set to $TimeZone"
            }
        }
        catch
        {
            $ErrorMsg = $_.Exception.Message
            Write-Verbose -Verbose $ErrorMsg
        }
    }
}


function Test-TargetResource
{
    [CmdletBinding()]
    [OutputType([Boolean])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output from Get-TargetResource
    $CurrentTimeZone = Get-TimeZone

    if($TimeZone -eq $CurrentTimeZone)
    {
        return $true
    }
    else
    {
        return $false
    }
}

Function Get-TimeZone {
    [CmdletBinding()]
    param()

    & tzutil.exe /g
}

Function Set-TimeZone {
    [CmdletBinding()]
    param(
        [Parameter(Mandatory=$true)]
        [System.String]
        $TimeZone
    )

    try
    {
        & tzutil.exe /s $TimeZone
    }
    catch
    {
        $ErrorMsg = $_.Exception.Message
        Write-Verbose $ErrorMsg
    }
}

Export-ModuleMember -Function *-TargetResource
```

<span data-ttu-id="fb003-122">Observe que a propriedade **TimeZone** propriedade não é mais uma chave.</span><span class="sxs-lookup"><span data-stu-id="fb003-122">Notice that the **TimeZone** property is no longer a key.</span></span> <span data-ttu-id="fb003-123">Agora, se uma configuração tentar definir o fuso horário duas vezes (usando dois blocos **xTimeZone** diferentes com valores de **TimeZone** diferentes), tentar compilar a configuração vai gerar um erro:</span><span class="sxs-lookup"><span data-stu-id="fb003-123">Now, if a configuration attempts to set the time zone twice (by using two different **xTimeZone** blocks with different **TimeZone** values), attempting to compile the configuration will cause an error:</span></span>

```powershell
Test-ConflictingResources : A conflict was detected between resources '[xTimeZone]TimeZoneExample (::15::10::xTimeZone)' and
'[xTimeZone]TimeZoneExample2 (::22::10::xTimeZone)' in node 'CONTOSO-CLIENT'. Resources have identical key properties but there are differences in the
following non-key properties: 'TimeZone'. Values 'Eastern Standard Time' don't match values 'Pacific Standard Time'. Please update these property
values so that they are identical in both cases.
At line:271 char:9
+         Test-ConflictingResources $keywordName $canonicalizedValue $k ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : ConflictingDuplicateResource,Test-ConflictingResources
Errors occurred while processing configuration 'SetTimeZone'.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3705 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (SetTimeZone:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```