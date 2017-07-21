---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Recursos de composição: usando uma configuração DSC como um recurso"
ms.openlocfilehash: 6c9a878c45a3e999e20dec5766ee8bda409905d3
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a><span data-ttu-id="eefdc-103">Recursos de composição: usando uma configuração DSC como um recurso</span><span class="sxs-lookup"><span data-stu-id="eefdc-103">Composite resources: Using a DSC configuration as a resource</span></span>

> <span data-ttu-id="eefdc-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="eefdc-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="eefdc-105">Em situações reais, as configurações podem se tornar longas e complexas, chamando muitos recursos diferentes e definindo um grande número de propriedades.</span><span class="sxs-lookup"><span data-stu-id="eefdc-105">In real-world situations, configurations can become long and complex, calling many different resources and setting a vast number of properties.</span></span> <span data-ttu-id="eefdc-106">Para ajudar a resolver essa complexidade, é possível usar uma configuração do tipo Configuração de Estado Desejado (DSC) do Windows PowerShell como um recurso para outras configurações.</span><span class="sxs-lookup"><span data-stu-id="eefdc-106">To help address this complexity, you can use a Windows PowerShell Desired State Configuration (DSC) configuration as a resource for other configurations.</span></span> <span data-ttu-id="eefdc-107">Chamamos isso de recurso de composição.</span><span class="sxs-lookup"><span data-stu-id="eefdc-107">We call this a composite resource.</span></span> <span data-ttu-id="eefdc-108">Um recurso de composição é uma configuração DSC que usa parâmetros.</span><span class="sxs-lookup"><span data-stu-id="eefdc-108">A composite resource is a DSC configuration that takes parameters.</span></span> <span data-ttu-id="eefdc-109">Os parâmetros da configuração atuam como as propriedades do recurso.</span><span class="sxs-lookup"><span data-stu-id="eefdc-109">The parameters of the configuration act as the properties of the resource.</span></span> <span data-ttu-id="eefdc-110">A configuração é salva como um arquivo com uma extensão **. schema.psm1** e assume o lugar do esquema MOF e do script de recurso em um recurso típico de DSC (para obter mais informações sobre os recursos de DSC, consulte [Recursos de Configuração de Estado Desejado do Windows PowerShell](resources.md).</span><span class="sxs-lookup"><span data-stu-id="eefdc-110">The configuration is saved as a file with a **.schema.psm1** extension, and takes the place of both the MOF schema and the resource script in a typical DSC resource (for more information about DSC resources, see [Windows PowerShell Desired State Configuration Resources](resources.md).</span></span>

## <a name="creating-the-composite-resource"></a><span data-ttu-id="eefdc-111">Criando o recurso de composição</span><span class="sxs-lookup"><span data-stu-id="eefdc-111">Creating the composite resource</span></span>

<span data-ttu-id="eefdc-112">Em nosso exemplo, criamos uma configuração que invoca uma série de recursos existentes para configurar máquinas virtuais.</span><span class="sxs-lookup"><span data-stu-id="eefdc-112">In our example, we create a configuration that invokes a number of existing resources to configure virtual machines.</span></span> <span data-ttu-id="eefdc-113">Em vez de especificar os valores a serem definidos em blocos de configuração, a configuração pega uma série de parâmetros que são usados nos blocos de configuração.</span><span class="sxs-lookup"><span data-stu-id="eefdc-113">Instead of specifying the values to be set in configuration blocks, the configuration takes a number of parameters that are then used in the configuration blocks.</span></span>

```powershell
Configuration xVirtualMachine
{
    param
    (
        # Name of VMs
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String[]] $VMName,

        # Name of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchName,

        # Type of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchType,

        # Source Path for VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDParentPath,

        # Destination path for diff VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDPath,

        # Startup Memory for VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMStartupMemory,

        # State of the VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMState
    )

    # Import the module that defines custom resources
    Import-DscResource -Module xComputerManagement,xHyper-V

    # Install the Hyper-V role
    WindowsFeature HyperV
    {
        Ensure = "Present"
        Name = "Hyper-V"
    }

    # Create the virtual switch
    xVMSwitch $SwitchName
    {
        Ensure = "Present"
        Name = $SwitchName
        Type = $SwitchType
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check for Parent VHD file
    File ParentVHDFile
    {
        Ensure = "Present"
        DestinationPath = $VHDParentPath
        Type = "File"
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check the destination VHD folder
    File VHDFolder
    {
        Ensure = "Present"
        DestinationPath = $VHDPath
        Type = "Directory"
        DependsOn = "[File]ParentVHDFile"
    }

    # Creae VM specific diff VHD
    foreach ($Name in $VMName)
    {
        xVHD "VHD$Name"
        {
            Ensure = "Present"
            Name = $Name
            Path = $VHDPath
            ParentPath = $VHDParentPath
            DependsOn = @("[WindowsFeature]HyperV",
                          "[File]VHDFolder")
        }
    }

    # Create VM using the above VHD
    foreach($Name in $VMName)
    {
        xVMHyperV "VMachine$Name"
        {
            Ensure = "Present"
            Name = $Name
            VhDPath = (Join-Path -Path $VHDPath -ChildPath $Name)
            SwitchName = $SwitchName
            StartupMemory = $VMStartupMemory
            State = $VMState
            MACAddress = $MACAddress
            WaitForIP = $true
            DependsOn = @("[WindowsFeature]HyperV",
                          "[xVHD]VHD$Name")
        }
    }
}
```

### <a name="saving-the-configuration-as-a-composite-resource"></a><span data-ttu-id="eefdc-114">Salvando a configuração como um recurso de composição</span><span class="sxs-lookup"><span data-stu-id="eefdc-114">Saving the configuration as a composite resource</span></span>

<span data-ttu-id="eefdc-115">Para usar a configuração com parâmetros como um recurso de DSC, salve-a em uma estrutura de diretórios semelhante à de qualquer outro recurso baseado em MOF e nomeie-a com uma extensão **. schema.psm1**.</span><span class="sxs-lookup"><span data-stu-id="eefdc-115">To use the parameterized configuration as a DSC resource, save it in a directory structure like that of any other MOF-based resource, and name it with a **.schema.psm1** extension.</span></span> <span data-ttu-id="eefdc-116">Para esse exemplo, chamaremos o arquivo de **xVirtualMachine.schema.psm1**.</span><span class="sxs-lookup"><span data-stu-id="eefdc-116">For this example, we’ll name the file **xVirtualMachine.schema.psm1**.</span></span> <span data-ttu-id="eefdc-117">Você também precisa criar um manifesto chamado **xVirtualMachine.psd1**, que contém a linha a seguir.</span><span class="sxs-lookup"><span data-stu-id="eefdc-117">You also need to create a manifest named **xVirtualMachine.psd1** that contains the following line.</span></span> <span data-ttu-id="eefdc-118">Observe que este se soma ao **MyDscResources.psd1**, o manifesto de módulo para todos os recursos na pasta **MyDscResources**.</span><span class="sxs-lookup"><span data-stu-id="eefdc-118">Note that this is in addition to **MyDscResources.psd1**, the module manifest for all resources under the **MyDscResources** folder.</span></span>

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

<span data-ttu-id="eefdc-119">Quando terminar, a estrutura de pastas deve ser a seguinte.</span><span class="sxs-lookup"><span data-stu-id="eefdc-119">When you are done, the folder structure should be as follows.</span></span>

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

<span data-ttu-id="eefdc-120">O recurso é detectável usando o cmdlet Get-DscResource; suas propriedades são detectáveis por meio desse cmdlet ou usando o preenchimento automático com **Ctrl + espaço** no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eefdc-120">The resource is now discoverable by using the Get-DscResource cmdlet, and its properties are discoverable by either that cmdlet or by using **Ctrl+Space** auto-complete in the Windows PowerShell ISE.</span></span>

## <a name="using-the-composite-resource"></a><span data-ttu-id="eefdc-121">Usando o recurso de composição</span><span class="sxs-lookup"><span data-stu-id="eefdc-121">Using the composite resource</span></span>

<span data-ttu-id="eefdc-122">Em seguida, criamos uma configuração que chama o recurso de composição.</span><span class="sxs-lookup"><span data-stu-id="eefdc-122">Next we create a configuration that calls the composite resource.</span></span> <span data-ttu-id="eefdc-123">Essa configuração chama o recurso de composição xVirtualMachine para criar uma máquina virtual e, em seguida, chama o recurso **xComputer** para renomeá-lo.</span><span class="sxs-lookup"><span data-stu-id="eefdc-123">This configuration calls the xVirtualMachine composite resource to create a virtual machine, and then calls the **xComputer** resource to rename it.</span></span>

```powershell

configuration RenameVM
{

    Import-DscResource -Module TestCompositeResource
    Node localhost
    {
        xVirtualMachine VM
        {
            VMName = "Test"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }

    Node "192.168.10.1"
    {
        xComputer Name
        {
            Name = "SQL01"
            DomainName = "fourthcoffee.com"
        }
    }
}
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="eefdc-124">Dando suporte a PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="eefdc-124">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="eefdc-125">**Observação:** **PsDscRunAsCredential** tem suporte no PowerShell 5.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="eefdc-125">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="eefdc-126">A propriedade **PsDscRunAsCredential** pode ser usada no bloco de recurso [Configurações DSC](configurations.md) para especificar que o recurso deve ser executado em um conjunto de credenciais específico.</span><span class="sxs-lookup"><span data-stu-id="eefdc-126">The **PsDscRunAsCredential** property can be used in [DSC configurations](configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="eefdc-127">Para obter mais informações, veja [Executando o DSC com as credenciais do usuário](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="eefdc-127">For more information, see [Running DSC with user credentials](runAsUser.md).</span></span>

<span data-ttu-id="eefdc-128">Para acessar o contexto do usuário de dentro de um recurso personalizado, você pode usar a variável automática `$PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="eefdc-128">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="eefdc-129">Por exemplo, o código a seguir escreveria o contexto do usuário em que o recurso está em execução para o fluxo de saída detalhada:</span><span class="sxs-lookup"><span data-stu-id="eefdc-129">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="eefdc-130">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="eefdc-130">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="eefdc-131">Conceitos</span><span class="sxs-lookup"><span data-stu-id="eefdc-131">Concepts</span></span>
* [<span data-ttu-id="eefdc-132">Escrevendo um recurso personalizado de DSC com MOF</span><span class="sxs-lookup"><span data-stu-id="eefdc-132">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="eefdc-133">Introdução à Configuração de Estado Desejado do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eefdc-133">Get Started with Windows PowerShell Desired State Configuration</span></span>](overview.md)

