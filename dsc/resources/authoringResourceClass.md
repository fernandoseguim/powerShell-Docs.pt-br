---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Escrevendo um recurso personalizado de DSC com classes do PowerShell
ms.openlocfilehash: 34356f65bcb83153e7395a16d2a4a5cf2e507332
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676414"
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a><span data-ttu-id="c616d-103">Escrevendo um recurso personalizado de DSC com classes do PowerShell</span><span class="sxs-lookup"><span data-stu-id="c616d-103">Writing a custom DSC resource with PowerShell classes</span></span>

> <span data-ttu-id="c616d-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c616d-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="c616d-105">Com a introdução de classes do PowerShell no Windows PowerShell 5.0, já é possível definir um recurso de DSC criando uma classe.</span><span class="sxs-lookup"><span data-stu-id="c616d-105">With the introduction of PowerShell classes in Windows PowerShell 5.0, you can now define a DSC resource by creating a class.</span></span> <span data-ttu-id="c616d-106">A classe define o esquema e a implementação do recurso; portanto, não há necessidade de criar um arquivo MOF separado.</span><span class="sxs-lookup"><span data-stu-id="c616d-106">The class defines both the schema and the implementation of the resource, so there is no need to create a separate MOF file.</span></span> <span data-ttu-id="c616d-107">A estrutura de pastas para um recurso baseado em classe também é mais simples, pois uma pasta **DSCResources** não é necessária.</span><span class="sxs-lookup"><span data-stu-id="c616d-107">The folder structure for a class-based resource is also simpler, because a **DSCResources** folder is not necessary.</span></span>

<span data-ttu-id="c616d-108">Em um recurso de DSC baseado em classes, o esquema é definido como propriedades da classe que pode ser modificado com atributos para especificar o tipo de propriedade...</span><span class="sxs-lookup"><span data-stu-id="c616d-108">In a class-based DSC resource, the schema is defined as properties of the class which can be modified with attributes to specify the property type..</span></span> <span data-ttu-id="c616d-109">O recurso é implementado pelos métodos **Get ()**, **Set()** e **Test ()** (equivalentes às funções **Get-TargetResource**, **Set-TargetResource** e **Test-TargetResource** em um recurso de script).</span><span class="sxs-lookup"><span data-stu-id="c616d-109">The resource is implemented by **Get()**, **Set()**, and **Test()** methods (equivalent to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="c616d-110">Neste tópico, criaremos um recurso simples chamado **FileResource**, que gerencia um arquivo em um caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="c616d-110">In this topic, we will create a simple resource named **FileResource** that manages a file in a specified path.</span></span>

<span data-ttu-id="c616d-111">Para obter mais informações sobre recursos de DSC, consulte [Criar recursos personalizados de configuração de estado desejado do Windows PowerShell](authoringResource.md)</span><span class="sxs-lookup"><span data-stu-id="c616d-111">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md)</span></span>

><span data-ttu-id="c616d-112">**Observação:** Não há suporte para coleções genéricas em recursos baseados em classe.</span><span class="sxs-lookup"><span data-stu-id="c616d-112">**Note:** Generic collections are not supported in class-based resources.</span></span>

## <a name="folder-structure-for-a-class-resource"></a><span data-ttu-id="c616d-113">Estrutura de pastas para um recurso de classe</span><span class="sxs-lookup"><span data-stu-id="c616d-113">Folder structure for a class resource</span></span>

<span data-ttu-id="c616d-114">Para implementar um recurso personalizado de DSC com uma classe do PowerShell, crie a seguinte estrutura de pastas.</span><span class="sxs-lookup"><span data-stu-id="c616d-114">To implement a DSC custom resource with a PowerShell class, create the following folder structure.</span></span> <span data-ttu-id="c616d-115">A classe é definida em **MyDscResource.psm1** e o manifesto de módulo é definido em **MyDscResource.psd1**.</span><span class="sxs-lookup"><span data-stu-id="c616d-115">The class is defined in **MyDscResource.psm1** and the module manifest is defined in **MyDscResource.psd1**.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        MyDscResource.psm1
        MyDscResource.psd1
```

## <a name="create-the-class"></a><span data-ttu-id="c616d-116">Criar a classe</span><span class="sxs-lookup"><span data-stu-id="c616d-116">Create the class</span></span>

<span data-ttu-id="c616d-117">A palavra-chave class é utilizada para criar uma classe do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c616d-117">You use the class keyword to create a PowerShell class.</span></span> <span data-ttu-id="c616d-118">Para especificar que uma classe é um recurso de DSC, use o atributo **DscResource()**.</span><span class="sxs-lookup"><span data-stu-id="c616d-118">To specify that a class is a DSC resource, use the **DscResource()** attribute.</span></span> <span data-ttu-id="c616d-119">O nome da classe é o nome do recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="c616d-119">The name of the class is the name of the DSC resource.</span></span>

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a><span data-ttu-id="c616d-120">Declarar propriedades</span><span class="sxs-lookup"><span data-stu-id="c616d-120">Declare properties</span></span>

<span data-ttu-id="c616d-121">O esquema do recurso de DSC é definido como propriedades da classe.</span><span class="sxs-lookup"><span data-stu-id="c616d-121">The DSC resource schema is defined as properties of the class.</span></span> <span data-ttu-id="c616d-122">Declaramos três propriedades da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="c616d-122">We declare three properties as follows.</span></span>

```powershell
[DscProperty(Key)]
[string]$Path

[DscProperty(Mandatory)]
[Ensure] $Ensure

[DscProperty(Mandatory)]
[string] $SourcePath

[DscProperty(NotConfigurable)]
[Nullable[datetime]] $CreationTime
```

<span data-ttu-id="c616d-123">Observe que as propriedades são modificadas por atributos.</span><span class="sxs-lookup"><span data-stu-id="c616d-123">Notice that the properties are modified by attributes.</span></span> <span data-ttu-id="c616d-124">O significado dos atributos é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c616d-124">The meaning of the attributes is as follows:</span></span>

- <span data-ttu-id="c616d-125">**DscProperty(Key)**: A propriedade é necessária.</span><span class="sxs-lookup"><span data-stu-id="c616d-125">**DscProperty(Key)**: The property is required.</span></span> <span data-ttu-id="c616d-126">A propriedade é uma chave.</span><span class="sxs-lookup"><span data-stu-id="c616d-126">The property is a key.</span></span> <span data-ttu-id="c616d-127">Os valores de todas as propriedades marcadas como chaves devem se combinar para identificar exclusivamente uma instância de recursos dentro de uma configuração.</span><span class="sxs-lookup"><span data-stu-id="c616d-127">The values of all properties marked as keys must combine to uniquely identify a resource instance within a configuration.</span></span>
- <span data-ttu-id="c616d-128">**Dscproperty (Mandatory)**: A propriedade é necessária.</span><span class="sxs-lookup"><span data-stu-id="c616d-128">**DscProperty(Mandatory)**: The property is required.</span></span>
- <span data-ttu-id="c616d-129">**DscProperty(NotConfigurable)**: a propriedade é somente leitura.</span><span class="sxs-lookup"><span data-stu-id="c616d-129">**DscProperty(NotConfigurable)**: The property is read-only.</span></span> <span data-ttu-id="c616d-130">As propriedades marcadas com esse atributo não podem ser definidas por uma configuração, mas são preenchidas pelo método **Get ()** quando presentes.</span><span class="sxs-lookup"><span data-stu-id="c616d-130">Properties marked with this attribute cannot be set by a configuration, but are populated by the **Get()** method when present.</span></span>
- <span data-ttu-id="c616d-131">**DscProperty()**: A propriedade é configurável, mas não é necessária.</span><span class="sxs-lookup"><span data-stu-id="c616d-131">**DscProperty()**: The property is configurable, but it is not required.</span></span>

<span data-ttu-id="c616d-132">As propriedades **$Path** e **$SourcePath** são ambas cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c616d-132">The **$Path** and **$SourcePath** properties are both strings.</span></span> <span data-ttu-id="c616d-133">O **$CreationTime** é uma propriedade [DateTime](/dotnet/api/system.datetime).</span><span class="sxs-lookup"><span data-stu-id="c616d-133">The **$CreationTime** is a [DateTime](/dotnet/api/system.datetime) property.</span></span> <span data-ttu-id="c616d-134">A propriedade **$Ensure** é um tipo de enumeração definido da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="c616d-134">The **$Ensure** property is an enumeration type, defined as follows.</span></span>

```powershell
enum Ensure
{
    Absent
    Present
}
```

### <a name="implementing-the-methods"></a><span data-ttu-id="c616d-135">Implementando os métodos</span><span class="sxs-lookup"><span data-stu-id="c616d-135">Implementing the methods</span></span>

<span data-ttu-id="c616d-136">Os métodos **Get()**, **Set()** e **Test()** são análogos às funções **Get-TargetResource**, **Set-TargetResource** e **Test-TargetResource** em um recurso de script.</span><span class="sxs-lookup"><span data-stu-id="c616d-136">The **Get()**, **Set()**, and **Test()** methods are analogous to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="c616d-137">Esse código também inclui a função CopyFile (), uma função auxiliar que copia o arquivo de **$SourcePath** para **$Path**.</span><span class="sxs-lookup"><span data-stu-id="c616d-137">This code also includes the CopyFile() function, a helper function that copies the file from **$SourcePath** to **$Path**.</span></span>

```powershell
    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)

        if ($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ErrorAction Ignore

        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = New-Object -TypeName System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
```

### <a name="the-complete-file"></a><span data-ttu-id="c616d-138">O arquivo completo</span><span class="sxs-lookup"><span data-stu-id="c616d-138">The complete file</span></span>

<span data-ttu-id="c616d-139">Segue o arquivo de classe completo.</span><span class="sxs-lookup"><span data-stu-id="c616d-139">The complete class file follows.</span></span>

```powershell
enum Ensure
{
    Absent
    Present
}

<#
   This resource manages the file in a specific path.
   [DscResource()] indicates the class is a DSC resource
#>

[DscResource()]
class FileResource
{
    <#
       This property is the fully qualified path to the file that is
       expected to be present or absent.

       The [DscProperty(Key)] attribute indicates the property is a
       key and its value uniquely identifies a resource instance.
       Defining this attribute also means the property is required
       and DSC will ensure a value is set before calling the resource.

       A DSC resource must define at least one key property.
    #>
    [DscProperty(Key)]
    [string]$Path

    <#
        This property indicates if the settings should be present or absent
        on the system. For present, the resource ensures the file pointed
        to by $Path exists. For absent, it ensures the file point to by
        $Path does not exist.

        The [DscProperty(Mandatory)] attribute indicates the property is
        required and DSC will guarantee it is set.

        If Mandatory is not specified or if it is defined as
        Mandatory=$false, the value is not guaranteed to be set when DSC
        calls the resource.  This is appropriate for optional properties.
    #>
    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    <#
       This property defines the fully qualified path to a file that will
       be placed on the system if $Ensure = Present and $Path does not
        exist.

       NOTE: This property is required because [DscProperty(Mandatory)] is
        set.
    #>
    [DscProperty(Mandatory)]
    [string] $SourcePath

    <#
       This property reports the file's create timestamp.

       [DscProperty(NotConfigurable)] attribute indicates the property is
       not configurable in DSC configuration.  Properties marked this way
       are populated by the Get() method to report additional details
       about the resource when it is present.

    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if ($this.ensure -eq [Ensure]::Present)
        {
            if (-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ea Ignore
        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = new-object System.IO.FileInfo($this.Path)
        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                 to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
} # This module defines a class for a DSC "FileResource" provider.
```

## <a name="create-a-manifest"></a><span data-ttu-id="c616d-140">Criar um manifesto</span><span class="sxs-lookup"><span data-stu-id="c616d-140">Create a manifest</span></span>

<span data-ttu-id="c616d-141">Para disponibilizar um recurso baseado em classes para o mecanismo de DSC, você precisa incluir uma declaração **DscResourcesToExport** no arquivo de manifesto que instrui o módulo para exportar recursos.</span><span class="sxs-lookup"><span data-stu-id="c616d-141">To make a class-based resource available to the DSC engine, you must include a **DscResourcesToExport** statement in the manifest file that instructs the module to export the resource.</span></span> <span data-ttu-id="c616d-142">Nosso manifesto tem essa aparência:</span><span class="sxs-lookup"><span data-stu-id="c616d-142">Our manifest looks like this:</span></span>

```powershell
@{

# Script module or binary module file associated with this manifest.
RootModule = 'MyDscResource.psm1'

DscResourcesToExport = 'FileResource'

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '81624038-5e71-40f8-8905-b1a87afe22d7'

# Author of this module
Author = 'Microsoft Corporation'

# Company or vendor of this module
CompanyName = 'Microsoft Corporation'

# Copyright statement for this module
Copyright = '(c) 2014 Microsoft. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''
}
```

## <a name="test-the-resource"></a><span data-ttu-id="c616d-143">Testar o recurso</span><span class="sxs-lookup"><span data-stu-id="c616d-143">Test the resource</span></span>

<span data-ttu-id="c616d-144">Depois de salvar a classe e os arquivos de manifesto na estrutura de pastas, conforme descrito anteriormente, você pode criar uma configuração que use o novo recurso.</span><span class="sxs-lookup"><span data-stu-id="c616d-144">After saving the class and manifest files in the folder structure as described earlier, you can create a configuration that uses the new resource.</span></span> <span data-ttu-id="c616d-145">Para obter informações sobre como executar uma configuração DSC, consulte [Impondo configurações](../pull-server/enactingConfigurations.md).</span><span class="sxs-lookup"><span data-stu-id="c616d-145">For information about how to run a DSC configuration, see [Enacting configurations](../pull-server/enactingConfigurations.md).</span></span> <span data-ttu-id="c616d-146">A configuração a seguir verificará se o arquivo em `c:\test\test.txt` existe e, em caso negativo, copia o arquivo de `c:\test.txt` (você deve criar `c:\test.txt` antes de executar a configuração).</span><span class="sxs-lookup"><span data-stu-id="c616d-146">The following configuration will check to see whether the file at `c:\test\test.txt` exists, and, if not, copies the file from `c:\test.txt` (you should create `c:\test.txt` before you run the configuration).</span></span>

```powershell
Configuration Test
{
    Import-DSCResource -module MyDscResource
    FileResource file
    {
        Path = "C:\test\test.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    }
}
Test
Start-DscConfiguration -Wait -Force Test
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="c616d-147">Dando suporte a PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="c616d-147">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="c616d-148">**Observação:** **PsDscRunAsCredential** tem suporte no PowerShell 5.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="c616d-148">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="c616d-149">A propriedade **PsDscRunAsCredential** pode ser usada no bloco de recurso [Configurações DSC](../configurations/configurations.md) para especificar que o recurso deve ser executado em um conjunto de credenciais específico.</span><span class="sxs-lookup"><span data-stu-id="c616d-149">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="c616d-150">Para obter mais informações, veja [Executando o DSC com as credenciais do usuário](../configurations/runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="c616d-150">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a><span data-ttu-id="c616d-151">Solicitar ou desautorizar PsDscRunAsCredential para o recurso</span><span class="sxs-lookup"><span data-stu-id="c616d-151">Require or disallow PsDscRunAsCredential for your resource</span></span>

<span data-ttu-id="c616d-152">O atributo **DscResource()** usa um parâmetro opcional **RunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="c616d-152">The **DscResource()** attribute takes an optional parameter **RunAsCredential**.</span></span>
<span data-ttu-id="c616d-153">Esse parâmetro usa um dos três valores:</span><span class="sxs-lookup"><span data-stu-id="c616d-153">This parameter takes one of three values:</span></span>

- <span data-ttu-id="c616d-154">`Optional` O **PsDscRunAsCredential** é opcional para as configurações que chamam esse recurso.</span><span class="sxs-lookup"><span data-stu-id="c616d-154">`Optional` **PsDscRunAsCredential** is optional for configurations that call this resource.</span></span> <span data-ttu-id="c616d-155">Este é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="c616d-155">This is the default value.</span></span>
- <span data-ttu-id="c616d-156">`Mandatory` O **PsDscRunAsCredential** deve ser usado para qualquer configuração que chame esse recurso.</span><span class="sxs-lookup"><span data-stu-id="c616d-156">`Mandatory` **PsDscRunAsCredential** must be used for any configuration that calls this resource.</span></span>
- <span data-ttu-id="c616d-157">`NotSupported` As configurações que chamam este recurso não podem usar o **PsDscRunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="c616d-157">`NotSupported` Configurations that call this resource cannot use **PsDscRunAsCredential**.</span></span>
- <span data-ttu-id="c616d-158">`Default` Igual a `Optional`.</span><span class="sxs-lookup"><span data-stu-id="c616d-158">`Default` Same as `Optional`.</span></span>

<span data-ttu-id="c616d-159">Por exemplo, use o seguinte atributo para especificar que o recurso personalizado não dá suporte ao uso de **PsDscRunAsCredential**:</span><span class="sxs-lookup"><span data-stu-id="c616d-159">For example, use the following attribute to specify that your custom resource does not support using **PsDscRunAsCredential**:</span></span>

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="declaring-multiple-class-resources-in-a-module"></a><span data-ttu-id="c616d-160">Declarar vários recursos de classe em um módulo</span><span class="sxs-lookup"><span data-stu-id="c616d-160">Declaring multiple class resources in a module</span></span>

<span data-ttu-id="c616d-161">Um módulo pode definir vários recursos de DSC baseado em classe.</span><span class="sxs-lookup"><span data-stu-id="c616d-161">A module can define multiple class based DSC resources.</span></span> <span data-ttu-id="c616d-162">Você pode criar a estrutura de pasta das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="c616d-162">You can create the folder structure in the following ways:</span></span>

1. <span data-ttu-id="c616d-163">Definir o primeiro recurso no "<ModuleName>. psm1" recursos de arquivo e subsequentes sob o **DSCResources** pasta.</span><span class="sxs-lookup"><span data-stu-id="c616d-163">Define the first resource in the "<ModuleName>.psm1" file and subsequent resources under the **DSCResources** folder.</span></span>

   ```
   $env:ProgramFiles\WindowsPowerShell\Modules (folder)
        |- MyDscResource (folder)
           |- MyDscResource.psm1
              MyDscResource.psd1
        |- DSCResources
           |- SecondResource.psm1
   ```

2. <span data-ttu-id="c616d-164">Definir todos os recursos sob o **DSCResources** pasta.</span><span class="sxs-lookup"><span data-stu-id="c616d-164">Define all resources under the **DSCResources** folder.</span></span>

   ```
   $env:ProgramFiles\WindowsPowerShell\Modules (folder)
        |- MyDscResource (folder)
           |- MyDscResource.psm1
              MyDscResource.psd1
        |- DSCResources
           |- FirstResource.psm1
              SecondResource.psm1
   ```

> [!NOTE]
> <span data-ttu-id="c616d-165">Nos exemplos acima, adicione todos os arquivos PSM1 sob o **DSCResources** para o **NestedModules** chave em seu arquivo PSD1.</span><span class="sxs-lookup"><span data-stu-id="c616d-165">In the examples above, add any PSM1 files under the **DSCResources** to the **NestedModules** key in your PSD1 file.</span></span>

### <a name="access-the-user-context"></a><span data-ttu-id="c616d-166">Acessar o contexto do usuário</span><span class="sxs-lookup"><span data-stu-id="c616d-166">Access the user context</span></span>

<span data-ttu-id="c616d-167">Para acessar o contexto do usuário de dentro de um recurso personalizado, você pode usar a variável automática `$global:PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="c616d-167">To access the user context from within a custom resource, you can use the automatic variable `$global:PsDscContext`.</span></span>

<span data-ttu-id="c616d-168">Por exemplo, o código a seguir escreveria o contexto do usuário em que o recurso está em execução para o fluxo de saída detalhada:</span><span class="sxs-lookup"><span data-stu-id="c616d-168">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="c616d-169">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="c616d-169">See Also</span></span>

[<span data-ttu-id="c616d-170">Criar recursos personalizados de configuração de estado desejado do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c616d-170">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)
