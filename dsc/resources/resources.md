---
ms.date: 12/12/2018
keywords: DSC,powershell,configuração,instalação
title: Recursos de DSC
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675841"
---
# <a name="dsc-resources"></a><span data-ttu-id="1de2a-103">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="1de2a-103">DSC Resources</span></span>

><span data-ttu-id="1de2a-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1de2a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="1de2a-105">Os Recursos de Configuração de Estado Desejado (DSC) fornecem os blocos de construção para uma configuração DSC.</span><span class="sxs-lookup"><span data-stu-id="1de2a-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="1de2a-106">Um recurso expõe propriedades que podem ser configuradas (esquema) e contém as funções de script do PowerShell que o Gerenciador de Configurações Local (LCM) chama de "realizar".</span><span class="sxs-lookup"><span data-stu-id="1de2a-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="1de2a-107">Um recurso pode modelar algo tão genérico quanto um arquivo ou tão específico quanto uma configuração de servidor do IIS.</span><span class="sxs-lookup"><span data-stu-id="1de2a-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="1de2a-108">Grupos de recursos semelhantes são combinados em um Módulo de DSC, que organiza todos os arquivos necessários em uma estrutura que é portátil e inclui metadados para identificar como os recursos devem ser usados.</span><span class="sxs-lookup"><span data-stu-id="1de2a-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="1de2a-109">Cada recurso tem um \* esquema que determina a sintaxe necessária para usar o recurso em um [configuração](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="1de2a-109">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span> <span data-ttu-id="1de2a-110">Esquema do recurso pode ser definida das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="1de2a-110">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="1de2a-111">**'Schema'** arquivo: A maioria dos recursos definir seus *esquema* em um 'Schema' de arquivos, usando o [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="1de2a-111">**'Schema.Mof'** file: Most resources define their *schema* in a 'schema.mof' file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="1de2a-112">**'\<Nome do recurso\>. schema.psm1'** arquivo: [Recursos de composição](../configurations/compositeConfigs.md) definir seus *esquema* em um '<ResourceName>. schema.psm1' arquivo usando um [bloco de parâmetro](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span><span class="sxs-lookup"><span data-stu-id="1de2a-112">**'\<Resource Name\>.schema.psm1'** file: [Composite Resources](../configurations/compositeConfigs.md) define their *schema* in a '<ResourceName>.schema.psm1' file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="1de2a-113">**'\<Nome do recurso\>psm1 '** arquivo: Classe com recursos de DSC definem seus *esquema* na definição de classe.</span><span class="sxs-lookup"><span data-stu-id="1de2a-113">**'\<Resource Name\>.psm1'** file: Class based DSC resources define their *schema* in the class definition.</span></span> <span data-ttu-id="1de2a-114">Itens de sintaxe são indicados como propriedades de classe.</span><span class="sxs-lookup"><span data-stu-id="1de2a-114">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="1de2a-115">Para obter mais informações, consulte [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span><span class="sxs-lookup"><span data-stu-id="1de2a-115">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="1de2a-116">Para recuperar a sintaxe para um recurso de DSC, use o [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet com o `-Syntax` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1de2a-116">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the `-Syntax` parameter.</span></span> <span data-ttu-id="1de2a-117">Esse uso é semelhante ao uso de [Get-Command](/powershell/module/microsoft.powershell.core/get-command) com o `-Syntax` para obter a sintaxe do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1de2a-117">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the `-Syntax` parameter to get cmdlet syntax.</span></span> <span data-ttu-id="1de2a-118">A saída que você consulte mostrará o modelo usado para um bloco de recursos para o recurso que você especificar.</span><span class="sxs-lookup"><span data-stu-id="1de2a-118">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="1de2a-119">A saída que você veja deve ser semelhante à saída abaixo, embora a sintaxe deste recurso foi alterado no futuro.</span><span class="sxs-lookup"><span data-stu-id="1de2a-119">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="1de2a-120">Como a sintaxe do cmdlet, o *chaves* visto entre colchetes, são opcionais.</span><span class="sxs-lookup"><span data-stu-id="1de2a-120">Like cmdlet syntax, the *keys* seen in square brackets, are optional.</span></span> <span data-ttu-id="1de2a-121">Os tipos de especificam o tipo de dados espera que cada chave.</span><span class="sxs-lookup"><span data-stu-id="1de2a-121">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="1de2a-122">O **Certifique-se de** chave é opcional porque o padrão é "Present".</span><span class="sxs-lookup"><span data-stu-id="1de2a-122">The **Ensure** key is optional because it defaults to "Present".</span></span>

```output
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

<span data-ttu-id="1de2a-123">Dentro de uma configuração, uma **Service** bloco de recurso poderia se parecer com a **Certifique-se de** que o serviço de Spooler está em execução.</span><span class="sxs-lookup"><span data-stu-id="1de2a-123">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="1de2a-124">Antes de usar um recurso em uma configuração, você deve importá-lo usando [Import-DSCResource](../configurations/import-dscresource.md).</span><span class="sxs-lookup"><span data-stu-id="1de2a-124">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

<span data-ttu-id="1de2a-125">Configurações podem conter várias instâncias do mesmo tipo de recurso.</span><span class="sxs-lookup"><span data-stu-id="1de2a-125">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="1de2a-126">Cada instância deve ser nomeada exclusivamente.</span><span class="sxs-lookup"><span data-stu-id="1de2a-126">Each instance must be uniquely named.</span></span> <span data-ttu-id="1de2a-127">No exemplo a seguir, um segundo **serviço** bloco de recurso é adicionado ao configurar o serviço "DHCP".</span><span class="sxs-lookup"><span data-stu-id="1de2a-127">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="1de2a-128">A partir do PowerShell 5.0, o intellisense foi adicionado para DSC.</span><span class="sxs-lookup"><span data-stu-id="1de2a-128">Beginning in PowerShell 5.0, intellisense was added for DSC.</span></span> <span data-ttu-id="1de2a-129">Esse novo recurso permite que você use \<guia\> e \<Ctrl + espaço\> para preenchimento automático de nomes de chave.</span><span class="sxs-lookup"><span data-stu-id="1de2a-129">This new feature allows you to use \<TAB\> and \<Ctrl+Space\> to auto-complete key names.</span></span>

![Conclusão de guia do recurso](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a><span data-ttu-id="1de2a-131">Recursos internos</span><span class="sxs-lookup"><span data-stu-id="1de2a-131">Built-in resources</span></span>

<span data-ttu-id="1de2a-132">Além dos recursos da comunidade, há recursos internos para recursos de dependência de nó cruzado, recursos para Linux e Windows.</span><span class="sxs-lookup"><span data-stu-id="1de2a-132">In addition to community resources, there are built-in resources for Windows, resources for Linux, and resources for cross-node dependency.</span></span> <span data-ttu-id="1de2a-133">Você pode usar as etapas acima para determinar a sintaxe desses recursos e como usá-los.</span><span class="sxs-lookup"><span data-stu-id="1de2a-133">You can use the steps above to determine the syntax of these resources and how to use them.</span></span> <span data-ttu-id="1de2a-134">As páginas que atendem a esses recursos foram arquivadas sob **referência**.</span><span class="sxs-lookup"><span data-stu-id="1de2a-134">The pages that serve these resources have been archived under **Reference**.</span></span>

<span data-ttu-id="1de2a-135">Windows built-in resources (Recursos internos do Windows)</span><span class="sxs-lookup"><span data-stu-id="1de2a-135">Windows built-in resources</span></span>

* [<span data-ttu-id="1de2a-136">Recurso Archive</span><span class="sxs-lookup"><span data-stu-id="1de2a-136">Archive Resource</span></span>](../reference/resources/windows/archiveResource.md)
* [<span data-ttu-id="1de2a-137">Recurso Environment</span><span class="sxs-lookup"><span data-stu-id="1de2a-137">Environment Resource</span></span>](../reference/resources/windows/environmentResource.md)
* [<span data-ttu-id="1de2a-138">Recurso File</span><span class="sxs-lookup"><span data-stu-id="1de2a-138">File Resource</span></span>](../reference/resources/windows/fileResource.md)
* [<span data-ttu-id="1de2a-139">Recurso Group</span><span class="sxs-lookup"><span data-stu-id="1de2a-139">Group Resource</span></span>](../reference/resources/windows/groupResource.md)
* [<span data-ttu-id="1de2a-140">Recurso GroupSet</span><span class="sxs-lookup"><span data-stu-id="1de2a-140">GroupSet Resource</span></span>](../reference/resources/windows/groupSetResource.md)
* [<span data-ttu-id="1de2a-141">Recurso Log</span><span class="sxs-lookup"><span data-stu-id="1de2a-141">Log Resource</span></span>](../reference/resources/windows/logResource.md)
* [<span data-ttu-id="1de2a-142">Recurso Package</span><span class="sxs-lookup"><span data-stu-id="1de2a-142">Package Resource</span></span>](../reference/resources/windows/packageResource.md)
* [<span data-ttu-id="1de2a-143">Recurso ProcessSet</span><span class="sxs-lookup"><span data-stu-id="1de2a-143">ProcessSet Resource</span></span>](../reference/resources/windows/ProcessSetResource.md)
* [<span data-ttu-id="1de2a-144">Recurso Registry</span><span class="sxs-lookup"><span data-stu-id="1de2a-144">Registry Resource</span></span>](../reference/resources/windows/registryResource.md)
* [<span data-ttu-id="1de2a-145">Recurso Script</span><span class="sxs-lookup"><span data-stu-id="1de2a-145">Script Resource</span></span>](../reference/resources/windows/scriptResource.md)
* [<span data-ttu-id="1de2a-146">Recurso Service</span><span class="sxs-lookup"><span data-stu-id="1de2a-146">Service Resource</span></span>](../reference/resources/windows/serviceResource.md)
* [<span data-ttu-id="1de2a-147">Recurso ServiceSet</span><span class="sxs-lookup"><span data-stu-id="1de2a-147">ServiceSet Resource</span></span>](../reference/resources/windows/serviceSetResource.md)
* [<span data-ttu-id="1de2a-148">Recurso User</span><span class="sxs-lookup"><span data-stu-id="1de2a-148">User Resource</span></span>](../reference/resources/windows/userResource.md)
* [<span data-ttu-id="1de2a-149">Recurso WindowsFeature</span><span class="sxs-lookup"><span data-stu-id="1de2a-149">WindowsFeature Resource</span></span>](../reference/resources/windows/windowsFeatureResource.md)
* [<span data-ttu-id="1de2a-150">Recurso WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="1de2a-150">WindowsFeatureSet Resource</span></span>](../reference/resources/windows/windowsFeatureSetResource.md)
* [<span data-ttu-id="1de2a-151">Recurso WindowsOptionalFeature</span><span class="sxs-lookup"><span data-stu-id="1de2a-151">WindowsOptionalFeature Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [<span data-ttu-id="1de2a-152">Recurso WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="1de2a-152">WindowsOptionalFeatureSet Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [<span data-ttu-id="1de2a-153">Recurso WindowsPackageCabResource</span><span class="sxs-lookup"><span data-stu-id="1de2a-153">WindowsPackageCabResource Resource</span></span>](../reference/resources/windows/windowsPackageCabResource.md)
* [<span data-ttu-id="1de2a-154">Recurso WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="1de2a-154">WindowsProcess Resource</span></span>](../reference/resources/windows/windowsProcessResource.md)

<span data-ttu-id="1de2a-155">[Dependência de nó cruzado](../configurations/crossNodeDependencies.md) recursos</span><span class="sxs-lookup"><span data-stu-id="1de2a-155">[Cross-Node dependency](../configurations/crossNodeDependencies.md) resources</span></span>

* [<span data-ttu-id="1de2a-156">WaitForAll recursos</span><span class="sxs-lookup"><span data-stu-id="1de2a-156">WaitForAll Resource</span></span>](../reference/resources/windows/waitForAllResource.md)
* [<span data-ttu-id="1de2a-157">WaitForSome recursos</span><span class="sxs-lookup"><span data-stu-id="1de2a-157">WaitForSome Resource</span></span>](../reference/resources/windows/waitForSomeResource.md)
* [<span data-ttu-id="1de2a-158">WaitForAny recursos</span><span class="sxs-lookup"><span data-stu-id="1de2a-158">WaitForAny Resource</span></span>](../reference/resources/windows/waitForAnyResource.md)

<span data-ttu-id="1de2a-159">Recursos do pacote de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="1de2a-159">Package Management resources</span></span>

* [<span data-ttu-id="1de2a-160">Recurso PackageManagement</span><span class="sxs-lookup"><span data-stu-id="1de2a-160">PackageManagement Resource</span></span>](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [<span data-ttu-id="1de2a-161">Recurso PackageManagementSource</span><span class="sxs-lookup"><span data-stu-id="1de2a-161">PackageManagementSource Resource</span></span>](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

<span data-ttu-id="1de2a-162">Recursos do Linux</span><span class="sxs-lookup"><span data-stu-id="1de2a-162">Linux resources</span></span>

* [<span data-ttu-id="1de2a-163">Recurso Archive do Linux</span><span class="sxs-lookup"><span data-stu-id="1de2a-163">Linux Archive Resource</span></span>](../reference/resources/linux/lnxArchiveResource.md)
* [<span data-ttu-id="1de2a-164">Recursos de ambiente do Linux</span><span class="sxs-lookup"><span data-stu-id="1de2a-164">Linux Environment Resource</span></span>](../reference/resources/linux/lnxEnvironmentResource.md)
* [<span data-ttu-id="1de2a-165">Recurso de FileLine do Linux</span><span class="sxs-lookup"><span data-stu-id="1de2a-165">Linux FileLine Resource</span></span>](../reference/resources/linux/lnxFileLineResource.md)
* [<span data-ttu-id="1de2a-166">Recursos de arquivo do Linux</span><span class="sxs-lookup"><span data-stu-id="1de2a-166">Linux File Resource</span></span>](../reference/resources/linux/lnxFileResource.md)
* [<span data-ttu-id="1de2a-167">Recurso de grupo Linux</span><span class="sxs-lookup"><span data-stu-id="1de2a-167">Linux Group Resource</span></span>](../reference/resources/linux/lnxGroupResource.md)
* [<span data-ttu-id="1de2a-168">Recurso do pacote do Linux</span><span class="sxs-lookup"><span data-stu-id="1de2a-168">Linux Package Resource</span></span>](../reference/resources/linux/lnxPackageResource.md)
* [<span data-ttu-id="1de2a-169">Recursos de Script do Linux</span><span class="sxs-lookup"><span data-stu-id="1de2a-169">Linux Script Resource</span></span>](../reference/resources/linux/lnxScriptResource.md)
* [<span data-ttu-id="1de2a-170">Recurso de serviço do Linux</span><span class="sxs-lookup"><span data-stu-id="1de2a-170">Linux Service Resource</span></span>](../reference/resources/linux/lnxServiceResource.md)
* [<span data-ttu-id="1de2a-171">Linux SshAuthorizedKeys Resource</span><span class="sxs-lookup"><span data-stu-id="1de2a-171">Linux SshAuthorizedKeys Resource</span></span>](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [<span data-ttu-id="1de2a-172">Recurso de usuário do Linux</span><span class="sxs-lookup"><span data-stu-id="1de2a-172">Linux User Resource</span></span>](../reference/resources/linux/lnxUserResource.md)
