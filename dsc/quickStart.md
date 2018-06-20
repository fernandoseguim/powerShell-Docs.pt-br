---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Início Rápido de Configuração de Estado Desejado
ms.openlocfilehash: eb7572f39f7a2710c82f132f42c3502b15c48d0f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219038"
---
> <span data-ttu-id="3a9a9-103">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3a9a9-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="desired-state-configuration-quick-start"></a><span data-ttu-id="3a9a9-104">Início Rápido de Configuração de Estado Desejado</span><span class="sxs-lookup"><span data-stu-id="3a9a9-104">Desired State Configuration Quick Start</span></span>

<span data-ttu-id="3a9a9-105">Este exercício oferece instruções de como criar e aplicar uma configuração para a Configuração Estado Desejado (DSC) do início ao fim.</span><span class="sxs-lookup"><span data-stu-id="3a9a9-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="3a9a9-106">O exemplo que usaremos garante que o recurso `Web-Server` (IIS) do servidor esteja habilitado e que o conteúdo para um site "Hello World" simples esteja presente no diretório do `intepub\wwwroot` desse servidor.</span><span class="sxs-lookup"><span data-stu-id="3a9a9-106">The example we'll use ensures that a server has the `Web-Server` (IIS) feature enabled, and that the content for a simple "Hello World" website is present in the `intepub\wwwroot` directory of that server.</span></span>

<span data-ttu-id="3a9a9-107">Para obter uma visão geral sobre o que é a DSC e como ela funciona, confira [Visão Geral da Configuração do Estado Desejado para Tomadores de Decisão](decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="3a9a9-107">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="3a9a9-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a9a9-108">Requirements</span></span>

<span data-ttu-id="3a9a9-109">Para executar este exemplo, você precisará de um computador com o Windows Server 2012 ou posterior e o PowerShell 4.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="3a9a9-109">To run this example, you will need a computer running Windows Server 2012 or later and PowerShell 4.0 or later.</span></span>

## <a name="write-and-place-the-indexhtm-file"></a><span data-ttu-id="3a9a9-110">Gravar e posicionar o arquivo index.htm</span><span class="sxs-lookup"><span data-stu-id="3a9a9-110">Write and place the index.htm file</span></span>

<span data-ttu-id="3a9a9-111">Primeiro, vamos criar o arquivo HTML que usaremos como o conteúdo do site.</span><span class="sxs-lookup"><span data-stu-id="3a9a9-111">First, we'll create the HTML file that we will use as the website content.</span></span>

<span data-ttu-id="3a9a9-112">Na pasta-raiz, crie uma pasta chamada `test`.</span><span class="sxs-lookup"><span data-stu-id="3a9a9-112">In your root folder, create a folder named `test`.</span></span>

<span data-ttu-id="3a9a9-113">Em um editor de texto, digite o texto a seguir:</span><span class="sxs-lookup"><span data-stu-id="3a9a9-113">In a text editor, type the following text:</span></span>

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

<span data-ttu-id="3a9a9-114">Salve-o como `index.htm` na pasta `test` que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="3a9a9-114">Save this as `index.htm` in the `test` folder you created earlier.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="3a9a9-115">Gravar a configuração</span><span class="sxs-lookup"><span data-stu-id="3a9a9-115">Write the configuration</span></span>

<span data-ttu-id="3a9a9-116">Uma [Configuração DSC](configurations.md) é uma função especial do PowerShell que define como você deseja configurar um ou mais computadores de destino (nós).</span><span class="sxs-lookup"><span data-stu-id="3a9a9-116">A [DSC configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (nodes).</span></span>

<span data-ttu-id="3a9a9-117">No ISE do PowerShell, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3a9a9-117">In the PowerShell ISE, type the following:</span></span>

```powershell
Configuration WebsiteTest {

    # Import the module that contains the resources we're using.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets this configuration will be applied to.
    Node 'localhost' {

        # The first resource block ensures that the Web-Server (IIS) feature is enabled.
        WindowsFeature WebServer {
            Ensure = "Present"
            Name   = "Web-Server"
        }

        # The second resource block ensures that the website content copied to the website root folder.
        File WebsiteContent {
            Ensure = 'Present'
            SourcePath = 'c:\test\index.htm'
            DestinationPath = 'c:\inetpub\wwwroot'
        }
    }
}
```

<span data-ttu-id="3a9a9-118">Salve o arquivo como `WebsiteTest.ps1`.</span><span class="sxs-lookup"><span data-stu-id="3a9a9-118">Save the file as `WebsiteTest.ps1`.</span></span>

<span data-ttu-id="3a9a9-119">Você pode ver que ele parece uma função do PowerShell, com a adição da palavra-chave **Configuração** usada antes do nome da função.</span><span class="sxs-lookup"><span data-stu-id="3a9a9-119">You can see that it looks like a PowerShell function, with the addition of the keyword **Configuration** used before the name of the function.</span></span>

<span data-ttu-id="3a9a9-120">O bloco **Nó** especifica o nó de destino a ser configurado, neste caso `localhost`.</span><span class="sxs-lookup"><span data-stu-id="3a9a9-120">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="3a9a9-121">A configuração chama dois [recursos](resources.md), [WindowsFeature](windowsFeatureResource.md) e [Arquivo](fileResource.md).</span><span class="sxs-lookup"><span data-stu-id="3a9a9-121">The configuration calls two [resources](resources.md), [WindowsFeature](windowsFeatureResource.md) and [File](fileResource.md).</span></span>
<span data-ttu-id="3a9a9-122">Os recursos fazem o trabalho de garantir que o nó de destino está no estado definido pela configuração.</span><span class="sxs-lookup"><span data-stu-id="3a9a9-122">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="3a9a9-123">Compilar a configuração</span><span class="sxs-lookup"><span data-stu-id="3a9a9-123">Compile the configuration</span></span>

<span data-ttu-id="3a9a9-124">Para que uma configuração DSC seja aplicada a um nó, ela deve primeiro ser compilada em um arquivo MOF.</span><span class="sxs-lookup"><span data-stu-id="3a9a9-124">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="3a9a9-125">Para fazer isso, você deve executar a configuração como uma função.</span><span class="sxs-lookup"><span data-stu-id="3a9a9-125">To do this, you run the configuration like a function.</span></span>
<span data-ttu-id="3a9a9-126">Em um console do PowerShell, navegue até a mesma pasta em que você salvou sua configuração e execute os seguintes comandos para compilar a configuração em um arquivo MOF:</span><span class="sxs-lookup"><span data-stu-id="3a9a9-126">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following commands to compile the configuration into a MOF file:</span></span>

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

<span data-ttu-id="3a9a9-127">Isso gerará os seguintes resultados:</span><span class="sxs-lookup"><span data-stu-id="3a9a9-127">This generates the following output:</span></span>

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

<span data-ttu-id="3a9a9-128">A primeira linha torna a função de configuração disponível no console.</span><span class="sxs-lookup"><span data-stu-id="3a9a9-128">The first line makes the configuration function available in the console.</span></span>
<span data-ttu-id="3a9a9-129">A segunda linha executa a configuração.</span><span class="sxs-lookup"><span data-stu-id="3a9a9-129">The second line runs the configuration.</span></span>
<span data-ttu-id="3a9a9-130">O resultado é que uma nova pasta, chamada `WebsiteTest`, é criada como uma subpasta da pasta atual.</span><span class="sxs-lookup"><span data-stu-id="3a9a9-130">The result is that a new folder, named `WebsiteTest` is created as a subfolder of the current folder.</span></span>
<span data-ttu-id="3a9a9-131">A pasta `WebsiteTest` contém um arquivo chamado `localhost.mof`.</span><span class="sxs-lookup"><span data-stu-id="3a9a9-131">The `WebsiteTest` folder contains a file named `localhost.mof`.</span></span>
<span data-ttu-id="3a9a9-132">É o arquivo que pode ser aplicado ao nó de destino.</span><span class="sxs-lookup"><span data-stu-id="3a9a9-132">It is this file that can then be applied to the target node.</span></span>

## <a name="apply-the-configuration"></a><span data-ttu-id="3a9a9-133">Aplicar a configuração</span><span class="sxs-lookup"><span data-stu-id="3a9a9-133">Apply the configuration</span></span>

<span data-ttu-id="3a9a9-134">Agora que você tem o MOF compilado, é possível aplicar a configuração ao nó de destino (neste caso, o computador local) chamando o cmdlet [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration).</span><span class="sxs-lookup"><span data-stu-id="3a9a9-134">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet.</span></span>

<span data-ttu-id="3a9a9-135">O cmdlet `Start-DscConfiguration` indica ao [Gerenciador de Configurações Local (LCM)](metaConfig.md), qual é o mecanismo de DSC a aplicar à configuração.</span><span class="sxs-lookup"><span data-stu-id="3a9a9-135">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](metaConfig.md), which is the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="3a9a9-136">O LCM realiza o trabalho de chamar os recursos de DSC para aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="3a9a9-136">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="3a9a9-137">Em um console do PowerShell, navegue até a mesma pasta em que você salvou sua configuração e execute o mesmo comando:</span><span class="sxs-lookup"><span data-stu-id="3a9a9-137">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following command:</span></span>

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a><span data-ttu-id="3a9a9-138">Testar a configuração</span><span class="sxs-lookup"><span data-stu-id="3a9a9-138">Test the configuration</span></span>

<span data-ttu-id="3a9a9-139">Você pode chamar o cmdlet [Get-DscConfigurationStatus](/reference/5.1/PSDesiredStateConfiguration/Get-DscConfigurationStatus) para ver se a configuração foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="3a9a9-139">You can call the [Get-DscConfigurationStatus](/reference/5.1/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet to see whether the configuration succeeded.</span></span>

<span data-ttu-id="3a9a9-140">Você também pode testar os resultados diretamente, neste caso, pesquisando o `http://localhost/` em um navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="3a9a9-140">You can also test the results directly, in this case by browsing to `http://localhost/` in a web browser.</span></span>
<span data-ttu-id="3a9a9-141">Você deve ver a página de HTML "Hello World" que criou como a primeira etapa deste exemplo.</span><span class="sxs-lookup"><span data-stu-id="3a9a9-141">You should see the "Hello World" HTML page you created as the first step in this example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3a9a9-142">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="3a9a9-142">Next steps</span></span>

- <span data-ttu-id="3a9a9-143">Saiba mais sobre configurações de DSC em [Configurações de DSC](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="3a9a9-143">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="3a9a9-144">Veja quais recursos de DSC estão disponíveis e como criar recursos personalizados de DSC em [Recursos de DSC](resources.md).</span><span class="sxs-lookup"><span data-stu-id="3a9a9-144">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](resources.md).</span></span>
- <span data-ttu-id="3a9a9-145">Localize as configurações e recursos de DSC na [Galeria do PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="3a9a9-145">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>