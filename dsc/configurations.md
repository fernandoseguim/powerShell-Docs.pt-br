---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Configurações DSC
ms.openlocfilehash: d98bf0e85c12103d9b1eeded155bab1af364bd4c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-configurations"></a><span data-ttu-id="41a8a-103">Configurações DSC</span><span class="sxs-lookup"><span data-stu-id="41a8a-103">DSC Configurations</span></span>

><span data-ttu-id="41a8a-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="41a8a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="41a8a-105">As configurações DSC são scripts do PowerShell que definem um tipo especial de função.</span><span class="sxs-lookup"><span data-stu-id="41a8a-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span>
<span data-ttu-id="41a8a-106">Para definir uma configuração utilize a palavra-chave do PowerShell **Configuration**.</span><span class="sxs-lookup"><span data-stu-id="41a8a-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

```powershell
Configuration MyDscConfiguration {

    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
MyDscConfiguration

```

<span data-ttu-id="41a8a-107">Salve o script como um arquivo .ps1.</span><span class="sxs-lookup"><span data-stu-id="41a8a-107">Save the script as a .ps1 file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="41a8a-108">Sintaxe da configuração</span><span class="sxs-lookup"><span data-stu-id="41a8a-108">Configuration syntax</span></span>

<span data-ttu-id="41a8a-109">Um script de configuração é composto por estas partes:</span><span class="sxs-lookup"><span data-stu-id="41a8a-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="41a8a-110">O bloco **Configuration**.</span><span class="sxs-lookup"><span data-stu-id="41a8a-110">The **Configuration** block.</span></span> <span data-ttu-id="41a8a-111">É o bloco de script externo.</span><span class="sxs-lookup"><span data-stu-id="41a8a-111">This is the outermost script block.</span></span> <span data-ttu-id="41a8a-112">Para defini-lo, use a palavra-chave **Configuration** e forneça um nome.</span><span class="sxs-lookup"><span data-stu-id="41a8a-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="41a8a-113">Nesse caso, o nome da configuração é "MyDscConfiguration".</span><span class="sxs-lookup"><span data-stu-id="41a8a-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="41a8a-114">Um ou mais blocos de **Nó**.</span><span class="sxs-lookup"><span data-stu-id="41a8a-114">One or more **Node** blocks.</span></span> <span data-ttu-id="41a8a-115">Definem os nós (computadores ou máquinas virtuais) que você está configurando.</span><span class="sxs-lookup"><span data-stu-id="41a8a-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="41a8a-116">Na configuração acima, há um bloco de **Nó** que tem como destino um computador denominado "TEST-PC1".</span><span class="sxs-lookup"><span data-stu-id="41a8a-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span>
- <span data-ttu-id="41a8a-117">Um ou mais blocos de recurso.</span><span class="sxs-lookup"><span data-stu-id="41a8a-117">One or more resource blocks.</span></span> <span data-ttu-id="41a8a-118">É onde a configuração define as propriedades para os recursos que estão sendo configurados.</span><span class="sxs-lookup"><span data-stu-id="41a8a-118">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="41a8a-119">Nesse caso, há dois blocos de recurso; cada um deles chama o recurso "WindowsFeature".</span><span class="sxs-lookup"><span data-stu-id="41a8a-119">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="41a8a-120">Dentro de um bloco de **configuração**, é possível fazer qualquer coisa que normalmente poderia ser feita em uma função do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41a8a-120">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="41a8a-121">No exemplo anterior, se você não quisesse embutir em código o nome do computador de destino na configuração, poderia adicionar um parâmetro para o nome do nó:</span><span class="sxs-lookup"><span data-stu-id="41a8a-121">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

```powershell
Configuration MyDscConfiguration {

    param(
        [string[]]$ComputerName="localhost"
    )
    Node $ComputerName {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
MyDscConfiguration -ComputerName $ComputerName

```

<span data-ttu-id="41a8a-122">Neste exemplo, você especifica o nome do nó passando-o como o parâmetro **ComputerName** quando compila a configuração.</span><span class="sxs-lookup"><span data-stu-id="41a8a-122">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="41a8a-123">O nome padrão é "localhost".</span><span class="sxs-lookup"><span data-stu-id="41a8a-123">The name defaults to "localhost".</span></span>

## <a name="compiling-the-configuration"></a><span data-ttu-id="41a8a-124">Compilando a configuração</span><span class="sxs-lookup"><span data-stu-id="41a8a-124">Compiling the configuration</span></span>

<span data-ttu-id="41a8a-125">Para poder aplicar uma configuração, você precisa compilá-la em um documento MOF.</span><span class="sxs-lookup"><span data-stu-id="41a8a-125">Before you can enact a configuration, you have to compile it into a MOF document.</span></span>
<span data-ttu-id="41a8a-126">Faça isso chamando a configuração como você chamaria uma função do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41a8a-126">You do this by calling the configuration like you would call a PowerShell function.</span></span>
<span data-ttu-id="41a8a-127">A última linha do exemplo contendo somente o nome da configuração, chama a configuração.</span><span class="sxs-lookup"><span data-stu-id="41a8a-127">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

><span data-ttu-id="41a8a-128">**Observação:** para chamar uma configuração, a função precisa estar no escopo global (como acontece com qualquer outra função do PowerShell).</span><span class="sxs-lookup"><span data-stu-id="41a8a-128">**Note:** To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span>
><span data-ttu-id="41a8a-129">Isso pode ser feito por meio de "dot-sourcing" do script ou ao executar o script de configuração usando F5 ou clicando no botão **Executar Script** no ISE.</span><span class="sxs-lookup"><span data-stu-id="41a8a-129">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span>
><span data-ttu-id="41a8a-130">Para fazer o dot-source do script, execute o comando `. .\myConfig.ps1`, em que `myConfig.ps1` é o nome do arquivo de script que contém sua configuração.</span><span class="sxs-lookup"><span data-stu-id="41a8a-130">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="41a8a-131">Quando você chama a configuração, ela:</span><span class="sxs-lookup"><span data-stu-id="41a8a-131">When you call the configuration, it:</span></span>

- <span data-ttu-id="41a8a-132">Resolve todas as variáveis</span><span class="sxs-lookup"><span data-stu-id="41a8a-132">Resolves all variables</span></span>
- <span data-ttu-id="41a8a-133">Uma pasta no diretório atual com o mesmo nome que a configuração.</span><span class="sxs-lookup"><span data-stu-id="41a8a-133">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="41a8a-134">Um arquivo chamado _NodeName_.mof no novo diretório, em que _NodeName_ é o nome do nó de destino da configuração.</span><span class="sxs-lookup"><span data-stu-id="41a8a-134">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span>
    <span data-ttu-id="41a8a-135">Se houver mais de um nó, será criado um arquivo MOF para cada nó.</span><span class="sxs-lookup"><span data-stu-id="41a8a-135">If there are more than one nodes, a MOF file will be created for each node.</span></span>

><span data-ttu-id="41a8a-136">**Observação**: o arquivo MOF contém todas as informações de configuração para o nó de destino.</span><span class="sxs-lookup"><span data-stu-id="41a8a-136">**Note**: The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="41a8a-137">Por isso, é importante mantê-lo seguro.</span><span class="sxs-lookup"><span data-stu-id="41a8a-137">Because of this, it’s important to keep it secure.</span></span>
><span data-ttu-id="41a8a-138">Para obter mais informações, consulte [Protegendo o arquivo MOF](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="41a8a-138">For more information, see [Securing the MOF file](secureMOF.md).</span></span>

<span data-ttu-id="41a8a-139">A compilação da primeira configuração acima resulta na seguinte estrutura de pastas:</span><span class="sxs-lookup"><span data-stu-id="41a8a-139">Compiling the first configuration above results in the following folder structure:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```

<span data-ttu-id="41a8a-140">Se a configuração utilizar um parâmetro, como no segundo exemplo, ele precisará ser fornecido no tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="41a8a-140">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="41a8a-141">A aparência deveria ser esta:</span><span class="sxs-lookup"><span data-stu-id="41a8a-141">Here's how that would look:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```

## <a name="using-dependson"></a><span data-ttu-id="41a8a-142">Usando o DependsOn</span><span class="sxs-lookup"><span data-stu-id="41a8a-142">Using DependsOn</span></span>

<span data-ttu-id="41a8a-143">Uma palavra-chave útil da DSC é **DependsOn**.</span><span class="sxs-lookup"><span data-stu-id="41a8a-143">A useful DSC keyword is **DependsOn**.</span></span> <span data-ttu-id="41a8a-144">Normalmente (mas nem sempre), a DSC aplica os recursos na ordem em que aparecem dentro da configuração.</span><span class="sxs-lookup"><span data-stu-id="41a8a-144">Typically (though not necessarily always), DSC applies the resources in the order that they appear within the configuration.</span></span>
<span data-ttu-id="41a8a-145">Contudo, o **DependsOn** especifica quais recursos dependem de outros recursos, enquanto o LCM garante que sejam aplicados na ordem correta, independentemente da ordem na qual as instâncias de recurso são definidas.</span><span class="sxs-lookup"><span data-stu-id="41a8a-145">However, **DependsOn** specifies which resources depend on other resources, and the LCM ensures that they are applied in the correct order, regardless of the order in which resource instances are defined.</span></span>
<span data-ttu-id="41a8a-146">Por exemplo, uma configuração pode especificar que uma instância do recurso **User** depende da existência de uma instância **Group**:</span><span class="sxs-lookup"><span data-stu-id="41a8a-146">For example, a configuration might specify that an instance of the **User** resource depends on the existence of a **Group** instance:</span></span>

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = "Present"
            GroupName = "TestGroup"
        }

        User UserExample {
            Ensure = "Present"
            UserName = "TestUser"
            FullName = "TestUser"
            DependsOn = "[Group]GroupExample"
        }
    }
}

```

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="41a8a-147">Uso de novos recursos na sua configuração</span><span class="sxs-lookup"><span data-stu-id="41a8a-147">Using new resources in Your configuration</span></span>

<span data-ttu-id="41a8a-148">Se você executou os exemplos anteriores, talvez tenha notado que foi informado que estava usando um recurso sem importá-lo explicitamente.</span><span class="sxs-lookup"><span data-stu-id="41a8a-148">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="41a8a-149">Atualmente, a DSC vem com 12 recursos como parte do módulo PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="41a8a-149">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span>
<span data-ttu-id="41a8a-150">Outros recursos em módulos externos devem ser colocados em `$env:PSModulePath` para serem reconhecidos pelo LCM.</span><span class="sxs-lookup"><span data-stu-id="41a8a-150">Other resources in external modules must be placed in `$env:PSModulePath` in order to be recognized by the LCM.</span></span>
<span data-ttu-id="41a8a-151">Um novo cmdlet, [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), pode ser usado para determinar quais recursos estão instalados no sistema e disponíveis para uso pelo LCM.</span><span class="sxs-lookup"><span data-stu-id="41a8a-151">A new cmdlet, [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span>
<span data-ttu-id="41a8a-152">Depois que esses módulos forem colocados em `$env:PSModulePath` e reconhecidos adequadamente pelo [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), ainda precisam ser carregados na sua configuração.</span><span class="sxs-lookup"><span data-stu-id="41a8a-152">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), they still need to be loaded within your configuration.</span></span>
<span data-ttu-id="41a8a-153">**Import-DscResource** é uma palavra-chave dinâmica que pode ser reconhecida apenas dentro de um bloco de **configuração** (ou seja, não é um cmdlet).</span><span class="sxs-lookup"><span data-stu-id="41a8a-153">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block (i.e. it is not a cmdlet).</span></span>
<span data-ttu-id="41a8a-154">O **Import-DscResource** dá suporte a dois parâmetros:</span><span class="sxs-lookup"><span data-stu-id="41a8a-154">**Import-DscResource** supports two parameters:</span></span>
- <span data-ttu-id="41a8a-155">**ModuleName** é a forma recomendada de usar o **Import-DscResource**.</span><span class="sxs-lookup"><span data-stu-id="41a8a-155">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="41a8a-156">Aceita o nome do módulo que contém os recursos que serão importados (assim como uma matriz de cadeia de caracteres de nomes de módulos).</span><span class="sxs-lookup"><span data-stu-id="41a8a-156">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span>
- <span data-ttu-id="41a8a-157">**Name** é o nome do recurso que será importado.</span><span class="sxs-lookup"><span data-stu-id="41a8a-157">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="41a8a-158">Não é o nome amigável gerado como "Name" pelo [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), mas o nome de classe usado na hora de definir o esquema de recurso (gerado como **ResourceType** pelo [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx)).</span><span class="sxs-lookup"><span data-stu-id="41a8a-158">This is not the friendly name returned as "Name" by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx)).</span></span>

## <a name="see-also"></a><span data-ttu-id="41a8a-159">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="41a8a-159">See Also</span></span>
* [<span data-ttu-id="41a8a-160">Visão Geral da Configuração de Estado Desejado do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="41a8a-160">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
* [<span data-ttu-id="41a8a-161">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="41a8a-161">DSC Resources</span></span>](resources.md)
* [<span data-ttu-id="41a8a-162">Configurando o Gerenciador de Configurações Local</span><span class="sxs-lookup"><span data-stu-id="41a8a-162">Configuring The Local Configuration Manager</span></span>](metaConfig.md)
