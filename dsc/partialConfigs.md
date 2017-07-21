---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Configurações parciais da Configuração de Estado Desejado do PowerShell"
ms.openlocfilehash: 1f1abd34e80a2e23aefe1e4d378cd36472d6e38d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a><span data-ttu-id="91bc1-103">Configurações parciais da Configuração de Estado Desejado do PowerShell</span><span class="sxs-lookup"><span data-stu-id="91bc1-103">PowerShell Desired State Configuration partial configurations</span></span>

><span data-ttu-id="91bc1-104">Aplica-se a: Windows PowerShell 5.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="91bc1-104">Applies To: Windows PowerShell 5.0 and later.</span></span>

<span data-ttu-id="91bc1-105">No PowerShell 5.0, a Configuração de Estado Desejado (DSC) permite que as configurações sejam entregues em fragmentos e de várias fontes.</span><span class="sxs-lookup"><span data-stu-id="91bc1-105">In PowerShell 5.0, Desired State Configuration (DSC) allows configurations to be delivered in fragments and from multiple sources.</span></span> <span data-ttu-id="91bc1-106">O Gerenciador de Configurações Local (LCM) no nó de destino reúne os fragmentos antes de aplicá-los como uma única configuração.</span><span class="sxs-lookup"><span data-stu-id="91bc1-106">The Local Configuration Manager (LCM) on the target node puts the fragments together before applying them as a single configuration.</span></span> <span data-ttu-id="91bc1-107">Essa capacidade permite compartilhar o controle de configuração entre equipes ou pessoas.</span><span class="sxs-lookup"><span data-stu-id="91bc1-107">This capability allows sharing control of configuration between teams or individuals.</span></span> <span data-ttu-id="91bc1-108">Por exemplo, se duas ou mais equipes de desenvolvedores estiverem colaborando em um serviço, cada uma poderá querer criar configurações para gerenciar sua parte do serviço.</span><span class="sxs-lookup"><span data-stu-id="91bc1-108">For example, if two or more teams of developers are collaborating on a service, they might each want to create configurations to manage their part of the service.</span></span> <span data-ttu-id="91bc1-109">Cada uma dessas configurações pode ser extraída de servidores de pull diferentes e adicionada em diferentes estágios do desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="91bc1-109">Each of these configurations could be pulled from different pull servers, and they could be added at different stages of development.</span></span> <span data-ttu-id="91bc1-110">Configurações parciais também permitem que diferentes pessoas ou equipes controlem diferentes aspectos da configuração de nós sem a necessidade de coordenar a edição de um documento único de configuração.</span><span class="sxs-lookup"><span data-stu-id="91bc1-110">Partial configurations also allow different individuals or teams to control different aspects of configuring nodes without having to coordinate the editing of a single configuration document.</span></span> <span data-ttu-id="91bc1-111">Por exemplo, uma equipe pode ser responsável por implantar uma VM e o sistema operacional, enquanto outra equipe pode implantar outros aplicativos e serviços em tal VM.</span><span class="sxs-lookup"><span data-stu-id="91bc1-111">For example, one team might be responsible for deploying a VM and operating system, while another team might deploy other applications and services on that VM.</span></span> <span data-ttu-id="91bc1-112">Com configurações parciais, cada equipe pode criar sua própria configuração, sem complicações desnecessárias.</span><span class="sxs-lookup"><span data-stu-id="91bc1-112">With partial configurations, each team can create its own configuration, without either of them being unnecessarily complicated.</span></span>

<span data-ttu-id="91bc1-113">É possível usar configurações parciais no modo de push, no modo de pull ou em uma combinação de ambos.</span><span class="sxs-lookup"><span data-stu-id="91bc1-113">You can use partial configurations in push mode, pull mode, or a combination of the two.</span></span>

## <a name="partial-configurations-in-push-mode"></a><span data-ttu-id="91bc1-114">Configurações parciais no modo de push</span><span class="sxs-lookup"><span data-stu-id="91bc1-114">Partial configurations in push mode</span></span>
<span data-ttu-id="91bc1-115">Para usar configurações parciais no modo de push, o LCM é configurado no nó de destino para receber as configurações parciais.</span><span class="sxs-lookup"><span data-stu-id="91bc1-115">To use partial configurations in push mode, you configure the LCM on the target node to receive the partial configurations.</span></span> <span data-ttu-id="91bc1-116">Cada configuração parcial deve ser enviada por push para o destino usando o cmdlet Publish-DSCConfiguration.</span><span class="sxs-lookup"><span data-stu-id="91bc1-116">Each partial configuration must be pushed to the target by using the Publish-DSCConfiguration cmdlet.</span></span> <span data-ttu-id="91bc1-117">Em seguida, o nó de destino combina a configuração parcial em uma única configuração; pode-se aplicar a configuração chamando o cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx).</span><span class="sxs-lookup"><span data-stu-id="91bc1-117">The target node then combines the partial configuration into a single configuration, and you can apply the configuration by calling the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span></span>

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a><span data-ttu-id="91bc1-118">Configurando o LCM para configurações parciais no modo de push</span><span class="sxs-lookup"><span data-stu-id="91bc1-118">Configuring the LCM for push-mode partial configurations</span></span>
<span data-ttu-id="91bc1-119">Para configurar o LCM para configurações parciais no modo de push, é criada uma configuração **DSCLocalConfigurationManager** com um bloco **PartialConfiguration** para cada configuração parcial.</span><span class="sxs-lookup"><span data-stu-id="91bc1-119">To configure the LCM for partial configurations in push mode, you create a **DSCLocalConfigurationManager** configuration with one **PartialConfiguration** block for each partial configuration.</span></span> <span data-ttu-id="91bc1-120">Para obter mais informações sobre como configurar o LCM, consulte [Configurando o Gerenciador de Configurações Local com o Windows](https://technet.microsoft.com/en-us/library/mt421188.aspx).</span><span class="sxs-lookup"><span data-stu-id="91bc1-120">For more information about configuring the LCM, see [Windows Configuring the Local Configuration Manager](https://technet.microsoft.com/en-us/library/mt421188.aspx).</span></span> <span data-ttu-id="91bc1-121">O exemplo a seguir mostra uma configuração do LCM que espera duas configurações parciais—uma que implanta o sistema operacional e outra que implanta e configura o SharePoint.</span><span class="sxs-lookup"><span data-stu-id="91bc1-121">The following example shows an LCM configuration that expects two partial configurations—one that deploys the OS, and one that deploys and configures SharePoint.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        
           PartialConfiguration ServiceAccountConfig
        {
            Description = 'Configuration to add the SharePoint service account to the Administrators group.'
            RefreshMode = 'Push'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the SharePoint server'
            RefreshMode = 'Push'
        }
    }
}
PartialConfigDemo 
```

<span data-ttu-id="91bc1-122">O **RefreshMode** para cada configuração parcial é definido como "Push".</span><span class="sxs-lookup"><span data-stu-id="91bc1-122">The **RefreshMode** for each partial configuration is set to "Push".</span></span> <span data-ttu-id="91bc1-123">Os nomes dos blocos **PartialConfiguration** (nesse caso, “ServiceAccountConfig” e “SharePointConfig”) devem corresponder exatamente aos nomes das configurações que são enviados por push para o nó de destino.</span><span class="sxs-lookup"><span data-stu-id="91bc1-123">The names of the **PartialConfiguration** blocks (in this case, "ServiceAccountConfig" and "SharePointConfig") must match exactly the names of the configurations that are pushed to the target node.</span></span>

><span data-ttu-id="91bc1-124">**Observação:** o nome de cada bloco **PartialConfiguration** deve corresponder ao nome real da configuração conforme especificado no script de configuração e não o nome do arquivo MOF, que deve ser o nome do nó de destino ou `localhost`.</span><span class="sxs-lookup"><span data-stu-id="91bc1-124">**Note:** The named of each **PartialConfiguration** block must match the actual name of the configuration as it is specified in the configuration script, not the name of the MOF file, which should be either the name of the target node or `localhost`.</span></span>

### <a name="publishing-and-starting-push-mode-partial-configurations"></a><span data-ttu-id="91bc1-125">Publicando e iniciando configurações parciais no modo de push</span><span class="sxs-lookup"><span data-stu-id="91bc1-125">Publishing and starting push-mode partial configurations</span></span>

<span data-ttu-id="91bc1-126">A seguir, chame [Publish-DSCConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) para cada configuração, passando as pastas que contêm os documentos de configuração como os parâmetros **Path**.</span><span class="sxs-lookup"><span data-stu-id="91bc1-126">You then call [Publish-DSCConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) for each configuration, passing the folders that contain the configuration documents as the **Path** parameters.</span></span> <span data-ttu-id="91bc1-127">O `Publish-DSCConfiguration` coloca os arquivos MOF de configuração para os nós de destino.</span><span class="sxs-lookup"><span data-stu-id="91bc1-127">`Publish-DSCConfiguration`places the configuration MOF files to the target nodes.</span></span> <span data-ttu-id="91bc1-128">Depois de publicar as duas configurações, é possível chamar `Start-DSCConfiguration –UseExisting` no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="91bc1-128">After publishing both configurations, you can call `Start-DSCConfiguration –UseExisting` on the target node.</span></span>

<span data-ttu-id="91bc1-129">Por exemplo, se você compilou os seguintes documentos MOF de configuração no nó de criação:</span><span class="sxs-lookup"><span data-stu-id="91bc1-129">For example, if you have compiled the following configuration MOF documents on the authoring node:</span></span>

```powershell
PS C:\PartialConfigTest> Get-ChildItem -Recurse


    Directory: C:\PartialConfigTest


Mode                LastWriteTime         Length Name                                                                                                                                         
----                -------------         ------ ----                                                                                                                                         
d-----        8/11/2016   1:55 PM                ServiceAccountConfig                                                                                                                  
d-----       11/17/2016   4:14 PM                SharePointConfig                                                                                                                                    


    Directory: C:\PartialConfigTest\ServiceAccountConfig


Mode                LastWriteTime         Length Name                                                                                                                                         
----                -------------         ------ ----                                                                                                                                         
-a----        8/11/2016   2:02 PM           2034 TestVM.mof                                                                                                                                


    Directory: C:\DscTests\SharePointConfig


Mode                LastWriteTime         Length Name                                                                                                                                         
----                -------------         ------ ----                                                                                                                                         
-a----       11/17/2016   4:14 PM           1930 TestVM.mof                                                                                                                                     
```

<span data-ttu-id="91bc1-130">É necessário publicar e executar as configurações da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="91bc1-130">You would publish and run the configurations as follows:</span></span>

```powershell
PS C:\PartialConfigTest> Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Start-Configuration -UseExisting -ComputerName 'TestVM'

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command                  
--     ----            -------------   -----         -----------     --------             -------                  
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

><span data-ttu-id="91bc1-131">**Observação:** o usuário que estiver executando o cmdlet [Publish-DSCConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) deve ter privilégios de administrador no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="91bc1-131">**Note:** The user running the [Publish-DSCConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) cmdlet must have administrator privileges on the target node.</span></span>

## <a name="partial-configurations-in-pull-mode"></a><span data-ttu-id="91bc1-132">Configurações parciais no modo de pull</span><span class="sxs-lookup"><span data-stu-id="91bc1-132">Partial configurations in pull mode</span></span>

<span data-ttu-id="91bc1-133">Configurações parciais podem ser extraídas por push de um ou mais servidores de pull (para obter mais informações sobre servidores de pull, consulte [Servidores de Pull de Configuração de Estado Desejado do Windows PowerShell](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="91bc1-133">Partial configurations can be pulled from one or more pull servers (for more information about pull servers, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="91bc1-134">Para fazer isso, você precisa configurar o LCM no nó de destino a fim de extrair por push as configurações parciais, bem como nomear e localizar os documentos de configuração corretamente nos servidores de pull.</span><span class="sxs-lookup"><span data-stu-id="91bc1-134">To do this, you have to configure the LCM on the target node to pull the partial configurations, and name and locate the configuration documents properly on the pull servers.</span></span>

### <a name="configuring-the-lcm-for-pull-node-configurations"></a><span data-ttu-id="91bc1-135">Configurando o LCM para configurações no nó de pull</span><span class="sxs-lookup"><span data-stu-id="91bc1-135">Configuring the LCM for pull node configurations</span></span>

<span data-ttu-id="91bc1-136">Para configurar o LCM para efetuar o pull de configurações parciais de um servidor de pull, defina o servidor de pull em um bloco **ConfigurationRepositoryWeb** (para um servidor de pull de HTTP) ou **ConfigurationRepositoryShare** (para um servidor de pull de SMB).</span><span class="sxs-lookup"><span data-stu-id="91bc1-136">To configure the LCM to pull partial configurations from a pull server, you define the pull server in either a **ConfigurationRepositoryWeb** (for an HTTP pull server) or **ConfigurationRepositoryShare** (for an SMB pull server) block.</span></span> <span data-ttu-id="91bc1-137">Em seguida, crie blocos **PartialConfiguration** que se refiram ao servidor de pull, usando a propriedade **ConfigurationSource**.</span><span class="sxs-lookup"><span data-stu-id="91bc1-137">You then create **PartialConfiguration** blocks that refer to the pull server by using the **ConfigurationSource** property.</span></span> <span data-ttu-id="91bc1-138">Também é necessário criar um bloco **Settings** para especificar que o LCM usa o modo de pull, além de especificar o **ConfigurationNames** ou o **ConfigurationID** que o servidor de pull e o nó de destino usam para identificar as configurações.</span><span class="sxs-lookup"><span data-stu-id="91bc1-138">You also need to create a **Settings** block to specify that the LCM uses pull mode, and to specify the **ConfigurationNames** or **ConfigurationID** that the pull server and target node use to identify the configurations.</span></span> <span data-ttu-id="91bc1-139">A metaconfiguração a seguir define um servidor de pull de HTTP denominado CONTOSO-PullSrv e duas configurações parciais que usam um servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="91bc1-139">The following meta-configuration defines an HTTP pull server named CONTOSO-PullSrv and two partial configurations that use that pull server.</span></span>

<span data-ttu-id="91bc1-140">Para obter mais informações sobre como configurar um LCM usando **ConfigurationNames**, consulte [Configurando um cliente de pull usando nomes de configuração](pullClientConfigNames.md).</span><span class="sxs-lookup"><span data-stu-id="91bc1-140">For more information about configuring the LCM using **ConfigurationNames**, see [Setting up a pull client using configuration names](pullClientConfigNames.md).</span></span> <span data-ttu-id="91bc1-141">Para obter mais informações sobre como configurar um LCM usando **ConfigurationID**, consulte [Configurando um cliente de pull usando a ID de configuração](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="91bc1-141">For information about configuring the LCM using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a><span data-ttu-id="91bc1-142">Configurando o LCM para configurações de modo de pull usando os nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="91bc1-142">Configuring the LCM for pull mode configurations using configuration names</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               ="ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'    
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38     
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }     
        
        PartialConfiguration ServiceAccountConfig 
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv") 
        }
 
        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
        }
   
}
``` 

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a><span data-ttu-id="91bc1-143">Configurando o LCM para configurações de modo de pull usando ConfigurationID</span><span class="sxs-lookup"><span data-stu-id="91bc1-143">Configuring the LCM for pull mode configurations using ConfigurationID</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemoConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode                     = 'Pull'
            ConfigurationID                 = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins            = 30 
            RebootNodeIfNeeded              = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            
        }
        
           PartialConfiguration ServiceAccountConfig
        {
            Description                     = 'Configuration for the Base OS'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode                     = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description                     = 'Configuration for the Sharepoint Server'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Pull'
        }
    }
}
PartialConfigDemo 
```

<span data-ttu-id="91bc1-144">É possível extrair configurações parciais de mais de um servidor de pull – você precisaria apenas definir cada servidor de pull e consultar o servidor de pull apropriado em cada bloco **PartialConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="91bc1-144">You can pull partial configurations from more than one pull server—you would just need to define each pull server, and then refer to the appropriate pull server in each **PartialConfiguration** block.</span></span>

<span data-ttu-id="91bc1-145">Depois de criar a metaconfiguração, deve executá-la para criar um documento de configuração (um arquivo MOF) e, em seguida, chamar [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621(v=wps.630).aspx) para configurar o LCM.</span><span class="sxs-lookup"><span data-stu-id="91bc1-145">After creating the meta-configuration, you must run it to create a configuration document (a MOF file), and then call [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621(v=wps.630).aspx) to configure the LCM.</span></span>

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a><span data-ttu-id="91bc1-146">Nomeando e colocando os documentos de configuração no servidor de pull (ConfigurationNames)</span><span class="sxs-lookup"><span data-stu-id="91bc1-146">Naming and placing the configuration documents on the pull server (ConfigurationNames)</span></span>

<span data-ttu-id="91bc1-147">Os documentos de configuração parcial devem ser colocados na pasta especificada como o **ConfigurationPath** no arquivo `web.config` para o servidor de pull (geralmente `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="91bc1-147">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> 

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a><span data-ttu-id="91bc1-148">Como nomear os documentos de configuração no servidor de pull no PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="91bc1-148">Naming configuration documents on the pull server in PowerShell 5.1</span></span>

<span data-ttu-id="91bc1-149">Se você estiver extraindo somente uma configuração parcial de um servidor de pull individual, o documento de configuração poderá ter qualquer nome.</span><span class="sxs-lookup"><span data-stu-id="91bc1-149">If you are pulling only one partial configuration from an individual pull server, the configuration document can have any name.</span></span> <span data-ttu-id="91bc1-150">Se você está extraindo mais de uma configuração parcial de um servidor de pull, o documento de configuração pode ser denominado `<ConfigurationName>.mof`, onde _ConfigurationName_ é o nome da configuração parcial, ou `<ConfigurationName>.<NodeName>.mof`, onde _ConfigurationName_ é o nome da configuração parcial, e _NodeName_ é o nome do nó de destino.</span><span class="sxs-lookup"><span data-stu-id="91bc1-150">If you are pulling more than one partial configuration from a pull server, the configuration document can be named either `<ConfigurationName>.mof`, where _ConfigurationName_ is the name of the partial configuration, or `<ConfigurationName>.<NodeName>.mof`, where  _ConfigurationName_ is the name of the partial configuration, and _NodeName_ is the name of the target node.</span></span> <span data-ttu-id="91bc1-151">Isso permite extrair configurações do servidor de pull de DSC de Automação do Azure.</span><span class="sxs-lookup"><span data-stu-id="91bc1-151">This allows you to pull configurations from Azure Automation DSC pull server.</span></span>


#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a><span data-ttu-id="91bc1-152">Como nomear os documentos de configuração no servidor de pull no PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="91bc1-152">Naming configuration documents on the pull server in PowerShell 5.0</span></span>

<span data-ttu-id="91bc1-153">Os documentos de configuração devem ser nomeados da seguinte maneira: `ConfigurationName.mof`, em que _ConfigurationName_ é o nome da configuração parcial.</span><span class="sxs-lookup"><span data-stu-id="91bc1-153">The configuration documents must be named as follows: `ConfigurationName.mof`, where _ConfigurationName_ is the name of the partial configuration.</span></span> <span data-ttu-id="91bc1-154">Para nosso exemplo, os documentos de configuração devem ser nomeados da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="91bc1-154">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a><span data-ttu-id="91bc1-155">Nomeando e colocando os documentos de configuração no servidor de pull (ConfigurationID)</span><span class="sxs-lookup"><span data-stu-id="91bc1-155">Naming and placing the configuration documents on the pull server (ConfigurationID)</span></span>

<span data-ttu-id="91bc1-156">Os documentos de configuração parcial devem ser colocados na pasta especificada como o **ConfigurationPath** no arquivo `web.config` para o servidor de pull (geralmente `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="91bc1-156">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> <span data-ttu-id="91bc1-157">Os documentos de configuração devem ser nomeados da seguinte maneira: _ConfigurationName_.</span><span class="sxs-lookup"><span data-stu-id="91bc1-157">The configuration documents must be named as follows: _ConfigurationName_.</span></span> <span data-ttu-id="91bc1-158">_ConfigurationID_`.mof`, em que _ConfigurationName_ é o nome da configuração parcial e _ConfigurationID_ é a ID de configuração definida no LCM no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="91bc1-158">_ConfigurationID_`.mof`, where _ConfigurationName_ is the name of the partial configuration and _ConfigurationID_ is the configuration ID defined in the LCM on the target node.</span></span> <span data-ttu-id="91bc1-159">Para nosso exemplo, os documentos de configuração devem ser nomeados da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="91bc1-159">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```


### <a name="running-partial-configurations-from-a-pull-server"></a><span data-ttu-id="91bc1-160">Executando configurações parciais de um servidor de pull</span><span class="sxs-lookup"><span data-stu-id="91bc1-160">Running partial configurations from a pull server</span></span>

<span data-ttu-id="91bc1-161">Depois que o LCM no nó de destino tiver sido configurado e os documentos de configuração tiverem sido criados e chamados corretamente no servidor de pull, o nó de destino vai efetuar o pull das configurações parciais, combiná-las e aplicar a configuração resultante em intervalos regulares, conforme especificado pela propriedade **RefreshFrequencyMins** do LCM.</span><span class="sxs-lookup"><span data-stu-id="91bc1-161">After the LCM on the target node has been configured, and the configuration documents have been created and properly named on the pull server, the target node will pull the partial configurations, combine them, and apply the resulting configuration at regular intervals as specified by the **RefreshFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="91bc1-162">Se você quiser forçar uma atualização, poderá chamar o cmdlet [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx) para efetuar o pull das configurações e, em seguida, `Start-DSCConfiguration –UseExisting` para aplicá-las.</span><span class="sxs-lookup"><span data-stu-id="91bc1-162">If you want to force a refresh, you can call the [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx) cmdlet, to pull the configurations, and then `Start-DSCConfiguration –UseExisting` to apply them.</span></span>


## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a><span data-ttu-id="91bc1-163">Configurações parciais nos modos de push e pull combinados</span><span class="sxs-lookup"><span data-stu-id="91bc1-163">Partial configurations in mixed push and pull modes</span></span>

<span data-ttu-id="91bc1-164">Também é possível combinar os modos de push e pull para configurações parciais.</span><span class="sxs-lookup"><span data-stu-id="91bc1-164">You can also mix push and pull modes for partial configurations.</span></span> <span data-ttu-id="91bc1-165">Ou seja, você pode ter uma configuração parcial que é extraída por pull de um servidor de pull, enquanto outra configuração parcial é enviada por push.</span><span class="sxs-lookup"><span data-stu-id="91bc1-165">That is, you could have one partial configuration that is pulled from a pull server, while another partial configuration is pushed.</span></span> <span data-ttu-id="91bc1-166">Especifique o modo de atualização para cada configuração parcial conforme descrito nas seções anteriores.</span><span class="sxs-lookup"><span data-stu-id="91bc1-166">Specify the refresh mode for each partial configuration as described in the previous sections.</span></span> <span data-ttu-id="91bc1-167">Por exemplo, a metaconfiguração a seguir descreve o mesmo exemplo, com a configuração parcial da `ServiceAccountConfig` no modo de pull e a configuração parcial do `SharePointConfig` no modo de push.</span><span class="sxs-lookup"><span data-stu-id="91bc1-167">For example, the following meta-configuration describes the same example, with the `ServiceAccountConfig` partial configuration in pull mode and the `SharePointConfig` partial configuration in push mode.</span></span>

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a><span data-ttu-id="91bc1-168">Modos de pull e push mistos usando ConfigurationNames</span><span class="sxs-lookup"><span data-stu-id="91bc1-168">Mixed push and pull modes using ConfigurationNames</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               = "ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'    
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38     
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }     
        
        PartialConfiguration ServiceAccountConfig 
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            RefreshMode                     = 'Pull' 
        }
 
        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Push'
        }
   
}
``` 

### <a name="mixed-push-and-pull-modes-using-configurationid"></a><span data-ttu-id="91bc1-169">Modos de pull e push mistos usando ConfigurationID</span><span class="sxs-lookup"><span data-stu-id="91bc1-169">Mixed push and pull modes using ConfigurationID</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        Settings
        {
            RefreshMode             = 'Pull'
            ConfigurationID         = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins    = 30 
            RebootNodeIfNeeded      = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL               = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            
        }
        
           PartialConfiguration ServiceAccountConfig
        {
            Description             = 'Configuration for the Base OS'
            ConfigurationSource     = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode             = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description             = 'Configuration for the Sharepoint Server'
            DependsOn               = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode             = 'Push'
        }
    }
}
PartialConfigDemo 
```

<span data-ttu-id="91bc1-170">Observe que o **RefreshMode** especificado no bloco Settings é "Pull", mas o **RefreshMode** para a configuração parcial `SharePointConfig` é "Push".</span><span class="sxs-lookup"><span data-stu-id="91bc1-170">Note that the **RefreshMode** specified in the Settings block is "Pull", but the **RefreshMode** for the `SharePointConfig` partial configuration is "Push".</span></span>

<span data-ttu-id="91bc1-171">É necessário nomear e localizar os documentos do MOF de configuração, conforme descrito acima, para os respectivos modos de atualização.</span><span class="sxs-lookup"><span data-stu-id="91bc1-171">Name and locate the configuration MOF files as described above for their respective refresh modes.</span></span> <span data-ttu-id="91bc1-172">Chame **Publish-DSCConfiguration** para publicar a configuração parcial de `SharePointConfig` e aguarde até que a configuração de `ServiceAccountConfig` seja extraída do servidor de pull ou force uma atualização chamando [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541(v=wps.630).aspx).</span><span class="sxs-lookup"><span data-stu-id="91bc1-172">Call **Publish-DSCConfiguration** to publish the `SharePointConfig` partial configuration, and either wait for the `ServiceAccountConfig` configuration to be pulled from the pull server, or force a refresh by calling [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541(v=wps.630).aspx).</span></span>

## <a name="example-serviceaccountconfig-partial-configuration"></a><span data-ttu-id="91bc1-173">Exemplo de configuração parcial de ServiceAccountConfig</span><span class="sxs-lookup"><span data-stu-id="91bc1-173">Example ServiceAccountConfig Partial Configuration</span></span>

```powershell
Configuration ServiceAccountConfig
{
    Param (
        [Parameter(Mandatory,
                   HelpMessage="Domain credentials required to add domain\sharepoint_svc to the local Administrators group.")]
        [ValidateNotNullOrEmpty()]
        [pscredential]$Credential
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration


    Node localhost
    {
        Group LocalAdmins
        {
            GroupName           = 'Administrators'
            MembersToInclude    = 'domain\sharepoint_svc',
                                  'admins@example.domain'
            Ensure              = 'Present'
            Credential          = $Credential
            
        }

        WindowsFeature Telnet
        {
            Name                = 'Telnet-Server'
            Ensure              = 'Absent'
        }
    }
}
ServiceAccountConfig

```
## <a name="example-sharepointconfig-partial-configuration"></a><span data-ttu-id="91bc1-174">Exemplo de configuração parcial do SharePointConfig</span><span class="sxs-lookup"><span data-stu-id="91bc1-174">Example SharePointConfig Partial Configuration</span></span>
```powershell
Configuration SharePointConfig
{
    Param (
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [pscredential]$ProductKey
    )

    Import-DscResource -ModuleName xSharePoint

    Node localhost
    {
        xSPInstall SharePointDefault
        {
            Ensure      = 'Present'
            BinaryDir   = '\\FileServer\Installers\Sharepoint\'
            ProductKey  = $ProductKey
        }
    }
}
SharePointConfig
```
##<a name="see-also"></a><span data-ttu-id="91bc1-175">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="91bc1-175">See Also</span></span> 

<span data-ttu-id="91bc1-176">**Conceitos**
[Servidores de Pull de Configuração de Estado Desejado do Windows PowerShell](pullServer.md)</span><span class="sxs-lookup"><span data-stu-id="91bc1-176">**Concepts**
[Windows PowerShell Desired State Configuration Pull Servers](pullServer.md)</span></span> 

[<span data-ttu-id="91bc1-177">Configurando o Gerenciador de Configurações Local com o Windows</span><span class="sxs-lookup"><span data-stu-id="91bc1-177">Windows Configuring the Local Configuration Manager</span></span>](https://technet.microsoft.com/en-us/library/mt421188.aspx) 

