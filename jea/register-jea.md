---
ms.date: 06/12/2017
keywords: jea,powershell,segurança
title: Registrando Configurações de JEA
ms.openlocfilehash: 2c4a8f64c966903a6eb8fcabe4cd25ae7f98b2c4
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522825"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="3f08b-103">Registrando Configurações de JEA</span><span class="sxs-lookup"><span data-stu-id="3f08b-103">Registering JEA Configurations</span></span>

> <span data-ttu-id="3f08b-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3f08b-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="3f08b-105">A última etapa antes de usar o JEA, depois que você tiver criado os [recursos de função](role-capabilities.md) e os [arquivo de configuração de sessão](session-configurations.md), é registrar o ponto de extremidade JEA.</span><span class="sxs-lookup"><span data-stu-id="3f08b-105">The last step before you can use JEA once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created is to register the JEA endpoint.</span></span>
<span data-ttu-id="3f08b-106">Esse processo aplica as informações de configuração de sessão no sistema e torna o ponto de extremidade disponível para uso pelos usuários e pelos mecanismos de automação.</span><span class="sxs-lookup"><span data-stu-id="3f08b-106">This process applies the session configuration information to the system and makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="3f08b-107">Configuração de computador único</span><span class="sxs-lookup"><span data-stu-id="3f08b-107">Single machine configuration</span></span>

<span data-ttu-id="3f08b-108">Em ambientes pequenos, você pode implantar o JEA ao registrar o arquivo de configuração de sessão usando o cmdlet [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration).</span><span class="sxs-lookup"><span data-stu-id="3f08b-108">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="3f08b-109">Antes de começar, verifique se os pré-requisitos a seguir foram atendidos:</span><span class="sxs-lookup"><span data-stu-id="3f08b-109">Before you begin, ensure that the following prerequisites have been met:</span></span>
- <span data-ttu-id="3f08b-110">Uma ou mais funções foram criadas e colocadas na pasta 'RoleCapabilities' de um módulo de PowerShell válido.</span><span class="sxs-lookup"><span data-stu-id="3f08b-110">One or more roles has been created and placed in the 'RoleCapabilities' folder of a valid PowerShell module.</span></span>
- <span data-ttu-id="3f08b-111">Um arquivo de configuração de sessão foi criado e testado.</span><span class="sxs-lookup"><span data-stu-id="3f08b-111">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="3f08b-112">O usuário que está registrando a configuração JEA tem direitos de administrador nos sistemas.</span><span class="sxs-lookup"><span data-stu-id="3f08b-112">The user registering the JEA configuration has administrator rights on the system(s).</span></span>

<span data-ttu-id="3f08b-113">Também é necessário selecionar um nome para o ponto de extremidade JEA.</span><span class="sxs-lookup"><span data-stu-id="3f08b-113">You will also need to select a name for your JEA endpoint.</span></span>
<span data-ttu-id="3f08b-114">O nome do ponto de extremidade JEA será necessário quando os usuários desejarem se conectar ao sistema usando o JEA.</span><span class="sxs-lookup"><span data-stu-id="3f08b-114">The name of the JEA endpoint will be required when users want to connect to the system using JEA.</span></span>
<span data-ttu-id="3f08b-115">Você pode usar o cmdlet [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) para verificar os nomes dos pontos de extremidade existentes no sistema.</span><span class="sxs-lookup"><span data-stu-id="3f08b-115">You can use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet to check the names of existing endpoints on the system.</span></span>
<span data-ttu-id="3f08b-116">Pontos de extremidade que começam com 'microsoft' geralmente são fornecidos com o Windows.</span><span class="sxs-lookup"><span data-stu-id="3f08b-116">Endpoints that start with 'microsoft' are typically shipped with Windows.</span></span>
<span data-ttu-id="3f08b-117">O ponto de extremidade 'microsoft.powershell' é o ponto de extremidade padrão usado ao se conectar a um ponto de extremidade remoto do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3f08b-117">The 'microsoft.powershell' endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="3f08b-118">Depois de determinar um nome apropriado para seu ponto de extremidade JEA, execute o seguinte comando para registrar o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="3f08b-118">When you have determined an appropriate name for your JEA endpoint, run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="3f08b-119">O comando acima reiniciará o serviço WinRM no sistema.</span><span class="sxs-lookup"><span data-stu-id="3f08b-119">The above command will restart the WinRM service on the system.</span></span>
> <span data-ttu-id="3f08b-120">Isso encerrará todas as sessões de comunicação remota do PowerShell, bem como quaisquer configurações de DSC em andamento.</span><span class="sxs-lookup"><span data-stu-id="3f08b-120">This will terminate all PowerShell remoting sessions as well as any ongoing DSC configurations.</span></span>
> <span data-ttu-id="3f08b-121">É recomendável que você coloque em offline todos computadores de produção antes de executar o comando para evitar interromper as operações de negócios.</span><span class="sxs-lookup"><span data-stu-id="3f08b-121">It is recommended that you take any production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="3f08b-122">Se o registro foi bem-sucedido, você estará pronto para [usar o JEA](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="3f08b-122">If registration was successful, you are ready to [use JEA](using-jea.md).</span></span>
<span data-ttu-id="3f08b-123">Você pode excluir o arquivo de configuração de sessão a qualquer momento; ele não é mais usado depois do registro.</span><span class="sxs-lookup"><span data-stu-id="3f08b-123">You may delete the session configuration file at any time; it is not used after registration.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="3f08b-124">Configuração de vários computadores com o DSC</span><span class="sxs-lookup"><span data-stu-id="3f08b-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="3f08b-125">Se você estiver implantando o JEA em vários computadores, o modelo de implantação mais simples é usar o recurso [Configuração de Estado Desejado](https://msdn.microsoft.com/powershell/dsc/overview) do JEA para implantar o JEA de forma rápida e consistente em cada computador.</span><span class="sxs-lookup"><span data-stu-id="3f08b-125">If you are deploying JEA on multiple machines, the simplest deployment model is to use the JEA [Desired State Configuration](https://msdn.microsoft.com/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="3f08b-126">Para implantar o JEA com o DSC, você precisará garantir que os seguintes pré-requisitos sejam atendidos:</span><span class="sxs-lookup"><span data-stu-id="3f08b-126">To deploy JEA with DSC, you will need to ensure the following prerequisites are met:</span></span>
- <span data-ttu-id="3f08b-127">Um ou mais recursos de função foram criados e adicionados a um módulo de PowerShell válido.</span><span class="sxs-lookup"><span data-stu-id="3f08b-127">One or more role capabilities have been authored and added to a valid PowerShell module.</span></span>
- <span data-ttu-id="3f08b-128">O módulo do PowerShell que contém as funções é armazenado em um compartilhamento de arquivo (somente leitura) acessível por cada computador.</span><span class="sxs-lookup"><span data-stu-id="3f08b-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="3f08b-129">As configurações para a configuração de sessão foram determinadas.</span><span class="sxs-lookup"><span data-stu-id="3f08b-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="3f08b-130">Não é necessário criar um arquivo de configuração de sessão ao usar o recurso DSC do JEA.</span><span class="sxs-lookup"><span data-stu-id="3f08b-130">You do not need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="3f08b-131">Você tem credenciais que permitem a execução de ações administrativas em cada computador ou tem acesso a um servidor de pull de DSC usado para gerenciar os computadores.</span><span class="sxs-lookup"><span data-stu-id="3f08b-131">You have credentials that will allow you to perform administrative actions on each machine, or have access to a DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="3f08b-132">O [recurso DSC do JEA](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource) foi baixado</span><span class="sxs-lookup"><span data-stu-id="3f08b-132">You have downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span></span>

<span data-ttu-id="3f08b-133">Em um computador de destino (ou servidor de pull, se você estiver usando um), crie uma configuração DSC para seu ponto de extremidade JEA.</span><span class="sxs-lookup"><span data-stu-id="3f08b-133">On a target machine (or pull server, if you are using one), create a DSC configuration for your JEA endpoint.</span></span>
<span data-ttu-id="3f08b-134">Nessa configuração, será utilizado o recurso DSC de JustEnoughAdministration para configurar o arquivo de configuração de sessão e o Recurso de arquivo para copiar sobre os recursos de função do compartilhamento de arquivos.</span><span class="sxs-lookup"><span data-stu-id="3f08b-134">In this configuration, you will use the JustEnoughAdministration DSC resource to set up the session configuration file and the File resource to copy over the role capabilities from the file share.</span></span>

<span data-ttu-id="3f08b-135">As seguintes propriedades são configuráveis usando o recurso de DSC:</span><span class="sxs-lookup"><span data-stu-id="3f08b-135">The following properties are configurable using the DSC resource:</span></span>
- <span data-ttu-id="3f08b-136">Definições de Função</span><span class="sxs-lookup"><span data-stu-id="3f08b-136">Role Definitions</span></span>
- <span data-ttu-id="3f08b-137">Grupos de Conta Virtual</span><span class="sxs-lookup"><span data-stu-id="3f08b-137">Virtual Account groups</span></span>
- <span data-ttu-id="3f08b-138">Nome de Conta de Serviço Gerenciado de Grupo</span><span class="sxs-lookup"><span data-stu-id="3f08b-138">Group Managed Service Account name</span></span>
- <span data-ttu-id="3f08b-139">Diretório de transcrição</span><span class="sxs-lookup"><span data-stu-id="3f08b-139">Transcript directory</span></span>
- <span data-ttu-id="3f08b-140">Unidade de usuário</span><span class="sxs-lookup"><span data-stu-id="3f08b-140">User drive</span></span>
- <span data-ttu-id="3f08b-141">Regras de acesso condicional</span><span class="sxs-lookup"><span data-stu-id="3f08b-141">Conditional access rules</span></span>
- <span data-ttu-id="3f08b-142">Scripts de inicialização para a sessão JEA</span><span class="sxs-lookup"><span data-stu-id="3f08b-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="3f08b-143">A sintaxe para cada uma dessas propriedades em uma configuração DSC é consistente com o arquivo de configuração de sessão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3f08b-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="3f08b-144">Abaixo está um exemplo de configuração de DSC para um módulo de manutenção geral do servidor.</span><span class="sxs-lookup"><span data-stu-id="3f08b-144">Below is a sample DSC configuration for a general server maintenance module.</span></span>

<span data-ttu-id="3f08b-145">Ele assume que um módulo válido do PowerShell contendo recursos de função em uma subpasta 'RoleCapabilities' está localizado no compartilhamento de arquivos '\\\\myfileshare\\JEA'.</span><span class="sxs-lookup"><span data-stu-id="3f08b-145">It assumes that a valid PowerShell module containing role capabilities in a 'RoleCapabilities' subfolder is located on the '\\\\myfileshare\\JEA' file share.</span></span>


```powershell
Configuration JEAMaintenance
{
    Import-DscResource -Module JustEnoughAdministration, PSDesiredStateConfiguration

    File MaintenanceModule
    {
        SourcePath = "\\myfileshare\JEA\ContosoMaintenance"
        DestinationPath = "C:\Program Files\WindowsPowerShell\Modules\ContosoMaintenance"
        Checksum = "SHA-256"
        Ensure = "Present"
        Type = "Directory"
        Recurse = $true
    }

    JeaEndpoint JEAMaintenanceEndpoint
    {
        EndpointName = "JEAMaintenance"
        RoleDefinitions = "@{ 'CONTOSO\JEAMaintenanceAuditors' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit' }; 'CONTOSO\JEAMaintenanceAdmins' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit', 'GeneralServerMaintenance-Admin' } }"
        TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
        DependsOn = '[File]MaintenanceModule'
    }
}
```

<span data-ttu-id="3f08b-146">Essa configuração pode ser aplicada em um sistema [invocando diretamente o Gerenciador de Configurações Local](https://msdn.microsoft.com/powershell/dsc/metaconfig) ou atualizando a [configuração do servidor de pull](https://msdn.microsoft.com/powershell/dsc/pullserver).</span><span class="sxs-lookup"><span data-stu-id="3f08b-146">This configuration can then be applied on a system by [directly invoking the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig) or updating the [pull server configuration](https://msdn.microsoft.com/powershell/dsc/pullserver).</span></span>

<span data-ttu-id="3f08b-147">O recurso DSC também permite que você substitua o ponto de extremidade de comunicação remota padrão Microsoft.PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3f08b-147">The DSC resource also allows you to replace the default Microsoft.PowerShell remoting endpoint.</span></span>
<span data-ttu-id="3f08b-148">Se você fizer isso, o recurso registrará automaticamente um ponto de extremidade irrestrito de backup chamado "Microsoft.PowerShell.Restricted", que tem a ACL do WinRM padrão (permitindo que Usuários de Gerenciamento Remoto e membros do grupo local de Administradores o acessem).</span><span class="sxs-lookup"><span data-stu-id="3f08b-148">If you do this, the resource will automatically register a backup unconstrainted endpoint named "Microsoft.PowerShell.Restricted" which has the default WinRM ACL (allowing Remote Management Users and local Administrators group members to access it).</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="3f08b-149">Cancelando o registro de configurações de JEA</span><span class="sxs-lookup"><span data-stu-id="3f08b-149">Unregistering JEA configurations</span></span>

<span data-ttu-id="3f08b-150">Para remover um ponto de extremidade JEA em um sistema, use o cmdlet [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration).</span><span class="sxs-lookup"><span data-stu-id="3f08b-150">To remove a JEA endpoint on a system, use the [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.</span></span>
<span data-ttu-id="3f08b-151">O cancelamento do registro de um ponto de extremidade JEA impedirá que novos usuários criem novas sessões de JEA no sistema.</span><span class="sxs-lookup"><span data-stu-id="3f08b-151">Unregistering a JEA endpoint will prevent new users from creating new JEA sessions on the system.</span></span>
<span data-ttu-id="3f08b-152">Ele também permite que você atualize uma configuração de JEA, registrando novamente um arquivo de configuração de sessão atualizado usando o mesmo nome de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="3f08b-152">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="3f08b-153">O cancelamento do registro de um ponto de extremidade JEA fará com que o serviço WinRM seja reiniciado.</span><span class="sxs-lookup"><span data-stu-id="3f08b-153">Unregistering a JEA endpoint will cause the WinRM service to restart.</span></span>
> <span data-ttu-id="3f08b-154">Isso interromperá a maioria das operações de gerenciamento remotas em andamento, incluindo outras sessões do PowerShell, invocações de WMI e algumas ferramentas de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="3f08b-154">This will interrupt most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span>
> <span data-ttu-id="3f08b-155">Cancele o registro de pontos de extremidade do PowerShell somente durante janelas de manutenção planejadas.</span><span class="sxs-lookup"><span data-stu-id="3f08b-155">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3f08b-156">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="3f08b-156">Next steps</span></span>

- [<span data-ttu-id="3f08b-157">Testar o ponto de extremidade JEA</span><span class="sxs-lookup"><span data-stu-id="3f08b-157">Test the JEA endpoint</span></span>](using-jea.md)