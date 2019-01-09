---
ms.date: 12/12/2018
keywords: DSC,powershell,configuração,instalação
title: Publicar em um servidor de Pull usando IDs de configuração (v4/v5)
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400166"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="a3786-103">Publicar em um servidor de Pull usando IDs de configuração (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="a3786-103">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="a3786-104">As seções a seguir pressupõem que você já configurou um servidor de recepção.</span><span class="sxs-lookup"><span data-stu-id="a3786-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="a3786-105">Se você não tiver configurado seu servidor de Pull, você pode usar os guias a seguir:</span><span class="sxs-lookup"><span data-stu-id="a3786-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="a3786-106">Configurar um servidor de pull SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="a3786-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="a3786-107">Configurar um servidor de pull HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="a3786-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="a3786-108">Cada nó de destino pode ser configurado para baixar as configurações, recursos e até mesmo relatar seu status.</span><span class="sxs-lookup"><span data-stu-id="a3786-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="a3786-109">Este artigo mostra como carregar recursos para que fiquem disponíveis para serem baixadas e configurar clientes para baixar os recursos automaticamente.</span><span class="sxs-lookup"><span data-stu-id="a3786-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="a3786-110">Quando o nó recebe uma configuração atribuída, por meio **Pull** ou **Push** (v5), ele baixa automaticamente todos os recursos necessários para a configuração do local especificado no LCM.</span><span class="sxs-lookup"><span data-stu-id="a3786-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="a3786-111">Compilar as configurações</span><span class="sxs-lookup"><span data-stu-id="a3786-111">Compile Configurations</span></span>

<span data-ttu-id="a3786-112">A primeira etapa para armazenar [configurações](../configurations/configurations.md) em um servidor de recepção, deverá compilá-los em arquivos ". MOF".</span><span class="sxs-lookup"><span data-stu-id="a3786-112">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into ".mof" files.</span></span> <span data-ttu-id="a3786-113">Para tornar uma configuração genérica e aplicáveis a mais clientes, use `localhost` em seu bloco de nó.</span><span class="sxs-lookup"><span data-stu-id="a3786-113">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="a3786-114">O exemplo a seguir mostra um shell de configuração que usa `localhost` em vez de um nome de cliente específico.</span><span class="sxs-lookup"><span data-stu-id="a3786-114">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="a3786-115">Depois de você ter compilado seu configuração genérica, você deve ter um arquivo de "localhost.mof".</span><span class="sxs-lookup"><span data-stu-id="a3786-115">Once you have compiled your generic configuration, you should have a "localhost.mof" file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="a3786-116">Renomeando o arquivo MOF</span><span class="sxs-lookup"><span data-stu-id="a3786-116">Renaming the MOF file</span></span>

<span data-ttu-id="a3786-117">Você pode armazenar arquivos de configuração de ". MOF" em um servidor de Pull por **ConfigurationName** ou **ConfigurationID**.</span><span class="sxs-lookup"><span data-stu-id="a3786-117">You can store Configuration ".mof" files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span></span> <span data-ttu-id="a3786-118">Dependendo de como você planeja configurar os clientes de pull, você pode escolher uma seção abaixo para renomear corretamente seus arquivos compilados ". MOF".</span><span class="sxs-lookup"><span data-stu-id="a3786-118">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled ".mof" files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="a3786-119">IDs de configuração (GUID)</span><span class="sxs-lookup"><span data-stu-id="a3786-119">Configuration IDs (GUID)</span></span>

<span data-ttu-id="a3786-120">Será necessário renomear o arquivo "localhost.mof" para "<GUID>. MOF" arquivo.</span><span class="sxs-lookup"><span data-stu-id="a3786-120">You will need to rename your "localhost.mof" file to "<GUID>.mof" file.</span></span> <span data-ttu-id="a3786-121">Você pode criar um aleatório **Guid** usando o exemplo abaixo, ou usando o [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a3786-121">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="a3786-122">Saída de exemplo</span><span class="sxs-lookup"><span data-stu-id="a3786-122">Sample Output</span></span>

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="a3786-123">Em seguida, você pode renomear o arquivo ". MOF" usando qualquer método aceitável.</span><span class="sxs-lookup"><span data-stu-id="a3786-123">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="a3786-124">O exemplo a seguir, usa o [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a3786-124">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="a3786-125">Para obter mais informações sobre como usar **Guids** em seu ambiente, consulte [planejar Guids](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="a3786-125">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="a3786-126">Nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="a3786-126">Configuration Names</span></span>

<span data-ttu-id="a3786-127">Será necessário renomear o arquivo "localhost.mof" para "<Configuration Name>. MOF" arquivo.</span><span class="sxs-lookup"><span data-stu-id="a3786-127">You will need to rename your "localhost.mof" file to "<Configuration Name>.mof" file.</span></span> <span data-ttu-id="a3786-128">No exemplo a seguir, o nome da configuração da seção anterior é usado.</span><span class="sxs-lookup"><span data-stu-id="a3786-128">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="a3786-129">Em seguida, você pode renomear o arquivo ". MOF" usando qualquer método aceitável.</span><span class="sxs-lookup"><span data-stu-id="a3786-129">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="a3786-130">O exemplo a seguir, usa o [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a3786-130">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="a3786-131">Criar a soma de verificação</span><span class="sxs-lookup"><span data-stu-id="a3786-131">Create the CheckSum</span></span>

<span data-ttu-id="a3786-132">Cada arquivo de ". MOF" armazenado em um servidor de Pull ou compartilhamento SMB precisa ter um arquivo associado ".checksum".</span><span class="sxs-lookup"><span data-stu-id="a3786-132">Each ".mof" file stored on a Pull Server, or SMB share needs to have an associated ".checksum" file.</span></span> <span data-ttu-id="a3786-133">Esse arquivo permite que os clientes saber quando o arquivo associado ". MOF" foi alterado e deve ser baixado novamente.</span><span class="sxs-lookup"><span data-stu-id="a3786-133">This file lets clients know when the associated ".mof" file has changed and should be downloaded again.</span></span>

<span data-ttu-id="a3786-134">Você pode criar uma **soma de verificação** com o [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a3786-134">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="a3786-135">Você também pode executar `New-DSCCheckSum` em relação a um diretório de arquivos usando o `-Path` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a3786-135">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="a3786-136">Se já existir uma soma de verificação, você pode forçá-lo a ser criada novamente com o `-Force` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a3786-136">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="a3786-137">O exemplo a seguir especificou um diretório que contém o arquivo ". MOF" da seção anterior e usa o `-Force` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a3786-137">The following example specified a directory containing the ".mof" file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="a3786-138">Nenhuma saída será mostrada, mas agora você deve ver um "<GUID or Configuration Name>. mof.checksum" arquivo.</span><span class="sxs-lookup"><span data-stu-id="a3786-138">No output will be shown, but you should now see a "<GUID or Configuration Name>.mof.checksum" file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="a3786-139">Onde armazenar os arquivos MOF e somas de verificação</span><span class="sxs-lookup"><span data-stu-id="a3786-139">Where to store MOF files and CheckSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="a3786-140">Em um servidor de Pull de HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="a3786-140">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="a3786-141">Ao configurar seu servidor de Pull de HTTP, conforme explicado em [configurar um servidor de recepção do DSC HTTP](pullServer.md), você especificar diretórios para o **ModulePath** e **ConfigurationPath** chaves.</span><span class="sxs-lookup"><span data-stu-id="a3786-141">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="a3786-142">O **ConfigurationPath** chave indica onde todos os arquivos ". MOF" devem ser armazenados.</span><span class="sxs-lookup"><span data-stu-id="a3786-142">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="a3786-143">O **ConfigurationPath** indica em que todos os arquivos ". MOF" e ".checksum" arquivos devem ser armazenados.</span><span class="sxs-lookup"><span data-stu-id="a3786-143">The **ConfigurationPath** indicates where any ".mof" files and ".checksum" files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="a3786-144">Em um compartilhamento SMB</span><span class="sxs-lookup"><span data-stu-id="a3786-144">On an SMB Share</span></span>

<span data-ttu-id="a3786-145">Quando você configurar um cliente de Pull para usar um compartilhamento SMB, você especifica um **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="a3786-145">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="a3786-146">Todos os arquivos ". MOF" e ".checksum" devem ser armazenados em, em seguida, o **SourcePath** diretório da **ConfigurationRepositoryShare** bloco.</span><span class="sxs-lookup"><span data-stu-id="a3786-146">All ".mof" files and ".checksum" files should then be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="a3786-147">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="a3786-147">Next Steps</span></span>

<span data-ttu-id="a3786-148">Em seguida, você desejará configurar clientes de Pull para extrair a configuração especificada.</span><span class="sxs-lookup"><span data-stu-id="a3786-148">Next, you will want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="a3786-149">Para obter mais informações, consulte um dos seguintes guias:</span><span class="sxs-lookup"><span data-stu-id="a3786-149">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="a3786-150">Configurar um cliente de Pull usando IDs de configuração (v4)</span><span class="sxs-lookup"><span data-stu-id="a3786-150">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="a3786-151">Configurar um cliente de Pull usando IDs de configuração (v5)</span><span class="sxs-lookup"><span data-stu-id="a3786-151">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="a3786-152">Configurar um cliente de Pull usando nomes de configuração (v5)</span><span class="sxs-lookup"><span data-stu-id="a3786-152">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="a3786-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3786-153">See also</span></span>

- [<span data-ttu-id="a3786-154">Configurar um servidor de pull SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="a3786-154">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="a3786-155">Configurar um servidor de pull HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="a3786-155">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="a3786-156">Pacote e os recursos de Upload para um servidor de Pull</span><span class="sxs-lookup"><span data-stu-id="a3786-156">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)
