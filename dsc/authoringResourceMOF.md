---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Escrevendo um recurso personalizado de DSC com MOF
ms.openlocfilehash: 50b5f2eddbac4571f5351b32648d45c54ded167e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189628"
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a><span data-ttu-id="d4732-103">Escrevendo um recurso personalizado de DSC com MOF</span><span class="sxs-lookup"><span data-stu-id="d4732-103">Writing a custom DSC resource with MOF</span></span>

> <span data-ttu-id="d4732-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d4732-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="d4732-105">Neste tópico, definiremos o esquema para um recurso personalizado de Configuração de Estado Desejado (DSC) do Windows PowerShell em um arquivo MOF, além de implementar o recurso em um arquivo de script do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d4732-105">In this topic, we will define the schema for a Windows PowerShell Desired State Configuration (DSC) custom resource in a MOF file, and implement the resource in a Windows PowerShell script file.</span></span> <span data-ttu-id="d4732-106">Esse recurso personalizado serve para criar e manter um site da web.</span><span class="sxs-lookup"><span data-stu-id="d4732-106">This custom resource is for creating and maintaining a web site.</span></span>

## <a name="creating-the-mof-schema"></a><span data-ttu-id="d4732-107">Criando o esquema MOF</span><span class="sxs-lookup"><span data-stu-id="d4732-107">Creating the MOF schema</span></span>

<span data-ttu-id="d4732-108">O esquema define as propriedades do recurso que pode ser configurado por um script de configuração DSC.</span><span class="sxs-lookup"><span data-stu-id="d4732-108">The schema defines the properties of your resource that can be configured by a DSC configuration script.</span></span>

### <a name="folder-structure-for-a-mof-resource"></a><span data-ttu-id="d4732-109">Estrutura de pastas para um recurso MOF</span><span class="sxs-lookup"><span data-stu-id="d4732-109">Folder structure for a MOF resource</span></span>

<span data-ttu-id="d4732-110">Para implementar um recurso personalizado de DSC com esquema MOF, crie a seguinte estrutura de pastas.</span><span class="sxs-lookup"><span data-stu-id="d4732-110">To implement a DSC custom resource with a MOF schema, create the following folder structure.</span></span> <span data-ttu-id="d4732-111">O esquema MOF é definido no arquivo Demo_IISWebsite.schema.mof e o script de recurso é definido no Demo_IISWebsite.psm1.</span><span class="sxs-lookup"><span data-stu-id="d4732-111">The MOF schema is defined in the file Demo_IISWebsite.schema.mof, and the resource script is defined in Demo_IISWebsite.psm1.</span></span> <span data-ttu-id="d4732-112">Opcionalmente, você pode criar um arquivo de manifesto do módulo (psd1).</span><span class="sxs-lookup"><span data-stu-id="d4732-112">Optionally, you can create a module manifest (psd1) file.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

<span data-ttu-id="d4732-113">Observe que é necessário criar uma pasta chamada DSCResources na pasta de nível superior e que a pasta para cada recurso deve ter o mesmo nome que o recurso.</span><span class="sxs-lookup"><span data-stu-id="d4732-113">Note that it is necessary to create a folder named DSCResources under the top-level folder, and that the folder for each resource must have the same name as the resource.</span></span>

### <a name="the-contents-of-the-mof-file"></a><span data-ttu-id="d4732-114">O conteúdo do arquivo MOF</span><span class="sxs-lookup"><span data-stu-id="d4732-114">The contents of the MOF file</span></span>

<span data-ttu-id="d4732-115">Segue um exemplo de arquivo MOF que pode ser usado para um recurso de sites personalizados.</span><span class="sxs-lookup"><span data-stu-id="d4732-115">Following is an example MOF file that can be used for a custom website resource.</span></span> <span data-ttu-id="d4732-116">Para seguir esse exemplo, salve o esquema em um arquivo e chame o arquivo de *Demo_IISWebsite.schema.mof*.</span><span class="sxs-lookup"><span data-stu-id="d4732-116">To follow this example, save this schema to a file, and call the file *Demo_IISWebsite.schema.mof*.</span></span>

```
[ClassVersion("1.0.0"), FriendlyName("Website")]
class Demo_IISWebsite : OMI_BaseResource
{
  [Key] string Name;
  [Required] string PhysicalPath;
  [write,ValueMap{"Present", "Absent"},Values{"Present", "Absent"}] string Ensure;
  [write,ValueMap{"Started","Stopped"},Values{"Started", "Stopped"}] string State;
  [write] string Protocol[];
  [write] string BindingInfo[];
  [write] string ApplicationPool;
  [read] string ID;
};
```

<span data-ttu-id="d4732-117">Observe o seguinte sobre o código anterior:</span><span class="sxs-lookup"><span data-stu-id="d4732-117">Note the following about the previous code:</span></span>

* <span data-ttu-id="d4732-118">`FriendlyName` define o nome que você pode usar para se referir a esse recurso personalizado em scripts de configuração DSC.</span><span class="sxs-lookup"><span data-stu-id="d4732-118">`FriendlyName` defines the name you can use to refer to this custom resource in DSC configuration scripts.</span></span> <span data-ttu-id="d4732-119">Neste exemplo, `Website` é equivalente ao nome amigável `Archive` para o recurso interno Archive.</span><span class="sxs-lookup"><span data-stu-id="d4732-119">In this example, `Website` is equivalent to the friendly name `Archive` for the built-in Archive resource.</span></span>
* <span data-ttu-id="d4732-120">A classe que você define para o recurso personalizado deve derivar de `OMI_BaseResource`.</span><span class="sxs-lookup"><span data-stu-id="d4732-120">The class you define for your custom resource must derive from `OMI_BaseResource`.</span></span>
* <span data-ttu-id="d4732-121">O qualificador de tipo, `[Key]`, em uma propriedade indica que essa propriedade identificará exclusivamente a instância do recurso.</span><span class="sxs-lookup"><span data-stu-id="d4732-121">The type qualifier, `[Key]`, on a property indicates that this property will uniquely identify the resource instance.</span></span> <span data-ttu-id="d4732-122">Pelo menos uma propriedade `[Key]` é necessária.</span><span class="sxs-lookup"><span data-stu-id="d4732-122">At least one `[Key]` property is required.</span></span>
* <span data-ttu-id="d4732-123">O qualificador `[Required]` indica que a propriedade é necessária (um valor deve ser especificado em qualquer script de configuração que usa esse recurso).</span><span class="sxs-lookup"><span data-stu-id="d4732-123">The `[Required]` qualifier indicates that the property is required (a value must be specified in any configuration script that uses this resource).</span></span>
* <span data-ttu-id="d4732-124">O qualificador `[write]` indica que essa propriedade é opcional ao usar o recurso personalizado em um script de configuração.</span><span class="sxs-lookup"><span data-stu-id="d4732-124">The `[write]` qualifier indicates that this property is optional when using the custom resource in a configuration script.</span></span> <span data-ttu-id="d4732-125">O qualificador `[read]` indica que uma propriedade não pode ser definida por uma configuração e destina-se apenas para fins de relatório.</span><span class="sxs-lookup"><span data-stu-id="d4732-125">The `[read]` qualifier indicates that a property cannot be set by a configuration, and is for reporting purposes only.</span></span>
* <span data-ttu-id="d4732-126">`Values` restringe os valores que podem ser atribuídos à propriedade para a lista de valores definidos em `ValueMap`.</span><span class="sxs-lookup"><span data-stu-id="d4732-126">`Values` restricts the values that can be assigned to the property to the list of values defined in `ValueMap`.</span></span> <span data-ttu-id="d4732-127">Para obter mais informações, consulte [ValueMap e Qualificadores de Valor](https://msdn.microsoft.com/library/windows/desktop/aa393965.aspx).</span><span class="sxs-lookup"><span data-stu-id="d4732-127">For more information, see [ValueMap and Value Qualifiers](https://msdn.microsoft.com/library/windows/desktop/aa393965.aspx).</span></span>
* <span data-ttu-id="d4732-128">É recomendável incluir uma propriedade chamada `Ensure` com os valores `Present` e `Absent` em seu recurso como uma maneira de manter um estilo consistente com recursos internos de DSC.</span><span class="sxs-lookup"><span data-stu-id="d4732-128">Including a property called `Ensure` with values `Present` and `Absent` in your resource is recommended as a way to maintain a consistent style with built-in DSC resources.</span></span>
* <span data-ttu-id="d4732-129">Nomeie o arquivo de esquema para o recurso personalizado da seguinte maneira: `classname.schema.mof`, em que `classname` é o identificador que segue a palavra-chave `class` na definição do esquema.</span><span class="sxs-lookup"><span data-stu-id="d4732-129">Name the schema file for your custom resource as follows: `classname.schema.mof`, where `classname` is the identifier that follows the `class` keyword in your schema definition.</span></span>

### <a name="writing-the-resource-script"></a><span data-ttu-id="d4732-130">Escrevendo o script de recurso</span><span class="sxs-lookup"><span data-stu-id="d4732-130">Writing the resource script</span></span>

<span data-ttu-id="d4732-131">O script de recurso implementa a lógica do recurso.</span><span class="sxs-lookup"><span data-stu-id="d4732-131">The resource script implements the logic of the resource.</span></span> <span data-ttu-id="d4732-132">Neste módulo, você deve incluir três funções chamadas **Get-TargetResource**, **Set-TargetResource** e **Test-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="d4732-132">In this module, you must include three functions called **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource**.</span></span> <span data-ttu-id="d4732-133">As três funções precisam usar um conjunto de parâmetros que seja idêntico ao conjunto de propriedades definidas no esquema MOF criado para seu recurso.</span><span class="sxs-lookup"><span data-stu-id="d4732-133">All three functions must take a parameter set that is identical to the set of properties defined in the MOF schema that you created for your resource.</span></span> <span data-ttu-id="d4732-134">Neste documento, esse conjunto de propriedades é chamado de “propriedades de recursos”.</span><span class="sxs-lookup"><span data-stu-id="d4732-134">In this document, this set of properties is referred to as the “resource properties.”</span></span> <span data-ttu-id="d4732-135">Armazene essas três funções em um arquivo chamado <ResourceName>.psm1.</span><span class="sxs-lookup"><span data-stu-id="d4732-135">Store these three functions in a file called <ResourceName>.psm1.</span></span> <span data-ttu-id="d4732-136">No exemplo a seguir, as funções são armazenadas em um arquivo chamado Demo_IISWebsite.psm1.</span><span class="sxs-lookup"><span data-stu-id="d4732-136">In the following example, the functions are stored in a file called Demo_IISWebsite.psm1.</span></span>

> <span data-ttu-id="d4732-137">**Observação**: quando você executa o mesmo script de configuração no recurso mais de uma vez, não deve receber erros e o recurso deve permanecer no mesmo estado do script executado uma vez.</span><span class="sxs-lookup"><span data-stu-id="d4732-137">**Note**: When you run the same configuration script on your resource more than once, you should receive no errors and the resource should remain in the same state as running the script once.</span></span> <span data-ttu-id="d4732-138">Para fazer isso, verifique se suas funções **Get-TargetResource** e **Test-TargetResource** deixam o recurso inalterado e se chamar a função **Set-TargetResource** mais de uma vez em uma sequência com os mesmos valores de parâmetro é sempre equivalente a chamá-la uma vez.</span><span class="sxs-lookup"><span data-stu-id="d4732-138">To accomplish this, ensure that your **Get-TargetResource** and **Test-TargetResource** functions leave the resource unchanged, and that invoking the **Set-TargetResource** function more than once in a sequence with the same parameter values is always equivalent to invoking it once.</span></span>

<span data-ttu-id="d4732-139">Na implementação da função **Get-TargetResource**, utilize os valores da propriedade de recurso de chave que são fornecidos como parâmetros para verificar o status da instância do recurso especificado.</span><span class="sxs-lookup"><span data-stu-id="d4732-139">In the **Get-TargetResource** function implementation, use the key resource property values that are provided as parameters to check the status of the specified resource instance.</span></span> <span data-ttu-id="d4732-140">Essa função deve gerar uma tabela de hash que liste todas as propriedades de recursos como chaves e os valores reais dessas propriedades como valores correspondentes.</span><span class="sxs-lookup"><span data-stu-id="d4732-140">This function must return a hash table that lists all the resource properties as keys and the actual values of these properties as the corresponding values.</span></span> <span data-ttu-id="d4732-141">O código a seguir fornece um exemplo.</span><span class="sxs-lookup"><span data-stu-id="d4732-141">The following code provides an example.</span></span>

```powershell
# DSC uses the Get-TargetResource function to fetch the status of the resource instance specified in the parameters for the target machine
function Get-TargetResource
{
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

        $getTargetResourceResult = $null;

        <# Insert logic that uses the mandatory parameter values to get the website and assign it to a variable called $Website #>
        <# Set $ensureResult to "Present" if the requested website exists and to "Absent" otherwise #>

        # Add all Website properties to the hash table
        # This simple example assumes that $Website is not null
        $getTargetResourceResult = @{
                                      Name = $Website.Name;
                                        Ensure = $ensureResult;
                                        PhysicalPath = $Website.physicalPath;
                                        State = $Website.state;
                                        ID = $Website.id;
                                        ApplicationPool = $Website.applicationPool;
                                        Protocol = $Website.bindings.Collection.protocol;
                                        Binding = $Website.bindings.Collection.bindingInformation;
                                    }

        $getTargetResourceResult;
}
```

<span data-ttu-id="d4732-142">Dependendo dos valores especificados para as propriedades do recurso no script de configuração, a função **Set-TargetResource** deve fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d4732-142">Depending on the values that are specified for the resource properties in the configuration script, the **Set-TargetResource** must do one of the following:</span></span>

* <span data-ttu-id="d4732-143">Criar um novo site da web</span><span class="sxs-lookup"><span data-stu-id="d4732-143">Create a new website</span></span>
* <span data-ttu-id="d4732-144">Atualizar um site da web existente</span><span class="sxs-lookup"><span data-stu-id="d4732-144">Update an existing website</span></span>
* <span data-ttu-id="d4732-145">Excluir um site da web existente</span><span class="sxs-lookup"><span data-stu-id="d4732-145">Delete an existing website</span></span>

<span data-ttu-id="d4732-146">O exemplo a seguir mostra isso.</span><span class="sxs-lookup"><span data-stu-id="d4732-146">The following example illustrates this.</span></span>

```powershell
# The Set-TargetResource function is used to create, delete or configure a website on the target machine.
function Set-TargetResource
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

    <# If Ensure is set to "Present" and the website specified in the mandatory input parameters does not exist, then create it using the specified parameter values #>
    <# Else, if Ensure is set to "Present" and the website does exist, then update its properties to match the values provided in the non-mandatory parameter values #>
    <# Else, if Ensure is set to "Absent" and the website does not exist, then do nothing #>
    <# Else, if Ensure is set to "Absent" and the website does exist, then delete the website #>
}
```

<span data-ttu-id="d4732-147">Por fim, a função **Test-TargetResource** precisa utilizar o mesmo parâmetro configurado como **Get-TargetResource** e **Set-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="d4732-147">Finally, the **Test-TargetResource** function must take the same parameter set as **Get-TargetResource** and **Set-TargetResource**.</span></span> <span data-ttu-id="d4732-148">Na implementação de **Test-TargetResource**, verifique o status da instância do recurso que está especificada nos parâmetros de chave.</span><span class="sxs-lookup"><span data-stu-id="d4732-148">In your implementation of **Test-TargetResource**, check the status of the resource instance that is specified in the key parameters.</span></span> <span data-ttu-id="d4732-149">Se o estado real da instância do recurso não coincidir com os valores especificados no conjunto de parâmetros, gere **$false**.</span><span class="sxs-lookup"><span data-stu-id="d4732-149">If the actual status of the resource instance does not match the values specified in the parameter set, return **$false**.</span></span> <span data-ttu-id="d4732-150">Caso contrário, gere **$true**.</span><span class="sxs-lookup"><span data-stu-id="d4732-150">Otherwise, return **$true**.</span></span>

<span data-ttu-id="d4732-151">O código a seguir implementa a função **Test-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="d4732-151">The following code implements the **Test-TargetResource** function.</span></span>

```powershell
function Test-TargetResource
{
[CmdletBinding()]
[OutputType([System.Boolean])]
param
(
[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[parameter(Mandatory = $true)]
[System.String]
$Name,

[parameter(Mandatory = $true)]
[System.String]
$PhysicalPath,

[ValidateSet("Started","Stopped")]
[System.String]
$State,

[System.String[]]
$Protocol,

[System.String[]]
$BindingData,

[System.String]
$ApplicationPool
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


#Include logic to
$result = [System.Boolean]
#Add logic to test whether the website is present and its status mathes the supplied parameter values. If it does, return true. If it does not, return false.
$result
}
```

<span data-ttu-id="d4732-152">**Observação**: para uma depuração mais fácil, use o cmdlet **Write-Verbose** na implementação das três funções anteriores.</span><span class="sxs-lookup"><span data-stu-id="d4732-152">**Note**: For easier debugging, use the **Write-Verbose** cmdlet in your implementation of the previous three functions.</span></span>
><span data-ttu-id="d4732-153">Esse cmdlet escreve o texto para o fluxo de mensagem detalhada.</span><span class="sxs-lookup"><span data-stu-id="d4732-153">This cmdlet writes text to the verbose message stream.</span></span>
><span data-ttu-id="d4732-154">Por padrão, o fluxo de mensagem detalhada não é exibido, mas você pode exibi-lo alterando o valor da variável **$VerbosePreference** ou usando o parâmetro **Verbose** nos cmdlets DSC = novo.</span><span class="sxs-lookup"><span data-stu-id="d4732-154">By default, the verbose message stream is not displayed, but you can display it by changing the value of the **$VerbosePreference** variable or by using the **Verbose** parameter in the DSC cmdlets = new.</span></span>

### <a name="creating-the-module-manifest"></a><span data-ttu-id="d4732-155">Criando o manifesto de módulo</span><span class="sxs-lookup"><span data-stu-id="d4732-155">Creating the module manifest</span></span>

<span data-ttu-id="d4732-156">Por fim, use o cmdlet **New-ModuleManifest** para definir um arquivo <ResourceName>.psd1 para o módulo de recurso personalizado.</span><span class="sxs-lookup"><span data-stu-id="d4732-156">Finally, use the **New-ModuleManifest** cmdlet to define a <ResourceName>.psd1 file for your custom resource module.</span></span> <span data-ttu-id="d4732-157">Quando invocar esse cmdlet, faça referência ao arquivo de módulo do script (.psm1) descrito na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="d4732-157">When you invoke this cmdlet, reference the script module (.psm1) file described in the previous section.</span></span> <span data-ttu-id="d4732-158">Inclua **Get-TargetResource**, **Set-TargetResource** e **Test-TargetResource** na lista de funções para exportar.</span><span class="sxs-lookup"><span data-stu-id="d4732-158">Include **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** in the list of functions to export.</span></span> <span data-ttu-id="d4732-159">Segue um exemplo de arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="d4732-159">Following is an example manifest file.</span></span>

```powershell
# Module manifest for module 'Demo.IIS.Website'
#
# Generated on: 1/10/2013
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '6AB5ED33-E923-41d8-A3A4-5ADDA2B301DE'

# Author of this module
Author = 'Contoso'

# Company or vendor of this module
CompanyName = 'Contoso'

# Copyright statement for this module
Copyright = 'Contoso. All rights reserved.'

# Description of the functionality provided by this module
Description = 'This Module is used to support the creation and configuration of IIS Websites through Get, Set and Test API on the DSC managed nodes.'

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '4.0'

# Minimum version of the common language runtime (CLR) required by this module
CLRVersion = '4.0'

# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @("WebAdministration")

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @("Demo_IISWebsite.psm1")

# Functions to export from this module
FunctionsToExport = @("Get-TargetResource", "Set-TargetResource", "Test-TargetResource")

# Cmdlets to export from this module
#CmdletsToExport = '*'

# HelpInfo URI of this module
# HelpInfoURI = ''
}
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="d4732-160">Dando suporte a PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="d4732-160">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="d4732-161">**Observação:** **PsDscRunAsCredential** tem suporte no PowerShell 5.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="d4732-161">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="d4732-162">A propriedade **PsDscRunAsCredential** pode ser usada no bloco de recurso [Configurações DSC](configurations.md) para especificar que o recurso deve ser executado em um conjunto de credenciais específico.</span><span class="sxs-lookup"><span data-stu-id="d4732-162">The **PsDscRunAsCredential** property can be used in [DSC configurations](configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="d4732-163">Para obter mais informações, veja [Executando o DSC com as credenciais do usuário](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="d4732-163">For more information, see [Running DSC with user credentials](runAsUser.md).</span></span>

<span data-ttu-id="d4732-164">Para acessar o contexto do usuário de dentro de um recurso personalizado, você pode usar a variável automática `$PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="d4732-164">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="d4732-165">Por exemplo, o código a seguir escreveria o contexto do usuário em que o recurso está em execução para o fluxo de saída detalhada:</span><span class="sxs-lookup"><span data-stu-id="d4732-165">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```