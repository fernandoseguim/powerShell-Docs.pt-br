---
ms.date: 12/12/2018
keywords: DSC,powershell,configuração,instalação
title: Pacote e os recursos de Upload para um servidor de Pull
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400141"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a><span data-ttu-id="2cbfb-103">Pacote e os recursos de Upload para um servidor de Pull</span><span class="sxs-lookup"><span data-stu-id="2cbfb-103">Package and Upload Resources to a Pull Server</span></span>

<span data-ttu-id="2cbfb-104">As seções a seguir pressupõem que você já configurou um servidor de recepção.</span><span class="sxs-lookup"><span data-stu-id="2cbfb-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="2cbfb-105">Se você não tiver configurado seu servidor de Pull, você pode usar os guias a seguir:</span><span class="sxs-lookup"><span data-stu-id="2cbfb-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="2cbfb-106">Configurar um servidor de pull SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="2cbfb-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="2cbfb-107">Configurar um servidor de pull HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="2cbfb-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="2cbfb-108">Cada nó de destino pode ser configurado para baixar as configurações, recursos e até mesmo relatar seu status.</span><span class="sxs-lookup"><span data-stu-id="2cbfb-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="2cbfb-109">Este artigo mostra como carregar recursos para que fiquem disponíveis para serem baixadas e configurar clientes para baixar os recursos automaticamente.</span><span class="sxs-lookup"><span data-stu-id="2cbfb-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="2cbfb-110">Quando o nó recebe uma configuração atribuída, por meio **Pull** ou **Push** (v5), ele baixa automaticamente todos os recursos necessários para a configuração do local especificado no LCM.</span><span class="sxs-lookup"><span data-stu-id="2cbfb-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="package-resource-modules"></a><span data-ttu-id="2cbfb-111">Módulos de recursos do pacote</span><span class="sxs-lookup"><span data-stu-id="2cbfb-111">Package Resource Modules</span></span>

<span data-ttu-id="2cbfb-112">Cada recurso disponível para baixar um cliente deve ser armazenado em um arquivo. zip".</span><span class="sxs-lookup"><span data-stu-id="2cbfb-112">Each resource available for a client to download must be stored in a ".zip" file.</span></span> <span data-ttu-id="2cbfb-113">O exemplo a seguir mostra as etapas necessárias usando o [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) recursos.</span><span class="sxs-lookup"><span data-stu-id="2cbfb-113">The example below will show the required steps using the [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resource.</span></span>

> [!NOTE]
> <span data-ttu-id="2cbfb-114">Se você tiver todos os clientes usando o PowerShell 4.0, você precisará flaten a estrutura de pasta de recursos e remova quaisquer pastas de versão.</span><span class="sxs-lookup"><span data-stu-id="2cbfb-114">If you have any clients using PowerShell 4.0, you will need to flaten the resource folder structure and remove any version folders.</span></span> <span data-ttu-id="2cbfb-115">Para obter mais informações, consulte [várias versões do recurso](../configurations/import-dscresource.md#multiple-resource-versions).</span><span class="sxs-lookup"><span data-stu-id="2cbfb-115">For more information, see [Multiple Resource Versions](../configurations/import-dscresource.md#multiple-resource-versions).</span></span>

<span data-ttu-id="2cbfb-116">Você pode compactar o diretório de recursos usando qualquer utilitário, um script ou um método que preferir.</span><span class="sxs-lookup"><span data-stu-id="2cbfb-116">You can compress the resource directory using any utility, script, or method that you prefer.</span></span> <span data-ttu-id="2cbfb-117">No Windows, você pode *com o botão direito* no diretório "xPSDesiredStateConfiguration" e selecione "Enviar", em seguida, "Pasta compactada".</span><span class="sxs-lookup"><span data-stu-id="2cbfb-117">In Windows, you can *right-click* on the "xPSDesiredStateConfiguration" directory, and select "Send To", then "Compressed Folder".</span></span>

![Clicar com o botão direito do mouse](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a><span data-ttu-id="2cbfb-119">Nomear o arquivo de recurso</span><span class="sxs-lookup"><span data-stu-id="2cbfb-119">Naming the Resource Archive</span></span>

<span data-ttu-id="2cbfb-120">O arquivo de recurso precisa ser nomeado com o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="2cbfb-120">The Resource archive needs to be named with the following format:</span></span>

```
{ModuleName}_{Version}.zip
```

<span data-ttu-id="2cbfb-121">No exemplo acima, "xPSDesiredStateConfiguration.zip" deve ser renomeado "xPSDesiredStateConfiguration_8.4.4.0.zip".</span><span class="sxs-lookup"><span data-stu-id="2cbfb-121">In the example above, "xPSDesiredStateConfiguration.zip" should be renamed "xPSDesiredStateConfiguration_8.4.4.0.zip".</span></span>

### <a name="create-checksums"></a><span data-ttu-id="2cbfb-122">Crie somas de verificação</span><span class="sxs-lookup"><span data-stu-id="2cbfb-122">Create CheckSums</span></span>

<span data-ttu-id="2cbfb-123">Quando o módulo de recurso foi compactado e renomeado, você precisará criar uma **soma de verificação**.</span><span class="sxs-lookup"><span data-stu-id="2cbfb-123">Once the Resource module has been compressed and renamed, you need to create a **CheckSum**.</span></span>  <span data-ttu-id="2cbfb-124">O **soma de verificação** é usado, por que o LCM no cliente, para determinar se o recurso foi alterado e precisa ser baixado novamente.</span><span class="sxs-lookup"><span data-stu-id="2cbfb-124">The **CheckSum** is used, by the LCM on the client, to determine if the resource has been changed, and needs to be downloaded again.</span></span> <span data-ttu-id="2cbfb-125">Você pode criar uma **soma de verificação** com o [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="2cbfb-125">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, as shown in the example below.</span></span>

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

<span data-ttu-id="2cbfb-126">Nenhuma saída será mostrada, mas agora você deve ver "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span><span class="sxs-lookup"><span data-stu-id="2cbfb-126">No output will be shown, but you should now see a "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span></span> <span data-ttu-id="2cbfb-127">Você também pode executar `New-DSCCheckSum` em relação a um diretório de arquivos usando o `-Path` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="2cbfb-127">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="2cbfb-128">Se já existir uma soma de verificação, você pode forçá-lo a ser criada novamente com o `-Force` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="2cbfb-128">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span>

### <a name="where-to-store-resource-archives"></a><span data-ttu-id="2cbfb-129">Onde armazenar os arquivos de recurso</span><span class="sxs-lookup"><span data-stu-id="2cbfb-129">Where to store Resource Archives</span></span>

#### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="2cbfb-130">Em um servidor de Pull de HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="2cbfb-130">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="2cbfb-131">Ao configurar seu servidor de Pull de HTTP, conforme explicado em [configurar um servidor de recepção do DSC HTTP](pullServer.md), você especificar diretórios para o **ModulePath** e **ConfigurationPath** chaves.</span><span class="sxs-lookup"><span data-stu-id="2cbfb-131">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="2cbfb-132">O **ConfigurationPath** chave indica onde todos os arquivos ". MOF" devem ser armazenados.</span><span class="sxs-lookup"><span data-stu-id="2cbfb-132">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="2cbfb-133">O **ModulePath** indica onde quaisquer módulos de recursos DSC deve ser armazenados.</span><span class="sxs-lookup"><span data-stu-id="2cbfb-133">The **ModulePath** indicates where any DSC Resource Modules should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a><span data-ttu-id="2cbfb-134">Em um compartilhamento SMB</span><span class="sxs-lookup"><span data-stu-id="2cbfb-134">On an SMB Share</span></span>

<span data-ttu-id="2cbfb-135">Se você tiver especificado uma **ResourceRepositoryShare**, quando a configuração do seu cliente de Pull, armazenar os arquivos e as somas de verificação na **SourcePath** diretório da **ResourceRepositoryShare** bloco.</span><span class="sxs-lookup"><span data-stu-id="2cbfb-135">If you specified a **ResourceRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ResourceRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Configurations'
}

ResourceRepositoryShare SMBResourceServer
{
    SourcePath = '\\SMBPullServer\Resources'
}
```

<span data-ttu-id="2cbfb-136">Se você tiver especificado apenas uma **ConfigurationRepositoryShare**, quando a configuração do seu cliente de Pull, armazenar os arquivos e as somas de verificação na **SourcePath** diretório da  **ConfigurationRepositoryShare** bloco.</span><span class="sxs-lookup"><span data-stu-id="2cbfb-136">If you specified only a **ConfigurationRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a><span data-ttu-id="2cbfb-137">Atualização de recursos</span><span class="sxs-lookup"><span data-stu-id="2cbfb-137">Updating resources</span></span>

<span data-ttu-id="2cbfb-138">Você pode forçar um nó para atualizar seus recursos, alterando o número de versão no nome de arquivo, ou criando uma nova soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="2cbfb-138">You can force a Node to update its resources by changing the version number in the archive's name, or by creating a new checksum.</span></span> <span data-ttu-id="2cbfb-139">O cliente de Pull verificará se há versões mais recentes dos recursos necessários, bem como atualizadas as somas de verificação quando o LCM é atualizada.</span><span class="sxs-lookup"><span data-stu-id="2cbfb-139">The Pull Client will check for newer versions of required resources, as well as updated checksums, when its LCM refreshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="2cbfb-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2cbfb-140">See also</span></span>

- [<span data-ttu-id="2cbfb-141">Configurar um servidor de pull SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="2cbfb-141">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="2cbfb-142">Configurar um servidor de pull HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="2cbfb-142">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
