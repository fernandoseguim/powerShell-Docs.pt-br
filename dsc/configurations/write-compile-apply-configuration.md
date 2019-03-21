---
ms.date: 12/12/2018
keywords: DSC,powershell,configuração,serviço,instalação
title: Escrever, compilar e aplicar uma configuração
ms.openlocfilehash: c884af9d92ac375457d6eb75d815ae9a9159e273
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795412"
---
> <span data-ttu-id="d74cf-103">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d74cf-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="write-compile-and-apply-a-configuration"></a><span data-ttu-id="d74cf-104">Escrever, compilar e aplicar uma configuração</span><span class="sxs-lookup"><span data-stu-id="d74cf-104">Write, Compile, and Apply a Configuration</span></span>

<span data-ttu-id="d74cf-105">Este exercício oferece instruções de como criar e aplicar uma configuração para a Configuração Estado Desejado (DSC) do início ao fim.</span><span class="sxs-lookup"><span data-stu-id="d74cf-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="d74cf-106">No exemplo a seguir, você aprenderá como escrever e aplicar uma configuração muito simples.</span><span class="sxs-lookup"><span data-stu-id="d74cf-106">In the following example, you will learn how to write and apply a very simple Configuration.</span></span> <span data-ttu-id="d74cf-107">A configuração garantirá que um arquivo "HelloWorld.txt" existe em seu computador local.</span><span class="sxs-lookup"><span data-stu-id="d74cf-107">The Configuration will ensure a "HelloWorld.txt" file exists on your local machine.</span></span> <span data-ttu-id="d74cf-108">Se você excluir o arquivo, a DSC o criará novamente em sua próxima atualização.</span><span class="sxs-lookup"><span data-stu-id="d74cf-108">If you delete the file, DSC will recreate it the next time it updates.</span></span>

<span data-ttu-id="d74cf-109">Para ter uma visão geral sobre o que é a DSC e como ela funciona, confira [Visão geral da Desired State Configuration para desenvolvedores](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="d74cf-109">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Developers](../overview/overview.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="d74cf-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d74cf-110">Requirements</span></span>

<span data-ttu-id="d74cf-111">Para executar este exemplo, você precisará de um computador com o PowerShell 4.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="d74cf-111">To run this example, you will need a computer running PowerShell 4.0 or later.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="d74cf-112">Gravar a configuração</span><span class="sxs-lookup"><span data-stu-id="d74cf-112">Write the configuration</span></span>

<span data-ttu-id="d74cf-113">Uma [Configuração](configurations.md) DSC é uma função especial do PowerShell que define como você deseja configurar um ou mais computadores de destino (nós).</span><span class="sxs-lookup"><span data-stu-id="d74cf-113">A DSC [Configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (Nodes).</span></span>

<span data-ttu-id="d74cf-114">No ISE do PowerShell ou em outro editor do PowerShell, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d74cf-114">In the PowerShell ISE, or other PowerShell editor, type the following:</span></span>

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

<span data-ttu-id="d74cf-115">Salve o arquivo como "HelloWorld.ps1".</span><span class="sxs-lookup"><span data-stu-id="d74cf-115">Save the file as "HelloWorld.ps1".</span></span>

<span data-ttu-id="d74cf-116">Definir uma configuração é semelhante a definir uma função.</span><span class="sxs-lookup"><span data-stu-id="d74cf-116">Defining a Configuration is like defining a Function.</span></span> <span data-ttu-id="d74cf-117">O bloco **Nó** especifica o nó de destino a ser configurado, neste caso `localhost`.</span><span class="sxs-lookup"><span data-stu-id="d74cf-117">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="d74cf-118">A configuração chama um [recurso](../resources/resources.md), o recurso `File`.</span><span class="sxs-lookup"><span data-stu-id="d74cf-118">The configuration calls one [resources](../resources/resources.md), the `File` resource.</span></span> <span data-ttu-id="d74cf-119">Os recursos fazem o trabalho de garantir que o nó de destino está no estado definido pela configuração.</span><span class="sxs-lookup"><span data-stu-id="d74cf-119">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="d74cf-120">Compilar a configuração</span><span class="sxs-lookup"><span data-stu-id="d74cf-120">Compile the configuration</span></span>

<span data-ttu-id="d74cf-121">Para que uma configuração DSC seja aplicada a um nó, ela deve primeiro ser compilada em um arquivo MOF.</span><span class="sxs-lookup"><span data-stu-id="d74cf-121">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="d74cf-122">Executar a configuração, assim como ocorre com uma função, compila um arquivo ".mof" para cada nó definido pelo bloco `Node`.</span><span class="sxs-lookup"><span data-stu-id="d74cf-122">Running the configuration, like a function, will compile one ".mof" file for every Node defined by the `Node` block.</span></span>
<span data-ttu-id="d74cf-123">Para executar a configuração, você precisa aplicar *dot source* ao seu script de "HelloWorld.ps1" no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="d74cf-123">In order to run the configuration, you need to *dot source* your "HelloWorld.ps1" script into the current scope.</span></span>
<span data-ttu-id="d74cf-124">Para obter mais informações, confira [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span><span class="sxs-lookup"><span data-stu-id="d74cf-124">For more information, see [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span></span>

<span data-ttu-id="d74cf-125"><!-- markdownlint-disable MD038 -->
*Aplique dot source* ao seu script de "HelloWorld.ps1" digitando o caminho em que você o armazenou, após o `. ` (ponto, espaço).</span><span class="sxs-lookup"><span data-stu-id="d74cf-125"><!-- markdownlint-disable MD038 -->
*Dot source* your "HelloWorld.ps1" script by typing in the path where you stored it, after the `. ` (dot, space).</span></span> <span data-ttu-id="d74cf-126">Em seguida, você pode executar a configuração chamando-a como uma função.</span><span class="sxs-lookup"><span data-stu-id="d74cf-126">You may then, run your configuration by calling it like a Function.</span></span>
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\WebsiteTest.ps1
HelloWolrd
```

<span data-ttu-id="d74cf-127">Isso gerará os seguintes resultados:</span><span class="sxs-lookup"><span data-stu-id="d74cf-127">This generates the following output:</span></span>

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a><span data-ttu-id="d74cf-128">Aplicar a configuração</span><span class="sxs-lookup"><span data-stu-id="d74cf-128">Apply the configuration</span></span>

<span data-ttu-id="d74cf-129">Agora que você tem o MOF compilado, é possível aplicar a configuração ao nó de destino (neste caso, o computador local) chamando o cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="d74cf-129">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="d74cf-130">O cmdlet `Start-DscConfiguration` instrui o [LCM (Gerenciador de Configurações Local)](../managing-nodes/metaConfig.md), que é o mecanismo da DSC, a aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="d74cf-130">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="d74cf-131">O LCM realiza o trabalho de chamar os recursos de DSC para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="d74cf-131">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="d74cf-132">Use o código a seguir para executar o cmdlet `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="d74cf-132">Use the code below to execute the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="d74cf-133">Especifique o caminho do diretório em que seu "localhost.mof" está armazenado para o parâmetro `-Path`.</span><span class="sxs-lookup"><span data-stu-id="d74cf-133">Specify the directory path where your "localhost.mof" is stored to the `-Path` parameter.</span></span> <span data-ttu-id="d74cf-134">O cmdlet `Start-DSCConfiguration` examina o diretório especificado para ver se há arquivos "\<nome de computador\>.mof".</span><span class="sxs-lookup"><span data-stu-id="d74cf-134">The `Start-DSCConfiguration` cmdlet looks through the directory specified for any "\<computername\>.mof" files.</span></span> <span data-ttu-id="d74cf-135">O cmdlet `Start-DSCConfiguration` tenta aplicar a cada arquivo ".mof" encontrado ao nome de computador especificado pelo nome do arquivo ("localhost", "server01", "dc-02", etc.).</span><span class="sxs-lookup"><span data-stu-id="d74cf-135">The `Start-DSCConfiguration` cmdlet attempts to apply each ".mof" file it finds to the computername specified by the filename ("localhost", "server01", "dc-02", etc.).</span></span>

> [!NOTE]
> <span data-ttu-id="d74cf-136">Se o parâmetro `-Wait` não for especificado, `Start-DSCConfiguration` criará um trabalho em segundo plano para executar a operação.</span><span class="sxs-lookup"><span data-stu-id="d74cf-136">If the `-Wait` parameter is not specified, `Start-DSCConfiguration` creates a background job to perform the operation.</span></span> <span data-ttu-id="d74cf-137">Especificar o parâmetro `-Verbose` permite que você inspecione a saída **Detalhada** da operação.</span><span class="sxs-lookup"><span data-stu-id="d74cf-137">Specifying the `-Verbose` parameter allows you to watch the **Verbose** output of the operation.</span></span> <span data-ttu-id="d74cf-138">`-Wait` e `-Verbose` são parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="d74cf-138">`-Wait`, and `-Verbose` are both optional parameters.</span></span>

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a><span data-ttu-id="d74cf-139">Testar a configuração</span><span class="sxs-lookup"><span data-stu-id="d74cf-139">Test the configuration</span></span>

<span data-ttu-id="d74cf-140">Quando o cmdlet `Start-DSCConfiguration` estiver concluído, você deverá ver um arquivo "HelloWorld.txt" na localização especificada.</span><span class="sxs-lookup"><span data-stu-id="d74cf-140">Once the `Start-DSCConfiguration` cmdlet is complete, you should see a "HelloWorld.txt" file in the location you specified.</span></span> <span data-ttu-id="d74cf-141">Você pode verificar o conteúdo com o cmdlet [Get-Content](/powershell/module/microsoft.powershell.management/get-content).</span><span class="sxs-lookup"><span data-stu-id="d74cf-141">You can verify the contents with the [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span></span>

<span data-ttu-id="d74cf-142">Você também pode *testar* o status atual usando [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="d74cf-142">You can also *test* the current status using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

<span data-ttu-id="d74cf-143">A saída deverá ser "True" se o nó for estiver em conformidade com a configuração aplicada.</span><span class="sxs-lookup"><span data-stu-id="d74cf-143">The output should be "True" if the Node is currently compliant with the applied Configuration.</span></span>

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

## <a name="re-applying-the-configuration"></a><span data-ttu-id="d74cf-144">Reaplicando a configuração</span><span class="sxs-lookup"><span data-stu-id="d74cf-144">Re-applying the configuration</span></span>

<span data-ttu-id="d74cf-145">Para ver sua configuração ser aplicada novamente, você pode remover o arquivo de texto criado por ela.</span><span class="sxs-lookup"><span data-stu-id="d74cf-145">To see your configuration get applied again, you can remove the text file created by your Configuration.</span></span> <span data-ttu-id="d74cf-146">Em seguida, use o cmdlet `Start-DSCConfiguration` com o parâmetro `-UseExisting`.</span><span class="sxs-lookup"><span data-stu-id="d74cf-146">The use the `Start-DSCConfiguration` cmdlet with the `-UseExisting` parameter.</span></span> <span data-ttu-id="d74cf-147">O parâmetro `-UseExisting` instrui `Start-DSCConfiguration` a reaplicar o arquivo "current.mof", que representa a configuração aplicada com sucesso mais recentemente.</span><span class="sxs-lookup"><span data-stu-id="d74cf-147">The `-UseExisting` parameter instructs `Start-DSCConfiguration` to re-apply the "current.mof" file, which represents the most recently successfully applied configuration.</span></span>

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a><span data-ttu-id="d74cf-148">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="d74cf-148">Next steps</span></span>

- <span data-ttu-id="d74cf-149">Saiba mais sobre configurações de DSC em [Configurações de DSC](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="d74cf-149">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="d74cf-150">Veja quais recursos de DSC estão disponíveis e como criar recursos personalizados de DSC em [Recursos de DSC](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="d74cf-150">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="d74cf-151">Localize as configurações e recursos de DSC na [Galeria do PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="d74cf-151">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
