---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: ponta a ponta Active Directory
ms.technology: powershell
ms.openlocfilehash: 3108f5dad96ef54feb3cf559fae38812ed46849c
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: pt-BR
---
# <a name="end-to-end---active-directory"></a><span data-ttu-id="437eb-103">Ponta a Ponta - Active Directory</span><span class="sxs-lookup"><span data-stu-id="437eb-103">End to End - Active Directory</span></span>
<span data-ttu-id="437eb-104">Imagine que o escopo do seu programa aumentou.</span><span class="sxs-lookup"><span data-stu-id="437eb-104">Imagine the scope of your program has increased.</span></span>
<span data-ttu-id="437eb-105">Agora você é responsável por adicionar JEA a Controladores de Domínio para executar ações do Active Directory.</span><span class="sxs-lookup"><span data-stu-id="437eb-105">You are now responsible for adding JEA to Domain Controllers to perform Active Directory actions.</span></span>
<span data-ttu-id="437eb-106">As pessoas do suporte técnico pretendem usar JEA para desbloquear contas, redefinir senhas e executar outras ações semelhantes.</span><span class="sxs-lookup"><span data-stu-id="437eb-106">The help desk people are going to use JEA to unlock accounts, reset passwords, and do other similar actions.</span></span>

<span data-ttu-id="437eb-107">Você precisa expor um conjunto totalmente novo de comandos para um grupo diferente de pessoas.</span><span class="sxs-lookup"><span data-stu-id="437eb-107">You need to expose a completely new set of commands to a different group of people.</span></span>
<span data-ttu-id="437eb-108">Além disso, você tem um monte de scripts do Active Directory existentes que precisa expor.</span><span class="sxs-lookup"><span data-stu-id="437eb-108">On top of that, you have a bunch of existing Active Directory scripts you need to expose.</span></span>
<span data-ttu-id="437eb-109">Esta seção guiará você pela criação de uma Configuração de Sessão e a Capacidade de Função para esta tarefa.</span><span class="sxs-lookup"><span data-stu-id="437eb-109">This section will walk through authoring a Session Configuration and Role Capability for this task.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="437eb-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="437eb-110">Prerequisites</span></span>
<span data-ttu-id="437eb-111">Para seguir esta seção passo a passo, você precisará estar operando em um controlador de domínio.</span><span class="sxs-lookup"><span data-stu-id="437eb-111">To follow this section step-by-step, you'll need to be operating on a domain controller.</span></span>
<span data-ttu-id="437eb-112">Se não tiver acesso ao controlador de domínio, não se preocupe.</span><span class="sxs-lookup"><span data-stu-id="437eb-112">If you don't have access to your domain controller, don't worry.</span></span>
<span data-ttu-id="437eb-113">Tente acompanhar trabalhando em outro cenário ou função com a qual você está familiarizado.</span><span class="sxs-lookup"><span data-stu-id="437eb-113">Try to follow along with by working against some other scenario or role with which you are familiar.</span></span>
<span data-ttu-id="437eb-114">Se você quiser configurar rapidamente um novo controlador de domínio, confira o apêndice [Criar um Controlador de Domínio](.\creating-a-domain-controller.md).</span><span class="sxs-lookup"><span data-stu-id="437eb-114">If you want to quickly set up a new domain controller, check out the [Creating a Domain Controller appendix](.\creating-a-domain-controller.md).</span></span>

## <a name="steps-to-make-a-new-role-capability-and-session-configuration"></a><span data-ttu-id="437eb-115">Etapas para criar uma nova Capacidade de Função e Configuração de Sessão</span><span class="sxs-lookup"><span data-stu-id="437eb-115">Steps to Make a new Role Capability and Session Configuration</span></span>

<span data-ttu-id="437eb-116">Criar uma nova capacidade de função pode parecer intimidador num primeiro momento, mas pode ser dividido em etapas bem simples:</span><span class="sxs-lookup"><span data-stu-id="437eb-116">Making a new role capability can seem daunting at first, but it can be broken into fairly simple steps:</span></span>

1.  <span data-ttu-id="437eb-117">Identificar as tarefas que você precisa habilitar</span><span class="sxs-lookup"><span data-stu-id="437eb-117">Identify the tasks you need to enable</span></span>
2.  <span data-ttu-id="437eb-118">Restringir as tarefas conforme necessário</span><span class="sxs-lookup"><span data-stu-id="437eb-118">Restrict those tasks as necessary</span></span>
3.  <span data-ttu-id="437eb-119">Confirmar se elas funcionam com JEA</span><span class="sxs-lookup"><span data-stu-id="437eb-119">Confirm they work with JEA</span></span>
4.  <span data-ttu-id="437eb-120">Colocá-las em um arquivo de Capacidade de Função</span><span class="sxs-lookup"><span data-stu-id="437eb-120">Put them in a Role Capability file</span></span>
5.  <span data-ttu-id="437eb-121">Registrar uma Configuração de Sessão que expõe essa Capacidade de Função</span><span class="sxs-lookup"><span data-stu-id="437eb-121">Register a Session Configuration that exposes that Role Capability</span></span>

## <a name="step-1-identify-what-needs-to-be-exposed"></a><span data-ttu-id="437eb-122">Etapa 1: Identificar o que precisa ser exposto</span><span class="sxs-lookup"><span data-stu-id="437eb-122">Step 1: Identify What Needs to Be Exposed</span></span>
<span data-ttu-id="437eb-123">Antes de criar uma nova Capacidade de Função ou Configuração de Sessão, você precisará identificar todas as coisas que os usuários precisarão fazer por meio do ponto de extremidade JEA, bem como realizá-las por meio do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="437eb-123">Before you make a new Role Capability or Session Configuration, you need to identify all of the things users will need to do through the JEA endpoint, as well as how to do them through PowerShell.</span></span>
<span data-ttu-id="437eb-124">Isso envolverá uma quantidade razoável de requisito de coleta e pesquisa.</span><span class="sxs-lookup"><span data-stu-id="437eb-124">This will involve a fair amount of requirement gathering and research.</span></span>
<span data-ttu-id="437eb-125">Como você efetuará esse processo dependerá das suas metas e da organização.</span><span class="sxs-lookup"><span data-stu-id="437eb-125">How you go about this process will depend on your organization and goals.</span></span>
<span data-ttu-id="437eb-126">É importante destacar o requisito de coleta e de pesquisa como uma parte essencial do processo do mundo real.</span><span class="sxs-lookup"><span data-stu-id="437eb-126">It is important to call out requirement gathering and research as a critical part of the real world process.</span></span>
<span data-ttu-id="437eb-127">Essa pode ser a etapa mais difícil no processo de adoção de JEA.</span><span class="sxs-lookup"><span data-stu-id="437eb-127">This may be the most difficult step in the process of adopting JEA.</span></span>

### <a name="find-resources"></a><span data-ttu-id="437eb-128">Encontrar Recursos</span><span class="sxs-lookup"><span data-stu-id="437eb-128">Find Resources</span></span>
<span data-ttu-id="437eb-129">Veja este conjunto de recursos online que podem surgir na sua pesquisa sobre a criação de um ponto de extremidade de gerenciamento do Active Directory:</span><span class="sxs-lookup"><span data-stu-id="437eb-129">Here is a set of online resources that might have come up in your research on creating an Active Directory management endpoint:</span></span>
-   [<span data-ttu-id="437eb-130">Active Directory PowerShell Overview</span><span class="sxs-lookup"><span data-stu-id="437eb-130">Active Directory PowerShell Overview</span></span>](http://blogs.msdn.com/b/adpowershell/archive/2009/03/05/active-directory-powershell-overview.aspx) (Visão geral do Active Directory PowerShell)
-   [<span data-ttu-id="437eb-131">CMD to PowerShell Guide for Active Directory</span><span class="sxs-lookup"><span data-stu-id="437eb-131">CMD to PowerShell Guide for Active Directory</span></span>](http://blogs.technet.com/b/ashleymcglone/archive/2013/01/02/free-download-cmd-to-powershell-guide-for-ad.aspx) (CMD para Guia do PowerShell para Active Directory)

### <a name="make-a-list"></a><span data-ttu-id="437eb-132">Faça uma lista</span><span class="sxs-lookup"><span data-stu-id="437eb-132">Make a List</span></span>
<span data-ttu-id="437eb-133">Veja este conjunto das dez ações das quais você estará trabalhando pelo restante desta seção.</span><span class="sxs-lookup"><span data-stu-id="437eb-133">Here is a set of ten actions that you will be working from in the remainder of this section.</span></span>
<span data-ttu-id="437eb-134">Tenha em mente que este é apenas um exemplo, os requisitos das suas organizações podem ser diferentes:</span><span class="sxs-lookup"><span data-stu-id="437eb-134">Keep in mind this is simply an example, your organizations requirements may be different:</span></span>

|<span data-ttu-id="437eb-135">Ação</span><span class="sxs-lookup"><span data-stu-id="437eb-135">Action</span></span>                                                         |<span data-ttu-id="437eb-136">Comando do PowerShell</span><span class="sxs-lookup"><span data-stu-id="437eb-136">PowerShell Command</span></span>                                             |
|---------------------------------------------------------------|---------------------------------------------------------------|
|<span data-ttu-id="437eb-137">Desbloquear Conta</span><span class="sxs-lookup"><span data-stu-id="437eb-137">Account Unlock</span></span>                                                 |`Unlock-ADAccount`                                             |
|<span data-ttu-id="437eb-138">Redefinir Senha</span><span class="sxs-lookup"><span data-stu-id="437eb-138">Password Reset</span></span>                                                 |<span data-ttu-id="437eb-139">`Set-ADAccountPassword` e `Set-ADUser -ChangePasswordAtLogon`</span><span class="sxs-lookup"><span data-stu-id="437eb-139">`Set-ADAccountPassword` and `Set-ADUser -ChangePasswordAtLogon`</span></span>|
|<span data-ttu-id="437eb-140">Alterar o título do usuário</span><span class="sxs-lookup"><span data-stu-id="437eb-140">Change a User's Title</span></span>                                          |`Set-ADUser -Title`                                            |  
|<span data-ttu-id="437eb-141">Localizar contas do AD que estão bloqueadas, desabilitadas, inativa, etc.</span><span class="sxs-lookup"><span data-stu-id="437eb-141">Find AD Accounts that are locked out, disabled, inactive, etc.</span></span> |`Search-ADAccount`                                             |
|<span data-ttu-id="437eb-142">Adicionar o usuário ao grupo</span><span class="sxs-lookup"><span data-stu-id="437eb-142">Add User to Group</span></span>                                              |`Add-ADGroupMember -Identity (with whitelist) -Members`        |
|<span data-ttu-id="437eb-143">Remover usuário de grupo</span><span class="sxs-lookup"><span data-stu-id="437eb-143">Remove User from Group</span></span>                                         |`Remove-ADGroupMember -Identity (with whitelist) -Members`     |
|<span data-ttu-id="437eb-144">Habilitar uma conta de usuário</span><span class="sxs-lookup"><span data-stu-id="437eb-144">Enable a user account</span></span>                                          |`Enable-ADAccount`                                             |
|<span data-ttu-id="437eb-145">Desabilitar uma conta de usuário</span><span class="sxs-lookup"><span data-stu-id="437eb-145">Disable a user account</span></span>                                         |`Disable-ADAccount`                                            |

## <a name="step-2-restrict-tasks-as-necessary"></a><span data-ttu-id="437eb-146">Etapa 2: Restringir as tarefas conforme necessário</span><span class="sxs-lookup"><span data-stu-id="437eb-146">Step 2: Restrict Tasks as Necessary</span></span>

<span data-ttu-id="437eb-147">Agora que você tem sua lista de ações, precisará considerar os recursos de cada comando.</span><span class="sxs-lookup"><span data-stu-id="437eb-147">Now that you have your list of actions, you need to think through the capabilities of each command.</span></span>
<span data-ttu-id="437eb-148">Há dois motivos importantes para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="437eb-148">There are two important reasons to do this:</span></span>

1.  <span data-ttu-id="437eb-149">É fácil dar aos usuários mais recursos do que você pretendia.</span><span class="sxs-lookup"><span data-stu-id="437eb-149">It is easy to give users more capabilities than you intend.</span></span>
<span data-ttu-id="437eb-150">Por exemplo, `Set-ADUser` é um comando incrivelmente poderoso e flexível.</span><span class="sxs-lookup"><span data-stu-id="437eb-150">For example, `Set-ADUser` is an incredibly powerful and flexible command.</span></span>
<span data-ttu-id="437eb-151">É recomendável não expor tudo o que ele pode fazer para ajudar os usuários do suporte técnico.</span><span class="sxs-lookup"><span data-stu-id="437eb-151">You may not want to expose everything it can do to help desk users.</span></span>  

2.  <span data-ttu-id="437eb-152">Pior ainda, é possível expor comandos que permitem aos usuários fugir das restrições do JEA.</span><span class="sxs-lookup"><span data-stu-id="437eb-152">Even worse, it's possible to expose commands that allow users to escape JEA's restrictions.</span></span>
<span data-ttu-id="437eb-153">Se isso acontecer, o JEA deixará de funcionar como um limite de segurança.</span><span class="sxs-lookup"><span data-stu-id="437eb-153">If this happens, JEA ceases to function as a security boundary.</span></span>
<span data-ttu-id="437eb-154">Tenha cuidado ao selecionar comandos.</span><span class="sxs-lookup"><span data-stu-id="437eb-154">Please be careful when selecting commands.</span></span>
<span data-ttu-id="437eb-155">Por exemplo, Invoke-Expression permitirá que os usuários executem código irrestrito.</span><span class="sxs-lookup"><span data-stu-id="437eb-155">For example, Invoke-Expression will allow users to run unrestricted code.</span></span>
<span data-ttu-id="437eb-156">Para ver mais discussões sobre esse tópico, consulte a seção Considerações ao restringir comandos.</span><span class="sxs-lookup"><span data-stu-id="437eb-156">For more discussion on this topic, check out the Considerations When Restricting Commands section.</span></span>

<span data-ttu-id="437eb-157">Depois de revisar cada comando, você decide restringir o seguinte:</span><span class="sxs-lookup"><span data-stu-id="437eb-157">After reviewing each command, you decide to restrict the following:</span></span>

1.  <span data-ttu-id="437eb-158">`Set-ADUser` deve ter permissão apenas para executar o parâmetro -Title</span><span class="sxs-lookup"><span data-stu-id="437eb-158">`Set-ADUser` should only be allowed to run with the -Title parameter</span></span>

2.  <span data-ttu-id="437eb-159">`Add-ADGroupMember` e `Remove-ADGroupMember` devem funcionar apenas com determinados grupos</span><span class="sxs-lookup"><span data-stu-id="437eb-159">`Add-ADGroupMember` and `Remove-ADGroupMember` should only work with certain groups</span></span>

### <a name="step-3-confirm-the-tasks-work-with-jea"></a><span data-ttu-id="437eb-160">Etapa 3: Confirmar o trabalho de tarefas com JEA</span><span class="sxs-lookup"><span data-stu-id="437eb-160">Step 3: Confirm the Tasks Work with JEA</span></span>
<span data-ttu-id="437eb-161">De fato suar esses cmdlets pode não ser simples no ambiente JEA restrito.</span><span class="sxs-lookup"><span data-stu-id="437eb-161">Actually using those cmdlets may not be straightforward in the restricted JEA environment.</span></span>
<span data-ttu-id="437eb-162">O JEA é executado no modo *NoLanguage* que, entre outras coisas, impede os usuários de usar variáveis.</span><span class="sxs-lookup"><span data-stu-id="437eb-162">JEA runs in *NoLanguage* mode which, among other things, prevents users from using variables.</span></span>
<span data-ttu-id="437eb-163">Para garantir que os usuários finais tenham uma experiência positiva, é importante verificar algumas coisas.</span><span class="sxs-lookup"><span data-stu-id="437eb-163">In order to ensure that end users have a smooth experience, it's important to check for a few things.</span></span>

<span data-ttu-id="437eb-164">Por exemplo, considere `Set-ADAccountPassword`.</span><span class="sxs-lookup"><span data-stu-id="437eb-164">As an example, consider `Set-ADAccountPassword`.</span></span>
<span data-ttu-id="437eb-165">O parâmetro -NewPassword requer uma cadeia de caracteres segura.</span><span class="sxs-lookup"><span data-stu-id="437eb-165">The -NewPassword parameter requires a secure string.</span></span>
<span data-ttu-id="437eb-166">Muitas vezes, os usuários criam uma cadeia de caracteres e passam-na como uma variável (como abaixo):</span><span class="sxs-lookup"><span data-stu-id="437eb-166">Often, users create a secure string and pass it in as a variable (as below):</span></span>

```PowerShell
$newPassword = Read-Host -Prompt "Specify a new password" -AsSecureString
Set-ADAccountPassword -Identity mollyd -NewPassword $newPassword -Reset
```

<span data-ttu-id="437eb-167">No entanto, o modo *NoLanguage* impede o uso de variáveis.</span><span class="sxs-lookup"><span data-stu-id="437eb-167">However, *NoLanguage* mode prevents the usage of variables.</span></span>
<span data-ttu-id="437eb-168">Você pode contornar essa restrição de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="437eb-168">You can get around this restriction in two ways:</span></span>

1.  <span data-ttu-id="437eb-169">Você pode exigir que os usuários executem o comando sem atribuir variáveis.</span><span class="sxs-lookup"><span data-stu-id="437eb-169">You can require users run the command without assigning variables.</span></span>
<span data-ttu-id="437eb-170">Ele é fácil de configurar, mas pode ser penoso para os operadores usando o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="437eb-170">This is easy to configure, but can be painful for the operators using the endpoint.</span></span>
<span data-ttu-id="437eb-171">Quem deseja digitar essa saída sempre que você redefinir uma senha?</span><span class="sxs-lookup"><span data-stu-id="437eb-171">Who wants to type this out every time you reset a password?</span></span>
```PowerShell
Set-ADAccountPassword -Identity mollyd -NewPassword (Read-Host -Prompt "Specify a new password" -AsSecureString) -Reset
```

2.  <span data-ttu-id="437eb-172">Você pode encapsular a complexidade em um script ou uma função que você expõe para os usuários finais.</span><span class="sxs-lookup"><span data-stu-id="437eb-172">You can wrap the complexity in a script or a function that you expose to end users.</span></span>
<span data-ttu-id="437eb-173">Scripts e funções que você expõe são executados em um contexto irrestrito; você pode escrever funções que usam variáveis e chamar outros comandos sem nenhum problema.</span><span class="sxs-lookup"><span data-stu-id="437eb-173">Scripts and functions that you expose run in an unrestricted context; you can write functions that use variables and call other commands without any issue.</span></span>
<span data-ttu-id="437eb-174">Essa abordagem simplifica a experiência do usuário final, evita erros, reduz o conhecimento necessário do PowerShell e reduz a exposição de funcionalidade em excesso.</span><span class="sxs-lookup"><span data-stu-id="437eb-174">This approach simplifies the end user experience, prevents errors, reduces required PowerShell knowledge, and reduces unintentionally exposing excess functionality.</span></span>
<span data-ttu-id="437eb-175">A única desvantagem é o custo de criação e manutenção da função.</span><span class="sxs-lookup"><span data-stu-id="437eb-175">The only downside is the cost of authoring and maintaining the function.</span></span>

### <a name="aside-adding-a-function-to-your-module"></a><span data-ttu-id="437eb-176">Ao lado: adicionar uma função ao seu Módulo</span><span class="sxs-lookup"><span data-stu-id="437eb-176">Aside: Adding a Function to your Module</span></span>
<span data-ttu-id="437eb-177">Adotando a abordagem nº 2, você vai escrever uma função do PowerShell chamada `Reset-ContosoUserPassword`.</span><span class="sxs-lookup"><span data-stu-id="437eb-177">Taking approach #2, you are going to write a PowerShell function called `Reset-ContosoUserPassword`.</span></span>
<span data-ttu-id="437eb-178">Essa função está prestes a fazer tudo o que deve acontecer quando você redefinir a senha do usuário.</span><span class="sxs-lookup"><span data-stu-id="437eb-178">This function is going to do everything that needs to happen when you reset a user's password.</span></span>
<span data-ttu-id="437eb-179">Na sua organização, isso pode envolver fazer coisas sofisticadas e complicadas.</span><span class="sxs-lookup"><span data-stu-id="437eb-179">In your organization, this may involve doing fancy and complicated things.</span></span>
<span data-ttu-id="437eb-180">Como esse é apenas um exemplo, o comando apenas redefinirá a senha e exigirá a alteração da senha pelo usuário no momento de logon.</span><span class="sxs-lookup"><span data-stu-id="437eb-180">Because this is just an example, your command will just reset the password and require the user change the password at logon.</span></span>
<span data-ttu-id="437eb-181">Nós o colocaremos no módulo Contoso_AD_Module criado na última seção.</span><span class="sxs-lookup"><span data-stu-id="437eb-181">We will put it in the Contoso_AD_Module module you made in the last section.</span></span>

1. <span data-ttu-id="437eb-182">No ISE do PowerShell, abra "Contoso_AD_Module.psm1"</span><span class="sxs-lookup"><span data-stu-id="437eb-182">In PowerShell ISE, open "Contoso_AD_Module.psm1"</span></span>
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1'
```

2. <span data-ttu-id="437eb-183">Pressione CTRL + J para abrir o menu de trechos de código.</span><span class="sxs-lookup"><span data-stu-id="437eb-183">Press Crtl+J to open the snippets menu.</span></span>

3. <span data-ttu-id="437eb-184">Pressione a seta para baixo até localizar "função" e pressione enter.</span><span class="sxs-lookup"><span data-stu-id="437eb-184">Key down until you find "function" and press enter.</span></span>
<span data-ttu-id="437eb-185">Isso prepara um esqueleto muito básico de uma função.</span><span class="sxs-lookup"><span data-stu-id="437eb-185">This puts up a super basic skeleton of a function.</span></span>

4. <span data-ttu-id="437eb-186">Renomeie a função "Reset-ContosoUserPassword".</span><span class="sxs-lookup"><span data-stu-id="437eb-186">Rename the function "Reset-ContosoUserPassword".</span></span>  

5. <span data-ttu-id="437eb-187">Renomeie um dos parâmetros "Identity" e exclua o segundo.</span><span class="sxs-lookup"><span data-stu-id="437eb-187">Rename one of the parameters "Identity" and delete the second.</span></span>

6. <span data-ttu-id="437eb-188">Copie o seguinte no corpo da função.</span><span class="sxs-lookup"><span data-stu-id="437eb-188">Copy the following into the body of the function.</span></span>
```PowerShell
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
```

7. <span data-ttu-id="437eb-189">Salve o arquivo.</span><span class="sxs-lookup"><span data-stu-id="437eb-189">Save the file.</span></span>
<span data-ttu-id="437eb-190">Você deve terminar com algo parecido com isso:</span><span class="sxs-lookup"><span data-stu-id="437eb-190">You should end up with something that looks like this:</span></span>
```PowerShell
function Reset-ContosoUserPassword ($Identity)
{
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
}
```
<span data-ttu-id="437eb-191">Agora, os usuários podem simplesmente chamar `Reset-ContosoUserPassword` e não precisam se lembrar a sintaxe para criar um cadeia de caracteres segura embutida.</span><span class="sxs-lookup"><span data-stu-id="437eb-191">Now, your users can simply call `Reset-ContosoUserPassword` and not have to remember the syntax to create a secure string inline.</span></span>

## <a name="step-4-edit-the-role-capability-file"></a><span data-ttu-id="437eb-192">Etapa 4: Editar o arquivo de Capacidade de Função</span><span class="sxs-lookup"><span data-stu-id="437eb-192">Step 4: Edit the Role Capability File</span></span>
<span data-ttu-id="437eb-193">Na seção [Criação de Capacidade de Função](./role-capabilities.md#role-capability-creation), você criou um arquivo de Capacidade de Função em branco.</span><span class="sxs-lookup"><span data-stu-id="437eb-193">In the [Role Capability Creation](./role-capabilities.md#role-capability-creation) section, you created a blank Role Capability file.</span></span>
<span data-ttu-id="437eb-194">Nesta seção, você preencherá os valores nesse arquivo.</span><span class="sxs-lookup"><span data-stu-id="437eb-194">In this section, you will fill in the values in that file.</span></span>

<span data-ttu-id="437eb-195">Comece abrindo o arquivo de capacidade de função no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="437eb-195">Start by opening the role capability file in PowerShell ISE.</span></span>
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc'
```
<span data-ttu-id="437eb-196">Atualize o arquivo com as seguintes alterações:</span><span class="sxs-lookup"><span data-stu-id="437eb-196">Update the file with the following changes:</span></span>
```PowerShell
# OLD: VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleCmdlets =
    'Unlock-ADAccount',
    'Search-ADAccount',
    'Enable-ADAccount',
    'Disable-ADAccount',
    @{ Name = 'Set-ADUser'; Parameters = @{ Name = 'Title'; ValidateSet = 'Manager', 'Engineer' }},
    @{ Name = 'Add-ADGroupMember'; Parameters =
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}},
    @{ Name = 'Remove-ADGroupMember'; Parameters =
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}}

# OLD: VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleFunctions = 'Reset-ContosoUserPassword'
```

<span data-ttu-id="437eb-197">Há algumas coisas a observar sobre o que foi indicado acima:</span><span class="sxs-lookup"><span data-stu-id="437eb-197">There are a few things to note about the above:</span></span>
1.  <span data-ttu-id="437eb-198">O PowerShell tentará carregar automaticamente os módulos necessários para a sua Capacidade de Função.</span><span class="sxs-lookup"><span data-stu-id="437eb-198">PowerShell will attempt to auto-load the modules needed for your Role Capability.</span></span>
<span data-ttu-id="437eb-199">Você precisará listar explicitamente nomes de módulo no campo "ModulesToImport" se você encontrar problemas com um módulo que não está sendo carregado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="437eb-199">You may need to explicitly list module names in the "ModulesToImport" field if you notice problems with a module not being autoloaded.</span></span>

2.  <span data-ttu-id="437eb-200">Se você não tiver certeza se um comando é uma função ou um cmdlet, execute `Get-Command` e examine a propriedade "CommandType"</span><span class="sxs-lookup"><span data-stu-id="437eb-200">If you aren't sure if a command is a cmdlet or a function, run `Get-Command` and look at the "CommandType" property</span></span>

3.  <span data-ttu-id="437eb-201">O ValidatePattern permite que você use uma expressão regular para restringir os argumentos do parâmetro se não for fácil de definir um conjunto de valores permitidos.</span><span class="sxs-lookup"><span data-stu-id="437eb-201">The ValidatePattern allows you to use a regular expression to restrict parameter arguments if it is not easy to define a set of allowable values.</span></span>
<span data-ttu-id="437eb-202">Você não pode definir um ValidatePattern e ValidateSet para um único parâmetro.</span><span class="sxs-lookup"><span data-stu-id="437eb-202">You cannot define both a ValidatePattern and ValidateSet for a single parameter.</span></span>

## <a name="step-5-register-a-new-session-configuration"></a><span data-ttu-id="437eb-203">Etapa 5: Registrar uma nova Configuração de Sessão</span><span class="sxs-lookup"><span data-stu-id="437eb-203">Step 5: Register a new Session Configuration</span></span>
<span data-ttu-id="437eb-204">Em seguida, você criará um novo arquivo de configuração de sessão que irá expor sua Capacidade de Função para os membros do grupo de AD "JEA_NonAdmin_HelpDesk".</span><span class="sxs-lookup"><span data-stu-id="437eb-204">Next, you will create a new session configuration file that will expose your Role Capability to members of the "JEA_NonAdmin_HelpDesk" AD group.</span></span>

<span data-ttu-id="437eb-205">Comece criando e abrindo um novo arquivo de Configuração de Sessão em branco no ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="437eb-205">Start by creating and opening a new blank Session Configuration file in PowerShell ISE.</span></span>
```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
ise "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
<span data-ttu-id="437eb-206">Modifique os campos a seguir no arquivo PSSC.</span><span class="sxs-lookup"><span data-stu-id="437eb-206">Modify the following fields in the PSSC file.</span></span>
<span data-ttu-id="437eb-207">Se você estiver trabalhando em seu próprio ambiente, substitua "CONTOSO\JEA_NonAdmins_Helpdesk" por seu próprio usuário ou grupo não administrador.</span><span class="sxs-lookup"><span data-stu-id="437eb-207">If you are working in your own environment, you should replace "CONTOSO\JEA_NonAdmins_Helpdesk" with your own non-administrator user or group.</span></span>
```PowerShell
# OLD: Description = ''
Description = 'An endpoint for Active Directory tasks.'

# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{ 'CONTOSO\JEA_NonAdmin_HelpDesk' = @{ RoleCapabilities =  'ADHelpDesk' }}
```
<span data-ttu-id="437eb-208">Salve e registrar a Configuração de Sessão</span><span class="sxs-lookup"><span data-stu-id="437eb-208">Save and register the Session Configuration</span></span>
```PowerShell
Register-PSSessionConfiguration -Name ADHelpDesk -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
## <a name="test-it-out"></a><span data-ttu-id="437eb-209">Experimente!</span><span class="sxs-lookup"><span data-stu-id="437eb-209">Test It Out!</span></span>
<span data-ttu-id="437eb-210">Obtenha suas credenciais de usuário não administrador:</span><span class="sxs-lookup"><span data-stu-id="437eb-210">Get your non-administrator user credentials:</span></span>
```PowerShell
$HelpDeskCred = Get-Credential
```
<span data-ttu-id="437eb-211">Se você acompanhou a seção [Configurar usuários e grupos](creating-a-domain-controller.md#set-up-users-and-groups), as credenciais serão:</span><span class="sxs-lookup"><span data-stu-id="437eb-211">If you followed the [Set Up Users and Groups](creating-a-domain-controller.md#set-up-users-and-groups) section, the credentials will be:</span></span>
-   <span data-ttu-id="437eb-212">Nome de usuário = "HelpDeskUser"</span><span class="sxs-lookup"><span data-stu-id="437eb-212">Username = "HelpDeskUser"</span></span>
-   <span data-ttu-id="437eb-213">Senha = "pa$$w0rd"</span><span class="sxs-lookup"><span data-stu-id="437eb-213">Password = "pa$$w0rd"</span></span>

<span data-ttu-id="437eb-214">Conexão remota para o ponto de extremidade do Suporte Técnico de AD usando a credencial não administrativa:</span><span class="sxs-lookup"><span data-stu-id="437eb-214">Remote into the ADHelpdesk endpoint using the non-admin credential:</span></span>
```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName ADHelpDesk -Credential $HelpDeskCred
```
<span data-ttu-id="437eb-215">Use Set-ADUser para redefinir o título do usuário.</span><span class="sxs-lookup"><span data-stu-id="437eb-215">Use Set-ADUser to reset a user's title.</span></span>
```PowerShell
Set-ADUser -Identity OperatorUser -Title Engineer
```
<span data-ttu-id="437eb-216">Verifique se que o título foi alterado.</span><span class="sxs-lookup"><span data-stu-id="437eb-216">Verify that the title has changed.</span></span>
```PowerShell
Get-ADUser -Identity OperatorUser -Property Title
```
<span data-ttu-id="437eb-217">Agora, use Add-ADGroupMember para adicionar um usuário ao TestGroup.</span><span class="sxs-lookup"><span data-stu-id="437eb-217">Now, use Add-ADGroupMember to add a user to the TestGroup.</span></span>
<span data-ttu-id="437eb-218">Observação: verifique se você criou o TestGroup com antecedência.</span><span class="sxs-lookup"><span data-stu-id="437eb-218">Note: make sure you've created the TestGroup beforehand.</span></span>
```PowerShell
Add-ADGroupMember TestGroup -Member OperatorUser -Verbose
```
<span data-ttu-id="437eb-219">Sair da sessão:</span><span class="sxs-lookup"><span data-stu-id="437eb-219">Exit the session:</span></span>
```PowerShell
Exit-PSSession
```
## <a name="key-concepts"></a><span data-ttu-id="437eb-220">Conceitos Principais</span><span class="sxs-lookup"><span data-stu-id="437eb-220">Key Concepts</span></span>
<span data-ttu-id="437eb-221">**Modo NoLanguage**: quando o PowerShell está no modo "NoLanguage", os usuários somente podem executar comandos, mas não podem usar elementos de linguagem.</span><span class="sxs-lookup"><span data-stu-id="437eb-221">**NoLanguage Mode**: When PowerShell is in "NoLanguage" mode, users may only run commands; they cannot use any language elements.</span></span>
<span data-ttu-id="437eb-222">Para obter mais informações, execute `Get-Help about_Language_Modes`.</span><span class="sxs-lookup"><span data-stu-id="437eb-222">For more information, run `Get-Help about_Language_Modes`.</span></span>

<span data-ttu-id="437eb-223">**Funções do PowerShell**: funções do PowerShell são partes do código do PowerShell que podem ser chamados por nome.</span><span class="sxs-lookup"><span data-stu-id="437eb-223">**PowerShell Functions**: PowerShell functions are bits of PowerShell code that you can call by name.</span></span>
<span data-ttu-id="437eb-224">Para obter mais informações, execute `Get-Help about_Functions`.</span><span class="sxs-lookup"><span data-stu-id="437eb-224">For more information, run `Get-Help about_Functions`.</span></span>

<span data-ttu-id="437eb-225">**ValidateSet/ValidatePattern**: ao expor um comando, você pode restringir os argumentos válidos para os parâmetros específicos.</span><span class="sxs-lookup"><span data-stu-id="437eb-225">**ValidateSet/ValidatePattern**: When exposing a command, you can restrict valid arguments for specific parameters.</span></span>
<span data-ttu-id="437eb-226">Um ValidateSet é uma lista específica de argumentos válidos.</span><span class="sxs-lookup"><span data-stu-id="437eb-226">A ValidateSet is a specific list of valid arguments.</span></span>
<span data-ttu-id="437eb-227">Um ValidatePattern é uma expressão regular à qual os argumentos para esse parâmetro devem corresponder.</span><span class="sxs-lookup"><span data-stu-id="437eb-227">A ValidatePattern is a regular expression that the arguments for that parameter must match.</span></span>

