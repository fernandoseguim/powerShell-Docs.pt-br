---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Lista de verificação da criação de recursos
ms.openlocfilehash: 76d9fecca8618fcc178975465f45cda0d0e04064
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="resource-authoring-checklist"></a><span data-ttu-id="e0e86-103">Lista de verificação da criação de recursos</span><span class="sxs-lookup"><span data-stu-id="e0e86-103">Resource authoring checklist</span></span>
<span data-ttu-id="e0e86-104">Esta lista de verificação é uma lista de melhores práticas ao criar um novo Recurso de DSC.</span><span class="sxs-lookup"><span data-stu-id="e0e86-104">This checklist is a list of best practices when authoring a new DSC Resource.</span></span>
## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a><span data-ttu-id="e0e86-105">O módulo de recurso contém os arquivos .psd1 e schema.mof de cada um dos recursos</span><span class="sxs-lookup"><span data-stu-id="e0e86-105">Resource module contains .psd1 file and schema.mof for every resource</span></span>
<span data-ttu-id="e0e86-106">Verifique se o recurso tem a estrutura correta e se ele contém todos os arquivos necessários.</span><span class="sxs-lookup"><span data-stu-id="e0e86-106">Check that your resource has correct structure and contains all required files.</span></span> <span data-ttu-id="e0e86-107">Cada módulo de recurso deve conter um arquivo .psd1 e cada recurso de não composição deve ter o arquivo schema.mof.</span><span class="sxs-lookup"><span data-stu-id="e0e86-107">Every resource module should contain a .psd1 file and every non-composite resource should have schema.mof file.</span></span> <span data-ttu-id="e0e86-108">Recursos que não contêm o esquema não serão listados por **Get-DscResource** e os usuários não poderão usar o IntelliSense ao escrever código nesses módulos no ISE.</span><span class="sxs-lookup"><span data-stu-id="e0e86-108">Resources that do not contain schema will not be listed by **Get-DscResource** and users will not be able to use the intellisense when writing code against those modules in ISE.</span></span>
<span data-ttu-id="e0e86-109">A estrutura de diretório para o recurso xRemoteFile, que faz parte do módulo de recurso [xPSDesiredStateConfiguration](https://github.com/PowerShell/xPSDesiredStateConfiguration), tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="e0e86-109">The directory structure for xRemoteFile resource, which is part of the [xPSDesiredStateConfiguration resource module](https://github.com/PowerShell/xPSDesiredStateConfiguration), looks as follows:</span></span>


```
xPSDesiredStateConfiguration
    DSCResources
        MSFT_xRemoteFile
            MSFT_xRemoteFile.psm1
            MSFT_xRemoteFile.schema.mof
    Examples
        xRemoteFile_DownloadFile.ps1
    ResourceDesignerScripts
        GenerateXRemoteFileSchema.ps1
    Tests
        ResourceDesignerTests.ps1
    xPSDesiredStateConfiguration.psd1
```

## <a name="resource-and-schema-are-correct"></a><span data-ttu-id="e0e86-110">Os recursos e o esquema estão corretos##</span><span class="sxs-lookup"><span data-stu-id="e0e86-110">Resource and schema are correct##</span></span>
<span data-ttu-id="e0e86-111">Verifique o arquivo de esquema do recurso (\*.schema.mof).</span><span class="sxs-lookup"><span data-stu-id="e0e86-111">Verify the resource schema (\*.schema.mof) file.</span></span> <span data-ttu-id="e0e86-112">Você pode usar o [Designer de Recursos da DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) para ajudar a desenvolver e testar seu esquema.</span><span class="sxs-lookup"><span data-stu-id="e0e86-112">You can use the [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) to help develop and test your schema.</span></span>
<span data-ttu-id="e0e86-113">Certifique-se de que:</span><span class="sxs-lookup"><span data-stu-id="e0e86-113">Make sure that:</span></span>
- <span data-ttu-id="e0e86-114">Os tipos de propriedade estão corretos (por exemplo, não use Cadeia de caracteres para propriedades que aceitam valores numéricos; em vez disso, use UInt32 ou outros tipos numéricos)</span><span class="sxs-lookup"><span data-stu-id="e0e86-114">Property types are correct (e.g. don’t use String for properties which accept numeric values, you should use UInt32 or other numeric types instead)</span></span>
- <span data-ttu-id="e0e86-115">Os atributos de propriedade foram especificados corretamente como: ([key], [required], [write] e [read])</span><span class="sxs-lookup"><span data-stu-id="e0e86-115">Property attributes are specified correctly as: ([key], [required], [write], [read])</span></span>
- <span data-ttu-id="e0e86-116">Pelo menos, um parâmetro no esquema deve estar marcado como [key]</span><span class="sxs-lookup"><span data-stu-id="e0e86-116">At least one parameter in the schema has to be marked as [key]</span></span>
- <span data-ttu-id="e0e86-117">A propriedade [read] não coexiste com nenhuma dessas: [required], [key] e [write]</span><span class="sxs-lookup"><span data-stu-id="e0e86-117">[read] property does not coexist together with any of: [required], [key], [write]</span></span>
- <span data-ttu-id="e0e86-118">Se forem especificados vários qualificadores, exceto [read], [key] terá precedência</span><span class="sxs-lookup"><span data-stu-id="e0e86-118">If multiple qualifiers are specified except [read], then [key] takes precedence</span></span>
- <span data-ttu-id="e0e86-119">Se [write] e [required] forem especificados, [required] terá precedência</span><span class="sxs-lookup"><span data-stu-id="e0e86-119">If [write] and [required] are specified, then [required] takes precedence</span></span>
- <span data-ttu-id="e0e86-120">ValueMap foi especificado, quando apropriado</span><span class="sxs-lookup"><span data-stu-id="e0e86-120">ValueMap is specified where appropriate</span></span>

<span data-ttu-id="e0e86-121">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="e0e86-121">Example:</span></span>
```
[Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
```

- <span data-ttu-id="e0e86-122">O nome amigável é especificado e está em conformidade com as convenções de nomenclatura do DSC</span><span class="sxs-lookup"><span data-stu-id="e0e86-122">Friendly name is specified and confirms to DSC naming conventions</span></span>

<span data-ttu-id="e0e86-123">Exemplo: ```[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]```</span><span class="sxs-lookup"><span data-stu-id="e0e86-123">Example: ```[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]```</span></span>

- <span data-ttu-id="e0e86-124">Cada campo contém uma descrição significativa.</span><span class="sxs-lookup"><span data-stu-id="e0e86-124">Every field has meaningful description.</span></span> <span data-ttu-id="e0e86-125">O repositório GitHub do PowerShell tem bons exemplos, como o [.schema.mof para xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span><span class="sxs-lookup"><span data-stu-id="e0e86-125">The PowerShell GitHub repository has good examples, such as [the .schema.mof for xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span></span>

<span data-ttu-id="e0e86-126">Além disso, é necessário usar os cmdlets **Test-xDscResource** e **Test-xDscSchema** do [Designer de Recursos da DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) para verificar automaticamente o recurso e o esquema:</span><span class="sxs-lookup"><span data-stu-id="e0e86-126">Additionally, you should use **Test-xDscResource** and **Test-xDscSchema** cmdlets from [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) to automatically verify the resource and schema:</span></span>
```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```
<span data-ttu-id="e0e86-127">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e0e86-127">For example:</span></span>
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a><span data-ttu-id="e0e86-128">O recurso é carregado sem erros</span><span class="sxs-lookup"><span data-stu-id="e0e86-128">Resource loads without errors</span></span> ##
<span data-ttu-id="e0e86-129">Verifique se o módulo de recurso poderá ser carregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="e0e86-129">Check whether the resource module can be successfully loaded.</span></span>
<span data-ttu-id="e0e86-130">Isso pode ser feito manualmente executando `Import-Module <resource_module> -force ` e confirmando se não ocorreu nenhum erro, ou ainda escrevendo uma automação de teste.</span><span class="sxs-lookup"><span data-stu-id="e0e86-130">This can be achieved manually, by running `Import-Module <resource_module> -force ` and confirming that no errors occurred, or by writing test automation.</span></span> <span data-ttu-id="e0e86-131">No caso do último, é possível seguir esta estrutura em seu caso de teste:</span><span class="sxs-lookup"><span data-stu-id="e0e86-131">In case of the latter, you can follow this structure in your test case:</span></span>
```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```
## <a name="resource-is-idempotent-in-the-positive-case"></a><span data-ttu-id="e0e86-132">O recurso é idempotente no caso positivo</span><span class="sxs-lookup"><span data-stu-id="e0e86-132">Resource is idempotent in the positive case</span></span>
<span data-ttu-id="e0e86-133">Uma das características fundamentais dos recursos da DSC é a idempotência.</span><span class="sxs-lookup"><span data-stu-id="e0e86-133">One of the fundamental characteristics of DSC resources is be idempotence.</span></span> <span data-ttu-id="e0e86-134">Isso significa que aplicar várias vezes uma configuração de DSC que contém esse recurso fará com que o mesmo resultado seja obtido sempre.</span><span class="sxs-lookup"><span data-stu-id="e0e86-134">It means that applying a DSC configuration containing that resource multiple times will always achieve the same result.</span></span> <span data-ttu-id="e0e86-135">Por exemplo, se criarmos uma configuração que contém o seguinte recurso File:</span><span class="sxs-lookup"><span data-stu-id="e0e86-135">For example, if we create a configuration which contains the following File resource:</span></span>
```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```
<span data-ttu-id="e0e86-136">Depois de aplicá-la pela primeira vez, o arquivo test.txt deve aparecer na pasta C:\test.</span><span class="sxs-lookup"><span data-stu-id="e0e86-136">After applying it for the first time, file test.txt should appear in C:\test folder.</span></span> <span data-ttu-id="e0e86-137">No entanto, execuções posteriores da mesma configuração não devem alterar o estado do computador (por exemplo, nenhuma cópia do arquivo test.txt deve ser criada).</span><span class="sxs-lookup"><span data-stu-id="e0e86-137">However, subsequent runs of the same configuration should not change the state of the machine (e.g. no copies of the test.txt file should be created).</span></span>
<span data-ttu-id="e0e86-138">Para garantir que um recurso é idempotente, você pode chamar repetidamente **Set-TargetResource** ao testar o recurso diretamente, ou chamar **Start-DscConfiguration** várias vezes ao realizar testes de ponta a ponta.</span><span class="sxs-lookup"><span data-stu-id="e0e86-138">To ensure a resource is idempotent you can repeatedly call **Set-TargetResource** when testing the resource directly, or call **Start-DscConfiguration** multiple times when doing end to end testing.</span></span> <span data-ttu-id="e0e86-139">O resultado deve ser o mesmo após cada execução.</span><span class="sxs-lookup"><span data-stu-id="e0e86-139">The result should be the same after every run.</span></span>


## <a name="test-user-modification-scenario"></a><span data-ttu-id="e0e86-140">Cenário de modificação de usuário de teste</span><span class="sxs-lookup"><span data-stu-id="e0e86-140">Test user modification scenario</span></span> ##
<span data-ttu-id="e0e86-141">Ao alterar o estado do computador e, em seguida, executar a DSC novamente, você poderá verificar se **Set-TargetResource** e **Test-TargetResource** funcionam corretamente.</span><span class="sxs-lookup"><span data-stu-id="e0e86-141">By changing the state of the machine and then rerunning DSC, you can verify that **Set-TargetResource** and **Test-TargetResource** function properly.</span></span> <span data-ttu-id="e0e86-142">Aqui estão as etapas que devem ser seguidas:</span><span class="sxs-lookup"><span data-stu-id="e0e86-142">Here are steps you should take:</span></span>
1.  <span data-ttu-id="e0e86-143">Inicie com o recurso fora do estado desejado.</span><span class="sxs-lookup"><span data-stu-id="e0e86-143">Start with the resource not in the desired state.</span></span>
2.  <span data-ttu-id="e0e86-144">Executar a configuração com o recurso</span><span class="sxs-lookup"><span data-stu-id="e0e86-144">Run configuration with your resource</span></span>
3.  <span data-ttu-id="e0e86-145">Verificar se **Test-DscConfiguration** retorna True</span><span class="sxs-lookup"><span data-stu-id="e0e86-145">Verify **Test-DscConfiguration** returns True</span></span>
4.  <span data-ttu-id="e0e86-146">Modificar o item configurado para ficar fora do estado desejado</span><span class="sxs-lookup"><span data-stu-id="e0e86-146">Modify the configured item to be out of the desired state</span></span>
5.  <span data-ttu-id="e0e86-147">Verifique se **Test-DscConfiguration** retorna false. Veja um exemplo mais concreto usando o recurso de Registro:</span><span class="sxs-lookup"><span data-stu-id="e0e86-147">Verify **Test-DscConfiguration** returns false Here’s a more concrete example using Registry resource:</span></span>
1.  <span data-ttu-id="e0e86-148">Inicie com a chave do Registro fora do estado desejado</span><span class="sxs-lookup"><span data-stu-id="e0e86-148">Start with registry key not in the desired state</span></span>
2.  <span data-ttu-id="e0e86-149">Executar **Start-DscConfiguration** com uma configuração para colocá-la no estado desejado e verificar se ela é passada.</span><span class="sxs-lookup"><span data-stu-id="e0e86-149">Run **Start-DscConfiguration** with a configuration to put it in the desired state and verify it passes.</span></span>
3.  <span data-ttu-id="e0e86-150">Executar **Test-DscConfiguration** e verificar se ela retorna True</span><span class="sxs-lookup"><span data-stu-id="e0e86-150">Run **Test-DscConfiguration** and verify it returns true</span></span>
4.  <span data-ttu-id="e0e86-151">Modificar o valor da chave para que ela não esteja no estado desejado</span><span class="sxs-lookup"><span data-stu-id="e0e86-151">Modify the value of the key so that it is not in the desired state</span></span>
5.  <span data-ttu-id="e0e86-152">Executar **Test-DscConfiguration** e verificar se ela retorna False</span><span class="sxs-lookup"><span data-stu-id="e0e86-152">Run **Test-DscConfiguration** and verify it returns false</span></span>
6.  <span data-ttu-id="e0e86-153">A funcionalidade de Get-TargetResource foi verificada usando Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="e0e86-153">Get-TargetResource functionality was verified using Get-DscConfiguration</span></span>

<span data-ttu-id="e0e86-154">Get-TargetResource deve retornar detalhes do estado atual do recurso.</span><span class="sxs-lookup"><span data-stu-id="e0e86-154">Get-TargetResource should return details of the current state of the resource.</span></span> <span data-ttu-id="e0e86-155">Certifique-se de testá-lo chamando Get-DscConfiguration depois de aplicar a configuração e verificar se a saída reflete corretamente o estado atual do computador.</span><span class="sxs-lookup"><span data-stu-id="e0e86-155">Make sure to test it by calling Get-DscConfiguration after you apply the configuration and verifying that output correctly reflects the current state of the machine.</span></span> <span data-ttu-id="e0e86-156">É importante testá-lo separadamente, pois quaisquer problemas nesta área não aparecerão ao chamar Start-DscConfiguration.</span><span class="sxs-lookup"><span data-stu-id="e0e86-156">It's important to test it separately, since any issues in this area won't appear when calling Start-DscConfiguration.</span></span>

## <a name="call-getsettest-targetresource-functions-directly"></a><span data-ttu-id="e0e86-157">Chame as funções **Get/Set/Test-TargetResource** diretamente</span><span class="sxs-lookup"><span data-stu-id="e0e86-157">Call **Get/Set/Test-TargetResource** functions directly</span></span> ##

<span data-ttu-id="e0e86-158">Certifique-se de testar as funções **Get/Set/Test-TargetResource** implementadas em seu recurso chamando-as diretamente e verificando se funcionam como esperado.</span><span class="sxs-lookup"><span data-stu-id="e0e86-158">Make sure you test the **Get/Set/Test-TargetResource** functions implemented in your resource by calling them directly and verifying that they work as expected.</span></span>

## <a name="verify-end-to-end-using-start-dscconfiguration"></a><span data-ttu-id="e0e86-159">Faça uma verificação completa usando **Start-DscConfiguration**</span><span class="sxs-lookup"><span data-stu-id="e0e86-159">Verify End to End using **Start-DscConfiguration**</span></span> ##

<span data-ttu-id="e0e86-160">É importante testar as funções **Get/Set/Test-TargetResource** chamando-as diretamente; no entanto, nem todos os problemas serão descobertos dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="e0e86-160">Testing **Get/Set/Test-TargetResource** functions by calling them directly is important, but not all issues will be discovered this way.</span></span> <span data-ttu-id="e0e86-161">Você deve concentrar uma parte significativa do teste no uso de **Start-DscConfiguration** ou no servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="e0e86-161">You should focus significant part of your testing on using **Start-DscConfiguration** or the pull server.</span></span> <span data-ttu-id="e0e86-162">Na verdade, essa é a forma como os usuários usarão o recurso; portanto, não subestime a importância desse tipo de testes.</span><span class="sxs-lookup"><span data-stu-id="e0e86-162">In fact, this is how users will use the resource, so don’t underestimate the significance of this type of tests.</span></span>
<span data-ttu-id="e0e86-163">Possíveis tipos de problemas:</span><span class="sxs-lookup"><span data-stu-id="e0e86-163">Possible types of issues:</span></span>
- <span data-ttu-id="e0e86-164">A Credencial/Sessão podem se comportar de maneira diferente, porque o agente do DSC é executado como um serviço.</span><span class="sxs-lookup"><span data-stu-id="e0e86-164">Credential/Session may behave differently because the DSC agent runs as a service.</span></span>  <span data-ttu-id="e0e86-165">Certifique-se de testar quaisquer recursos aqui de ponta a ponta.</span><span class="sxs-lookup"><span data-stu-id="e0e86-165">Be sure to test any features here end to end.</span></span>
- <span data-ttu-id="e0e86-166">Os erros gerados por **Start-DscConfiguration** podem ser diferentes daqueles exibidos ao chamar diretamente a função **Set-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="e0e86-166">Errors output by **Start-DscConfiguration** may be different than those displayed when calling the **Set-TargetResource** function directly.</span></span>

## <a name="test-compatability-on-all-dsc-supported-platforms"></a><span data-ttu-id="e0e86-167">Teste a compatibilidade em todas as plataformas com suporte para DSC</span><span class="sxs-lookup"><span data-stu-id="e0e86-167">Test compatability on all DSC supported platforms</span></span> ##
<span data-ttu-id="e0e86-168">O recurso deve funcionar em todas as plataformas do DSC com suporte (Windows Server 2008 R2 e mais recente).</span><span class="sxs-lookup"><span data-stu-id="e0e86-168">Resource should work on all DSC supported platforms (Windows Server 2008 R2 and newer).</span></span> <span data-ttu-id="e0e86-169">Instale o WMF (Windows Management Framework) mais recente em seu sistema operacional para obter a versão mais recente da DSC.</span><span class="sxs-lookup"><span data-stu-id="e0e86-169">Install the latest WMF (Windows Management Framework) on your OS to get the latest version of DSC.</span></span> <span data-ttu-id="e0e86-170">Se seu recurso não funcionar em algumas dessas plataformas por design, uma mensagem de erro específica deverá ser retornada.</span><span class="sxs-lookup"><span data-stu-id="e0e86-170">If your resource does not work on some of these platforms by design, a specific error message should be returned.</span></span> <span data-ttu-id="e0e86-171">Além disso, certifique-se de que o recurso verifica se os cmdlets que estão sendo chamados estão presentes em um computador específico.</span><span class="sxs-lookup"><span data-stu-id="e0e86-171">Also, make sure your resource checks whether cmdlets you are calling are present on particular machine.</span></span> <span data-ttu-id="e0e86-172">O Windows Server 2012 adicionou um grande número de novos cmdlets que não estão disponíveis no Windows Server 2008R2, mesmo com o WMF instalado.</span><span class="sxs-lookup"><span data-stu-id="e0e86-172">Windows Server 2012 added a large number of new cmdlets that are not available on Windows Server 2008R2, even with WMF installed.</span></span>

## <a name="verify-on-windows-client-if-applicable"></a><span data-ttu-id="e0e86-173">Verifique no Windows Client (se aplicável)</span><span class="sxs-lookup"><span data-stu-id="e0e86-173">Verify on Windows Client (if applicable)</span></span> ##
<span data-ttu-id="e0e86-174">Um intervalo de teste muito comum é verificar o recurso somente nas versões do servidor do Windows.</span><span class="sxs-lookup"><span data-stu-id="e0e86-174">One very common test gap is verifying the resource only on server versions of Windows.</span></span> <span data-ttu-id="e0e86-175">Muitos recursos também foram projetados para funcionar em SKUs do Cliente; portanto, se esse for o seu caso, não se esqueça de testá-lo nessas plataformas também.</span><span class="sxs-lookup"><span data-stu-id="e0e86-175">Many resources are also designed to work on Client SKUs, so if that’s true in your case, don’t forget to test it on those platforms as well.</span></span>
## <a name="get-dscresource-lists-the-resource"></a><span data-ttu-id="e0e86-176">Get-DSCResource lista os recursos</span><span class="sxs-lookup"><span data-stu-id="e0e86-176">Get-DSCResource lists the resource</span></span> ##
<span data-ttu-id="e0e86-177">Depois de implantar o módulo, uma chamada a Get-DscResource deverá listar seu recurso, entre outros, como resultado.</span><span class="sxs-lookup"><span data-stu-id="e0e86-177">After deploying the module, calling Get-DscResource should list your resource among others as a result.</span></span> <span data-ttu-id="e0e86-178">Se não encontrar seu recurso na lista, verifique se o arquivo schema.mof para esse recurso existe.</span><span class="sxs-lookup"><span data-stu-id="e0e86-178">If you can’t find your resource in the list, make sure that schema.mof file for that resource exists.</span></span>
## <a name="resource-module-contains-examples"></a><span data-ttu-id="e0e86-179">O módulo de recurso contém exemplos</span><span class="sxs-lookup"><span data-stu-id="e0e86-179">Resource module contains examples</span></span> ##
<span data-ttu-id="e0e86-180">Criando exemplos de qualidade que ajudarão outros a entender como usá-los.</span><span class="sxs-lookup"><span data-stu-id="e0e86-180">Creating quality examples which will help others understand how to use it.</span></span> <span data-ttu-id="e0e86-181">Isso é crucial, especialmente porque muitos usuários tratam o código de exemplo como documentação.</span><span class="sxs-lookup"><span data-stu-id="e0e86-181">This is crucial, especially since many users treat sample code as documentation.</span></span>
- <span data-ttu-id="e0e86-182">Primeiro, é necessário determinar os exemplos que serão incluídos com o módulo – no mínimo, deve-se abranger os casos de uso mais importantes para o recurso:</span><span class="sxs-lookup"><span data-stu-id="e0e86-182">First, you should determine the examples that will be included with the module – at minimum, you should cover most important use cases for your resource:</span></span>
- <span data-ttu-id="e0e86-183">Se o módulo contiver vários recursos que precisam funcionar juntos para um cenário de ponta a ponta, o exemplo de ponta a ponta básico seria, teoricamente, o primeiro.</span><span class="sxs-lookup"><span data-stu-id="e0e86-183">If your module contains several resources that need to work together for an end-to-end scenario, the basic end-to-end example would ideally be first.</span></span>
- <span data-ttu-id="e0e86-184">Os exemplos inicias devem ser bem simples – como começar a usar seus recursos em partes gerenciáveis pequenas (por exemplo, criar um novo VHD)</span><span class="sxs-lookup"><span data-stu-id="e0e86-184">The initial examples should be very simple -- how to get started with your resources in small manageable chunks (e.g. creating a new VHD)</span></span>
- <span data-ttu-id="e0e86-185">Os exemplos posteriores devem se basear nesses exemplos (por exemplo, criar uma VM desde um VHD, remover a VM e modificá-la) e mostrar a funcionalidade avançada (por exemplo, criar uma VM com memória dinâmica)</span><span class="sxs-lookup"><span data-stu-id="e0e86-185">Subsequent examples should build on those examples (e.g. creating a VM from a VHD, removing VM, modifying VM), and show advanced functionality (e.g. creating a VM with dynamic memory)</span></span>
- <span data-ttu-id="e0e86-186">Os exemplos de configurações devem ser parametrizados (todos os valores devem ser passados para a configuração como parâmetros e não deve haver nenhum valor fixo):</span><span class="sxs-lookup"><span data-stu-id="e0e86-186">Example configurations should be parameterized (all values should be passed to the configuration as parameters and there should be no hardcoded values):</span></span>
```powershell
configuration Sample_xRemoteFile_DownloadFile
{
    param
    (
        [string[]] $nodeName = 'localhost',

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $destinationPath,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $uri,

        [String] $userAgent,

        [Hashtable] $headers
    )

    Import-DscResource -Name MSFT_xRemoteFile -ModuleName xPSDesiredStateConfiguration

    Node $nodeName
    {
        xRemoteFile DownloadFile
        {
            DestinationPath = $destinationPath
            Uri = $uri
            UserAgent = $userAgent
            Headers = $headers
        }
    }
}
```
- <span data-ttu-id="e0e86-187">É uma prática recomendada incluir um exemplo (comentado) de como chamar a configuração com os valores reais no final do script de exemplo.</span><span class="sxs-lookup"><span data-stu-id="e0e86-187">It’s a good practice to include (commented out) example of how to call the configuration with the actual values at the end of the example script.</span></span>
<span data-ttu-id="e0e86-188">Por exemplo, na configuração acima, não é absolutamente óbvio que a melhor maneira de especificar o UserAgent é:</span><span class="sxs-lookup"><span data-stu-id="e0e86-188">For example, in the configuration above it isn't neccessarily obvious that the best way to specify UserAgent is:</span></span>

<span data-ttu-id="e0e86-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` Nesse caso, um comentário pode esclarecer a execução pretendida da configuração:</span><span class="sxs-lookup"><span data-stu-id="e0e86-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` In which case a comment can clarify the intended execution of the configuration:</span></span>
```
<#
Sample use (parameter values need to be changed according to your scenario):

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
-userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
#>
```
- <span data-ttu-id="e0e86-190">Para cada exemplo, escreva uma breve descrição que explica o que ele faz e o significado dos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="e0e86-190">For each example, write a short description which explains what it does, and the meaning of the parameters.</span></span>
- <span data-ttu-id="e0e86-191">Certifique-se de que os exemplos abrangem a maioria dos cenários importantes para o recurso e que nada está faltando, verifique se todos eles são executados e coloque o computador no estado desejado.</span><span class="sxs-lookup"><span data-stu-id="e0e86-191">Make sure examples cover most the important scenarios for your resource and if there’s nothing missing, verify that they all execute and put machine in the desired state.</span></span>

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a><span data-ttu-id="e0e86-192">Mensagens de erro são fáceis de entender e ajudam os usuários a resolver problemas</span><span class="sxs-lookup"><span data-stu-id="e0e86-192">Error messages are easy to understand and help users solve problems</span></span> ##
<span data-ttu-id="e0e86-193">Mensagens de erro úteis devem ser:</span><span class="sxs-lookup"><span data-stu-id="e0e86-193">Good error messages should be:</span></span>
- <span data-ttu-id="e0e86-194">Existentes: o maior problema com mensagens de erro é que elas, geralmente, não existem; portanto, certifique-se de que elas existem.</span><span class="sxs-lookup"><span data-stu-id="e0e86-194">There: The biggest problem with error messages is that they often don’t exist, so make sure they are there.</span></span>
- <span data-ttu-id="e0e86-195">Fáceis de entender: legíveis por humanos e sem códigos de erro obscuros</span><span class="sxs-lookup"><span data-stu-id="e0e86-195">Easy to understand: Human readable, no obscure error codes</span></span>
- <span data-ttu-id="e0e86-196">Precisas: descrevem qual é exatamente o problema</span><span class="sxs-lookup"><span data-stu-id="e0e86-196">Precise: Describe what’s exactly the problem</span></span>
- <span data-ttu-id="e0e86-197">Construtivas: fazem recomendações sobre como corrigir o problema</span><span class="sxs-lookup"><span data-stu-id="e0e86-197">Constructive: Advice how to fix the issue</span></span>
- <span data-ttu-id="e0e86-198">Cortês: não culpe o usuário nem o faça se sentir mal. Verifique os erros nos cenários de ponta a ponta (usando **Start-DscConfiguration**), pois eles podem ser diferentes daqueles retornados ao executar as funções de recurso diretamente.</span><span class="sxs-lookup"><span data-stu-id="e0e86-198">Polite: Don’t blame user or make them feel bad Make sure you verify errors in End to End scenarios (using **Start-DscConfiguration**), because they may differ from those returned when running resource functions directly.</span></span>

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a><span data-ttu-id="e0e86-199">Mensagens de log são informativas e fáceis de entender (incluindo –verbose, –debug e logs do ETW)</span><span class="sxs-lookup"><span data-stu-id="e0e86-199">Log messages are easy to understand and informative (including –verbose, –debug and ETW logs)</span></span> ##
<span data-ttu-id="e0e86-200">Certifique-se de que logs gerados pelo recurso são fáceis de entender e fornecem valor ao usuário.</span><span class="sxs-lookup"><span data-stu-id="e0e86-200">Ensure that logs outputted by the resource are easy to understand and provide value to the user.</span></span> <span data-ttu-id="e0e86-201">Os recursos devem gerar todas as informações que podem ser úteis para o usuário; contudo, mais logs nem sempre são o melhor.</span><span class="sxs-lookup"><span data-stu-id="e0e86-201">Resources should output all information which might be helpful to the user, but more logs is not always better.</span></span> <span data-ttu-id="e0e86-202">É necessário evitar a redundância e gerar dados que não fornecem valor adicional – não faça alguém percorrer centenas de entradas de log para encontrar o que está procurando.</span><span class="sxs-lookup"><span data-stu-id="e0e86-202">You should avoid redundancy and outputting data which does not provide additional value – don’t make someone go through hundreds of log entries in order to find what they're looking for.</span></span> <span data-ttu-id="e0e86-203">Obviamente, não fornecer nenhum log também não é uma solução aceitável para esse problema.</span><span class="sxs-lookup"><span data-stu-id="e0e86-203">Of course, no logs is not an acceptable solution for this problem either.</span></span>

<span data-ttu-id="e0e86-204">Durante o teste, também é necessário analisar logs detalhados e de depuração (executando **Start-DscConfiguration** com as opções –verbose e –debug de maneira adequada), bem como os logs do ETW.</span><span class="sxs-lookup"><span data-stu-id="e0e86-204">When testing, you should also analyze verbose and debug logs (by running **Start-DscConfiguration** with –verbose and –debug switches appropriately), as well as ETW logs.</span></span> <span data-ttu-id="e0e86-205">Para ver os logs do ETW no DSC, vá para o Visualizador de Eventos e abra a seguinte pasta: Aplicativos e Serviços – Microsoft – Windows – Configuração de Estado Desejado.</span><span class="sxs-lookup"><span data-stu-id="e0e86-205">To see DSC ETW logs, go to Event Viewer and open the following folder: Applications and Services- Microsoft - Windows - Desired State Configuration.</span></span>  <span data-ttu-id="e0e86-206">Por padrão, haverá o canal Operacional, mas lembre-se de habilitar os canais Analítico e de Depuração antes de executar a configuração.</span><span class="sxs-lookup"><span data-stu-id="e0e86-206">By default there will be Operational channel, but make sure you enable Analytic and Debug channels before running the configuration.</span></span>
<span data-ttu-id="e0e86-207">Para habilitar os canais Analítico/de Depuração, é possível executar o script abaixo:</span><span class="sxs-lookup"><span data-stu-id="e0e86-207">To enable Analytic/Debug channels, you can execute script below:</span></span>
```powershell
$statusEnabled = $true
# Use "Analytic" to enable Analytic channel
$eventLogFullName = "Microsoft-Windows-Dsc/Debug"
$commandToExecute = "wevtutil set-log $eventLogFullName /e:$statusEnabled /q:$statusEnabled   "
$log = New-Object System.Diagnostics.Eventing.Reader.EventLogConfiguration $eventLogFullName
if($statusEnabled -eq $log.IsEnabled)
{
    Write-Host -Verbose "The channel event log is already enabled"
    return
}
Invoke-Expression $commandToExecute
```
## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a><span data-ttu-id="e0e86-208">A implementação de recurso não contêm caminhos fixos</span><span class="sxs-lookup"><span data-stu-id="e0e86-208">Resource implementation does not contain hardcoded paths</span></span> ##
<span data-ttu-id="e0e86-209">Assegure-se de que não há nenhum caminho fixo na implementação de recurso, especialmente, se ele assume um idioma (en-us) ou quando houver variáveis do sistema que podem ser usadas.</span><span class="sxs-lookup"><span data-stu-id="e0e86-209">Ensure there are no hardcoded paths in the resource implementation, particularly if they assume language (en-us), or when there are system variables that can be used.</span></span>
<span data-ttu-id="e0e86-210">Se o recurso precisar acessar caminhos específicos, use variáveis de ambiente em vez de fixar o caminho no código, pois ele pode ser diferente em outros computadores.</span><span class="sxs-lookup"><span data-stu-id="e0e86-210">If your resource need to access specific paths, use environment variables instead of hardcoding the path, as it may differ on other machines.</span></span>

<span data-ttu-id="e0e86-211">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="e0e86-211">Example:</span></span>

<span data-ttu-id="e0e86-212">Em vez de:</span><span class="sxs-lookup"><span data-stu-id="e0e86-212">Instead of:</span></span>
```
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
 ```
<span data-ttu-id="e0e86-213">É possível escrever:</span><span class="sxs-lookup"><span data-stu-id="e0e86-213">You can write:</span></span>
```
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```
## <a name="resource-implementation-does-not-contain-user-information"></a><span data-ttu-id="e0e86-214">A implementação de recurso não contêm informações do usuário</span><span class="sxs-lookup"><span data-stu-id="e0e86-214">Resource implementation does not contain user information</span></span> ##
<span data-ttu-id="e0e86-215">Assegure-se de que não há nenhum nome de email, informações de conta ou nome de pessoas no código.</span><span class="sxs-lookup"><span data-stu-id="e0e86-215">Make sure there are no email names, account information, or names of people in the code.</span></span>
## <a name="resource-was-tested-with-validinvalid-credentials"></a><span data-ttu-id="e0e86-216">O recurso foi testado com credenciais válidas/inválidas</span><span class="sxs-lookup"><span data-stu-id="e0e86-216">Resource was tested with valid/invalid credentials</span></span> ##
<span data-ttu-id="e0e86-217">Caso o recurso use uma credencial como parâmetro:</span><span class="sxs-lookup"><span data-stu-id="e0e86-217">If your resource takes a credential as parameter:</span></span>
- <span data-ttu-id="e0e86-218">Verifique se o recurso funciona quando o Sistema Local (ou a conta de computador de recursos remotos) não tem acesso.</span><span class="sxs-lookup"><span data-stu-id="e0e86-218">Verify the resource works when Local System (or the computer account for remote resources) does not have access.</span></span>
- <span data-ttu-id="e0e86-219">Verifique se o recurso funciona com uma credencial especificada para Get, Set e Test</span><span class="sxs-lookup"><span data-stu-id="e0e86-219">Verify the resource works with a credential specified for Get, Set and Test</span></span>
- <span data-ttu-id="e0e86-220">Caso o recurso acesse os compartilhamentos, teste todas as variantes para as quais é necessário dar suporte, como:</span><span class="sxs-lookup"><span data-stu-id="e0e86-220">If your resource accesses shares, test all the variants you need to support, such as:</span></span>
  - <span data-ttu-id="e0e86-221">Compartilhamentos de janelas padrão.</span><span class="sxs-lookup"><span data-stu-id="e0e86-221">Standard windows shares.</span></span>
  - <span data-ttu-id="e0e86-222">Compartilhamentos DFS.</span><span class="sxs-lookup"><span data-stu-id="e0e86-222">DFS shares.</span></span>
  - <span data-ttu-id="e0e86-223">Compartilhamentos SAMBA (se desejar dar suporte ao Linux).</span><span class="sxs-lookup"><span data-stu-id="e0e86-223">SAMBA shares (if you want to support Linux.)</span></span>

## <a name="resource-does-not-require-interactive-input"></a><span data-ttu-id="e0e86-224">O recurso não requer entrada interativa</span><span class="sxs-lookup"><span data-stu-id="e0e86-224">Resource does not require interactive input</span></span> ##
<span data-ttu-id="e0e86-225">As funções **Get/Set/Test-TargetResource** devem ser executadas automaticamente e não devem aguardar pela entrada do usuário em nenhum estágio de execução (por exemplo, não se deve usar **Get-Credential** dentro dessas funções).</span><span class="sxs-lookup"><span data-stu-id="e0e86-225">**Get/Set/Test-TargetResource** functions should be executed automatically and must not wait for user’s input at any stage of execution (e.g. you should not use **Get-Credential** inside these functions).</span></span> <span data-ttu-id="e0e86-226">Se precisar fornecer a entrada do usuário, será necessário passá-la para a configuração como parâmetro durante a fase de compilação.</span><span class="sxs-lookup"><span data-stu-id="e0e86-226">If you need to provide user’s input, you should pass it to the configuration as parameter during the compilation phase.</span></span>
## <a name="resource-functionality-was-thoroughly-tested"></a><span data-ttu-id="e0e86-227">A funcionalidade do recurso foi totalmente testada</span><span class="sxs-lookup"><span data-stu-id="e0e86-227">Resource functionality was thoroughly tested</span></span> ##
<span data-ttu-id="e0e86-228">Esta lista de verificação contém itens cujo teste é importante e/ou que, frequentemente, estão ausentes.</span><span class="sxs-lookup"><span data-stu-id="e0e86-228">This checklist contains items which are important to be tested and/or are often missed.</span></span> <span data-ttu-id="e0e86-229">Haverá vários testes, principalmente, aqueles funcionais que serão específicos ao recurso que está sendo testado e que não são mencionados aqui.</span><span class="sxs-lookup"><span data-stu-id="e0e86-229">There will be bunch of tests, mainly functional ones which will be specific to the resource you are testing and are not mentioned here.</span></span> <span data-ttu-id="e0e86-230">Não se esqueça dos casos de teste negativos.</span><span class="sxs-lookup"><span data-stu-id="e0e86-230">Don’t forget about negative test cases.</span></span>
## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a><span data-ttu-id="e0e86-231">Prática recomendada: o módulo de recurso contém a pasta Tests com o script ResourceDesignerTests.ps1</span><span class="sxs-lookup"><span data-stu-id="e0e86-231">Best practice: Resource module contains Tests folder with ResourceDesignerTests.ps1 script</span></span> ##
<span data-ttu-id="e0e86-232">É uma prática recomendada criar a pasta “Tests” dentro do módulo de recurso, criar o arquivo ResourceDesignerTests.ps1 e adicionar testes usando **Test-xDscResource** e **Test-xDscSchema** para todos os recursos em determinado módulo.</span><span class="sxs-lookup"><span data-stu-id="e0e86-232">It’s a good practice to create folder “Tests” inside resource module, create ResourceDesignerTests.ps1 file and add tests using **Test-xDscResource** and **Test-xDscSchema** for all resources in given module.</span></span>
<span data-ttu-id="e0e86-233">Dessa forma, você pode validar rapidamente os esquemas de todos os recursos de determinado módulo e fazer a verificação de integridade antes da publicação.</span><span class="sxs-lookup"><span data-stu-id="e0e86-233">This way you can quickly validate schemas of all resources from the given modules and do a sanity check before publishing.</span></span>
<span data-ttu-id="e0e86-234">Para xRemoteFile, ResourceTests.ps1 poderá ser bem simples, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="e0e86-234">For xRemoteFile, ResourceTests.ps1 could look as simple as:</span></span>
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```
##<a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a><span data-ttu-id="e0e86-235">Prática recomendada: a pasta do recurso contém um script de designer de recurso para geração de esquema##</span><span class="sxs-lookup"><span data-stu-id="e0e86-235">Best practice: Resource folder contains resource designer script for generating schema##</span></span>
<span data-ttu-id="e0e86-236">Cada recurso deve conter um script do designer de recursos que gera um esquema mof do recurso.</span><span class="sxs-lookup"><span data-stu-id="e0e86-236">Each resource should contain a resource designer script which generates a mof schema of the resource.</span></span> <span data-ttu-id="e0e86-237">Esse arquivo deve ser colocado em <ResourceName>\ResourceDesignerScripts e ser nomeado Generate<ResourceName>Schema.ps1 Para o recurso xRemoteFile, esse arquivo será chamado GenerateXRemoteFileSchema.ps1 e conterá:</span><span class="sxs-lookup"><span data-stu-id="e0e86-237">This file should be placed in <ResourceName>\ResourceDesignerScripts and be named Generate<ResourceName>Schema.ps1 For xRemoteFile resource this file would be called GenerateXRemoteFileSchema.ps1 and contain:</span></span>
```powershell
$DestinationPath = New-xDscResourceProperty -Name DestinationPath -Type String -Attribute Key -Description 'Path under which downloaded or copied file should be accessible after operation.'
$Uri = New-xDscResourceProperty -Name Uri -Type String -Attribute Required -Description 'Uri of a file which should be copied or downloaded. This parameter supports HTTP and HTTPS values.'
$Headers = New-xDscResourceProperty -Name Headers -Type Hashtable[] -Attribute Write -Description 'Headers of the web request.'
$UserAgent = New-xDscResourceProperty -Name UserAgent -Type String -Attribute Write -Description 'User agent for the web request.'
$Ensure = New-xDscResourceProperty -Name Ensure -Type String -Attribute Read -ValidateSet "Present", "Absent" -Description 'Says whether DestinationPath exists on the machine'
$Credential = New-xDscResourceProperty -Name Credential -Type PSCredential -Attribute Write -Description 'Specifies a user account that has permission to send the request.'
$CertificateThumbprint = New-xDscResourceProperty -Name CertificateThumbprint -Type String -Attribute Write -Description 'Digital public key certificate that is used to send the request.'

New-xDscResource -Name MSFT_xRemoteFile -Property @($DestinationPath, $Uri, $Headers, $UserAgent, $Ensure, $Credential, $CertificateThumbprint) -ModuleName xPSDesiredStateConfiguration2 -FriendlyName xRemoteFile
```
## <a name="best-practice-resource-supports--whatif"></a><span data-ttu-id="e0e86-238">Melhor prática: o recurso dá suporte a -whatif</span><span class="sxs-lookup"><span data-stu-id="e0e86-238">Best practice: Resource supports -whatif</span></span> ##
<span data-ttu-id="e0e86-239">Caso o recurso esteja executando operações “perigosas”, é uma prática recomendada implementar a funcionalidade –whatif.</span><span class="sxs-lookup"><span data-stu-id="e0e86-239">If your resource is performing “dangerous” operations, it’s a good practice to implement -whatif functionality.</span></span> <span data-ttu-id="e0e86-240">Após a conclusão, certifique-se de que a saída –whatif descreve corretamente as operações que ocorreriam se o comando fosse executado sem a opção –whatif.</span><span class="sxs-lookup"><span data-stu-id="e0e86-240">After it’s done, make sure that whatif output correctly describes operations which would happen if command was executed without whatif switch.</span></span>
<span data-ttu-id="e0e86-241">Além disso, verifique se as operações não são executadas (não é feita nenhuma alteração ao estado do nó) quando a opção –whatif está presente.</span><span class="sxs-lookup"><span data-stu-id="e0e86-241">Also, verify that operations does not execute (no changes to the node’s state are made) when –whatif switch is present.</span></span>
<span data-ttu-id="e0e86-242">Por exemplo, vamos supor que estamos testando o recurso File.</span><span class="sxs-lookup"><span data-stu-id="e0e86-242">For example, let’s assume we are testing File resource.</span></span> <span data-ttu-id="e0e86-243">Veja abaixo uma configuração simples que cria o arquivo “test.txt” com o conteúdo “test”:</span><span class="sxs-lookup"><span data-stu-id="e0e86-243">Below is simple configuration which creates file “test.txt” with contents “test”:</span></span>
```powershell
configuration config
{
    node localhost
    {
        File file
        {
            Contents="test"
            DestinationPath="C:\test\test.txt"
        }
    }
}
config
```
<span data-ttu-id="e0e86-244">Se compilarmos e, em seguida, executarmos a configuração com a opção –whatif, a saída nos informará exatamente o que aconteceria quando a configuração fosse executada.</span><span class="sxs-lookup"><span data-stu-id="e0e86-244">If we compile and then execute the configuration with the –whatif switch, the output is telling us exactly what would happen when we run the configuration.</span></span> <span data-ttu-id="e0e86-245">Todavia, a configuração propriamente dita não foi executada (o arquivo test.txt não foi criado).</span><span class="sxs-lookup"><span data-stu-id="e0e86-245">The configuration itself however was not executed (test.txt file was not created).</span></span>
```powershell
Start-DscConfiguration -path .\config -ComputerName localhost -wait -verbose -whatif
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer CHARLESX1 with user sid
S-1-5-21-397955417-626881126-188441444-5179871.
What if: [X]: LCM:  [ Start  Set      ]
What if: [X]: LCM:  [ Start  Resource ]  [[File]file]
What if: [X]: LCM:  [ Start  Test     ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]: LCM:  [ End    Test     ]  [[File]file]  in 0.0270 seconds.
What if: [X]: LCM:  [ Start  Set      ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]:                            [C:\test\test.txt] Creating and writing contents and setting attributes.
What if: [X]: LCM:  [ End    Set      ]  [[File]file]  in 0.0180 seconds.
What if: [X]: LCM:  [ End    Resource ]  [[File]file]
What if: [X]: LCM:  [ End    Set      ]
VERBOSE: [X]: LCM:  [ End    Set      ]    in  0.1050 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

<span data-ttu-id="e0e86-246">Esta lista não é completa, mas abrange muitos problemas importantes que podem ser encontrados durante a criação, o desenvolvimento e o teste dos recursos da DSC.</span><span class="sxs-lookup"><span data-stu-id="e0e86-246">This list is not exhaustive, but it covers many important issues which can be encountered while designing, developing and testing DSC resources.</span></span>