---
ms.date: 06/12/2017
keywords: jea,powershell,segurança
title: Recursos de Função JEA
ms.openlocfilehash: 0531baa284e66a42a162329ea20ecfdca6d0b526
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="jea-role-capabilities"></a><span data-ttu-id="8f883-103">Recursos de Função JEA</span><span class="sxs-lookup"><span data-stu-id="8f883-103">JEA Role Capabilities</span></span>

> <span data-ttu-id="8f883-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8f883-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="8f883-105">Ao criar um ponto de extremidade JEA, é necessário definir um ou mais "recursos de função" que descrevem *o que* alguém pode fazer em uma sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="8f883-105">When creating a JEA endpoint, you will need to define one or more "role capabilities" which describe *what* someone can do in a JEA session.</span></span>
<span data-ttu-id="8f883-106">Uma capacidade de função é um arquivo de dados do PowerShell com a extensão .psrc que lista todos os cmdlets, as funções, os provedores e os programas externos que devem ser disponibilizados para usuários que estão se conectando.</span><span class="sxs-lookup"><span data-stu-id="8f883-106">A role capability is a PowerShell data file with the .psrc extension that lists all the cmdlets, functions, providers, and external programs that should be made available to connecting users.</span></span>

<span data-ttu-id="8f883-107">Este tópico descreve como criar um arquivo da capacidade de função do PowerShell para seus usuários JEA.</span><span class="sxs-lookup"><span data-stu-id="8f883-107">This topic describes how to create a PowerShell role capability file for your JEA users.</span></span>

## <a name="determine-which-commands-to-allow"></a><span data-ttu-id="8f883-108">Determinar quais comandos permitir</span><span class="sxs-lookup"><span data-stu-id="8f883-108">Determine which commands to allow</span></span>

<span data-ttu-id="8f883-109">A primeira etapa ao criar um arquivo de capacidade de função é considerar o que os usuários que recebem a função precisarão acessar.</span><span class="sxs-lookup"><span data-stu-id="8f883-109">The first step when creating a role capability file is to consider what the users who are assigned the role will need access to.</span></span>
<span data-ttu-id="8f883-110">Esse processo de coleta de requisitos pode levar algum tempo, mas é um processo muito importante.</span><span class="sxs-lookup"><span data-stu-id="8f883-110">This requirements gathering process can take a while, but it is a very important process.</span></span>
<span data-ttu-id="8f883-111">Conceder aos usuários acesso a poucos cmdlets e funções pode impedi-los de cumprir suas tarefas.</span><span class="sxs-lookup"><span data-stu-id="8f883-111">Giving users access to too few cmdlets and functions can prevent them from getting their job done.</span></span>
<span data-ttu-id="8f883-112">Permitir o acesso a muitos cmdlets e funções pode resultar em usuários fazendo mais do que você pretendia com os privilégios implícitos de administrador, enfraquecendo a sua postura de segurança.</span><span class="sxs-lookup"><span data-stu-id="8f883-112">Allowing access to too many cmdlets and functions can lead to users doing more than you intended with their implicit admin privileges, weakening your security stance.</span></span>

<span data-ttu-id="8f883-113">A maneira como você avança nesse processo dependerá da sua organização e dos objetivos, no entanto, as dicas a seguir podem ajudar a garantir que você esteja no caminho certo.</span><span class="sxs-lookup"><span data-stu-id="8f883-113">How you go about this process will depend on your organization and goals, however the following tips can help ensure you're on the right path.</span></span>

1. <span data-ttu-id="8f883-114">**Identificar** os comandos que os usuários estão usando para executar seus trabalhos.</span><span class="sxs-lookup"><span data-stu-id="8f883-114">**Identify** the commands users are using to get their jobs done.</span></span> <span data-ttu-id="8f883-115">Isso pode envolver pesquisar a equipe de TI, verificar scripts de automação ou analisar transcrições ou logs de sessão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8f883-115">This may involve surveying IT staff, checking automation scripts, or analyzing PowerShell session transcripts or logs.</span></span>
2. <span data-ttu-id="8f883-116">**Atualizar** o uso de ferramentas de linha de comando para equivalentes do PowerShell, sempre que possível, para uma melhor experiência de auditoria e de personalização de JEA.</span><span class="sxs-lookup"><span data-stu-id="8f883-116">**Update** use of command line tools to PowerShell equivalents, where possible, for the best auditing and JEA customization experience.</span></span> <span data-ttu-id="8f883-117">Os programas externos não podem ser restritos de forma tão granular como os cmdlets e funções nativas do PowerShell no JEA.</span><span class="sxs-lookup"><span data-stu-id="8f883-117">External programs cannot be constrained as granularly as native PowerShell cmdlets and functions in JEA.</span></span>
3. <span data-ttu-id="8f883-118">**Restringir** o escopo dos cmdlets se necessário, para permitir apenas parâmetros ou valores de parâmetro específicos.</span><span class="sxs-lookup"><span data-stu-id="8f883-118">**Restrict** the scope of the cmdlets if necessary to only allow specific parameters or parameter values.</span></span> <span data-ttu-id="8f883-119">Isso é particularmente importante se os usuários devem ser capazes de gerenciar apenas uma parte de um sistema.</span><span class="sxs-lookup"><span data-stu-id="8f883-119">This is particularly important if users should only be able to manage part of a system.</span></span>
4. <span data-ttu-id="8f883-120">**Criar** funções personalizadas para substituir comandos complexos ou comandos que são difíceis de restringir no JEA.</span><span class="sxs-lookup"><span data-stu-id="8f883-120">**Create** custom functions to replace complex commands or commands which are difficult to constrain in JEA.</span></span> <span data-ttu-id="8f883-121">Uma função simples que encapsula um comando complexo ou que aplica lógica de validação adicional pode oferecer controle adicional para administradores e simplicidade para usuários finais.</span><span class="sxs-lookup"><span data-stu-id="8f883-121">A simple function that wraps a complex command or applies additional validation logic can offer additional control for admins and end-user simplicity.</span></span>
5. <span data-ttu-id="8f883-122">**Testar** a lista de escopo de comandos permitidos com seus usuários e/ou serviços de automação e ajustar conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="8f883-122">**Test** the scoped list of allowable commands with your users and/or automation services and adjust as necessary.</span></span>

<span data-ttu-id="8f883-123">É importante lembrar que os comandos em uma sessão JEA são geralmente executados com privilégios de administrador (ou elevados de outra maneira).</span><span class="sxs-lookup"><span data-stu-id="8f883-123">It is important to remember that commands in a JEA session are often run with admin (or otherwise elevated) privileges.</span></span>
<span data-ttu-id="8f883-124">A seleção cuidadosa de comandos disponíveis é importante para garantir que o ponto de extremidade JEA não permita que o usuário que está se conectando eleve suas permissões.</span><span class="sxs-lookup"><span data-stu-id="8f883-124">Careful selection of available commands is important to ensure the JEA endpoint does not allow the connecting user to elevate their permissions.</span></span>
<span data-ttu-id="8f883-125">Abaixo estão alguns exemplos de comandos que podem ser usados maliciosamente se forem permitidos em um estado sem restrições.</span><span class="sxs-lookup"><span data-stu-id="8f883-125">Below are some examples of commands that can be used maliciously if allowed in an unconstrained state.</span></span>
<span data-ttu-id="8f883-126">Observe que essa não é uma lista completa e só deve ser usada como um ponto de partida preventivo.</span><span class="sxs-lookup"><span data-stu-id="8f883-126">Note that this is not an exhaustive list and should only be used as a cautionary starting point.</span></span>

### <a name="examples-of-potentially-dangerous-commands"></a><span data-ttu-id="8f883-127">Exemplos de comandos potencialmente perigosos</span><span class="sxs-lookup"><span data-stu-id="8f883-127">Examples of potentially dangerous commands</span></span>

<span data-ttu-id="8f883-128">Risco</span><span class="sxs-lookup"><span data-stu-id="8f883-128">Risk</span></span> | <span data-ttu-id="8f883-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8f883-129">Example</span></span> | <span data-ttu-id="8f883-130">Comandos relacionados</span><span class="sxs-lookup"><span data-stu-id="8f883-130">Related commands</span></span>
-----|---------|-----------------
<span data-ttu-id="8f883-131">Concedendo privilégios de administrador ao usuário que está se conectando, para ignorar o JEA</span><span class="sxs-lookup"><span data-stu-id="8f883-131">Granting the connecting user admin privileges to bypass JEA</span></span> | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | <span data-ttu-id="8f883-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span><span class="sxs-lookup"><span data-stu-id="8f883-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span></span>
<span data-ttu-id="8f883-133">Execução de código arbitrário, como malware, explorações ou scripts personalizados para ignorar proteções</span><span class="sxs-lookup"><span data-stu-id="8f883-133">Running arbitrary code, such as malware, exploits, or custom scripts to bypass protections</span></span> | `Start-Process -FilePath '\\san\share\malware.exe'` | <span data-ttu-id="8f883-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span><span class="sxs-lookup"><span data-stu-id="8f883-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span></span>

## <a name="create-a-role-capability-file"></a><span data-ttu-id="8f883-135">Criar um arquivo de capacidade de função</span><span class="sxs-lookup"><span data-stu-id="8f883-135">Create a role capability file</span></span>

<span data-ttu-id="8f883-136">Você pode criar um novo arquivo de capacidade de função do PowerShell com o cmdlet [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile).</span><span class="sxs-lookup"><span data-stu-id="8f883-136">You can create a new PowerShell role capability file with the [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.</span></span>

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

<span data-ttu-id="8f883-137">O arquivo de capacidade de função resultante pode ser aberto em um editor de texto e modificado para permitir os comandos desejados para a função.</span><span class="sxs-lookup"><span data-stu-id="8f883-137">The resulting role capability file can be opened in a text editor and modified to allow the desired commands for the role.</span></span>
<span data-ttu-id="8f883-138">A documentação de ajuda do PowerShell contém vários exemplos de como você pode configurar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="8f883-138">The PowerShell help documentation contains several examples of how you can configure the file.</span></span>

### <a name="allowing-powershell-cmdlets-and-functions"></a><span data-ttu-id="8f883-139">Permitir cmdlets e funções do PowerShell</span><span class="sxs-lookup"><span data-stu-id="8f883-139">Allowing PowerShell cmdlets and functions</span></span>

<span data-ttu-id="8f883-140">Para autorizar usuários a executar funções ou cmdlets do PowerShell, adicione o nome do cmdlet ou da função nos campos VisbibleCmdlets ou VisibleFunctions.</span><span class="sxs-lookup"><span data-stu-id="8f883-140">To authorize users to run PowerShell cmdlets or functions, add the cmdlet or function name to the VisbibleCmdlets or VisibleFunctions fields.</span></span>
<span data-ttu-id="8f883-141">Se você não tiver certeza se um comando é um cmdlet ou uma função, você poderá executar `Get-Command <name>` e verificar a propriedade "CommandType" na saída.</span><span class="sxs-lookup"><span data-stu-id="8f883-141">If you aren't sure whether a command is a cmdlet or function, you can run `Get-Command <name>` and check the "CommandType" property in the output.</span></span>

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

<span data-ttu-id="8f883-142">Às vezes, o escopo de um cmdlet ou de uma função específica é muito amplo para as necessidades dos usuários.</span><span class="sxs-lookup"><span data-stu-id="8f883-142">Sometimes the scope of a specific cmdlet or function is too broad for your users' needs.</span></span>
<span data-ttu-id="8f883-143">Um administrador de DNS, por exemplo, provavelmente só precisa de acesso para reiniciar o serviço DNS.</span><span class="sxs-lookup"><span data-stu-id="8f883-143">A DNS admin, for example, probably only needs access to restart the DNS service.</span></span>
<span data-ttu-id="8f883-144">Em um ambiente de multilocatário em que os locatários recebem acesso a ferramentas de gerenciamento de autoatendimento, os locatários devem ser limitados ao gerenciamento com seus próprios recursos.</span><span class="sxs-lookup"><span data-stu-id="8f883-144">In a multi-tenant environment where tenants are granted access to self-service management tools, tenants should be limited to managing with their own resources.</span></span>
<span data-ttu-id="8f883-145">Nesses casos, você pode restringir quais parâmetros são expostos do cmdlet ou da função.</span><span class="sxs-lookup"><span data-stu-id="8f883-145">For these cases, you can restrict which parameters are exposed from the cmdlet or function.</span></span>

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

<span data-ttu-id="8f883-146">Em cenários mais avançados, também pode ser necessário restringir os valores que alguém pode fornecer a esses parâmetros.</span><span class="sxs-lookup"><span data-stu-id="8f883-146">In more advanced scenarios, you may also need to restrict which values someone can supply to these parameters.</span></span>
<span data-ttu-id="8f883-147">Os recursos de função permitem que seja definido um conjunto de valores permitidos ou um padrão de expressão regular que é avaliado para determinar se uma determinada entrada é permitida.</span><span class="sxs-lookup"><span data-stu-id="8f883-147">Role capabilities let you define a set of allowed values or a regular expression pattern that is evaluated to determine if a given input is allowed.</span></span>

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> <span data-ttu-id="8f883-148">Os [parâmetros comuns do PowerShell](https://technet.microsoft.com/library/hh847884.aspx) são sempre permitidos, mesmo que você restrinja os parâmetros disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8f883-148">The [common PowerShell parameters](https://technet.microsoft.com/library/hh847884.aspx) are always allowed, even if you restrict the available parameters.</span></span>
> <span data-ttu-id="8f883-149">Você não deve listá-los explicitamente no campo Parâmetros.</span><span class="sxs-lookup"><span data-stu-id="8f883-149">You should not explicitly list them in the Parameters field.</span></span>

<span data-ttu-id="8f883-150">A tabela a seguir descreve as várias maneiras que podem ser usadas para personalizar um cmdlet ou função visível.</span><span class="sxs-lookup"><span data-stu-id="8f883-150">The table below describes the various ways you can customize a visible cmdlet or function.</span></span>
<span data-ttu-id="8f883-151">Você pode misturar e combinar qualquer item abaixo no campo VisibleCmdlets.</span><span class="sxs-lookup"><span data-stu-id="8f883-151">You can mix and match any of the below in the VisibleCmdlets field.</span></span>

<span data-ttu-id="8f883-152">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8f883-152">Example</span></span>                                                                                      | <span data-ttu-id="8f883-153">Caso de uso</span><span class="sxs-lookup"><span data-stu-id="8f883-153">Use case</span></span>
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
<span data-ttu-id="8f883-154">`'My-Func'` ou `@{ Name = 'My-Func' }`</span><span class="sxs-lookup"><span data-stu-id="8f883-154">`'My-Func'` or `@{ Name = 'My-Func' }`</span></span>                                                       | <span data-ttu-id="8f883-155">Permite que o usuário execute `My-Func` sem quaisquer restrições nos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="8f883-155">Allows the user to run `My-Func` without any restrictions on the parameters.</span></span>
`'MyModule\My-Func'`                                                                         | <span data-ttu-id="8f883-156">Permite que o usuário execute `My-Func` do módulo `MyModule` sem quaisquer restrições nos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="8f883-156">Allows the user to run `My-Func` from the module `MyModule` without any restrictions on the parameters.</span></span>
`'My-*'`                                                                                     | <span data-ttu-id="8f883-157">Permite que o usuário execute qualquer cmdlet ou função com o verbo `My`.</span><span class="sxs-lookup"><span data-stu-id="8f883-157">Allows the user to run any cmdlet or function with the verb `My`.</span></span>
`'*-Func'`                                                                                   | <span data-ttu-id="8f883-158">Permite que o usuário execute qualquer cmdlet ou função com o substantivo `Func`.</span><span class="sxs-lookup"><span data-stu-id="8f883-158">Allows the user to run any cmdlet or function with the noun `Func`.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | <span data-ttu-id="8f883-159">Permite que o usuário execute `My-Func` com os parâmetros `Param1` e/ou `Param2`.</span><span class="sxs-lookup"><span data-stu-id="8f883-159">Allows the user to run `My-Func` with the `Param1` and/or `Param2` parameters.</span></span> <span data-ttu-id="8f883-160">Qualquer valor pode ser fornecido para os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="8f883-160">Any value can be supplied to the parameters.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | <span data-ttu-id="8f883-161">Permite que o usuário execute `My-Func` com o parâmetro `Param1`.</span><span class="sxs-lookup"><span data-stu-id="8f883-161">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="8f883-162">Somente "Value1" e "Value2" podem ser fornecidos ao parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8f883-162">Only "Value1" and "Value2" can be supplied to the parameter.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | <span data-ttu-id="8f883-163">Permite que o usuário execute `My-Func` com o parâmetro `Param1`.</span><span class="sxs-lookup"><span data-stu-id="8f883-163">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="8f883-164">Qualquer valor começando com "contoso" pode ser fornecido ao parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8f883-164">Any value starting with "contoso" can be supplied to the parameter.</span></span>


> [!WARNING]
> <span data-ttu-id="8f883-165">Como práticas recomendadas de segurança, não é recomendável usar curingas ao definir cmdlets ou funções visíveis.</span><span class="sxs-lookup"><span data-stu-id="8f883-165">For best security practices, it is not recommended to use wildcards when defining visible cmdlets or functions.</span></span>
> <span data-ttu-id="8f883-166">Em vez disso, você deve listar explicitamente cada comando confiável para garantir que outros comandos que compartilham o mesmo esquema de nomenclatura não sejam acidentalmente autorizados.</span><span class="sxs-lookup"><span data-stu-id="8f883-166">Instead, you should explicitly list each trusted command to ensure no other commands that share the same naming scheme are unintentionally authorized.</span></span>

<span data-ttu-id="8f883-167">Você não pode aplicar um ValidatePattern e ValidateSet no mesmo cmdlet ou função.</span><span class="sxs-lookup"><span data-stu-id="8f883-167">You cannot apply both a ValidatePattern and ValidateSet to the same cmdlet or function.</span></span>

<span data-ttu-id="8f883-168">Se isso acontecer, o ValidatePattern substituirá o ValidateSet.</span><span class="sxs-lookup"><span data-stu-id="8f883-168">If you do, the ValidatePattern will override the ValidateSet.</span></span>

<span data-ttu-id="8f883-169">Para obter mais informações sobre ValidatePattern, dê uma olhada [nessa postagem *Hey, Scripting Guy!*](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) e no conteúdo de referência [Expressões regulares do PowerShell](https://technet.microsoft.com/library/hh847880.aspx).</span><span class="sxs-lookup"><span data-stu-id="8f883-169">For more information about ValidatePattern, check out [this *Hey, Scripting Guy!* post](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) and the [PowerShell Regular Expressions](https://technet.microsoft.com/library/hh847880.aspx) reference content.</span></span>

### <a name="allowing-external-commands-and-powershell-scripts"></a><span data-ttu-id="8f883-170">Permitindo comandos externos e scripts do PowerShell</span><span class="sxs-lookup"><span data-stu-id="8f883-170">Allowing external commands and PowerShell scripts</span></span>

<span data-ttu-id="8f883-171">Para permitir que os usuários executem scripts do PowerShell (.ps1) e arquivos executáveis em uma sessão JEA, é necessário adicionar o caminho completo para cada programa no campo VisibleExternalCommands.</span><span class="sxs-lookup"><span data-stu-id="8f883-171">To allow users to run executables and PowerShell scripts (.ps1) in a JEA session, you have to add the full path to each program in the VisibleExternalCommands field.</span></span>

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

<span data-ttu-id="8f883-172">É recomendável, sempre que possível, usar cmdlets ou funções do PowerShell equivalentes às dos arquivos externos executáveis que você autorizar, pois você tem controle sobre quais parâmetros são permitidos com cmdlets ou funções do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8f883-172">It is advised, where possible, to use PowerShell cmdlet/function equivalents of any external executables you authorize since you have control over which parameters are allowed with PowerShell cmdlets/functions.</span></span>

<span data-ttu-id="8f883-173">Muitos executáveis permitem que você leia o estado atual e, em seguida, altere-o simplesmente fornecendo parâmetros diferentes.</span><span class="sxs-lookup"><span data-stu-id="8f883-173">Many executables allow you to both read the current state and then change it just by providing different parameters.</span></span>

<span data-ttu-id="8f883-174">Por exemplo, considere a função de um administrador de servidor de arquivo que deseja verificar quais compartilhamentos de rede são hospedados pelo computador local.</span><span class="sxs-lookup"><span data-stu-id="8f883-174">For example, consider the role of a file server admin who wants to check which network shares are hosted by the local machine.</span></span>
<span data-ttu-id="8f883-175">Uma maneira de verificar é usar `net share`.</span><span class="sxs-lookup"><span data-stu-id="8f883-175">One way to check is to use `net share`.</span></span>
<span data-ttu-id="8f883-176">No entanto, permitir o net.exe é muito perigoso, pois o administrador poderia facilmente usar o comando para obter privilégios de administrador com `net group Administrators unprivilegedjeauser /add`.</span><span class="sxs-lookup"><span data-stu-id="8f883-176">However, allowing net.exe is very dangerous becuase the admin could just as easily use the command to gain admin privileges with `net group Administrators unprivilegedjeauser /add`.</span></span>
<span data-ttu-id="8f883-177">Uma abordagem melhor é permitir o [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) que alcança o mesmo resultado, mas tem um escopo muito mais limitado.</span><span class="sxs-lookup"><span data-stu-id="8f883-177">A better approach is to allow [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) which achieves the same result but has a much more limited scope.</span></span>

<span data-ttu-id="8f883-178">Ao disponibilizar comandos externos aos usuários em uma sessão JEA, sempre especifique o caminho completo para o executável para garantir que um programa nomeado da mesma forma (e potencialmente mal-intencionado) colocado em outro lugar no sistema não seja executado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="8f883-178">When making external commands available to users in a JEA session, always specify the complete path to the executable to ensure a similarly named (and potentially malicous) program placed elsewhere on the system does not get executed instead.</span></span>

### <a name="allowing-access-to-powershell-providers"></a><span data-ttu-id="8f883-179">Permitindo acesso aos provedores do PowerShell</span><span class="sxs-lookup"><span data-stu-id="8f883-179">Allowing access to PowerShell providers</span></span>

<span data-ttu-id="8f883-180">Por padrão, nenhum provedor de PowerShell está disponível em sessões JEA.</span><span class="sxs-lookup"><span data-stu-id="8f883-180">By default, no PowerShell providers are available in JEA sessions.</span></span>

<span data-ttu-id="8f883-181">Isso é, principalmente, para reduzir o risco da revelação de informações confidenciais e definições de configuração ao usuário que está se conectando.</span><span class="sxs-lookup"><span data-stu-id="8f883-181">This is primarily to reduce the risk of sensitive information and configuration settings being disclosed to the connecting user.</span></span>

<span data-ttu-id="8f883-182">Quando necessário, você pode permitir acesso aos provedores do PowerShell usando o comando `VisibleProviders`.</span><span class="sxs-lookup"><span data-stu-id="8f883-182">When necessary, you can allow access to the PowerShell providers using the `VisibleProviders` command.</span></span>
<span data-ttu-id="8f883-183">Para obter uma lista completa dos provedores, execute o `Get-PSProvider`.</span><span class="sxs-lookup"><span data-stu-id="8f883-183">For a full list of providers, run `Get-PSProvider`.</span></span>

```powershell
VisibleProviders = 'Registry'
```

<span data-ttu-id="8f883-184">Para tarefas simples que exigem acesso ao sistema de arquivos, Registro, repositório de certificados ou outros provedores confidenciais, você também pode considerar escrever uma função personalizada que funcione com o provedor em nome do usuário.</span><span class="sxs-lookup"><span data-stu-id="8f883-184">For simple tasks that require access to the file system, registry, certificate store, or other sensitive providers, you can also consider writing a custom function that works with the provider on the user's behalf.</span></span>
<span data-ttu-id="8f883-185">Funções, cmdlets e programas externos que estão disponíveis em uma sessão JEA não estão sujeitos às mesmas restrições que o JEA. Eles podem acessar qualquer provedor por padrão.</span><span class="sxs-lookup"><span data-stu-id="8f883-185">Functions, cmdlets, and external programs that are available in a JEA session are not subject to the same constraints as JEA -- they can access any provider by default.</span></span>
<span data-ttu-id="8f883-186">Considere também usar a [unidade de usuário](session-configurations.md#user-drive) quando for necessário copiar arquivos para/de um ponto de extremidade JEA.</span><span class="sxs-lookup"><span data-stu-id="8f883-186">Also consider using the [user drive](session-configurations.md#user-drive) when copying files to/from a JEA endpoint is required.</span></span>

### <a name="creating-custom-functions"></a><span data-ttu-id="8f883-187">Criando funções personalizadas</span><span class="sxs-lookup"><span data-stu-id="8f883-187">Creating custom functions</span></span>

<span data-ttu-id="8f883-188">Você pode criar funções personalizadas em um arquivo de capacidade de função para simplificar tarefas complexas para os seus usuários finais.</span><span class="sxs-lookup"><span data-stu-id="8f883-188">You can author custom functions in a role capability file to simplify complex tasks for your end users.</span></span>
<span data-ttu-id="8f883-189">As funções personalizadas também são úteis quando você precisar de lógica de validação avançada para valores de parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8f883-189">Custom functions are also useful when you require advanced validation logic for cmdlet parameter values.</span></span>
<span data-ttu-id="8f883-190">É possível escrever funções simples no campo **FunctionDefinitions**:</span><span class="sxs-lookup"><span data-stu-id="8f883-190">You can write simple functions in the **FunctionDefinitions** field:</span></span>

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending | Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="8f883-191">Não se esqueça de adicionar o nome de suas funções personalizadas no campo **VisibleFunctions** para que elas possam ser executadas pelos usuários JEA.</span><span class="sxs-lookup"><span data-stu-id="8f883-191">Don't forget to add the name of your custom functions to the **VisibleFunctions** field so they can be run by the JEA users.</span></span>


<span data-ttu-id="8f883-192">O corpo (bloco de script) de funções personalizadas é executado no modo de idioma padrão do sistema e não está sujeito a restrições de linguagem do JEA.</span><span class="sxs-lookup"><span data-stu-id="8f883-192">The body (script block) of custom functions runs in the default language mode for the system and is not subject to JEA's language constraints.</span></span>
<span data-ttu-id="8f883-193">Isso significa que as funções podem acessar o sistema de arquivos e o Registro e executar comandos que não foram tornados visíveis no arquivo de capacidade de função.</span><span class="sxs-lookup"><span data-stu-id="8f883-193">This means that functions can access the file system and registry, and run commands that were not made visible in the role capability file.</span></span>
<span data-ttu-id="8f883-194">Tome cuidado para evitar a permissão de execução de códigos arbitrários ao usar parâmetros e evitar redirecionar a entrada do usuário diretamente em cmdlets como o `Invoke-Expression`.</span><span class="sxs-lookup"><span data-stu-id="8f883-194">Take care to avoid allowing arbitrary code to be run when using parameters and avoid piping user input directly into cmdlets like `Invoke-Expression`.</span></span>

<span data-ttu-id="8f883-195">No exemplo acima, você observará que o FQMN (nome do módulo totalmente qualificado) `Microsoft.PowerShell.Utility\Select-Object` foi usado em vez da abreviação `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="8f883-195">In the above example, you will notice that the fully qualified module name (FQMN) `Microsoft.PowerShell.Utility\Select-Object` was used instead of the shorthand `Select-Object`.</span></span>
<span data-ttu-id="8f883-196">As funções definidas em arquivos de capacidade de função ainda estão sujeitas ao escopo das sessões JEA, que inclui as funções de proxy que o JEA cria para restringir os comandos existentes.</span><span class="sxs-lookup"><span data-stu-id="8f883-196">Functions defined in role capability files are still subject to the scope of JEA sessions, which includes the proxy functions JEA creates to constrain existing commands.</span></span>

<span data-ttu-id="8f883-197">O Select-Object é um cmdlet padrão, restrito em todas as sessões JEA que não permite que você selecione propriedades arbitrárias em objetos.</span><span class="sxs-lookup"><span data-stu-id="8f883-197">Select-Object is a default, constrained cmdlet in all JEA sessions that doesn't allow you to select arbitrary properties on objects.</span></span>
<span data-ttu-id="8f883-198">Para usar o Select-Object irrestrito nas funções, você deve solicitar explicitamente a implementação completa, especificando o FQMN.</span><span class="sxs-lookup"><span data-stu-id="8f883-198">To use the unconstrained Select-Object in functions, you must explicitly request the full implementation by specifying the FQMN.</span></span>
<span data-ttu-id="8f883-199">Qualquer cmdlet restrito em uma sessão JEA exibirá o mesmo comportamento ao ser invocado de uma função, em acordo com a [precedência de comando](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence) do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8f883-199">Any constrained cmdlet in a JEA session will exhibit the same behavior when invoked from a function, in line with PowerShell's [command precedence](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span></span>

<span data-ttu-id="8f883-200">Se você estiver escrevendo muitas funções personalizadas, poderá ser mais fácil colocá-las em um [Módulo de Script do PowerShell](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="8f883-200">If you are writing a lot of custom functions, it may be easier to put them in a [PowerShell Script Module](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx).</span></span>
<span data-ttu-id="8f883-201">Em seguida, você pode tornar essas funções visíveis na sessão JEA, usando o campo VisibleFunctions, assim como faria com módulos internos e de terceiros.</span><span class="sxs-lookup"><span data-stu-id="8f883-201">You can then make those functions visible in the JEA session using the VisibleFunctions field like you would with built-in and third party modules.</span></span>

## <a name="place-role-capabilities-in-a-module"></a><span data-ttu-id="8f883-202">Colocar recursos de função em um módulo</span><span class="sxs-lookup"><span data-stu-id="8f883-202">Place role capabilities in a module</span></span>

<span data-ttu-id="8f883-203">Para que o PowerShell localize um arquivo de capacidade de função, ele deve ser armazenado em uma pasta "RoleCapabilities" em um módulo do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8f883-203">In order for PowerShell to find a role capability file, it must be stored in a "RoleCapabilities" folder in a PowerShell module.</span></span>
<span data-ttu-id="8f883-204">O módulo pode ser armazenado em qualquer pasta incluída na variável de ambiente `$env:PSModulePath`, porém você não deve colocá-lo na System32 (reservada para módulos internos) ou uma pasta em que os usuários não confiáveis que estejam se conectando poderiam modificar os arquivos.</span><span class="sxs-lookup"><span data-stu-id="8f883-204">The module can be stored in any folder included in the `$env:PSModulePath` environment variable, however you should not place it in System32 (reserved for built-in modules) or a folder where the untrusted, connecting users could modify the files.</span></span>
<span data-ttu-id="8f883-205">Abaixo está um exemplo de criação de um módulo de script do PowerShell básico chamado *ContosoJEA* no caminho "Arquivos de Programas".</span><span class="sxs-lookup"><span data-stu-id="8f883-205">Below is an example of creating a basic PowerShell script module called *ContosoJEA* in the "Program Files" path.</span></span>

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest. At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

<span data-ttu-id="8f883-206">Consulte [Noções básicas sobre um Módulo do PowerShell](https://msdn.microsoft.com/en-us/library/dd878324.aspx) para obter mais informações sobre módulos do PowerShell, manifestos de módulo e sobre a variável de ambiente PSModulePath.</span><span class="sxs-lookup"><span data-stu-id="8f883-206">See [Understanding a PowerShell Module](https://msdn.microsoft.com/en-us/library/dd878324.aspx) for more information about PowerShell modules, module manifests, and the PSModulePath environment variable.</span></span>

## <a name="updating-role-capabilities"></a><span data-ttu-id="8f883-207">Atualizando recursos de função</span><span class="sxs-lookup"><span data-stu-id="8f883-207">Updating role capabilities</span></span>


<span data-ttu-id="8f883-208">Você pode atualizar um arquivo de capacidade de função a qualquer momento, bastando salvar as alterações no arquivo de capacidade de função.</span><span class="sxs-lookup"><span data-stu-id="8f883-208">You can update a role capability file at any time by simply saving changes to the role capability file.</span></span>
<span data-ttu-id="8f883-209">Qualquer nova sessão JEA iniciada depois que a capacidade de função foi atualizado refletirá os recursos revisados.</span><span class="sxs-lookup"><span data-stu-id="8f883-209">Any new JEA sessions started after the role capability has been updated will reflect the revised capabilities.</span></span>

<span data-ttu-id="8f883-210">É por isso que é tão importante controlar o acesso à pasta de recursos de função.</span><span class="sxs-lookup"><span data-stu-id="8f883-210">This is why controlling access to the role capabilities folder is so important.</span></span>
<span data-ttu-id="8f883-211">Apenas administradores altamente confiáveis devem ser capazes de alterar os arquivos de capacidade de função.</span><span class="sxs-lookup"><span data-stu-id="8f883-211">Only highly trusted administrators should be able to change role capability files.</span></span>
<span data-ttu-id="8f883-212">Se um usuário não confiável puder alterar os arquivos de capacidade de função, poderá facilmente conceder a si próprio o acesso aos cmdlets que permitem que ele eleve seus privilégios.</span><span class="sxs-lookup"><span data-stu-id="8f883-212">If an untrusted user can change role capability files, they can easily give themselves access to cmdlets which allow them to elevate their privileges.</span></span>


<span data-ttu-id="8f883-213">Para os administradores que desejam bloquear o acesso às capacidades de função, verifique se a Sistema Local tem acesso de leitura aos arquivos de capacidade de função e aos módulos nesses arquivos.</span><span class="sxs-lookup"><span data-stu-id="8f883-213">For administrators looking to lock down access to the role capabilities, ensure Local System has read access to the role capability files and containing modules.</span></span>

## <a name="how-role-capabilities-are-merged"></a><span data-ttu-id="8f883-214">Como os recursos de função são mesclados</span><span class="sxs-lookup"><span data-stu-id="8f883-214">How role capabilities are merged</span></span>

<span data-ttu-id="8f883-215">Os usuários podem ter acesso a vários recursos de função quando ingressam em uma sessão JEA, dependendo dos mapeamentos de função no [arquivo de configuração de sessão](session-configurations.md).</span><span class="sxs-lookup"><span data-stu-id="8f883-215">Users can be granted access to multiple role capabilities when they enter a JEA session depending on the role mappings in the [session configuration file](session-configurations.md).</span></span>
<span data-ttu-id="8f883-216">Quando isso acontece, o JEA tenta conceder ao usuário o conjunto *mais permissivo* de comandos, permitido por qualquer uma das funções.</span><span class="sxs-lookup"><span data-stu-id="8f883-216">When this happens, JEA tries to give the user the *most permissive* set of commands allowed by any of the roles.</span></span>

<span data-ttu-id="8f883-217">**VisibleCmdlets e VisibleFunctions**</span><span class="sxs-lookup"><span data-stu-id="8f883-217">**VisibleCmdlets and VisibleFunctions**</span></span>

<span data-ttu-id="8f883-218">A lógica mais complexa de mesclagem afeta cmdlets e funções, que podem ter seus parâmetros e valores de parâmetro limitados no JEA.</span><span class="sxs-lookup"><span data-stu-id="8f883-218">The most complex merge logic affects cmdlets and functions, which can have their parameters and parameter values limited in JEA.</span></span>

<span data-ttu-id="8f883-219">As regras são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="8f883-219">The rules are as follows:</span></span>

1. <span data-ttu-id="8f883-220">Se um cmdlet só for visível em uma função, será visível para o usuário com qualquer restrição de parâmetro aplicável.</span><span class="sxs-lookup"><span data-stu-id="8f883-220">If a cmdlet is only made visible in one role, it will be visible to the user with any applicable parameter constraints.</span></span>
2. <span data-ttu-id="8f883-221">Se um cmdlet se torna visível em mais de uma função e cada função tem as mesmas restrições sobre o cmdlet, o cmdlet será visível para o usuário com essas restrições.</span><span class="sxs-lookup"><span data-stu-id="8f883-221">If a cmdlet is made visible in more than one role, and each role has the same constraints on the cmdlet, the cmdlet will be visible to the user with those constraints.</span></span>
3. <span data-ttu-id="8f883-222">Se um cmdlet se torna visível em mais de uma função e cada função permite um conjunto diferente de parâmetros, o cmdlet e todos os parâmetros definidos em cada função serão visíveis ao usuário.</span><span class="sxs-lookup"><span data-stu-id="8f883-222">If a cmdlet is made visible in more than one role, and each role allows a different set of parameters, the cmdlet and all of the parameters defined across every role will be visible to the user.</span></span> <span data-ttu-id="8f883-223">Se uma função não tem restrições nos parâmetros, todos os parâmetros serão permitidos.</span><span class="sxs-lookup"><span data-stu-id="8f883-223">If one role doesn't have constraints on the parameters, all parameters will be allowed.</span></span>
4. <span data-ttu-id="8f883-224">Se uma função define um conjunto de validação ou padrão de validação para um parâmetro de cmdlet e a outra função permite o parâmetro, mas não restringe os valores do parâmetro, o conjunto ou padrão de validação serão ignorados.</span><span class="sxs-lookup"><span data-stu-id="8f883-224">If one role defines a validate set or validate pattern for a cmdlet parameter, and the other role allows the parameter but does not constrain the parameter values, the validate set or pattern will be ignored.</span></span>
5. <span data-ttu-id="8f883-225">Se um conjunto de validação for definido para o mesmo parâmetro de cmdlet em mais de uma função, todos os valores de todos os conjuntos de validação serão permitidos.</span><span class="sxs-lookup"><span data-stu-id="8f883-225">If a validate set is defined for the same cmdlet parameter in more than one role, all values from all validate sets will be allowed.</span></span>
6. <span data-ttu-id="8f883-226">Se um padrão de validação for definido para o mesmo parâmetro de cmdlet em mais de uma função, qualquer valor que corresponde a qualquer dos padrões será permitido.</span><span class="sxs-lookup"><span data-stu-id="8f883-226">If a validate pattern is defined for the same cmdlet parameter in more than one role, any values that match any of the patterns will be allowed.</span></span>
7. <span data-ttu-id="8f883-227">Se um conjunto de validação for definido em uma ou mais funções e um padrão de validação for definido em outra função para o mesmo parâmetro de cmdlet, o conjunto de validação será ignorado e a regra (6) se aplica aos padrões de validação restantes.</span><span class="sxs-lookup"><span data-stu-id="8f883-227">If a validate set is defined in one or more roles, and a validate pattern is defined in another role for the same cmdlet parameter, the validate set is ignored and rule (6) applies to the remaining validate patterns.</span></span>

<span data-ttu-id="8f883-228">O exemplo abaixo mostra como as funções são mescladas de acordo com essas regras:</span><span class="sxs-lookup"><span data-stu-id="8f883-228">Below is an example of how roles are merged according to these rules:</span></span>

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permisisons for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service is ignored becuase of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```



<span data-ttu-id="8f883-229">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span><span class="sxs-lookup"><span data-stu-id="8f883-229">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span></span>

<span data-ttu-id="8f883-230">Todos os outros campos no arquivo de capacidade de função são simplesmente adicionados a um conjunto cumulativo de comandos externos permitidos, aliases, provedores e scripts de inicialização.</span><span class="sxs-lookup"><span data-stu-id="8f883-230">All other fields in the role capability file are simply added to a cumulative set of allowable external commands, aliases, providers, and startup scripts.</span></span>
<span data-ttu-id="8f883-231">Qualquer comando, alias, provedor ou script disponível em um capacidade de função estará disponível para o usuário JEA.</span><span class="sxs-lookup"><span data-stu-id="8f883-231">Any command, alias, provider, or script available in one role capability will be available to the JEA user.</span></span>

<span data-ttu-id="8f883-232">Verifique com cuidado se o conjunto combinado de provedores de um capacidade de função e funções/cmdlets/comandos de outro recurso de função não permitem aos usuários que estão se conectando o acesso involuntário aos recursos do sistema.</span><span class="sxs-lookup"><span data-stu-id="8f883-232">Be careful to ensure that the combined set of providers from one role capability and cmdlets/functions/commands from another do not allow connecting users unintentional access to system resources.</span></span>
<span data-ttu-id="8f883-233">Por exemplo, se uma função permite o cmdlet `Remove-Item` e outra função permite o provedor `FileSystem`, haverá um risco de um usuário JEA excluir arquivos arbitrários no seu computador.</span><span class="sxs-lookup"><span data-stu-id="8f883-233">For example, if one role allows the `Remove-Item` cmdlet and another allows the `FileSystem` provider, you are at risk of a JEA user deleting arbitrary files on your computer.</span></span>
<span data-ttu-id="8f883-234">Informações adicionais sobre como identificar as permissões efetivas dos usuários podem ser encontradas no [tópico auditoria do JEA](audit-and-report.md).</span><span class="sxs-lookup"><span data-stu-id="8f883-234">Additional information about identifying users' effective permissions can be found in the [auditing JEA topic](audit-and-report.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="8f883-235">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="8f883-235">Next steps</span></span>

- [<span data-ttu-id="8f883-236">Criar um arquivo de configuração de sessão</span><span class="sxs-lookup"><span data-stu-id="8f883-236">Create a session configuration file</span></span>](session-configurations.md)