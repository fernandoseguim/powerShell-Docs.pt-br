---
ms.date: 06/12/2017
keywords: jea,powershell,segurança
title: Configurações de Sessão de JEA
ms.openlocfilehash: bdf3659357045203d90e8083613e51cce657da1a
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522938"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="306d7-103">Configurações de Sessão de JEA</span><span class="sxs-lookup"><span data-stu-id="306d7-103">JEA Session Configurations</span></span>

> <span data-ttu-id="306d7-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="306d7-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="306d7-105">Um ponto de extremidade JEA é registrado em um sistema através da criação e registro de um arquivo de configuração de sessão do PowerShell de uma maneira específica.</span><span class="sxs-lookup"><span data-stu-id="306d7-105">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file in a specific way.</span></span>
<span data-ttu-id="306d7-106">As configurações de sessão determinam *quem* pode usar o ponto de extremidade JEA e a quais funções eles terão acesso.</span><span class="sxs-lookup"><span data-stu-id="306d7-106">Session configurations determine *who* can use the JEA endpoint, and which role(s) they will have access to.</span></span>
<span data-ttu-id="306d7-107">Elas também definem configurações globais que se aplicam aos usuários de qualquer função na sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="306d7-107">They also define global settings that apply to users of any role in the JEA session.</span></span>

<span data-ttu-id="306d7-108">Este tópico descreve como criar um arquivo de configuração de sessão do PowerShell e registrar um ponto de extremidade JEA.</span><span class="sxs-lookup"><span data-stu-id="306d7-108">This topic describes how to create a PowerShell session configuration file and register a JEA endpoint.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="306d7-109">Criar um arquivo de configuração de sessão</span><span class="sxs-lookup"><span data-stu-id="306d7-109">Create a session configuration file</span></span>

<span data-ttu-id="306d7-110">Para registrar um ponto de extremidade JEA, você precisa especificar como esse ponto de extremidade deve ser configurado.</span><span class="sxs-lookup"><span data-stu-id="306d7-110">In order to register a JEA endpoint, you need to specify how that endpoint should be configured.</span></span>
<span data-ttu-id="306d7-111">Há muitas opções a serem considerados aqui e as mais importantes delas são: quem devem ter acesso ao ponto de extremidade JEA, quais funções serão atribuídas a eles, qual identidade será usada pelo JEA nos bastidores e qual será o nome do ponto de extremidade JEA.</span><span class="sxs-lookup"><span data-stu-id="306d7-111">There are many options to consider here, the most important of which being who should have access to the JEA endpoint, which roles will they be assigned, which identity will JEA use under the covers, and what will be the name of the JEA endpoint.</span></span>
<span data-ttu-id="306d7-112">Todas essas opções são definidas em um arquivo de configuração de sessão do PowerShell, que é um arquivo de dados do PowerShell que termina com uma extensão .pssc.</span><span class="sxs-lookup"><span data-stu-id="306d7-112">These are all defined in a PowerShell session configuration file, which is a PowerShell data file ending with a .pssc extension.</span></span>

<span data-ttu-id="306d7-113">Para criar um arquivo de configuração esqueleto de sessão para pontos de extremidade JEA, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="306d7-113">To create a skeleton session configuration file for JEA endpoints, run the following command.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="306d7-114">Apenas as opções de configuração mais comuns são incluídas no arquivo esqueleto por padrão.</span><span class="sxs-lookup"><span data-stu-id="306d7-114">Only the most common configuration options are included in the skeleton file by default.</span></span>
> <span data-ttu-id="306d7-115">Use a opção `-Full` para incluir todas as configurações aplicáveis no PSSC gerado.</span><span class="sxs-lookup"><span data-stu-id="306d7-115">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="306d7-116">Você pode abrir o arquivo de configuração de sessão em qualquer editor de texto.</span><span class="sxs-lookup"><span data-stu-id="306d7-116">You can open the session configuration file in any text editor.</span></span>
<span data-ttu-id="306d7-117">O campo `-SessionType RestrictedRemoteServer` indica que a configuração da sessão será usada pelo JEA para gerenciamento seguro.</span><span class="sxs-lookup"><span data-stu-id="306d7-117">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration will be used by JEA for secure management.</span></span>
<span data-ttu-id="306d7-118">As sessões configuradas dessa forma funcionarão no [modo NoLanguage](https://technet.microsoft.com/library/dn433292.aspx) e só terão estes oito comandos (e aliases) padrão disponíveis:</span><span class="sxs-lookup"><span data-stu-id="306d7-118">Sessions configured this way will operate in [NoLanguage mode](https://technet.microsoft.com/library/dn433292.aspx) and only have the following 8 default commands (and aliases) available:</span></span>

- <span data-ttu-id="306d7-119">Clear-Host (cls, limpar)</span><span class="sxs-lookup"><span data-stu-id="306d7-119">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="306d7-120">Exit-PSSession (exsn, sair)</span><span class="sxs-lookup"><span data-stu-id="306d7-120">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="306d7-121">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="306d7-121">Get-Command (gcm)</span></span>
- <span data-ttu-id="306d7-122">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="306d7-122">Get-FormatData</span></span>
- <span data-ttu-id="306d7-123">Get-Help</span><span class="sxs-lookup"><span data-stu-id="306d7-123">Get-Help</span></span>
- <span data-ttu-id="306d7-124">Measure-Object (medida)</span><span class="sxs-lookup"><span data-stu-id="306d7-124">Measure-Object (measure)</span></span>
- <span data-ttu-id="306d7-125">Out-Default</span><span class="sxs-lookup"><span data-stu-id="306d7-125">Out-Default</span></span>
- <span data-ttu-id="306d7-126">Select-Object (selecionar)</span><span class="sxs-lookup"><span data-stu-id="306d7-126">Select-Object (select)</span></span>

<span data-ttu-id="306d7-127">Não estão disponíveis provedores de PowerShell, nem programas externos (executáveis, scripts, etc).</span><span class="sxs-lookup"><span data-stu-id="306d7-127">No PowerShell providers are available, nor are any external programs (executables, scripts, etc.).</span></span>

<span data-ttu-id="306d7-128">Há vários outros campos que você pode configurar para a sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="306d7-128">There are several other fields you will want to configure for the JEA session.</span></span>
<span data-ttu-id="306d7-129">Eles são abordados nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="306d7-129">They are covered in the following sections.</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="306d7-130">Escolha a identidade JEA</span><span class="sxs-lookup"><span data-stu-id="306d7-130">Choose the JEA identity</span></span>

<span data-ttu-id="306d7-131">Nos bastidores, o JEA precisa de uma identidade (conta) para usar ao executar os comandos do usuário conectado.</span><span class="sxs-lookup"><span data-stu-id="306d7-131">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="306d7-132">Você pode decidir qual identidade JEA será usada no arquivo de configuração de sessão.</span><span class="sxs-lookup"><span data-stu-id="306d7-132">You decide which identity JEA will use in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="306d7-133">Conta Virtual Local</span><span class="sxs-lookup"><span data-stu-id="306d7-133">Local Virtual Account</span></span>

<span data-ttu-id="306d7-134">Se as funções com suporte nesse ponto de extremidade JEA são usadas para gerenciar o computador local e uma conta de administrador local for suficiente para executar os comandos com êxito, você deverá configurar o JEA para usar uma conta virtual local.</span><span class="sxs-lookup"><span data-stu-id="306d7-134">If the roles supported by this JEA endpoint are all used to manage the local machine, and a local administrator account is sufficient to run the commands succesfully, you should configure JEA to use a local virtual account.</span></span>
<span data-ttu-id="306d7-135">As contas virtuais são contas temporárias exclusivas para um usuário específico e permanecem ativas apenas durante a sessão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="306d7-135">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span>
<span data-ttu-id="306d7-136">Em um servidor membro ou estação de trabalho, as contas virtuais pertencem ao grupo de **Administradores** do computador local e têm acesso à maioria dos recursos do sistema.</span><span class="sxs-lookup"><span data-stu-id="306d7-136">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group, and have access to most system resources.</span></span>
<span data-ttu-id="306d7-137">Em um Controlador de Domínio do Active Directory, as contas virtuais pertencem ao grupo **Administradores do domínio** do domínio.</span><span class="sxs-lookup"><span data-stu-id="306d7-137">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="306d7-138">Se as funções com suporte pela configuração de sessão não exigem esses privilégios amplos, você pode, opcionalmente, especificar os grupos de segurança aos quais a conta virtual pertencerá.</span><span class="sxs-lookup"><span data-stu-id="306d7-138">If the roles supported by the session configuration do not require such broad privileges, you can optionally specify the security groups to which the virtual account will belong.</span></span>
<span data-ttu-id="306d7-139">Em um servidor membro ou estação de trabalho, os grupos de segurança especificados devem ser grupos locais e não grupos de um domínio.</span><span class="sxs-lookup"><span data-stu-id="306d7-139">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="306d7-140">Quando um ou mais grupos de segurança forem especificados, a conta virtual não pertencerá mais ao grupo local de administradores local ou grupo de administradores de domínio.</span><span class="sxs-lookup"><span data-stu-id="306d7-140">When one or more security groups is specified, the virtual account will no longer belong to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

#### <a name="group-managed-service-account"></a><span data-ttu-id="306d7-141">Conta de Serviço Gerenciado de Grupo</span><span class="sxs-lookup"><span data-stu-id="306d7-141">Group Managed Service Account</span></span>


<span data-ttu-id="306d7-142">Para cenários que exigem que o usuário JEA acesse recursos de rede, como outros computadores ou serviços Web, uma gMSA (conta de serviço gerenciado de grupo) é uma identidade mais apropriada a ser usada.</span><span class="sxs-lookup"><span data-stu-id="306d7-142">For scenarios requiring the JEA user to access network resources such as other machines or web services, a group managed service account (gMSA) is a more appropriate identity to use.</span></span>
<span data-ttu-id="306d7-143">As contas gMSA fornecem uma identidade de domínio que pode ser usada para autenticar para recursos em qualquer computador no domínio.</span><span class="sxs-lookup"><span data-stu-id="306d7-143">gMSA accounts give you a domain identity which can be used to authenticate against resources on any machine within the domain.</span></span>
<span data-ttu-id="306d7-144">Os direitos concedidos pela conta gMSA são determinados pelos recursos que você está acessando.</span><span class="sxs-lookup"><span data-stu-id="306d7-144">The rights the gMSA account gives you is determined by the resources you are accessing.</span></span>
<span data-ttu-id="306d7-145">Você não terá automaticamente direitos de administrador em todos os computadores ou serviços, a menos que o administrador de computador/serviços tenha explicitamente concedido privilégios de administrador à conta gMSA.</span><span class="sxs-lookup"><span data-stu-id="306d7-145">You will not automatically have admin rights on any machines or services unless the machine/service administrator has explicitly granted the gMSA account admin privileges.</span></span>

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

<span data-ttu-id="306d7-146">As contas gMSA só devem ser usadas quando for necessário o acesso aos recursos de rede por alguns motivos:</span><span class="sxs-lookup"><span data-stu-id="306d7-146">gMSA accounts should only be used when access to network resources are required for a few reasons:</span></span>

- <span data-ttu-id="306d7-147">É mais difícil rastrear ações de um usuário ao usar uma conta gMSA, pois cada usuário compartilha a mesma identidade Run As.</span><span class="sxs-lookup"><span data-stu-id="306d7-147">It is harder to trace back actions to a user when using a gMSA account since every user shares the same run-as identity.</span></span> <span data-ttu-id="306d7-148">Você precisará consultar transcrições e logs de sessão do PowerShell para correlacionar os usuários e suas ações.</span><span class="sxs-lookup"><span data-stu-id="306d7-148">You will need to consult PowerShell session transcripts and logs to correlate users with their actions.</span></span>

- <span data-ttu-id="306d7-149">A conta gMSA pode ter acesso a vários recursos de rede que o usuário conectado não necessita acessar.</span><span class="sxs-lookup"><span data-stu-id="306d7-149">The gMSA account may have access to many network resources which the connecting user does not need access to.</span></span> <span data-ttu-id="306d7-150">Sempre tente limitar as permissões efetivas em uma sessão JEA para seguir o princípio de privilégio mínimo.</span><span class="sxs-lookup"><span data-stu-id="306d7-150">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="306d7-151">As contas de serviço gerenciado de grupo estão disponíveis apenas no Windows PowerShell 5.1 ou mais recente e em computadores que ingressaram no domínio.</span><span class="sxs-lookup"><span data-stu-id="306d7-151">Group managed service accounts are only available in Windows PowerShell 5.1 or newer and on domain-joined machines.</span></span>


#### <a name="more-information-about-run-as-users"></a><span data-ttu-id="306d7-152">Mais informações sobre usuários Run As</span><span class="sxs-lookup"><span data-stu-id="306d7-152">More information about run as users</span></span>

<span data-ttu-id="306d7-153">Informações adicionais sobre identidades Run As e como elas influenciam na segurança de uma sessão JEA podem ser encontradas no artigo [considerações de segurança](security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="306d7-153">Additional information about run as identities and how they factor into the security of a JEA session can be found in the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="306d7-154">Transcrições de sessão</span><span class="sxs-lookup"><span data-stu-id="306d7-154">Session transcripts</span></span>

<span data-ttu-id="306d7-155">É recomendável configurar um arquivo de configuração de sessão JEA para registrar automaticamente as transcrições de sessões de usuários.</span><span class="sxs-lookup"><span data-stu-id="306d7-155">It is recommended that you configure a JEA session configuration file to automatically record transcripts of users' sessions.</span></span>
<span data-ttu-id="306d7-156">As transcrições de sessão do PowerShell contêm informações sobre o usuário conectado, a identidade Run As atribuída a ele e os comandos executados pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="306d7-156">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span>
<span data-ttu-id="306d7-157">Elas podem ser úteis para uma equipe de auditoria que precisa entender quem executou uma alteração específica em um sistema.</span><span class="sxs-lookup"><span data-stu-id="306d7-157">They can be useful to an auditing team who needs to understand who performed a specific change to a system.</span></span>

<span data-ttu-id="306d7-158">Para configurar a transcrição automática no arquivo de configuração de sessão, forneça um caminho para uma pasta em que as transcrições devem ser armazenadas.</span><span class="sxs-lookup"><span data-stu-id="306d7-158">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="306d7-159">A pasta especificada deve ser configurada para impedir que os usuários modifiquem ou excluam qualquer dado nela.</span><span class="sxs-lookup"><span data-stu-id="306d7-159">The specified folder should be configured to prevent users from modifying or deleting any data in it.</span></span>
<span data-ttu-id="306d7-160">As transcrições são gravadas na pasta pela conta Sistema Local, que requer acesso de leitura e gravação no diretório.</span><span class="sxs-lookup"><span data-stu-id="306d7-160">Transcripts are written to the folder by the Local System account, which requires read and write access to the directory.</span></span>
<span data-ttu-id="306d7-161">Os usuários padrão não devem ter nenhum acesso à pasta e um conjunto limitado de administradores de segurança deve ter acesso para auditar as transcrições.</span><span class="sxs-lookup"><span data-stu-id="306d7-161">Standard users should have no access to the folder, and a limited set of security administrators should have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="306d7-162">Unidade de usuário</span><span class="sxs-lookup"><span data-stu-id="306d7-162">User drive</span></span>

<span data-ttu-id="306d7-163">Se os usuários que estão se conectando precisarem copiar arquivos do ou para o ponto de extremidade JEA para executar um comando, você poderá habilitar a unidade do usuário no arquivo de configuração de sessão.</span><span class="sxs-lookup"><span data-stu-id="306d7-163">If your connecting users will need to copy files to/from the JEA endpoint in order to run a command, you can enable the user drive in the session configuration file.</span></span>
<span data-ttu-id="306d7-164">A unidade de usuário é um [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) que é mapeada para uma pasta exclusiva para cada usuário que está se conectando.</span><span class="sxs-lookup"><span data-stu-id="306d7-164">The user drive is a [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) that is mapped to a unique folder for each connecting user.</span></span>
<span data-ttu-id="306d7-165">Essa pasta serve como um espaço para que eles possam copiar arquivos do sistema ou para o sistema, sem fornecer acesso ao sistema de arquivos completo ou expor o provedor FileSystem.</span><span class="sxs-lookup"><span data-stu-id="306d7-165">This folder serves as a space for them to copy files to/from the system, without giving them access to the full file system or exposing the FileSystem provider.</span></span>
<span data-ttu-id="306d7-166">Os conteúdos da unidade de usuário são persistentes entre as sessões para se adaptar a situações em que a conectividade de rede pode ser interrompida.</span><span class="sxs-lookup"><span data-stu-id="306d7-166">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="306d7-167">Por padrão, a unidade de usuário permite que seja armazenado um máximo de 50 MB de dados por usuário.</span><span class="sxs-lookup"><span data-stu-id="306d7-167">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span>
<span data-ttu-id="306d7-168">Você pode limitar a quantidade de dados que um usuário pode consumir com o campo *UserDriveMaximumSize*.</span><span class="sxs-lookup"><span data-stu-id="306d7-168">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="306d7-169">Se quiser que os dados na unidade de usuário não sejam persistentes, você poderá configurar uma tarefa agendada no sistema para limpar automaticamente a pasta toda noite.</span><span class="sxs-lookup"><span data-stu-id="306d7-169">If you do not want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="306d7-170">A unidade de usuário só está disponível no Windows PowerShell 5.1 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="306d7-170">The user drive is only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="role-definitions"></a><span data-ttu-id="306d7-171">Definições de função</span><span class="sxs-lookup"><span data-stu-id="306d7-171">Role definitions</span></span>

<span data-ttu-id="306d7-172">As definições de função em um arquivo de configuração de sessão definem o mapeamento de *usuários* para as *funções*.</span><span class="sxs-lookup"><span data-stu-id="306d7-172">Role definitions in a session configuration file define the mapping of *users* to *roles*.</span></span>
<span data-ttu-id="306d7-173">Cada usuário ou grupo incluído nesse campo automaticamente receberá permissão para o ponto de extremidade JEA quando ele for registrado.</span><span class="sxs-lookup"><span data-stu-id="306d7-173">Every user or group included in this field will automatically be granted permission to the JEA endpoint when it is registered.</span></span>
<span data-ttu-id="306d7-174">Cada usuário ou grupo pode ser incluído como uma chave na tabela de hash somente uma vez, mas pode ser atribuído a várias funções.</span><span class="sxs-lookup"><span data-stu-id="306d7-174">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span>
<span data-ttu-id="306d7-175">O nome da capacidade de função deve ser o nome do arquivo de capacidade de função, sem a extensão .psrc.</span><span class="sxs-lookup"><span data-stu-id="306d7-175">The name of the role capability should be the name of the role capability file, without the .psrc extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="306d7-176">Se um usuário pertencer a mais de um grupo na definição de função, ele receberá acesso às funções de cada grupo.</span><span class="sxs-lookup"><span data-stu-id="306d7-176">If a user belongs to more than one group in the role definition, they will get access to the roles of each.</span></span>
<span data-ttu-id="306d7-177">Se duas funções de concedem acesso aos mesmos cmdlets, o conjunto de parâmetros mais permissivo será concedido ao usuário.</span><span class="sxs-lookup"><span data-stu-id="306d7-177">If two roles grant access to the same cmdlets, the most permissive parameter set will be granted to the user.</span></span>

<span data-ttu-id="306d7-178">Ao especificar usuários ou grupos locais no campo de definições de função, use o nome do computador (não *localhost* ou *.*) antes da barra invertida.</span><span class="sxs-lookup"><span data-stu-id="306d7-178">When specifying local users or groups in the role definitions field, be sure to use the computer name (not *localhost* or *.*) before the backslash.</span></span>
<span data-ttu-id="306d7-179">Você pode verificar o nome do computador inspecionando a variável `$env:computername`.</span><span class="sxs-lookup"><span data-stu-id="306d7-179">You can check the computer name by inspecting the `$env:computername` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="306d7-180">Ordem de pesquisa de capacidade de função</span><span class="sxs-lookup"><span data-stu-id="306d7-180">Role capability search order</span></span>
<span data-ttu-id="306d7-181">Conforme mostrado no exemplo acima, os recursos de função são referenciados pelo nome simples (nome sem a extensão) do arquivo de capacidade de função.</span><span class="sxs-lookup"><span data-stu-id="306d7-181">As shown in the example above, role capabilities are referenced by the flat name (filename without the extension) of the role capability file.</span></span>
<span data-ttu-id="306d7-182">Se vários recursos de função estão disponíveis no sistema com o mesmo nome simples, o PowerShell usará sua ordem de pesquisa implícita para selecionar o arquivo de capacidade de função efetivo.</span><span class="sxs-lookup"><span data-stu-id="306d7-182">If multiple role capabilities are available on the system with the same flat name, PowerShell will use its implicit search order to select the effective role capability file.</span></span>
<span data-ttu-id="306d7-183">Ele **não** dará acesso a todos os arquivos de capacidade de função com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="306d7-183">It will **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="306d7-184">A JEA usa a variável de ambiente do `$env:PSModulePath` para determinar quais caminhos verificar para os arquivos de capacidade da função.</span><span class="sxs-lookup"><span data-stu-id="306d7-184">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span>
<span data-ttu-id="306d7-185">Em cada um desses caminhos, a JEA procurará módulos válidos do PowerShell que contenham uma subpasta "RoleCapabilities".</span><span class="sxs-lookup"><span data-stu-id="306d7-185">Within each of those paths, JEA will look for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span>
<span data-ttu-id="306d7-186">Como com a importação de módulos, a JEA prefere as capacidades de função que são fornecidas com o Windows para capacidades de função personalizadas com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="306d7-186">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>
<span data-ttu-id="306d7-187">Para todos os outros conflitos de nomenclatura, a precedência é determinada pela ordem na qual o Windows enumera os arquivos no diretório (não é garantido que seja em ordem alfabética).</span><span class="sxs-lookup"><span data-stu-id="306d7-187">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory (not guaranteed to be alphabetically).</span></span>
<span data-ttu-id="306d7-188">O primeiro arquivo de capacidade de função encontrado que corresponder ao nome será usado para o usuário que está se conectando.</span><span class="sxs-lookup"><span data-stu-id="306d7-188">The first role capability file found that matches the desired name will be used for the connecting user.</span></span>

<span data-ttu-id="306d7-189">Como a ordem de pesquisa de capacidade de função não é determinista quando duas ou mais capacidades de função compartilham o mesmo nome, é **altamente recomendável** garantir que as capacidades de função tenham nomes exclusivos em seu computador.</span><span class="sxs-lookup"><span data-stu-id="306d7-189">Since the role capability search order is not deterministic when two or more role capabilities share the same name, it is **strongly recommended** that you ensure role capabilities have unique names on your machine.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="306d7-190">Regras de acesso condicional</span><span class="sxs-lookup"><span data-stu-id="306d7-190">Conditional access rules</span></span>

<span data-ttu-id="306d7-191">Todos os usuários e grupos incluídos no campo RoleDefinitions recebem automaticamente acesso a pontos de extremidade JEA.</span><span class="sxs-lookup"><span data-stu-id="306d7-191">All users and groups included in the RoleDefinitions field are automatically granted access to JEA endpoints.</span></span>
<span data-ttu-id="306d7-192">As regras de acesso condicional permitem que você refine esse acesso e exigem que os usuários façam parte de grupos de segurança adicionais, o que não afeta as funções atribuídas a eles.</span><span class="sxs-lookup"><span data-stu-id="306d7-192">Conditional access rules allow you to refine this access and require users to belong to additional security groups which do not impact the roles which they are assigned.</span></span>
<span data-ttu-id="306d7-193">Isso pode ser útil se você deseja integrar uma solução de gerenciamento de acesso privilegiado "just-in-time", uma autenticação de cartão inteligente ou outra solução de autenticação multifator com o JEA.</span><span class="sxs-lookup"><span data-stu-id="306d7-193">This can be useful if you want to integrate a "just in time" privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="306d7-194">As regras de acesso condicional são definidas no campo RequiredGroups em um arquivo de configuração de sessão.</span><span class="sxs-lookup"><span data-stu-id="306d7-194">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="306d7-195">Lá, você pode fornecer uma tabela de hash (opcionalmente aninhada) que usa chaves 'E' e 'Ou' para construir suas regras.</span><span class="sxs-lookup"><span data-stu-id="306d7-195">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span>
<span data-ttu-id="306d7-196">Aqui estão alguns exemplos de como utilizar esse campo:</span><span class="sxs-lookup"><span data-stu-id="306d7-196">Here are some examples of how to leverage this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

> [!NOTE]
> <span data-ttu-id="306d7-197">As regras de acesso condicional só estão disponíveis no Windows PowerShell 5.1 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="306d7-197">Conditional access rules are only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="306d7-198">Outras propriedades</span><span class="sxs-lookup"><span data-stu-id="306d7-198">Other properties</span></span>
<span data-ttu-id="306d7-199">Os arquivos de configuração de sessão também podem fazer tudo o que um arquivo de recurso de função pode fazer, mas sem a capacidade de fornecer aos usuários que estão se conectando o acesso a comandos diferentes.</span><span class="sxs-lookup"><span data-stu-id="306d7-199">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span>
<span data-ttu-id="306d7-200">Se quiser permitir que todos os usuários acessem provedores, funções ou cmdlets específicos, você poderá fazer isso diretamente no arquivo de configuração de sessão.</span><span class="sxs-lookup"><span data-stu-id="306d7-200">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="306d7-201">Para obter uma lista completa das propriedades com suporte no arquivo de configuração de sessão, execute `Get-Help New-PSSessionConfigurationFile -Full`.</span><span class="sxs-lookup"><span data-stu-id="306d7-201">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="306d7-202">Testando um arquivo de configuração de sessão</span><span class="sxs-lookup"><span data-stu-id="306d7-202">Testing a session configuration file</span></span>

<span data-ttu-id="306d7-203">Você pode testar uma configuração de sessão usando o cmdlet [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile).</span><span class="sxs-lookup"><span data-stu-id="306d7-203">You can test a session configuration using the [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span>
<span data-ttu-id="306d7-204">É altamente recomendável que você teste o arquivo de configuração de sessão caso tenha editado o arquivo pssc manualmente usando um editor de texto, a fim de garantir que a sintaxe está correta.</span><span class="sxs-lookup"><span data-stu-id="306d7-204">It is strongly recommended that you test your session configuration file if you have edited the pssc file manually using a text editor to ensure the syntax is correct.</span></span>
<span data-ttu-id="306d7-205">Se um arquivo de configuração de sessão não passar nesse teste, não poderá ser registrado com êxito no sistema.</span><span class="sxs-lookup"><span data-stu-id="306d7-205">If a session configuration file does not pass this test, it will not be able to be successfully registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="306d7-206">Arquivo de configuração de sessão de exemplo</span><span class="sxs-lookup"><span data-stu-id="306d7-206">Sample session configuration file</span></span>

<span data-ttu-id="306d7-207">Abaixo há um exemplo completo que mostra como criar e validar uma configuração de sessão para o JEA.</span><span class="sxs-lookup"><span data-stu-id="306d7-207">Below is a complete example showing how to create and validate a session configuration for JEA.</span></span>
<span data-ttu-id="306d7-208">Observe que as definições de função são criadas e armazenadas na variável `$roles` para conveniência e legibilidade.</span><span class="sxs-lookup"><span data-stu-id="306d7-208">Note that the role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span>
<span data-ttu-id="306d7-209">Não é um requisito fazer assim.</span><span class="sxs-lookup"><span data-stu-id="306d7-209">It is not a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="306d7-210">Atualizando arquivos de configuração de sessão</span><span class="sxs-lookup"><span data-stu-id="306d7-210">Updating session configuration files</span></span>

<span data-ttu-id="306d7-211">Se você precisar alterar as propriedades de uma configuração de sessão JEA, incluindo o mapeamento de usuários às funções, você deverá [cancelar o registro](register-jea.md#unregistering-jea-configurations) e [registrar novamente](register-jea.md) a configuração de sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="306d7-211">If you need to change properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations) and [re-register](register-jea.md) the JEA session configuration.</span></span>
<span data-ttu-id="306d7-212">Quando registrar novamente a configuração da sessão JEA, use um arquivo de configuração de sessão do PowerShell atualizado que inclui as alterações desejadas.</span><span class="sxs-lookup"><span data-stu-id="306d7-212">When you re-register the JEA session configuration, use an updated PowerShell session configuration file that includes your desired changes.</span></span>

## <a name="next-steps"></a><span data-ttu-id="306d7-213">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="306d7-213">Next steps</span></span>

- [<span data-ttu-id="306d7-214">Registrar uma configuração de JEA</span><span class="sxs-lookup"><span data-stu-id="306d7-214">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="306d7-215">Funções de autor de JEA</span><span class="sxs-lookup"><span data-stu-id="306d7-215">Author JEA roles</span></span>](role-capabilities.md)