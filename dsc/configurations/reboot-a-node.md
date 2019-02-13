---
ms.date: 1/17/2019
keywords: DSC,powershell,configuração,instalação
title: Reiniciar um nó
ms.openlocfilehash: 33ecd98aa62c3dc94a8ff2213fd3e68bf0c05cb7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675787"
---
# <a name="reboot-a-node"></a><span data-ttu-id="def44-103">Reiniciar um nó</span><span class="sxs-lookup"><span data-stu-id="def44-103">Reboot a Node</span></span>

> [!NOTE]
> <span data-ttu-id="def44-104">Este tópico fala sobre como reiniciar um nó.</span><span class="sxs-lookup"><span data-stu-id="def44-104">This topic talks about how to reboot a Node.</span></span> <span data-ttu-id="def44-105">Para que a reinicialização seja executada com êxito a **ActionAfterReboot** e **RebootNodeIfNeeded** as configurações de LCM precisam ser configurados corretamente.</span><span class="sxs-lookup"><span data-stu-id="def44-105">In order for the reboot to be successful the **ActionAfterReboot** and **RebootNodeIfNeeded** LCM settings need to be configured properly.</span></span>
> <span data-ttu-id="def44-106">Para ler sobre as configurações do Gerenciador de configurações Local, consulte [configurar o Gerenciador de configurações Local](../managing-nodes/metaConfig.md), ou [configurar o Gerenciador de configurações Local (v4)](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="def44-106">To read about Local Configuration Manager settings, see [Configure the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configure the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>

<span data-ttu-id="def44-107">Nós podem ser reinicializados de dentro de um recurso, usando o `$global:DSCMachineStatus` sinalizador.</span><span class="sxs-lookup"><span data-stu-id="def44-107">Nodes can be rebooted from within a resource, by using the `$global:DSCMachineStatus` flag.</span></span> <span data-ttu-id="def44-108">Defina esse sinalizador como `1` no `Set-TargetResource` função força o LCM para reinicializar o nó diretamente após o **definir** método do recurso atual.</span><span class="sxs-lookup"><span data-stu-id="def44-108">Setting this flag to `1` in the `Set-TargetResource` function forces the LCM to reboot the Node directly after the **Set** method of the current resource.</span></span> <span data-ttu-id="def44-109">Usar este sinalizador, o **xPendingReboot** recurso detecta se uma reinicialização fica pendente fora do DSC.</span><span class="sxs-lookup"><span data-stu-id="def44-109">Using this flag, the **xPendingReboot** resource detects if a reboot is pending outside of DSC.</span></span>

<span data-ttu-id="def44-110">Sua [configurações](configurations.md) pode seguir as etapas que exigem o nó a reinicialização.</span><span class="sxs-lookup"><span data-stu-id="def44-110">Your [configurations](configurations.md) may perform steps that require the Node to reboot.</span></span> <span data-ttu-id="def44-111">Isso pode incluir as coisas, como:</span><span class="sxs-lookup"><span data-stu-id="def44-111">This could include things such as:</span></span>

- <span data-ttu-id="def44-112">Windows: Atualizações</span><span class="sxs-lookup"><span data-stu-id="def44-112">Windows updates</span></span>
- <span data-ttu-id="def44-113">Instalação de software</span><span class="sxs-lookup"><span data-stu-id="def44-113">Software install</span></span>
- <span data-ttu-id="def44-114">Arquivo renomeia</span><span class="sxs-lookup"><span data-stu-id="def44-114">File renames</span></span>
- <span data-ttu-id="def44-115">Renomeação do computador</span><span class="sxs-lookup"><span data-stu-id="def44-115">Computer rename</span></span>

<span data-ttu-id="def44-116">O **xPendingReboot** recurso verifica os locais de computador específico para determinar se uma reinicialização está pendente.</span><span class="sxs-lookup"><span data-stu-id="def44-116">The **xPendingReboot** resource checks specific computer locations to determine if a reboot is pending.</span></span> <span data-ttu-id="def44-117">Se o nó requer uma reinicialização fora do DSC, o **xPendingReboot** conjuntos de recursos a `$global:DSCMachineStatus` sinalizador como `1` forçar uma reinicialização e resolução da condição pendente.</span><span class="sxs-lookup"><span data-stu-id="def44-117">If the Node requires a reboot outside of DSC, the **xPendingReboot** resource sets the `$global:DSCMachineStatus` flag to `1` forcing a reboot and resolving the pending condition.</span></span>

> [!NOTE]
> <span data-ttu-id="def44-118">Qualquer recurso de DSC pode instruir o LCM para reinicializar o nó ao definir esse sinalizador `Set-TargetResource` função.</span><span class="sxs-lookup"><span data-stu-id="def44-118">Any DSC resource can instruct the LCM to reboot the node by setting this flag in the `Set-TargetResource` function.</span></span> <span data-ttu-id="def44-119">Para obter mais informações, consulte [escrevendo um recurso personalizado de DSC com MOF](../resources/authoringResourceMOF.md).</span><span class="sxs-lookup"><span data-stu-id="def44-119">For more information, see [Writing a custom DSC resource with MOF](../resources/authoringResourceMOF.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="def44-120">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="def44-120">Syntax</span></span>

```
xPendingReboot [String] #ResourceName
{
    Name = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [SkipCcmClientSDK = [bool]]
    [SkipComponentBasedServicing = [bool]]
    [SkipPendingComputerRename = [bool]]
    [SkipPendingFileRename = [bool]]
    [SkipWindowsUpdate = [bool]]
}
```

## <a name="properties"></a><span data-ttu-id="def44-121">Propriedades</span><span class="sxs-lookup"><span data-stu-id="def44-121">Properties</span></span>

| <span data-ttu-id="def44-122">Propriedade</span><span class="sxs-lookup"><span data-stu-id="def44-122">Property</span></span> | <span data-ttu-id="def44-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="def44-123">Description</span></span> |
| --- | --- |
| <span data-ttu-id="def44-124">Nome</span><span class="sxs-lookup"><span data-stu-id="def44-124">Name</span></span>| <span data-ttu-id="def44-125">Parâmetro obrigatório que deve ser exclusivo por instância do recurso dentro de uma configuração.</span><span class="sxs-lookup"><span data-stu-id="def44-125">Required parameter that must be unique per instance of the resource within a configuration.</span></span>|
| <span data-ttu-id="def44-126">SkipComponentBasedServicing</span><span class="sxs-lookup"><span data-stu-id="def44-126">SkipComponentBasedServicing</span></span> | <span data-ttu-id="def44-127">Reinicializações de ignorar disparadas pelo componente de serviço baseado em componente.</span><span class="sxs-lookup"><span data-stu-id="def44-127">Skip reboots triggered by the Component-Based Servicing component.</span></span> |
| <span data-ttu-id="def44-128">SkipWindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="def44-128">SkipWindowsUpdate</span></span> | <span data-ttu-id="def44-129">Reinicializações de ignorar disparadas pelo Windows Update.</span><span class="sxs-lookup"><span data-stu-id="def44-129">Skip reboots triggered by Windows Update.</span></span>|
| <span data-ttu-id="def44-130">SkipPendingFileRename</span><span class="sxs-lookup"><span data-stu-id="def44-130">SkipPendingFileRename</span></span> | <span data-ttu-id="def44-131">Ignore as reinicializações de renomeação de arquivo pendente.</span><span class="sxs-lookup"><span data-stu-id="def44-131">Skip pending file rename reboots.</span></span> |
| <span data-ttu-id="def44-132">SkipCcmClientSDK</span><span class="sxs-lookup"><span data-stu-id="def44-132">SkipCcmClientSDK</span></span> | <span data-ttu-id="def44-133">Reinicializações de ignorar disparadas pelo cliente do ConfigMgr.</span><span class="sxs-lookup"><span data-stu-id="def44-133">Skip reboots triggered by the ConfigMgr client.</span></span> |
| <span data-ttu-id="def44-134">SkipComputerRename</span><span class="sxs-lookup"><span data-stu-id="def44-134">SkipComputerRename</span></span> | <span data-ttu-id="def44-135">Ignorar reinicializações disparada por renomeações de computador.</span><span class="sxs-lookup"><span data-stu-id="def44-135">Skip reboots triggerd by Computer renames.</span></span> |
| <span data-ttu-id="def44-136">PSDSCRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="def44-136">PSDSCRunAsCredential</span></span> | <span data-ttu-id="def44-137">Suporte para v5.</span><span class="sxs-lookup"><span data-stu-id="def44-137">Supported in v5.</span></span> <span data-ttu-id="def44-138">Executa o recurso como o usuário especificado.</span><span class="sxs-lookup"><span data-stu-id="def44-138">Executes the resource as the specified user.</span></span> |
| <span data-ttu-id="def44-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="def44-139">DependsOn</span></span> | <span data-ttu-id="def44-140">Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado.</span><span class="sxs-lookup"><span data-stu-id="def44-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="def44-141">Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="def44-141">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="def44-142">Para obter mais informações, consulte [usando DependsOn](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="def44-142">For more information, see [Using DependsOn](resource-depends-on.md)</span></span>|

## <a name="example"></a><span data-ttu-id="def44-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="def44-143">Example</span></span>

<span data-ttu-id="def44-144">O exemplo a seguir instala o Microsoft Exchange usando o [xExchange](https://github.com/PowerShell/xExchange) recursos.</span><span class="sxs-lookup"><span data-stu-id="def44-144">The following example installs Microsoft Exchange using the [xExchange](https://github.com/PowerShell/xExchange) resource.</span></span>
<span data-ttu-id="def44-145">Durante a instalação, o **xPendingReboot** recurso é usado para reinicializar o nó.</span><span class="sxs-lookup"><span data-stu-id="def44-145">Throughout the install, the **xPendingReboot** resource is used to reboot the Node.</span></span>

> [!NOTE]
> <span data-ttu-id="def44-146">Esse exemplo requer a credencial de uma conta que tenha direitos para adicionar um servidor do Exchange na floresta.</span><span class="sxs-lookup"><span data-stu-id="def44-146">This example requires the credential of an account that has rights to add an Exchange server to the forest.</span></span> <span data-ttu-id="def44-147">Para obter mais informações sobre como usar as credenciais na DSC, consulte [tratamento de credenciais na DSC](../configurations/configDataCredentials.md)</span><span class="sxs-lookup"><span data-stu-id="def44-147">For more information on using credentials in DSC, see [Handling Credentials in DSC](../configurations/configDataCredentials.md)</span></span>

```powershell
$ConfigurationData = @{
    AllNodes = @(
        @{
            NodeName                    = '*'
            PSDSCAllowPlainTextPassword = $true
        },
        @{
            NodeName = 'DSCPULL-1'
        }
    )
}

Configuration Example
{
    param
    (
        [Parameter(Mandatory = $true)]
        [System.Management.Automation.PSCredential]
        $ExchangeAdminCredential
    )

    Import-DscResource -Module xExchange
    Import-DscResource -Module xPendingReboot

    Node $AllNodes.NodeName
    {
        # Copy the Exchange setup files locally
        File ExchangeBinaries
        {
            Ensure          = 'Present'
            Type            = 'Directory'
            Recurse         = $true
            SourcePath      = '\\rras-1\Binaries\E15CU6'
            DestinationPath = 'C:\Binaries\E15CU6'
        }

        # Check if a reboot is needed before installing Exchange
        xPendingReboot BeforeExchangeInstall
        {
            Name       = 'BeforeExchangeInstall'
            DependsOn  = '[File]ExchangeBinaries'
        }

        # Do the Exchange install
        xExchInstall InstallExchange
        {
            Path       = 'C:\Binaries\E15CU6\Setup.exe'
            Arguments  = '/mode:Install /role:Mailbox /Iacceptexchangeserverlicenseterms'
            Credential = $ExchangeAdminCredential
            DependsOn  = '[xPendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        xPendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="def44-148">Este exemplo pressupõe que você tenha configurado o Gerenciador de configurações Local para permitir reinicializações e continuar a configuração após uma reinicialização.</span><span class="sxs-lookup"><span data-stu-id="def44-148">This example assumes that you have configured your Local Configuration Manager to allow reboots and continue the configuration after a reboot.</span></span>

## <a name="where-to-download"></a><span data-ttu-id="def44-149">Onde fazer Download</span><span class="sxs-lookup"><span data-stu-id="def44-149">Where to Download</span></span>

<span data-ttu-id="def44-150">Você pode baixar os recursos usados neste tópico, nos seguintes locais, ou usando a Galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="def44-150">You can download the resources used in this topic at the following locations, or by using the PowerShell gallery.</span></span>

- [<span data-ttu-id="def44-151">xPendingReboot</span><span class="sxs-lookup"><span data-stu-id="def44-151">xPendingReboot</span></span>](https://github.com/PowerShell/xPendingReboot)
- [<span data-ttu-id="def44-152">xExchange</span><span class="sxs-lookup"><span data-stu-id="def44-152">xExchange</span></span>](https://github.com/PowerShell/xExchange)
