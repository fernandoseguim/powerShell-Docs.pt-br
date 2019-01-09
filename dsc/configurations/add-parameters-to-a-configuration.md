---
ms.date: 12/12/2018
keywords: DSC, powershell, recursos, da galeria, instalação
title: Adicionar parâmetros a uma configuração
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400205"
---
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="812a6-103">Adicionar parâmetros a uma configuração</span><span class="sxs-lookup"><span data-stu-id="812a6-103">Add Parameters to a Configuration</span></span>

<span data-ttu-id="812a6-104">Assim como as funções, [configurações](configurations.md) pode ser parametrizado para permitir que as configurações mais dinâmicas com base na entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="812a6-104">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="812a6-105">As etapas são semelhantes aos descritos em [funções com parâmetros](/powershell/module/microsoft.powershell.core/about/about_functions).</span><span class="sxs-lookup"><span data-stu-id="812a6-105">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="812a6-106">Este exemplo começa com uma configuração básica que configura o serviço de "Spooler" para "Running".</span><span class="sxs-lookup"><span data-stu-id="812a6-106">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}
```

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="812a6-107">Parâmetros de configuração internos</span><span class="sxs-lookup"><span data-stu-id="812a6-107">Built-in Configuration parameters</span></span>

<span data-ttu-id="812a6-108">Ao contrário de uma função, o [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) atributo não adiciona nenhuma funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="812a6-108">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="812a6-109">Além [parâmetros comuns de](/powershell/module/microsoft.powershell.core/about/about_commonparameters), as configurações também podem usar as seguintes internas em parâmetros, sem a necessidade de você defini-las.</span><span class="sxs-lookup"><span data-stu-id="812a6-109">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|<span data-ttu-id="812a6-110">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="812a6-110">Parameter</span></span>  |<span data-ttu-id="812a6-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="812a6-111">Description</span></span>  |
|---------|---------|
|`-InstanceName`|<span data-ttu-id="812a6-112">Usado na definição [configurações composto](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="812a6-112">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-DependsOn`|<span data-ttu-id="812a6-113">Usado na definição [configurações composto](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="812a6-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-PSDSCRunAsCredential`|<span data-ttu-id="812a6-114">Usado na definição [configurações composto](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="812a6-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-ConfigurationData`|<span data-ttu-id="812a6-115">Usado para passar em estruturado [dados de configuração](configData.md) para uso na configuração.</span><span class="sxs-lookup"><span data-stu-id="812a6-115">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span>|
|`-OutputPath`|<span data-ttu-id="812a6-116">Usado para especificar onde o "\<computername\>. MOF" arquivo será compilado</span><span class="sxs-lookup"><span data-stu-id="812a6-116">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>|

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="812a6-117">Adicionar seus próprios parâmetros a configurações</span><span class="sxs-lookup"><span data-stu-id="812a6-117">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="812a6-118">Além dos parâmetros internos, você também pode adicionar seus próprios parâmetros para suas configurações.</span><span class="sxs-lookup"><span data-stu-id="812a6-118">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span> <span data-ttu-id="812a6-119">O bloco de parâmetro vai diretamente dentro da declaração de configuração, assim como uma função.</span><span class="sxs-lookup"><span data-stu-id="812a6-119">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="812a6-120">Um bloco de parâmetro de configuração deve estar fora de qualquer **nó** declarações e acima de qualquer *importar* instruções.</span><span class="sxs-lookup"><span data-stu-id="812a6-120">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="812a6-121">Adicionando parâmetros, você pode fazer suas configurações mais robustos e dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="812a6-121">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="812a6-122">Adicionar um parâmetro ComputerName</span><span class="sxs-lookup"><span data-stu-id="812a6-122">Add a ComputerName parameter</span></span>

<span data-ttu-id="812a6-123">O primeiro parâmetro, você pode adicionar é um `-Computername` parâmetro, portanto, você pode compilar um arquivo ". MOF" dinamicamente para qualquer `-Computername` passar à sua configuração.</span><span class="sxs-lookup"><span data-stu-id="812a6-123">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="812a6-124">Como funções, você também pode definir um valor padrão, caso o usuário não passa um valor para `-ComputerName`</span><span class="sxs-lookup"><span data-stu-id="812a6-124">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="812a6-125">Em sua configuração, em seguida, você pode especificar seu `-ComputerName` parâmetro ao definir seu bloco de nó.</span><span class="sxs-lookup"><span data-stu-id="812a6-125">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="812a6-126">Chamar a sua configuração com parâmetros</span><span class="sxs-lookup"><span data-stu-id="812a6-126">Calling your Configuration with parameters</span></span>

<span data-ttu-id="812a6-127">Depois de adicionar parâmetros à sua configuração, você pode usá-los exatamente como você faria com um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="812a6-127">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="812a6-128">Compilar vários arquivos. MOF</span><span class="sxs-lookup"><span data-stu-id="812a6-128">Compiling multiple .mof files</span></span>

<span data-ttu-id="812a6-129">O bloco de nó também pode aceitar uma lista separada por vírgulas de nomes de computador e irá gerar os arquivos ". MOF" para cada um.</span><span class="sxs-lookup"><span data-stu-id="812a6-129">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="812a6-130">Você pode executar o exemplo a seguir para gerar arquivos de ". MOF" para todos os computadores no passado para o `-ComputerName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="812a6-130">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}

TestConfig -ComputerName "server01", "server02", "server03"
```

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="812a6-131">Parâmetros avançados em configurações</span><span class="sxs-lookup"><span data-stu-id="812a6-131">Advanced parameters in Configurations</span></span>

<span data-ttu-id="812a6-132">Além um `-ComputerName` parâmetro, podemos adicionar parâmetros para o nome do serviço e o estado.</span><span class="sxs-lookup"><span data-stu-id="812a6-132">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span> <span data-ttu-id="812a6-133">O exemplo a seguir adiciona um bloco de parâmetro com um `-ServiceName` parâmetro e o utiliza para definir dinamicamente o **Service** bloco de recurso.</span><span class="sxs-lookup"><span data-stu-id="812a6-133">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="812a6-134">Ele também adiciona uma `-State` parâmetro para definir dinamicamente o **estado** no **serviço** bloco de recurso.</span><span class="sxs-lookup"><span data-stu-id="812a6-134">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ServiceName,

        [String]
        $State,

        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="812a6-135">Em mais cenários de advacned, pode fazer mais sentido para mover os dados dinâmicos em um estruturados [dados de configuração](configData.md).</span><span class="sxs-lookup"><span data-stu-id="812a6-135">In more advacned scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="812a6-136">O exemplo de configuração agora leva dinâmico `$ServiceName`, mas se um não for especificado, resulta em um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="812a6-136">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="812a6-137">Você pode adicionar um valor padrão, como neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="812a6-137">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="812a6-138">Nesse caso, faz mais sentido simplesmente forçar o usuário especifique um valor para o `$ServiceName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="812a6-138">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="812a6-139">O `parameter` atributo permite que você adicionar a validação adicional e o pipeline que dão suporte a parâmetros de configuração.</span><span class="sxs-lookup"><span data-stu-id="812a6-139">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="812a6-140">Acima de qualquer declaração de parâmetro, adicione o `parameter` bloco de atributo, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="812a6-140">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="812a6-141">Você pode especificar argumentos para cada `parameter` atributo aos aspectos de controle do parâmetro definido.</span><span class="sxs-lookup"><span data-stu-id="812a6-141">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="812a6-142">O exemplo a seguir faz o `$ServiceName` uma **obrigatório** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="812a6-142">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="812a6-143">Para o `$State` parâmetro, gostaríamos de impedir que o usuário especificar valores fora de um conjunto predefinido (como em execução, parado) a `ValidationSet*`atributo possam impedir o usuário especificar valores fora de um conjunto predefinido (como em execução, Parado).</span><span class="sxs-lookup"><span data-stu-id="812a6-143">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="812a6-144">O exemplo a seguir adiciona o `ValidationSet` de atributo para o `$State` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="812a6-144">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="812a6-145">Uma vez que não queremos nos assegurar a `$State` parâmetro **obrigatório**, precisamos adicionar um valor padrão para ele.</span><span class="sxs-lookup"><span data-stu-id="812a6-145">Since we do not want to make the `$State` parameter **Mandatory**, we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="812a6-146">Você não precisará especificar uma `parameter` atributo ao usar um `validation` atributo.</span><span class="sxs-lookup"><span data-stu-id="812a6-146">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="812a6-147">Você pode ler mais sobre o `parameter` e os atributos de validação na [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="812a6-147">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="812a6-148">Totalmente com parâmetros de configuração</span><span class="sxs-lookup"><span data-stu-id="812a6-148">Fully parameterized Configuration</span></span>

<span data-ttu-id="812a6-149">Agora temos uma configuração com parâmetros que força o usuário a especificar uma `-InstanceName`, `-ServiceName`e valida o `-State` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="812a6-149">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [parameter(Mandatory)]
        [String]
        $ServiceName,

        [ValidateSet("Running","Stopped")]
        [String]
        $State="Running",

        [String]
        $ComputerName="localhost",
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="812a6-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="812a6-150">See also</span></span>

- [<span data-ttu-id="812a6-151">Gravar ajuda para configurações de DSC</span><span class="sxs-lookup"><span data-stu-id="812a6-151">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="812a6-152">Configurações dinâmicas</span><span class="sxs-lookup"><span data-stu-id="812a6-152">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="812a6-153">Usar dados de configuração em suas configurações</span><span class="sxs-lookup"><span data-stu-id="812a6-153">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="812a6-154">Dados de configuração e de ambiente separado</span><span class="sxs-lookup"><span data-stu-id="812a6-154">Separate configuration and environment data</span></span>](separatingEnvData.md)
