---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,instalação
contributor: ryanpu
title: Aprimoramentos no recurso JEA (Administração Suficiente)
ms.openlocfilehash: 47a58a6fae9f3a41ec527ec1f77ac1c196336669
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="improvements-to-just-enough-administration-jea"></a><span data-ttu-id="0e647-103">Aprimoramentos no recurso JEA (Administração Suficiente)</span><span class="sxs-lookup"><span data-stu-id="0e647-103">Improvements to Just Enough Administration (JEA)</span></span>

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a><span data-ttu-id="0e647-104">Cópia de arquivo restrito de/para pontos de extremidade JEA</span><span class="sxs-lookup"><span data-stu-id="0e647-104">Constrained file copy to/from JEA endpoints</span></span>

<span data-ttu-id="0e647-105">Agora, você pode remotamente copiar arquivos de/para um ponto de extremidade JEA ficar tranquilo que o usuário conectado não poderá copiar *nenhum* arquivo em seu sistema.</span><span class="sxs-lookup"><span data-stu-id="0e647-105">You can now remotely copy files to/from a JEA endpoint and rest assured that the connecting user can't copy just *any* file on your system.</span></span>
<span data-ttu-id="0e647-106">Isso é possível ao configurar seu arquivo PSSC para montar uma unidade de usuário para conectar usuários.</span><span class="sxs-lookup"><span data-stu-id="0e647-106">This is possible by configuring your PSSC file to mount a user drive for connecting users.</span></span>
<span data-ttu-id="0e647-107">A unidade de usuário é um novo PSDrive exclusivo para cada usuário conectado e persiste nas sessões.</span><span class="sxs-lookup"><span data-stu-id="0e647-107">The user drive is a new PSDrive that is unique to each connecting user and persists across sessions.</span></span>
<span data-ttu-id="0e647-108">Quando Copy-Item é usado para copiar arquivos de ou para uma sessão JEA, ele é restrito para permitir apenas acesso à unidade do usuário.</span><span class="sxs-lookup"><span data-stu-id="0e647-108">When Copy-Item is used to copy files to or from a JEA session, it is constrained to only allow access to the user drive.</span></span>
<span data-ttu-id="0e647-109">As tentativas de copiar arquivos para qualquer outro PSDrive falharão.</span><span class="sxs-lookup"><span data-stu-id="0e647-109">Attempts to copy files to any other PSDrive will fail.</span></span>

<span data-ttu-id="0e647-110">Para configurar a unidade de usuário no arquivo de configuração de sessão JEA, use os novos campos a seguir:</span><span class="sxs-lookup"><span data-stu-id="0e647-110">To set up the user drive in your JEA session configuration file, use the following new fields:</span></span>

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

<span data-ttu-id="0e647-111">A pasta que dá suporte à unidade do usuário será criada em `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span><span class="sxs-lookup"><span data-stu-id="0e647-111">The folder backing the user drive will be created at `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span></span>

<span data-ttu-id="0e647-112">Para utilizar a unidade de usuário e copiar arquivos de/para um ponto de extremidade JEA configurado para expor a unidade do usuário, use os parâmetros `-ToSession` e `-FromSession` em Copy-Item.</span><span class="sxs-lookup"><span data-stu-id="0e647-112">To utilize the user drive and copy files to/from a JEA endpoint configured to expose the User drive, use the `-ToSession` and `-FromSession` parameters on Copy-Item.</span></span>

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine. You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

<span data-ttu-id="0e647-113">Em seguida, você pode escrever funções personalizadas para processar os dados armazenados na unidade do usuário e disponibilizar esses para os usuários no arquivo de Capacidade de Função.</span><span class="sxs-lookup"><span data-stu-id="0e647-113">You can then write custom functions to process the data stored in the user drive and make those available to users in your Role Capability file.</span></span>

## <a name="support-for-group-managed-service-accounts"></a><span data-ttu-id="0e647-114">Suporte para Contas de Serviço Gerenciado de Grupo</span><span class="sxs-lookup"><span data-stu-id="0e647-114">Support for Group Managed Service Accounts</span></span>

<span data-ttu-id="0e647-115">Em alguns casos, uma tarefa que um usuário precisa para executar em uma sessão JEA precisará acessar recursos fora do computador local.</span><span class="sxs-lookup"><span data-stu-id="0e647-115">In some cases, a task a user needs to perform in a JEA session may need to access resources beyond the local machine.</span></span>
<span data-ttu-id="0e647-116">Quando uma sessão JEA é configurada para usar uma conta virtual, qualquer tentativa de acessar esses recursos parecem que serão provenientes da identidade do computador local, não da conta virtual ou do usuário conectado.</span><span class="sxs-lookup"><span data-stu-id="0e647-116">When a JEA session is configured to use a virtual account, any attempt to reach such resources will appear to come from the local machine's identity, not the virtual account or connected user.</span></span>
<span data-ttu-id="0e647-117">No TP5, habilitamos o suporte para executar o JEA sob o contexto de uma [Conta de Serviço Gerenciado de Grupo] (https://technet.microsoft.com/en-us/library/jj128431(v=ws.11\).aspx)), tornando muito mais fácil acessar recursos de rede usando uma identidade de domínio.</span><span class="sxs-lookup"><span data-stu-id="0e647-117">In TP5, we have enabled support for running JEA under the context of a [Group Managed Service Account](https://technet.microsoft.com/en-us/library/jj128431(v=ws.11\).aspx), making it much easier to access network resources by using a domain identity.</span></span>

<span data-ttu-id="0e647-118">Para configurar uma sessão JEA para executar sob uma conta gMSA, use a nova chave a seguir no arquivo PSSC:</span><span class="sxs-lookup"><span data-stu-id="0e647-118">To configure a JEA session to run under a gMSA account, use the following new key in your PSSC file:</span></span>

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> <span data-ttu-id="0e647-119">**Observação:** Contas de Serviço Gerenciado de Grupo não arcam com o isolamento ou o escopo limitado de contas virtuais.</span><span class="sxs-lookup"><span data-stu-id="0e647-119">**Note:** Group Managed Service Accounts do not afford the isolation or limited scope of virtual accounts.</span></span>
> <span data-ttu-id="0e647-120">Cada usuário conectado compartilha a mesma identidade de gMSA, que pode ter permissões em toda a empresa.</span><span class="sxs-lookup"><span data-stu-id="0e647-120">Every connecting user will share the same gMSA identity, which may have permissions across your entire enterprise.</span></span>
> <span data-ttu-id="0e647-121">Tenha muito cuidado ao optar por usar uma gMSA, e sempre prefira contas virtuais que são limitadas no computador local, quando possível.</span><span class="sxs-lookup"><span data-stu-id="0e647-121">Be very careful when selecting to use a gMSA, and always prefer virtual accounts which are limited to the local machine when possible.</span></span>

## <a name="conditional-access-policies"></a><span data-ttu-id="0e647-122">Políticas de acesso condicional</span><span class="sxs-lookup"><span data-stu-id="0e647-122">Conditional access policies</span></span>

<span data-ttu-id="0e647-123">O JEA é excelente para limitar o que alguém pode fazer quando ele se conecta a um sistema para gerenciá-lo, mas e se você também desejar limitar *quando* alguém pode usar JEA?</span><span class="sxs-lookup"><span data-stu-id="0e647-123">JEA is great at limiting what someone can do when they've connected to a system to manage it, but what if you also want to limit *when* someone can use JEA?</span></span>
<span data-ttu-id="0e647-124">Adicionamos opções de configuração aos arquivos de configuração de sessão (.pssc) para permitir que você especifique grupos de segurança aos quais um usuário deve pertencer para estabelecer uma sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="0e647-124">We have added configuration options into the session configuration files (.pssc) to let you specify security groups to which a user must belong in order to establish a JEA session.</span></span>
<span data-ttu-id="0e647-125">Isso pode ser especialmente útil se você tiver um sistema JIT (Just In Time) em seu ambiente e quiser que seus usuários elevem seus privilégios antes de acessar um ponto de extremidade JEA altamente privilegiado.</span><span class="sxs-lookup"><span data-stu-id="0e647-125">This can be particularly helpful if you have a Just In Time (JIT) system in your environment, and want to make your users elevate their privileges before accessing a highly-privileged JEA endpoint.</span></span>

<span data-ttu-id="0e647-126">O novo campo *RequiredGroups* no arquivo de PSSC permite que você especifique a lógica para determinar se um usuário pode se conectar ao JEA.</span><span class="sxs-lookup"><span data-stu-id="0e647-126">The new *RequiredGroups* field in the PSSC file allows you to specify the logic to determine if a user can connect to JEA.</span></span>
<span data-ttu-id="0e647-127">Ele consiste em especificar uma tabela de hash (opcionalmente aninhada) que usa as chaves 'E' e 'Ou' para construir as regras.</span><span class="sxs-lookup"><span data-stu-id="0e647-127">It consists of specifying a hashtable (optionally nested) that uses the 'And' and 'Or' keys to construct your rules.</span></span>
<span data-ttu-id="0e647-128">Aqui estão alguns exemplos de como utilizar esse campo:</span><span class="sxs-lookup"><span data-stu-id="0e647-128">Here are some examples of how to leverage this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a><span data-ttu-id="0e647-129">Corrigido: contas virtuais agora têm suporte no Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="0e647-129">Fixed: Virtual accounts are now supported on Windows Server 2008 R2</span></span>
<span data-ttu-id="0e647-130">No WMF 5.1, agora você poderá usar contas virtuais no Windows Server 2008 R2, permitindo configurações consistentes e paridade de recursos entre o Windows Server 2008 R2 - 2016.</span><span class="sxs-lookup"><span data-stu-id="0e647-130">In WMF 5.1, you are now able to use virtual accounts on Windows Server 2008 R2, enabling consistent configurations and feature parity across Windows Server 2008 R2 - 2016.</span></span>
<span data-ttu-id="0e647-131">Contas virtuais permanecem sem suporte ao usar JEA no Windows 7.</span><span class="sxs-lookup"><span data-stu-id="0e647-131">Virtual accounts remain unsupported when using JEA on Windows 7.</span></span>
