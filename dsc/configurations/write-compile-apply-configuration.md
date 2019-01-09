---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, serviço, a instalação
title: Escrever, compilar e aplicar uma configuração
ms.openlocfilehash: fa4d98fd12202439ba7025fd8af3fa398653ca05
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400153"
---
> <span data-ttu-id="e29c7-103">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e29c7-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="write-compile-and-apply-a-configuration"></a><span data-ttu-id="e29c7-104">Escrever, compilar e aplicar uma configuração</span><span class="sxs-lookup"><span data-stu-id="e29c7-104">Write, Compile, and Apply a Configuration</span></span>

<span data-ttu-id="e29c7-105">Este exercício oferece instruções de como criar e aplicar uma configuração para a Configuração Estado Desejado (DSC) do início ao fim.</span><span class="sxs-lookup"><span data-stu-id="e29c7-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="e29c7-106">O exemplo a seguir, você aprenderá como escrever e aplicar uma configuração muito simple.</span><span class="sxs-lookup"><span data-stu-id="e29c7-106">In the following example, you will learn how to write and apply a very simple Configuration.</span></span> <span data-ttu-id="e29c7-107">A configuração garantirá que existe um arquivo de "HelloWorld.txt" em seu computador local.</span><span class="sxs-lookup"><span data-stu-id="e29c7-107">The Configuration will ensure a "HelloWorld.txt" file exists on your local machine.</span></span> <span data-ttu-id="e29c7-108">Se você excluir o arquivo, DSC irá recriá-lo na próxima vez que ele atualiza.</span><span class="sxs-lookup"><span data-stu-id="e29c7-108">If you delete the file, DSC will recreate it the next time it updates.</span></span>

<span data-ttu-id="e29c7-109">Para uma visão geral do DSC What ' s e como ele funciona, consulte [Desired State Configuration visão geral para desenvolvedores](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="e29c7-109">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Developers](../overview/overview.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="e29c7-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e29c7-110">Requirements</span></span>

<span data-ttu-id="e29c7-111">Para executar este exemplo, você precisará de um computador que executa o PowerShell 4.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="e29c7-111">To run this example, you will need a computer running PowerShell 4.0 or later.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="e29c7-112">Gravar a configuração</span><span class="sxs-lookup"><span data-stu-id="e29c7-112">Write the configuration</span></span>

<span data-ttu-id="e29c7-113">Uma [Configuração](configurations.md) DSC é uma função especial do PowerShell que define como você deseja configurar um ou mais computadores de destino (nós).</span><span class="sxs-lookup"><span data-stu-id="e29c7-113">A DSC [Configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (Nodes).</span></span>

<span data-ttu-id="e29c7-114">No ISE do PowerShell, ou outro editor do PowerShell, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e29c7-114">In the PowerShell ISE, or other PowerShell editor, type the following:</span></span>

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

<span data-ttu-id="e29c7-115">Salve o arquivo como "HelloWorld.ps1".</span><span class="sxs-lookup"><span data-stu-id="e29c7-115">Save the file as "HelloWorld.ps1".</span></span>

<span data-ttu-id="e29c7-116">Definir uma configuração é como a definição de uma função.</span><span class="sxs-lookup"><span data-stu-id="e29c7-116">Defining a Configuration is like defining a Function.</span></span> <span data-ttu-id="e29c7-117">O bloco **Nó** especifica o nó de destino a ser configurado, neste caso `localhost`.</span><span class="sxs-lookup"><span data-stu-id="e29c7-117">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="e29c7-118">A configuração chama um [recursos](../resources/resources.md), o `File` recursos.</span><span class="sxs-lookup"><span data-stu-id="e29c7-118">The configuration calls one [resources](../resources/resources.md), the `File` resource.</span></span> <span data-ttu-id="e29c7-119">Os recursos fazem o trabalho de garantir que o nó de destino está no estado definido pela configuração.</span><span class="sxs-lookup"><span data-stu-id="e29c7-119">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="e29c7-120">Compilar a configuração</span><span class="sxs-lookup"><span data-stu-id="e29c7-120">Compile the configuration</span></span>

<span data-ttu-id="e29c7-121">Para que uma configuração DSC seja aplicada a um nó, ela deve primeiro ser compilada em um arquivo MOF.</span><span class="sxs-lookup"><span data-stu-id="e29c7-121">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="e29c7-122">Executando a configuração, como uma função, compilar um arquivo ". MOF" para cada nó definido pelo `Node` bloco.</span><span class="sxs-lookup"><span data-stu-id="e29c7-122">Running the configuration, like a function, will compile one ".mof" file for every Node defined by the `Node` block.</span></span>
<span data-ttu-id="e29c7-123">Para executar a configuração, você precisa *origem dot* seu script de "HelloWorld.ps1" no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="e29c7-123">In order to run the configuration, you need to *dot source* your "HelloWorld.ps1" script into the current scope.</span></span>
<span data-ttu-id="e29c7-124">Para obter mais informações, consulte [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span><span class="sxs-lookup"><span data-stu-id="e29c7-124">For more information, see [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span></span>

<span data-ttu-id="e29c7-125">*Origem de ponto* seu script de "HelloWorld.ps1" digitando o caminho onde você armazenou, após o `. ` (ponto, espaço).</span><span class="sxs-lookup"><span data-stu-id="e29c7-125">*Dot source* your "HelloWorld.ps1" script by typing in the path where you stored it, after the `. ` (dot, space).</span></span> <span data-ttu-id="e29c7-126">Você pode em seguida, execute a configuração chamando-o como uma função.</span><span class="sxs-lookup"><span data-stu-id="e29c7-126">You may then, run your configuration by calling it like a Function.</span></span>

```powershell
. C:\Scripts\WebsiteTest.ps1
HelloWolrd
```

<span data-ttu-id="e29c7-127">Isso gerará os seguintes resultados:</span><span class="sxs-lookup"><span data-stu-id="e29c7-127">This generates the following output:</span></span>

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a><span data-ttu-id="e29c7-128">Aplicar a configuração</span><span class="sxs-lookup"><span data-stu-id="e29c7-128">Apply the configuration</span></span>

<span data-ttu-id="e29c7-129">Agora que você tem o MOF compilado, é possível aplicar a configuração ao nó de destino (neste caso, o computador local) chamando o cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="e29c7-129">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="e29c7-130">O `Start-DscConfiguration` cmdlet informa o [Gerenciador de configurações Local (LCM)](../managing-nodes/metaConfig.md), o mecanismo de DSC para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="e29c7-130">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="e29c7-131">O LCM realiza o trabalho de chamar os recursos de DSC para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="e29c7-131">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="e29c7-132">Use o código a seguir para executar o `Start-DSCConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e29c7-132">Use the code below to execute the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="e29c7-133">Especifique o caminho de diretório em que "localhost.mof" é armazenado para o `-Path` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e29c7-133">Specify the directory path where your "localhost.mof" is stored to the `-Path` parameter.</span></span> <span data-ttu-id="e29c7-134">O `Start-DSCConfiguration` cmdlet examinará o diretório especificado para qualquer "\<computername\>. MOF" arquivos.</span><span class="sxs-lookup"><span data-stu-id="e29c7-134">The `Start-DSCConfiguration` cmdlet looks through the directory specified for any "\<computername\>.mof" files.</span></span> <span data-ttu-id="e29c7-135">O `Start-DSCConfiguration` cmdlet tenta aplicar a cada arquivo ". MOF" encontrado para o nome do computador especificado pelo nome do arquivo ("localhost", "server01", "controlador de domínio-02", etc.).</span><span class="sxs-lookup"><span data-stu-id="e29c7-135">The `Start-DSCConfiguration` cmdlet attempts to apply each ".mof" file it finds to the computername specified by the filename ("localhost", "server01", "dc-02", etc.).</span></span>

> [!NOTE]
> <span data-ttu-id="e29c7-136">Se o `-Wait` parâmetro não for especificado, `Start-DSCConfiguration` cria um trabalho em segundo plano para executar a operação.</span><span class="sxs-lookup"><span data-stu-id="e29c7-136">If the `-Wait` parameter is not specified, `Start-DSCConfiguration` creates a background job to perform the operation.</span></span> <span data-ttu-id="e29c7-137">Especificando o `-Verbose` parâmetro permite que você assista a **detalhado** saída da operação.</span><span class="sxs-lookup"><span data-stu-id="e29c7-137">Specifying the `-Verbose` parameter allows you to watch the **Verbose** output of the operation.</span></span> <span data-ttu-id="e29c7-138">`-Wait`, e `-Verbose` são ambos os parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="e29c7-138">`-Wait`, and `-Verbose` are both optional parameters.</span></span>

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a><span data-ttu-id="e29c7-139">Testar a configuração</span><span class="sxs-lookup"><span data-stu-id="e29c7-139">Test the configuration</span></span>

<span data-ttu-id="e29c7-140">Uma vez o `Start-DSCConfiguration` cmdlet estiver concluída, você deverá ver um arquivo de "HelloWorld.txt" no local especificado por você.</span><span class="sxs-lookup"><span data-stu-id="e29c7-140">Once the `Start-DSCConfiguration` cmdlet is complete, you should see a "HelloWorld.txt" file in the location you specified.</span></span> <span data-ttu-id="e29c7-141">Você pode verificar o conteúdo com o [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e29c7-141">You can verify the contents with the [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span></span>

<span data-ttu-id="e29c7-142">Você também pode *testar* o status atual usando [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="e29c7-142">You can also *test* the current status using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

<span data-ttu-id="e29c7-143">A saída deve ser "True" se o nó é atualmente compatível com a configuração aplicada.</span><span class="sxs-lookup"><span data-stu-id="e29c7-143">The output should be "True" if the Node is currently compliant with the applied Configuration.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a><span data-ttu-id="e29c7-144">Novamente, aplicando a configuração</span><span class="sxs-lookup"><span data-stu-id="e29c7-144">Re-applying the configuration</span></span>

<span data-ttu-id="e29c7-145">Para ver sua configuração serão aplicadas novamente, você pode remover o arquivo de texto criado por sua configuração.</span><span class="sxs-lookup"><span data-stu-id="e29c7-145">To see your configuration get applied again, you can remove the text file created by your Configuration.</span></span> <span data-ttu-id="e29c7-146">O uso de `Start-DSCConfiguration` cmdlet com o `-UseExisting` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e29c7-146">The use the `Start-DSCConfiguration` cmdlet with the `-UseExisting` parameter.</span></span> <span data-ttu-id="e29c7-147">O `-UseExisting` parâmetro instrui `Start-DSCConfiguration` para reaplicar o arquivo "Current", que representa mais recentemente com êxito aplicado configuração.</span><span class="sxs-lookup"><span data-stu-id="e29c7-147">The `-UseExisting` parameter instructs `Start-DSCConfiguration` to re-apply the "current.mof" file, which represents the most recently successfully applied configuration.</span></span>

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a><span data-ttu-id="e29c7-148">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="e29c7-148">Next steps</span></span>

- <span data-ttu-id="e29c7-149">Saiba mais sobre configurações de DSC em [Configurações de DSC](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="e29c7-149">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="e29c7-150">Veja quais recursos de DSC estão disponíveis e como criar recursos personalizados de DSC em [Recursos de DSC](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="e29c7-150">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="e29c7-151">Localize as configurações e recursos de DSC na [Galeria do PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="e29c7-151">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
