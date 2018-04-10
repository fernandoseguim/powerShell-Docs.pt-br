---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC,powershell,configuração,instalação
title: Configurando um servidor de pull de SMB para DSC
ms.openlocfilehash: e9228c050d6f496e30e94404a564ed2e425a5412
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="setting-up-a-dsc-smb-pull-server"></a><span data-ttu-id="b45a0-103">Configurando um servidor de pull de SMB para DSC</span><span class="sxs-lookup"><span data-stu-id="b45a0-103">Setting up a DSC SMB pull server</span></span>

><span data-ttu-id="b45a0-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b45a0-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b45a0-105">Um servidor de pull do [SMB](https://technet.microsoft.com/library/hh831795.aspx) é um computador que hospeda compartilhamentos de arquivo SMB que disponibilizam arquivos de configuração DSC e/ou recursos de DSC para nós de destino quando esses nós os solicitam.</span><span class="sxs-lookup"><span data-stu-id="b45a0-105">A DSC [SMB](https://technet.microsoft.com/library/hh831795.aspx) pull server is a computer hosting SMB file shares that make DSC configuration files and DSC resources available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="b45a0-106">Para usar um servidor de pull de SMB para DSC, você precisa:</span><span class="sxs-lookup"><span data-stu-id="b45a0-106">To use an SMB pull server for DSC, you have to:</span></span>
- <span data-ttu-id="b45a0-107">Configurar um compartilhamento de arquivos SMB em um servidor executando o PowerShell 4.0 ou superior</span><span class="sxs-lookup"><span data-stu-id="b45a0-107">Set up an SMB file share on a server running PowerShell 4.0 or higher</span></span>
- <span data-ttu-id="b45a0-108">Configurar um cliente executando o PowerShell 4.0 ou superior para efetuar pull desse compartilhamento SMB</span><span class="sxs-lookup"><span data-stu-id="b45a0-108">Configure a client running PowerShell 4.0 or higher to pull from that SMB share</span></span>

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a><span data-ttu-id="b45a0-109">Usando o recurso xSmbShare para criar um compartilhamento de arquivos SMB</span><span class="sxs-lookup"><span data-stu-id="b45a0-109">Using the xSmbShare resource to create an SMB file share</span></span>

<span data-ttu-id="b45a0-110">Há várias maneiras para configurar um compartilhamento de arquivos SMB, mas vamos ver como você pode fazer isso usando DSC.</span><span class="sxs-lookup"><span data-stu-id="b45a0-110">There are a number of ways to set up an SMB file share, but let's look at how you can do this by using DSC.</span></span>

### <a name="install-the-xsmbshare-resource"></a><span data-ttu-id="b45a0-111">Instalar o recurso xSmbShare</span><span class="sxs-lookup"><span data-stu-id="b45a0-111">Install the xSmbShare resource</span></span>

<span data-ttu-id="b45a0-112">Chame o cmdlet [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) para instalar o módulo **xSmbShare**.</span><span class="sxs-lookup"><span data-stu-id="b45a0-112">Call the [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet to install the **xSmbShare** module.</span></span>
><span data-ttu-id="b45a0-113">**Observação**: **Install-Module** está incluído no módulo **PowerShellGet**, que está incluído no PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="b45a0-113">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="b45a0-114">É possível baixar o módulo **PowerShellGet** para o PowerShell 3.0 e 4.0 em [Visualização de Módulos do PowerShell do PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="b45a0-114">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span> <span data-ttu-id="b45a0-115">O **xSmbShare** contém o recurso de DSC **xSmbShare**, que pode ser usado para criar um compartilhamento de arquivo SMB.</span><span class="sxs-lookup"><span data-stu-id="b45a0-115">The **xSmbShare** contains the DSC resource **xSmbShare**, which can be used to create an SMB file share.</span></span>

### <a name="create-the-directory-and-file-share"></a><span data-ttu-id="b45a0-116">Criar o diretório e o compartilhamento de arquivos</span><span class="sxs-lookup"><span data-stu-id="b45a0-116">Create the directory and file share</span></span>

<span data-ttu-id="b45a0-117">A configuração a seguir usa o recurso [File](fileResource.md) para criar o diretório para o compartilhamento e o recurso **xSmbShare** para configurar o compartilhamento SMB:</span><span class="sxs-lookup"><span data-stu-id="b45a0-117">The following configuration uses the [File](fileResource.md) resource to create the directory for the share and the **xSmbShare** resource to set up the SMB share:</span></span>

```powershell
Configuration SmbShare {

Import-DscResource -ModuleName PSDesiredStateConfiguration
Import-DscResource -ModuleName xSmbShare

    Node localhost {

        File CreateFolder {

            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'

        }

        xSMBShare CreateShare {

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

<span data-ttu-id="b45a0-118">A configuração cria o diretório `C:\DscSmbShare` se ele ainda não existir e, em seguida, usa esse diretório como um compartilhamento de arquivos SMB.</span><span class="sxs-lookup"><span data-stu-id="b45a0-118">The configuration creates the directory `C:\DscSmbShare` if it doesn't already exists, and then uses that directory as an SMB file share.</span></span> <span data-ttu-id="b45a0-119">**FullAccess** deve ser fornecido a qualquer conta que precise gravar no compartilhamento de arquivo ou excluir algo dele e **ReadAccess** deve ser fornecido a qualquer nó de cliente que obterá configurações e/ou recursos de DSC do compartilhamento (isso porque o DSC é executado como a conta do sistema por padrão, de modo que o computador em si precisa ter acesso ao compartilhamento).</span><span class="sxs-lookup"><span data-stu-id="b45a0-119">**FullAccess** should be given to any account that needs to write to or delete from the file share, and **ReadAccess** must be given to any client nodes that get configurations and/or DSC resources from the share ( this is because DSC runs as the system account by default, so the computer itself has to have access to the share).</span></span>


### <a name="give-file-system-access-to-the-pull-client"></a><span data-ttu-id="b45a0-120">Conceder acesso ao sistema de arquivos para o cliente de pull</span><span class="sxs-lookup"><span data-stu-id="b45a0-120">Give file system access to the pull client</span></span>

<span data-ttu-id="b45a0-121">Conceder **ReadAccess** para um nó do cliente permite que esse nó acesse o compartilhamento SMB, mas não arquivos ou pastas dentro desse compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="b45a0-121">Giving **ReadAccess** to a client node allows that node to access the SMB share, but not to files or folders within that share.</span></span> <span data-ttu-id="b45a0-122">Você precisa conceder explicitamente aos nós do cliente acesso à pasta e às subpastas de compartilhamento SMB.</span><span class="sxs-lookup"><span data-stu-id="b45a0-122">You have to explicitly grant client nodes access to the SMB share folder and sub-folders.</span></span> <span data-ttu-id="b45a0-123">Podemos fazer isso com o DSC adicionando/usando o recurso **cNtfsPermissionEntry**, que está contido no módulo [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0).</span><span class="sxs-lookup"><span data-stu-id="b45a0-123">We can do this with DSC by adding using the **cNtfsPermissionEntry** resource, which is contained in the [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module.</span></span> <span data-ttu-id="b45a0-124">A configuração a seguir adiciona um bloco **cNtfsPermissionEntry**, que concede acesso ReadAndExecute ao cliente de pull:</span><span class="sxs-lookup"><span data-stu-id="b45a0-124">The following configuration adds a **cNtfsPermissionEntry** block that grants ReadAndExecute access to the pull client:</span></span>

```powershell
Configuration DSCSMB {

Import-DscResource -ModuleName PSDesiredStateConfiguration
Import-DscResource -ModuleName xSmbShare
Import-DscResource -ModuleName cNtfsAccessControl

    Node localhost {

        File CreateFolder {

            DestinationPath = 'DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'

        }

        xSMBShare CreateShare {

            Name = 'DscSmbShare'
            Path = 'DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'

        }

        cNtfsPermissionEntry PermissionSet1 {

        Ensure = 'Present'
        Path = 'C:\DSCSMB'
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

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="b45a0-125">Colocando configurações e recursos</span><span class="sxs-lookup"><span data-stu-id="b45a0-125">Placing configurations and resources</span></span>

<span data-ttu-id="b45a0-126">Salve todos os arquivos MOF de configuração e/ou recursos DSC que você deseja que sejam obtidos por pull do compartilhamento de pasta SMB pelos nós do cliente.</span><span class="sxs-lookup"><span data-stu-id="b45a0-126">Save any configuration MOF files and/or DSC resources that you want client nodes to pull in the SMB share folder.</span></span>

<span data-ttu-id="b45a0-127">O arquivo MOF de configuração no servidor de pull deve ser nomeado como _ConfigurationID_.mof, em que _ConfigurationID_ é o valor da propriedade **ConfigurationID** do LCM do nó de destino.</span><span class="sxs-lookup"><span data-stu-id="b45a0-127">Any configuration MOF file must be named _ConfigurationID_.mof, where _ConfigurationID_ is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="b45a0-128">Para obter mais informações sobre como configurar clientes de pull, confira [Configurando um cliente de pull usando uma ID de configuração](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="b45a0-128">For more information about setting up pull clients, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

><span data-ttu-id="b45a0-129">**Observação:** você deverá usar IDs de configuração se estiver usando um servidor de pull de SMB.</span><span class="sxs-lookup"><span data-stu-id="b45a0-129">**Note:** You must use configuration IDs if you are using an SMB pull server.</span></span> <span data-ttu-id="b45a0-130">Não há suporte para nomes de configuração para SMB.</span><span class="sxs-lookup"><span data-stu-id="b45a0-130">Configuration names are not supported for SMB.</span></span>

<span data-ttu-id="b45a0-131">Cada módulo de recurso precisa ser compactado e nomeado de acordo com o padrão a seguir `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="b45a0-131">Each resource module needs to be zipped and named according the the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="b45a0-132">Por exemplo, um módulo chamado xWebAdminstration com uma versão do módulo correspondente a 3.1.2.0 seria nomeado 'xWebAdministration_3.2.1.0.zip'.</span><span class="sxs-lookup"><span data-stu-id="b45a0-132">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="b45a0-133">Cada versão de um módulo deve estar contido em um único arquivo zip.</span><span class="sxs-lookup"><span data-stu-id="b45a0-133">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="b45a0-134">Como há apenas uma única versão de um recurso em cada arquivo zip, não há suporte para o formato do módulo adicionado ao WMF 5.0 com suporte para várias versões de módulo em um único diretório.</span><span class="sxs-lookup"><span data-stu-id="b45a0-134">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span> <span data-ttu-id="b45a0-135">Isso significa que antes de empacotar módulos de recursos DSC para uso com o servidor de pull, você precisará fazer uma pequena alteração na estrutura de diretórios.</span><span class="sxs-lookup"><span data-stu-id="b45a0-135">This means that before packaging up DSC resource modules for use with pull server you need to make a small change to the directory structure.</span></span> <span data-ttu-id="b45a0-136">O formato padrão dos módulos contendo o recurso DSC no WMF 5.0 é '{Pasta do Módulo}\{{Versão do Módulo}\DscResources\{{Pasta do Recurso DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="b45a0-136">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="b45a0-137">Antes do empacotamento para o servidor de pull, simplesmente remova a pasta **{Versão do módulo}** de modo que o caminho se torne '{Pasta do Módulo}\DscResources\{{Pasta do Recurso DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="b45a0-137">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="b45a0-138">Com essa alteração, compacte a pasta conforme descrito acima e coloque esses arquivos zip na pasta de compartilhamento SMB.</span><span class="sxs-lookup"><span data-stu-id="b45a0-138">With this change, zip the folder as described above and place these zip files in the SMB share folder.</span></span>

## <a name="creating-the-mof-checksum"></a><span data-ttu-id="b45a0-139">Criando a soma de verificação de MOF</span><span class="sxs-lookup"><span data-stu-id="b45a0-139">Creating the MOF checksum</span></span>
<span data-ttu-id="b45a0-140">Um arquivo MOF de configuração precisa ser emparelhado com um arquivo de soma de verificação para que um LCM em um nó de destino possa validar a configuração.</span><span class="sxs-lookup"><span data-stu-id="b45a0-140">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="b45a0-141">Para criar uma soma de verificação, chame o cmdlet [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx).</span><span class="sxs-lookup"><span data-stu-id="b45a0-141">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span> <span data-ttu-id="b45a0-142">O cmdlet usa um parâmetro **Path** que especifica a pasta na qual se encontra o MOF de configuração.</span><span class="sxs-lookup"><span data-stu-id="b45a0-142">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="b45a0-143">O cmdlet cria um arquivo de soma de verificação chamado `ConfigurationMOFName.mof.checksum`, em que `ConfigurationMOFName` é o nome do arquivo MOF de configuração.</span><span class="sxs-lookup"><span data-stu-id="b45a0-143">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="b45a0-144">Se houver mais de um arquivo MOF de configuração na pasta especificada, será criada uma soma de verificação para cada configuração na pasta.</span><span class="sxs-lookup"><span data-stu-id="b45a0-144">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>

<span data-ttu-id="b45a0-145">O arquivo de soma de verificação deve estar presente no mesmo diretório em que o arquivo MOF de configuração (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` por padrão) e ter o mesmo nome com a extensão `.checksum` anexada.</span><span class="sxs-lookup"><span data-stu-id="b45a0-145">The checksum file must be present in the same directory as the configuration MOF file (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` by default), and have the same name with the `.checksum` extension appended.</span></span>

><span data-ttu-id="b45a0-146">**Observação**: se alterar o arquivo MOF de configuração de qualquer forma, você também deverá recriar o arquivo de soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="b45a0-146">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="setting-up-a-pull-client-for-smb"></a><span data-ttu-id="b45a0-147">Configurando um cliente de pull para SMB</span><span class="sxs-lookup"><span data-stu-id="b45a0-147">Setting up a pull client for SMB</span></span>

<span data-ttu-id="b45a0-148">Para configurar um cliente que recebe as configurações e/ou recursos de um compartilhamento SMB, você configura o LCM (Gerenciador de Configurações Local) do cliente com blocos **ConfigurationRepositoryShare** e **ResourceRepositoryShare** que especificam o compartilhamento do qual efetuar o configurações de pull e recursos DSC.</span><span class="sxs-lookup"><span data-stu-id="b45a0-148">To set up a client that pulls configurations and/or resources from an SMB share, you configure the client's Local Configuration Manager (LCM) with **ConfigurationRepositoryShare** and **ResourceRepositoryShare** blocks that specify the share from which to pull configurations and DSC resources.</span></span>

<span data-ttu-id="b45a0-149">Para obter mais informações sobre como configurar um LCM, consulte [Configurando um cliente de pull usando a ID de configuração](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="b45a0-149">For more information about configuring the LCM, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

><span data-ttu-id="b45a0-150">**Observação:** para simplificar, este exemplo usa o **PSDscAllowPlainTextPassword** para permitir a passagem de uma senha de texto não criptografado para o parâmetro **Credencial**.</span><span class="sxs-lookup"><span data-stu-id="b45a0-150">**Note:** For simplicity, this example uses the **PSDscAllowPlainTextPassword** to allow passing a plaintext password to the **Credential** parameter.</span></span> <span data-ttu-id="b45a0-151">Para obter informações sobre como passar credenciais de forma mais segura, consulte [Opções de Credenciais nos Dados de Configuração](configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="b45a0-151">For information about passing credentials more securely, see [Credentials Options in Configuration Data](configDataCredentials.md).</span></span>

><span data-ttu-id="b45a0-152">**Observação:** você deve especificar uma **ConfigurationID** no bloco **Configurações** de uma metaconfiguração de um servidor de pull de SMB, mesmo que só esteja extraindo recursos.</span><span class="sxs-lookup"><span data-stu-id="b45a0-152">**Note:** You must specify a **ConfigurationID** in the **Settings** block of a metaconfiguration for an SMB pull server, even if you are only pulling resources.</span></span>

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

## <a name="acknowledgements"></a><span data-ttu-id="b45a0-153">Agradecimentos</span><span class="sxs-lookup"><span data-stu-id="b45a0-153">Acknowledgements</span></span>

<span data-ttu-id="b45a0-154">Agradecimentos especiais às pessoas a seguir:</span><span class="sxs-lookup"><span data-stu-id="b45a0-154">Special thanks to the following:</span></span>

- <span data-ttu-id="b45a0-155">Mike F. Robbins, cujas postagens sobre o uso de SMB para DSC ajudaram a informar o conteúdo deste tópico.</span><span class="sxs-lookup"><span data-stu-id="b45a0-155">Mike F. Robbins, whose posts on using SMB for DSC helped inform the content in this topic.</span></span> <span data-ttu-id="b45a0-156">Seu blog está em [Mike F Robbins](http://mikefrobbins.com/).</span><span class="sxs-lookup"><span data-stu-id="b45a0-156">His blog is at [Mike F Robbins](http://mikefrobbins.com/).</span></span>
- <span data-ttu-id="b45a0-157">Serge Nikalaichyk, que criou o módulo **cNtfsAccessControl**.</span><span class="sxs-lookup"><span data-stu-id="b45a0-157">Serge Nikalaichyk, who authored the **cNtfsAccessControl** module.</span></span> <span data-ttu-id="b45a0-158">A fonte para esse módulo está em https://github.com/SNikalaichyk/cNtfsAccessControl.</span><span class="sxs-lookup"><span data-stu-id="b45a0-158">The source for this module is at https://github.com/SNikalaichyk/cNtfsAccessControl.</span></span>

## <a name="see-also"></a><span data-ttu-id="b45a0-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b45a0-159">See also</span></span>
- [<span data-ttu-id="b45a0-160">Visão Geral da Configuração de Estado Desejado do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b45a0-160">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="b45a0-161">Aplicando configurações</span><span class="sxs-lookup"><span data-stu-id="b45a0-161">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="b45a0-162">Configurando um cliente de pull usando uma ID de configuração</span><span class="sxs-lookup"><span data-stu-id="b45a0-162">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)