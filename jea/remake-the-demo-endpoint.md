---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "recriar o ponto de extremidade da demonstração"
ms.technology: powershell
ms.openlocfilehash: 4a56272b6f995500d443d441f5e03db85dac6f96
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: pt-BR
---
# <a name="remake-the-demo-endpoint"></a><span data-ttu-id="92d98-103">Recriar o Ponto de Extremidade de Demonstração</span><span class="sxs-lookup"><span data-stu-id="92d98-103">Remake the Demo Endpoint</span></span>
<span data-ttu-id="92d98-104">Nesta seção, você aprenderá como gerar uma réplica exata do ponto de extremidade de demonstração usado na seção acima.</span><span class="sxs-lookup"><span data-stu-id="92d98-104">In this section, you will learn how to generate an exact replica of the demo endpoint you used in the above section.</span></span>
<span data-ttu-id="92d98-105">Ela apresentará os conceitos fundamentais que são necessários para compreender o JEA, incluindo as Configurações de Sessão e Capacidades de Função do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="92d98-105">This will introduce core concepts that are necessary to understand JEA, including PowerShell Session Configurations and Role Capabilities.</span></span>

## <a name="powershell-session-configurations"></a><span data-ttu-id="92d98-106">Configurações de Sessão do PowerShell</span><span class="sxs-lookup"><span data-stu-id="92d98-106">PowerShell Session Configurations</span></span>
<span data-ttu-id="92d98-107">Ao usar o JEA na seção acima, você começou executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="92d98-107">When you used JEA in the above section, you started by running the following command:</span></span>

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred
```

<span data-ttu-id="92d98-108">Enquanto a maioria dos parâmetros são auto-explicativos, o *ConfigurationName* pode parecer confuso a princípio.</span><span class="sxs-lookup"><span data-stu-id="92d98-108">While most of the parameters are self-explanatory, the *ConfigurationName* parameter may seem confusing at first.</span></span>
<span data-ttu-id="92d98-109">Esse parâmetro especificou a Configuração de Sessão do PowerShell para o qual você se conectou.</span><span class="sxs-lookup"><span data-stu-id="92d98-109">That parameter specified the PowerShell Session Configuration to which you were connecting.</span></span>

<span data-ttu-id="92d98-110">*Configuração de Sessão do PowerShell* é um termo especial para um ponto de extremidade do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="92d98-110">*PowerShell Session Configuration* is a fancy term for a PowerShell endpoint.</span></span>
<span data-ttu-id="92d98-111">Ele é o “local” figurativo no qual os usuários se conectam e obtém acesso à funcionalidade do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="92d98-111">It is the figurative "place" where users connect and get access to PowerShell functionality.</span></span>
<span data-ttu-id="92d98-112">Dependendo de como você definiu uma Configuração de Sessão, ele pode fornecer uma funcionalidade diferente para conectar os usuários.</span><span class="sxs-lookup"><span data-stu-id="92d98-112">Based on how you set up a Session Configuration, it can provide different functionality to connecting users.</span></span>
<span data-ttu-id="92d98-113">Para JEA, usamos as Configurações de Sessão para restringir o PowerShell a um conjunto limitado de funcionalidades e para executá-lo como uma conta virtual privilegiada.</span><span class="sxs-lookup"><span data-stu-id="92d98-113">For JEA, we use Session Configurations to restrict PowerShell to a limited set of functionality and to run as a privileged virtual account.</span></span>

<span data-ttu-id="92d98-114">Você já tem várias Configurações de Sessão do PowerShell registradas no seu computador, cada uma configurada de forma ligeiramente diferente.</span><span class="sxs-lookup"><span data-stu-id="92d98-114">You already have several registered PowerShell Session Configurations on your machine, each set up slightly differently.</span></span>
<span data-ttu-id="92d98-115">A maioria deles é fornecida com o Windows, mas a Configuração de Sessão “JEA_Demo” foi definida na seção [Pré-requisitos](prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="92d98-115">Most of them come with Windows, but the "JEA_Demo" Session Configuration was set up in the [prerequisites](prerequisites.md) section.</span></span>
<span data-ttu-id="92d98-116">Você pode ver que todas as Configurações de Sessão registradas executando o seguinte comando em um prompt de Administrador do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="92d98-116">You can see all registered Session Configurations by running the following command in an Administrator PowerShell prompt:</span></span>

```PowerShell
Get-PSSessionConfiguration
```

## <a name="powershell-session-configuration-files"></a><span data-ttu-id="92d98-117">Arquivos de Configuração de Sessão do PowerShell</span><span class="sxs-lookup"><span data-stu-id="92d98-117">PowerShell Session Configuration Files</span></span>
<span data-ttu-id="92d98-118">Você pode criar novas Configurações de Sessão registrando novos *Arquivos de Configuração de Sessão do PowerShell*.</span><span class="sxs-lookup"><span data-stu-id="92d98-118">You can make new Session Configurations by registering new *PowerShell Session Configuration Files*.</span></span>
<span data-ttu-id="92d98-119">Arquivos de Configuração de Sessão têm extensões de arquivo “.pssc”.</span><span class="sxs-lookup"><span data-stu-id="92d98-119">Session Configuration Files have ".pssc" file extensions.</span></span>
<span data-ttu-id="92d98-120">Você pode gerar os Arquivos de Configuração de Sessão com o cmdlet New-PSSessionConfigurationFile.</span><span class="sxs-lookup"><span data-stu-id="92d98-120">You can generate Session Configuration Files with the New-PSSessionConfigurationFile cmdlet.</span></span>

<span data-ttu-id="92d98-121">Em seguida, você criará e registrará uma nova Configuração de Sessão para JEA.</span><span class="sxs-lookup"><span data-stu-id="92d98-121">Next, you are going to create and register a new Session Configuration for JEA.</span></span>

## <a name="generate-and-modify-your-powershell-session-configuration"></a><span data-ttu-id="92d98-122">Gerar e modificar a Configuração de Sessão do PowerShell</span><span class="sxs-lookup"><span data-stu-id="92d98-122">Generate and Modify your PowerShell Session Configuration</span></span>
<span data-ttu-id="92d98-123">Execute o seguinte comando para gerar um arquivo “esqueleto” de Configuração de Sessão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="92d98-123">Run the following command to generate a PowerShell Session Configuration "skeleton" file.</span></span>

```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

> <span data-ttu-id="92d98-124">**DICA:** apenas as definições de configuração mais comuns são incluídas no arquivo esqueleto por padrão.</span><span class="sxs-lookup"><span data-stu-id="92d98-124">**TIP:** Only the most common configuration settings are included in the skeleton file by default.</span></span>
> <span data-ttu-id="92d98-125">Use o parâmetro `-Full` para incluir todas as configurações aplicáveis no PSSC gerado.</span><span class="sxs-lookup"><span data-stu-id="92d98-125">Use the `-Full` parameter to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="92d98-126">Abra o arquivo no ISE do PowerShell ou seu editor de texto favorito.</span><span class="sxs-lookup"><span data-stu-id="92d98-126">Open the file in PowerShell ISE, or your favorite text editor.</span></span>

```PowerShell
ise "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

<span data-ttu-id="92d98-127">Atualize os campos a seguir no arquivo com os valores abaixo (lembre-se de substituir em seu próprio grupo de segurança não administrador):</span><span class="sxs-lookup"><span data-stu-id="92d98-127">Update the following fields in the file with the values below (remember to substitute in your own non-administrator security group):</span></span>

```PowerShell
# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: # RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{'CONTOSO\JEA_NonAdmin_Operator' = @{ RoleCapabilities =  'Maintenance' }}
```

<span data-ttu-id="92d98-128">Aqui está o que significa cada uma dessas entradas:</span><span class="sxs-lookup"><span data-stu-id="92d98-128">Here is what each of those entries mean:</span></span>

1.  <span data-ttu-id="92d98-129">O campo *SessionType* define as configurações padrão predefinidas para serem usadas com esse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="92d98-129">The *SessionType* field defines preset default settings to use with this endpoint.</span></span>
<span data-ttu-id="92d98-130">O *RestrictedRemoteServer* define as configurações mínimas necessárias para o gerenciamento remoto.</span><span class="sxs-lookup"><span data-stu-id="92d98-130">*RestrictedRemoteServer* defines the minimal settings necessary for remote management.</span></span>
<span data-ttu-id="92d98-131">Por padrão, um ponto de extremidade *RestrictedRemoteServer* expõe Get-Command, Get-FormatData, Select-Object, Get-Help, Measure-Object, Exit-PSSession, Clear-Host e Out-Default.</span><span class="sxs-lookup"><span data-stu-id="92d98-131">By default, a *RestrictedRemoteServer* endpoint will expose Get-Command, Get-FormatData, Select-Object, Get-Help, Measure-Object, Exit-PSSession, Clear-Host, and Out-Default.</span></span>
<span data-ttu-id="92d98-132">Ele definirá *ExecutionPolicy* para *RemoteSigned* e *LanguageMode* para *NoLanguage*.</span><span class="sxs-lookup"><span data-stu-id="92d98-132">It will set the *ExecutionPolicy* to *RemoteSigned*, and the *LanguageMode* to *NoLanguage*.</span></span>
<span data-ttu-id="92d98-133">O efeito dessas configurações é um ponto de partida mínimo e seguro para configurar o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="92d98-133">The net effect of these settings is a secure and minimal starting point for configuring your endpoint.</span></span>

2.  <span data-ttu-id="92d98-134">O campo *RoleDefinitions* atribui a Capacidades de Função para grupos específicos.</span><span class="sxs-lookup"><span data-stu-id="92d98-134">The *RoleDefinitions* field assigns Role Capabilities to specific groups.</span></span>
<span data-ttu-id="92d98-135">Ele define quem pode fazer o que como uma conta privilegiada.</span><span class="sxs-lookup"><span data-stu-id="92d98-135">It defines who can do what as a privileged account.</span></span>
<span data-ttu-id="92d98-136">Com este campo, você pode especificar a funcionalidade disponível para qualquer usuário conectado com base na associação de grupo.</span><span class="sxs-lookup"><span data-stu-id="92d98-136">With this field, you can specify the functionality available to any connecting user based on group membership.</span></span>
<span data-ttu-id="92d98-137">Esse é o núcleo da funcionalidade de RBAC do JEA.</span><span class="sxs-lookup"><span data-stu-id="92d98-137">This is the core of JEA's RBAC functionality.</span></span>
<span data-ttu-id="92d98-138">Neste exemplo, você está expondo o RoleCapability de "manutenção" predefinido para membros do grupo "Contoso\JEA_NonAdmin_Operator".</span><span class="sxs-lookup"><span data-stu-id="92d98-138">In this example, you are exposing the pre-made "Maintenance" RoleCapability to members of the "Contoso\JEA_NonAdmin_Operator" group.</span></span>

3.  <span data-ttu-id="92d98-139">O campo *RunAsVirtualAccount* indica que PowerShell deve "Executar como" uma Conta Virtual neste ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="92d98-139">The *RunAsVirtualAccount* field indicates that PowerShell should "run as" a Virtual Account at this endpoint.</span></span>
<span data-ttu-id="92d98-140">Por padrão, a Conta Virtual é um membro do grupo Administradores interno.</span><span class="sxs-lookup"><span data-stu-id="92d98-140">By default, the Virtual Account is a member of the built in Administrators group.</span></span>
<span data-ttu-id="92d98-141">Em um controlador de domínio, ele também é um membro do grupo Administradores de Domínio por padrão.</span><span class="sxs-lookup"><span data-stu-id="92d98-141">On a domain controller, it is also a member of the Domain Administrators group by default.</span></span>
<span data-ttu-id="92d98-142">Posteriormente neste guia, você aprenderá como personalizar os privilégios da Conta Virtual.</span><span class="sxs-lookup"><span data-stu-id="92d98-142">Later in this guide, you will learn how to customize the privileges of the Virtual Account.</span></span>

4.  <span data-ttu-id="92d98-143">O campo *TranscriptDirectory* define onde as transcrições “Over the Shoulder” do PowerShell são salvas após cada sessão remota.</span><span class="sxs-lookup"><span data-stu-id="92d98-143">The *TranscriptDirectory* field defines where "over-the-shoulder" PowerShell transcripts are saved after each remote session.</span></span>
<span data-ttu-id="92d98-144">Essas transcrições permitem que você inspecione as ações executadas em cada sessão de forma legível.</span><span class="sxs-lookup"><span data-stu-id="92d98-144">These transcripts allow you to inspect the actions taken in each session in a readable way.</span></span>
<span data-ttu-id="92d98-145">Para obter mais informações sobre transcrições do PowerShell, confira este [post de blog](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).</span><span class="sxs-lookup"><span data-stu-id="92d98-145">For more information about PowerShell transcripts, check out this [blog post](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).</span></span>
<span data-ttu-id="92d98-146">Observação: os Eventos do Windows também capturam informações sobre o que cada usuário executou com o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="92d98-146">Note: regular Windows Eventing also captures information about what each user ran with PowerShell.</span></span>
<span data-ttu-id="92d98-147">Transcrições são apenas um pouco mais legíveis.</span><span class="sxs-lookup"><span data-stu-id="92d98-147">Transcripts are just a bit more readable.</span></span>

<span data-ttu-id="92d98-148">Por fim, salve suas alterações em *JEADemo2.pssc*.</span><span class="sxs-lookup"><span data-stu-id="92d98-148">Finally, save your changes to *JEADemo2.pssc*.</span></span>

## <a name="apply-the-powershell-session-configuration"></a><span data-ttu-id="92d98-149">Aplique a Configuração de Sessão do PowerShell</span><span class="sxs-lookup"><span data-stu-id="92d98-149">Apply the PowerShell Session Configuration</span></span>

<span data-ttu-id="92d98-150">Para criar um ponto de extremidade de um arquivo de Configuração de Sessão, você precisa registrar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="92d98-150">To create an endpoint from a Session Configuration file, you need to register the file.</span></span>
<span data-ttu-id="92d98-151">Isso requer algumas informações:</span><span class="sxs-lookup"><span data-stu-id="92d98-151">This requires a few pieces of information:</span></span>

1. <span data-ttu-id="92d98-152">O caminho para o arquivo de Configuração de Sessão.</span><span class="sxs-lookup"><span data-stu-id="92d98-152">The path to the Session Configuration file.</span></span>
2. <span data-ttu-id="92d98-153">O nome da sua Configuração de Sessão registrada.</span><span class="sxs-lookup"><span data-stu-id="92d98-153">The name of your registered Session Configuration.</span></span> <span data-ttu-id="92d98-154">Esse é o mesmo nome que os usuários fornecem para o parâmetro "ConfigurationName" ao se conectarem ao ponto de extremidade com `Enter-PSSession` ou `New-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="92d98-154">This is the same name users provide to the "ConfigurationName" parameter when they connect to your endpoint with `Enter-PSSession` or `New-PSSession`.</span></span>

<span data-ttu-id="92d98-155">Para registrar a Configuração de Sessão no computador local, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="92d98-155">To register the Session Configuration on your local machine, run the following command:</span></span>

```PowerShell
Register-PSSessionConfiguration -Name 'JEADemo2' -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

<span data-ttu-id="92d98-156">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="92d98-156">Congratulations!</span></span> <span data-ttu-id="92d98-157">Você configurou o seu ponto de extremidade JEA.</span><span class="sxs-lookup"><span data-stu-id="92d98-157">You have set up your JEA endpoint.</span></span>

## <a name="test-out-your-endpoint"></a><span data-ttu-id="92d98-158">Testar seu ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="92d98-158">Test Out Your Endpoint</span></span>
<span data-ttu-id="92d98-159">Execute novamente as etapas listadas na seção [Usando o JEA](using-jea.md) no novo ponto de extremidade para confirmar se ele está funcionando conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="92d98-159">Re-run the steps listed in the [Using JEA](using-jea.md) section against your new endpoint to confirm it is operating as intended.</span></span>
<span data-ttu-id="92d98-160">Use o novo nome de ponto de extremidade (JEADemo2) ao informar o nome de configuração para `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="92d98-160">Be sure to use the new endpoint name (JEADemo2) when providing the configuration name to `Enter-PSSession`.</span></span>

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
```

## <a name="key-concepts"></a><span data-ttu-id="92d98-161">Conceitos Principais</span><span class="sxs-lookup"><span data-stu-id="92d98-161">Key Concepts</span></span>
<span data-ttu-id="92d98-162">**Configuração de Sessão do PowerShell**: às vezes chamado de *Ponto de Extremidade do PowerShell*, esse é o "local" figurado em que os usuários se conectam e obtém acesso à funcionalidade do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="92d98-162">**PowerShell Session Configuration**: Sometimes referred to as *PowerShell Endpoint*, this is the figurative "place" where users connect and get access to PowerShell functionality.</span></span>
<span data-ttu-id="92d98-163">Você pode listar as Configurações de Sessão registradas no sistema executando `Get-PSSessionConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="92d98-163">You can list the registered Session Configurations on your system by running `Get-PSSessionConfiguration`.</span></span>
<span data-ttu-id="92d98-164">Quando configurado de forma específica, uma Configuração de Sessão do PowerShell pode ser chamada de *Ponto de Extremidade JEA*.</span><span class="sxs-lookup"><span data-stu-id="92d98-164">When configured in a specific way, a PowerShell Session Configuration can be called a *JEA Endpoint*.</span></span>

<span data-ttu-id="92d98-165">**Arquivo de Configuração de Sessão do PowerShell (.pssc)**: um arquivo que, quando registrado, define as configurações para uma Configuração de Sessão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="92d98-165">**PowerShell Session Configuration File (.pssc)**: A file that, when registered, defines settings for a PowerShell Session Configuration.</span></span>
<span data-ttu-id="92d98-166">Ele contém especificações para funções de usuário que podem se conectar ao ponto de extremidade, à Conta Virtual "Executar como" e muito mais.</span><span class="sxs-lookup"><span data-stu-id="92d98-166">It contains specifications for user roles that can connect to the endpoint, the "run as" Virtual Account, and more.</span></span>     

<span data-ttu-id="92d98-167">**Definições de Função**: o campo em um Arquivo de Configuração de Sessão que define a Capacidades de Função concedida para conectar usuários.</span><span class="sxs-lookup"><span data-stu-id="92d98-167">**Role Definitions**: The field in a Session Configuration File that defines the Role Capabilities granted to connecting users.</span></span>
<span data-ttu-id="92d98-168">Ele define *quem* pode fazer *o que* como uma conta privilegiada.</span><span class="sxs-lookup"><span data-stu-id="92d98-168">It defines *who* can do *what* as a privileged account.</span></span>
<span data-ttu-id="92d98-169">Esse é o núcleo das capacidades de RBAC do JEA.</span><span class="sxs-lookup"><span data-stu-id="92d98-169">This is the core of JEA's RBAC capabilities.</span></span>

<span data-ttu-id="92d98-170">**SessionType**: um campo em um Arquivo de Configuração de Sessão que representa as configurações padrão para uma Configuração de Sessão.</span><span class="sxs-lookup"><span data-stu-id="92d98-170">**SessionType**: A field in a Session Configuration File that represents default settings for a Session Configuration.</span></span>
<span data-ttu-id="92d98-171">Para pontos de extremidade JEA, é necessário definir isso como RestrictedRemoteServer.</span><span class="sxs-lookup"><span data-stu-id="92d98-171">For JEA endpoints, this must be set to RestrictedRemoteServer.</span></span>

<span data-ttu-id="92d98-172">**Transcrição de PowerShell**: um arquivo que contém uma exibição "Over The Shoulder" de uma sessão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="92d98-172">**PowerShell Transcript**: A file containing an "over-the-shoulder" view of a PowerShell session.</span></span>
<span data-ttu-id="92d98-173">Você pode configurar o PowerShell para gerar transcrições para sessões JEA usando o campo TranscriptDirectory.</span><span class="sxs-lookup"><span data-stu-id="92d98-173">You can set PowerShell to generate transcripts for JEA sessions using the TranscriptDirectory field.</span></span>
<span data-ttu-id="92d98-174">Para obter mais informações sobre transcrições, confira este [post de blog](https://technet.microsoft.com/en-us/magazine/ff687007.aspx).</span><span class="sxs-lookup"><span data-stu-id="92d98-174">For more information on transcripts, check out this [blog post](https://technet.microsoft.com/en-us/magazine/ff687007.aspx).</span></span>

