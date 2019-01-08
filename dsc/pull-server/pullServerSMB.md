---
ms.date: 04/11/2018
keywords: DSC,powershell,configuração,instalação
title: Configurando um servidor de pull de SMB para DSC
ms.openlocfilehash: 722120369df9ff383a02c69111e0bacf2e2e76a5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400131"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a><span data-ttu-id="33456-103">Configurando um servidor de pull de SMB para DSC</span><span class="sxs-lookup"><span data-stu-id="33456-103">Setting up a DSC SMB pull server</span></span>

<span data-ttu-id="33456-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="33456-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="33456-105">O Servidor de Recepção (Recurso do Windows *Serviço DSC*) é um componente compatível com o Windows Server, no entanto, não há planos de oferecer novos recursos ou funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="33456-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="33456-106">É recomendável começar a fazer a transição dos clientes gerenciados para o [DSC de Automação do Azure](/azure/automation/automation-dsc-getting-started) (inclui recursos além do Servidor de Recepção no Windows Server) ou para uma das soluções da comunidade listadas [aqui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="33456-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="33456-107">Um servidor de pull do [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) é um computador que hospeda compartilhamentos de arquivo SMB que disponibilizam arquivos de configuração DSC e/ou recursos de DSC para nós de destino quando esses nós os solicitam.</span><span class="sxs-lookup"><span data-stu-id="33456-107">A DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) pull server is a computer hosting SMB file shares that make DSC configuration files and DSC resources available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="33456-108">Para usar um servidor de pull de SMB para DSC, você precisa:</span><span class="sxs-lookup"><span data-stu-id="33456-108">To use an SMB pull server for DSC, you have to:</span></span>

- <span data-ttu-id="33456-109">Configurar um compartilhamento de arquivos SMB em um servidor executando o PowerShell 4.0 ou superior</span><span class="sxs-lookup"><span data-stu-id="33456-109">Set up an SMB file share on a server running PowerShell 4.0 or higher</span></span>
- <span data-ttu-id="33456-110">Configurar um cliente executando o PowerShell 4.0 ou superior para efetuar pull desse compartilhamento SMB</span><span class="sxs-lookup"><span data-stu-id="33456-110">Configure a client running PowerShell 4.0 or higher to pull from that SMB share</span></span>

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a><span data-ttu-id="33456-111">Usando o recurso xSmbShare para criar um compartilhamento de arquivos SMB</span><span class="sxs-lookup"><span data-stu-id="33456-111">Using the xSmbShare resource to create an SMB file share</span></span>

<span data-ttu-id="33456-112">Há várias maneiras para configurar um compartilhamento de arquivos SMB, mas vamos ver como você pode fazer isso usando DSC.</span><span class="sxs-lookup"><span data-stu-id="33456-112">There are a number of ways to set up an SMB file share, but let's look at how you can do this by using DSC.</span></span>

### <a name="install-the-xsmbshare-resource"></a><span data-ttu-id="33456-113">Instalar o recurso xSmbShare</span><span class="sxs-lookup"><span data-stu-id="33456-113">Install the xSmbShare resource</span></span>

<span data-ttu-id="33456-114">Chame o cmdlet [Install-Module](/powershell/module/PowershellGet/Install-Module) para instalar o módulo **xSmbShare**.</span><span class="sxs-lookup"><span data-stu-id="33456-114">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xSmbShare** module.</span></span>

> [!NOTE]
> <span data-ttu-id="33456-115">`Install-Module` está incluído no módulo **PowerShellGet**, que está incluído no PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="33456-115">`Install-Module` is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="33456-116">É possível baixar o módulo **PowerShellGet** para o PowerShell 3.0 e 4.0 em [Visualização de Módulos do PowerShell do PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="33456-116">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
> <span data-ttu-id="33456-117">O **xSmbShare** contém o recurso de DSC **xSmbShare**, que pode ser usado para criar um compartilhamento de arquivo SMB.</span><span class="sxs-lookup"><span data-stu-id="33456-117">The **xSmbShare** contains the DSC resource **xSmbShare**, which can be used to create an SMB file share.</span></span>

### <a name="create-the-directory-and-file-share"></a><span data-ttu-id="33456-118">Criar o diretório e o compartilhamento de arquivos</span><span class="sxs-lookup"><span data-stu-id="33456-118">Create the directory and file share</span></span>

<span data-ttu-id="33456-119">A configuração a seguir usa o recurso **File** para criar o diretório para o compartilhamento e o recurso **xSmbShare** para configurar o compartilhamento SMB:</span><span class="sxs-lookup"><span data-stu-id="33456-119">The following configuration uses the **File** resource to create the directory for the share and the **xSmbShare** resource to set up the SMB share:</span></span>

```powershell
Configuration SmbShare
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'admininstrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

<span data-ttu-id="33456-120">A configuração cria o diretório `C:\DscSmbShare`, se ainda não existir e, em seguida, usa esse diretório como um compartilhamento de arquivos SMB.</span><span class="sxs-lookup"><span data-stu-id="33456-120">The configuration creates the directory `C:\DscSmbShare`, if it doesn't already exist, and then uses that directory as an SMB file share.</span></span> <span data-ttu-id="33456-121">**FullAccess** deve ser fornecido a qualquer conta que precise gravar ou excluir do compartilhamento de arquivos.</span><span class="sxs-lookup"><span data-stu-id="33456-121">**FullAccess** should be given to any account that needs to write to or delete from the file share.</span></span> <span data-ttu-id="33456-122">**ReadAccess** deve ser fornecido a quaisquer nós de cliente que obtêm as configurações e/ou recursos de DSC do compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="33456-122">**ReadAccess** must be given to any client nodes that get configurations and/or DSC resources from the share.</span></span>

> [!NOTE]
> <span data-ttu-id="33456-123">DSC é executado como a conta do sistema por padrão, o próprio computador deve ter acesso ao compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="33456-123">DSC runs as the system account by default, so the computer itself must have access to the share.</span></span>

### <a name="give-file-system-access-to-the-pull-client"></a><span data-ttu-id="33456-124">Conceder acesso ao sistema de arquivos para o cliente de pull</span><span class="sxs-lookup"><span data-stu-id="33456-124">Give file system access to the pull client</span></span>

<span data-ttu-id="33456-125">Conceder **ReadAccess** para um nó do cliente permite que esse nó acesse o compartilhamento SMB, mas não arquivos ou pastas dentro desse compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="33456-125">Giving **ReadAccess** to a client node allows that node to access the SMB share, but not to files or folders within that share.</span></span> <span data-ttu-id="33456-126">Você precisa conceder explicitamente acesso de nós para a pasta de compartilhamento SMB e as subpastas de cliente.</span><span class="sxs-lookup"><span data-stu-id="33456-126">You have to explicitly grant client nodes access to the SMB share folder and subfolders.</span></span> <span data-ttu-id="33456-127">Podemos fazer isso com o DSC adicionando/usando o recurso **cNtfsPermissionEntry**, que está contido no módulo [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0).</span><span class="sxs-lookup"><span data-stu-id="33456-127">We can do this with DSC by adding using the **cNtfsPermissionEntry** resource, which is contained in the [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module.</span></span> <span data-ttu-id="33456-128">A configuração a seguir adiciona um bloco **cNtfsPermissionEntry**, que concede acesso ReadAndExecute ao cliente de pull:</span><span class="sxs-lookup"><span data-stu-id="33456-128">The following configuration adds a **cNtfsPermissionEntry** block that grants ReadAndExecute access to the pull client:</span></span>

```powershell
Configuration DSCSMB
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare
    Import-DscResource -ModuleName cNtfsAccessControl

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }

        cNtfsPermissionEntry PermissionSet1
        {
            Ensure = 'Present'
            Path = 'C:\DscSmbShare'
            Principal = 'myDomain\Contoso-Server$'
            AccessControlInformation = @(
                cNtfsAccessControlInformation
                {
                    AccessControlType = 'Allow'
                    FileSystemRights = 'ReadAndExecute'
                    Inheritance = 'ThisFolderSubfoldersAndFiles'
                    NoPropagateInherit = $false
                }
            )
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="33456-129">Colocando configurações e recursos</span><span class="sxs-lookup"><span data-stu-id="33456-129">Placing configurations and resources</span></span>

<span data-ttu-id="33456-130">Salve todos os arquivos MOF de configuração e/ou recursos DSC que você deseja que sejam obtidos por pull do compartilhamento de pasta SMB pelos nós do cliente.</span><span class="sxs-lookup"><span data-stu-id="33456-130">Save any configuration MOF files and/or DSC resources that you want client nodes to pull in the SMB share folder.</span></span>

<span data-ttu-id="33456-131">O arquivo MOF de configuração no servidor de pull deve ser nomeado como *ConfigurationID*.mof, em que *ConfigurationID* é o valor da propriedade **ConfigurationID** do LCM do nó de destino.</span><span class="sxs-lookup"><span data-stu-id="33456-131">Any configuration MOF file must be named *ConfigurationID*.mof, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="33456-132">Para obter mais informações sobre como configurar clientes de pull, confira [Configurando um cliente de pull usando uma ID de configuração](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="33456-132">For more information about setting up pull clients, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="33456-133">Você deverá usar IDs de configuração se estiver usando um servidor de pull de SMB.</span><span class="sxs-lookup"><span data-stu-id="33456-133">You must use configuration IDs if you are using an SMB pull server.</span></span> <span data-ttu-id="33456-134">Não há suporte para nomes de configuração para SMB.</span><span class="sxs-lookup"><span data-stu-id="33456-134">Configuration names are not supported for SMB.</span></span>

<span data-ttu-id="33456-135">Cada módulo de recurso precisa ser compactado e nomeado de acordo com o seguinte padrão `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="33456-135">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="33456-136">Por exemplo, um módulo chamado xWebAdminstration com uma versão do módulo correspondente a 3.1.2.0 seria nomeado 'xWebAdministration_3.2.1.0.zip'.</span><span class="sxs-lookup"><span data-stu-id="33456-136">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="33456-137">Cada versão de um módulo deve estar contido em um único arquivo zip.</span><span class="sxs-lookup"><span data-stu-id="33456-137">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="33456-138">Não há suporte para versões separadas de um módulo em um arquivo zip.</span><span class="sxs-lookup"><span data-stu-id="33456-138">Separate versions of a module in a zip file are not supported.</span></span> <span data-ttu-id="33456-139">Antes de empacotar módulos de recursos de DSC para uso com o servidor de pull, você precisa fazer uma pequena alteração na estrutura de diretório.</span><span class="sxs-lookup"><span data-stu-id="33456-139">Before packaging up DSC resource modules for use with pull server, you need to make a small change to the directory structure.</span></span>

<span data-ttu-id="33456-140">O formato padrão de módulos contendo recursos DSC no WMF 5.0 é `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="33456-140">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span>

<span data-ttu-id="33456-141">Antes de empacotar o servidor de pull, simplesmente remova a pasta `{Module version}` para que o caminho se torne `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="33456-141">Before packaging up for the pull server simply remove the `{Module version}` folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="33456-142">Com essa alteração, compacte a pasta conforme descrito acima e coloque esses arquivos zip na pasta de compartilhamento SMB.</span><span class="sxs-lookup"><span data-stu-id="33456-142">With this change, zip the folder as described above and place these zip files in the SMB share folder.</span></span>

## <a name="creating-the-mof-checksum"></a><span data-ttu-id="33456-143">Criando a soma de verificação de MOF</span><span class="sxs-lookup"><span data-stu-id="33456-143">Creating the MOF checksum</span></span>

<span data-ttu-id="33456-144">Um arquivo MOF de configuração precisa ser emparelhado com um arquivo de soma de verificação para que um LCM em um nó de destino possa validar a configuração.</span><span class="sxs-lookup"><span data-stu-id="33456-144">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="33456-145">Para criar uma soma de verificação, chame o cmdlet [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum).</span><span class="sxs-lookup"><span data-stu-id="33456-145">To create a checksum, call the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet.</span></span> <span data-ttu-id="33456-146">O cmdlet usa um parâmetro `Path` que especifica a pasta na qual se encontra o MOF de configuração.</span><span class="sxs-lookup"><span data-stu-id="33456-146">The cmdlet takes a `Path` parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="33456-147">O cmdlet cria um arquivo de soma de verificação chamado `ConfigurationMOFName.mof.checksum`, em que `ConfigurationMOFName` é o nome do arquivo MOF de configuração.</span><span class="sxs-lookup"><span data-stu-id="33456-147">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="33456-148">Se houver mais de um arquivo MOF de configuração na pasta especificada, será criada uma soma de verificação para cada configuração na pasta.</span><span class="sxs-lookup"><span data-stu-id="33456-148">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>

<span data-ttu-id="33456-149">O arquivo de soma de verificação deve estar presente no mesmo diretório em que o arquivo MOF de configuração (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` por padrão) e ter o mesmo nome com a extensão `.checksum` anexada.</span><span class="sxs-lookup"><span data-stu-id="33456-149">The checksum file must be present in the same directory as the configuration MOF file (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` by default), and have the same name with the `.checksum` extension appended.</span></span>

> [!NOTE]
> <span data-ttu-id="33456-150">Se alterar o arquivo MOF de configuração de qualquer forma, você também deverá recriar o arquivo de soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="33456-150">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="setting-up-a-pull-client-for-smb"></a><span data-ttu-id="33456-151">Configurando um cliente de pull para SMB</span><span class="sxs-lookup"><span data-stu-id="33456-151">Setting up a pull client for SMB</span></span>

<span data-ttu-id="33456-152">Para configurar um cliente que recebe as configurações e/ou recursos de um compartilhamento SMB, você configura o LCM (Gerenciador de Configurações Local) do cliente com blocos **ConfigurationRepositoryShare** e **ResourceRepositoryShare** que especificam o compartilhamento do qual efetuar o configurações de pull e recursos DSC.</span><span class="sxs-lookup"><span data-stu-id="33456-152">To set up a client that pulls configurations and/or resources from an SMB share, you configure the client's Local Configuration Manager (LCM) with **ConfigurationRepositoryShare** and **ResourceRepositoryShare** blocks that specify the share from which to pull configurations and DSC resources.</span></span>

<span data-ttu-id="33456-153">Para obter mais informações sobre como configurar um LCM, consulte [Configurando um cliente de pull usando a ID de configuração](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="33456-153">For more information about configuring the LCM, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="33456-154">Para simplificar, este exemplo usa o **PSDscAllowPlainTextPassword** para permitir a passagem de uma senha de texto não criptografado para o parâmetro **Credencial**.</span><span class="sxs-lookup"><span data-stu-id="33456-154">For simplicity, this example uses the **PSDscAllowPlainTextPassword** to allow passing a plaintext password to the **Credential** parameter.</span></span> <span data-ttu-id="33456-155">Para obter informações sobre como passar credenciais de forma mais segura, consulte [Opções de Credenciais nos Dados de Configuração](../configurations/configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="33456-155">For information about passing credentials more securely, see [Credentials Options in Configuration Data](../configurations/configDataCredentials.md).</span></span>
>
> <span data-ttu-id="33456-156">Você **DEVE** especificar uma **ConfigurationID** no bloco **Configurações** de uma metaconfiguração de um servidor de pull de SMB, mesmo que só esteja extraindo recursos.</span><span class="sxs-lookup"><span data-stu-id="33456-156">You **MUST** specify a **ConfigurationID** in the **Settings** block of a metaconfiguration for an SMB pull server, even if you are only pulling resources.</span></span>

```powershell
$secpasswd = ConvertTo-SecureString “Pass1Word” -AsPlainText -Force
$mycreds = New-Object System.Management.Automation.PSCredential (“TestUser”, $secpasswd)

[DSCLocalConfigurationManager()]
configuration SmbCredTest
{
    Node $AllNodes.NodeName
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
            ConfigurationID    = '16db7357-9083-4806-a80c-ebbaf4acd6c1'
        }

         ConfigurationRepositoryShare SmbConfigShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds
        }

        ResourceRepositoryShare SmbResourceShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds

        }
    }
}

$ConfigurationData = @{
    AllNodes = @(
        @{
            #the "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
            NodeName="localhost"
            PSDscAllowPlainTextPassword = $true
        })
}
```

## <a name="acknowledgements"></a><span data-ttu-id="33456-157">Agradecimentos</span><span class="sxs-lookup"><span data-stu-id="33456-157">Acknowledgements</span></span>

<span data-ttu-id="33456-158">Agradecimentos especiais a seguintes pessoas:</span><span class="sxs-lookup"><span data-stu-id="33456-158">Special thanks to the following individuals:</span></span>

- <span data-ttu-id="33456-159">Mike F. Robbins, cujas postagens sobre o uso de SMB para DSC ajudaram a informar o conteúdo deste tópico.</span><span class="sxs-lookup"><span data-stu-id="33456-159">Mike F. Robbins, whose posts on using SMB for DSC helped inform the content in this topic.</span></span> <span data-ttu-id="33456-160">Seu blog está em [Mike F Robbins](http://mikefrobbins.com/).</span><span class="sxs-lookup"><span data-stu-id="33456-160">His blog is at [Mike F Robbins](http://mikefrobbins.com/).</span></span>
- <span data-ttu-id="33456-161">Serge Nikalaichyk, que criou o módulo **cNtfsAccessControl**.</span><span class="sxs-lookup"><span data-stu-id="33456-161">Serge Nikalaichyk, who authored the **cNtfsAccessControl** module.</span></span> <span data-ttu-id="33456-162">A fonte para esse módulo está em [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span><span class="sxs-lookup"><span data-stu-id="33456-162">The source for this module is at [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span></span>

## <a name="see-also"></a><span data-ttu-id="33456-163">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33456-163">See also</span></span>

[<span data-ttu-id="33456-164">Visão Geral da Configuração de Estado Desejado do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="33456-164">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)

[<span data-ttu-id="33456-165">Aplicando configurações</span><span class="sxs-lookup"><span data-stu-id="33456-165">Enacting configurations</span></span>](enactingConfigurations.md)

[<span data-ttu-id="33456-166">Configurando um cliente de pull usando uma ID de configuração</span><span class="sxs-lookup"><span data-stu-id="33456-166">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)
