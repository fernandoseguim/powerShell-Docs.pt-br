---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Como usar perfis no ISE do Windows PowerShell
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
ms.openlocfilehash: b319aa089c2a4a7008acd9850f15342dac70aee2
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400278"
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a><span data-ttu-id="ddeec-103">Como usar perfis no ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ddeec-103">How to Use Profiles in Windows PowerShell ISE</span></span>

<span data-ttu-id="ddeec-104">Este tópico explica como usar perfis no ISE (Ambiente de Script Integrado) do Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="ddeec-104">This topic explains how to use Profiles in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="ddeec-105">Antes de executar as tarefas nesta seção, recomendamos examinar [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) ou, no Painel de Console, digite `Get-Help about_Profiles` e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="ddeec-105">We recommend that before performing the tasks in this section, you review [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), or in the Console Pane, type, `Get-Help about_Profiles` and press **ENTER**.</span></span>

<span data-ttu-id="ddeec-106">Um perfil é um script do ISE do Windows PowerShell executado automaticamente quando você inicia uma nova sessão.</span><span class="sxs-lookup"><span data-stu-id="ddeec-106">A profile is a Windows PowerShell ISE script that runs automatically when you start a new session.</span></span>  <span data-ttu-id="ddeec-107">Você pode criar um ou mais perfis do Windows PowerShell para o ISE do Windows PowerShell e usá-los para adicionar a configuração do Windows PowerShell ou o ambiente ISE do Windows PowerShell, preparando-o para seu uso, com variáveis, aliases, funções, cores e preferências de fonte que você quer disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ddeec-107">You can create one or more Windows PowerShell profiles for Windows PowerShell ISE and use them to add the configure the Windows PowerShell or Windows PowerShell ISE environment, preparing it for your use, with variables, aliases, functions, and color and font preferences that you want available.</span></span> <span data-ttu-id="ddeec-108">Um perfil afeta cada sessão de ISE do Windows PowerShell que você começar.</span><span class="sxs-lookup"><span data-stu-id="ddeec-108">A profile affects every Windows PowerShell ISE session that you start.</span></span>

> [!NOTE]
> <span data-ttu-id="ddeec-109">A política de execução do Windows PowerShell determina se você pode executar scripts e carregar um perfil.</span><span class="sxs-lookup"><span data-stu-id="ddeec-109">The Windows PowerShell execution policy determines whether you can run scripts and load a profile.</span></span> <span data-ttu-id="ddeec-110">A política de execução padrão, “Restricted”, impede a execução de todos os scripts, incluindo perfis.</span><span class="sxs-lookup"><span data-stu-id="ddeec-110">The default execution policy, “Restricted,” prevents all scripts from running, including profiles.</span></span> <span data-ttu-id="ddeec-111">Se você usar a política “Restricted”, não será possível carregar o perfil.</span><span class="sxs-lookup"><span data-stu-id="ddeec-111">If you use the “Restricted” policy, the profile cannot load.</span></span> <span data-ttu-id="ddeec-112">Para saber mais sobre Política de Execução, confira [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="ddeec-112">For more information about execution policy, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a><span data-ttu-id="ddeec-113">Selecionar um perfil para usar com o ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ddeec-113">Selecting a profile to use in the Windows PowerShell ISE</span></span>

<span data-ttu-id="ddeec-114">O ISE do Windows PowerShell dá suporte a perfis para o usuário atual e todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="ddeec-114">Windows PowerShell ISE supports profiles for the current user and all users.</span></span> <span data-ttu-id="ddeec-115">Ele também dá suporte a perfis do Windows PowerShell que se aplicam a todos os hosts.</span><span class="sxs-lookup"><span data-stu-id="ddeec-115">It also supports the Windows PowerShell profiles that apply to all hosts.</span></span>

<span data-ttu-id="ddeec-116">O perfil que você usa é determinado pela forma como você usa o Windows PowerShell e o ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ddeec-116">The profile that you use is determined by how you use Windows PowerShell and Windows PowerShell ISE.</span></span>

- <span data-ttu-id="ddeec-117">Se você usar apenas o ISE do Windows PowerShell para executar o Windows PowerShell, salve todos os seus itens em um dos perfis específicos do ISE, como o perfil CurrentUserCurrentHost ou o perfil AllUsersCurrentHost para o ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ddeec-117">If you use only Windows PowerShell ISE to run Windows PowerShell, then save all your items in one of the ISE-specific profiles, such as the CurrentUserCurrentHost profile for Windows PowerShell ISE or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="ddeec-118">Se você usar vários programas host para executar o Windows PowerShell, salve funções, aliases, variáveis e comandos em um perfil que afete todos os programas host, como o perfil CurrentUserAllHosts ou AllUsersAllHosts, e salve recursos específicos do ISE, como cor e personalização de fonte, no perfil CurrentUserCurrentHost do perfil do ISE do Windows PowerShell ou o perfil AllUsersCurrentHost do ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ddeec-118">If you use multiple host programs to run Windows PowerShell, save your functions, aliases, variables, and commands in a profile that affects all host programs, such as the CurrentUserAllHosts or the AllUsersAllHosts profile, and save ISE-specific features, like color and font customization in the CurrentUserCurrentHost profile for Windows PowerShell ISE profile or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

<span data-ttu-id="ddeec-119">A seguir, os perfis que podem ser criados e usados no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ddeec-119">The following are profiles that can be created and used in Windows PowerShell ISE.</span></span> <span data-ttu-id="ddeec-120">Cada perfil é salvo em seu próprio caminho específico.</span><span class="sxs-lookup"><span data-stu-id="ddeec-120">Each profile is saved to its own specific path.</span></span>

| <span data-ttu-id="ddeec-121">Tipo de Perfil</span><span class="sxs-lookup"><span data-stu-id="ddeec-121">Profile Type</span></span> | <span data-ttu-id="ddeec-122">Caminho do Perfil</span><span class="sxs-lookup"><span data-stu-id="ddeec-122">Profile Path</span></span> |
| --- | --- |
| <span data-ttu-id="ddeec-123">**Usuário atual, ISE do PowerShell**</span><span class="sxs-lookup"><span data-stu-id="ddeec-123">**Current user, PowerShell ISE**</span></span>| <span data-ttu-id="ddeec-124">`$PROFILE.CurrentUserCurrentHost` ou `$PROFILE`</span><span class="sxs-lookup"><span data-stu-id="ddeec-124">`$PROFILE.CurrentUserCurrentHost`, or `$PROFILE`</span></span> |
| <span data-ttu-id="ddeec-125">**Todos os usuários, ISE do PowerShell**</span><span class="sxs-lookup"><span data-stu-id="ddeec-125">**All users, PowerShell ISE**</span></span>| `$PROFILE.AllUsersCurrentHost` |
| <span data-ttu-id="ddeec-126">**Usuário atual, Todos os hosts**</span><span class="sxs-lookup"><span data-stu-id="ddeec-126">**Current user, All hosts**</span></span>| `$PROFILE.CurrentUserAllHosts` |
| <span data-ttu-id="ddeec-127">**Todos os usuários, Todos os hosts**</span><span class="sxs-lookup"><span data-stu-id="ddeec-127">**All users, All hosts**</span></span> | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a><span data-ttu-id="ddeec-128">Para criar um novo perfil</span><span class="sxs-lookup"><span data-stu-id="ddeec-128">To create a new profile</span></span>

<span data-ttu-id="ddeec-129">Para criar um novo perfil de "Usuário atual, ISE do Windows PowerShell", execute este comando:</span><span class="sxs-lookup"><span data-stu-id="ddeec-129">To create a new “Current user, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

<span data-ttu-id="ddeec-130">Para criar um novo perfil de "Todos os usuários, ISE do Windows PowerShell", execute este comando:</span><span class="sxs-lookup"><span data-stu-id="ddeec-130">To create a new “All users, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

<span data-ttu-id="ddeec-131">Para criar um novo perfil de "Usuário atual, Todos os Hosts", execute este comando:</span><span class="sxs-lookup"><span data-stu-id="ddeec-131">To create a new “Current user, All Hosts” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

<span data-ttu-id="ddeec-132">Para criar um novo perfil de "Todos os usuários, Todos os Hosts", digite:</span><span class="sxs-lookup"><span data-stu-id="ddeec-132">To create a new “All users, All Hosts” profile, type:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a><span data-ttu-id="ddeec-133">Para editar um perfil</span><span class="sxs-lookup"><span data-stu-id="ddeec-133">To edit a profile</span></span>

1. <span data-ttu-id="ddeec-134">Para abrir o perfil, execute o comando psedit com a variável que especifica o perfil que você deseja editar.</span><span class="sxs-lookup"><span data-stu-id="ddeec-134">To open the profile, run the command psedit with the variable that specifies the profile you want to edit.</span></span> <span data-ttu-id="ddeec-135">Por exemplo, para abrir o perfil de "Usuário atual, ISE do Windows PowerShell", digite: `psEdit $PROFILE`</span><span class="sxs-lookup"><span data-stu-id="ddeec-135">For example, to open the “Current user, Windows PowerShell ISE” profile, type: `psEdit $PROFILE`</span></span>

2. <span data-ttu-id="ddeec-136">Adicione alguns itens ao seu perfil.</span><span class="sxs-lookup"><span data-stu-id="ddeec-136">Add some items to your profile.</span></span> <span data-ttu-id="ddeec-137">A seguir estão alguns exemplos para começar:</span><span class="sxs-lookup"><span data-stu-id="ddeec-137">The following are a few examples to get you started:</span></span>

   - <span data-ttu-id="ddeec-138">Para alterar a cor da tela de fundo padrão do Painel de Console para azul, digite o seguinte no arquivo do perfil: `$psISE.Options.OutputPaneBackground = 'blue'` .</span><span class="sxs-lookup"><span data-stu-id="ddeec-138">To change the default background color of the Console Pane to blue, in the profile file type: `$psISE.Options.OutputPaneBackground = 'blue'` .</span></span> <span data-ttu-id="ddeec-139">Para obter mais informações sobre a variável $psISE, consulte a [Referência de Modelo de Objeto do ISE do Windows PowerShell](object-model/The-ISE-Object-Model-Hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="ddeec-139">For more information about the $psISE variable, see [Windows PowerShell ISE Object Model Reference](object-model/The-ISE-Object-Model-Hierarchy.md).</span></span>

   - <span data-ttu-id="ddeec-140">Para alterar o tamanho da fonte para 20, digite o seguinte no tipo de arquivo do perfil: `$psISE.Options.FontSize =20`</span><span class="sxs-lookup"><span data-stu-id="ddeec-140">To change font size to 20, in the profile file type: `$psISE.Options.FontSize =20`</span></span>

3. <span data-ttu-id="ddeec-141">Para salvar esse arquivo de perfil, no menu **Arquivo**, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="ddeec-141">To save your profile file, on the **File** menu, click **Save**.</span></span> <span data-ttu-id="ddeec-142">Da próxima vez que você abrir o ISE do Windows PowerShell, as personalizações serão aplicadas.</span><span class="sxs-lookup"><span data-stu-id="ddeec-142">Next time you open the Windows PowerShell ISE, your customizations are applied.</span></span>

## <a name="see-also"></a><span data-ttu-id="ddeec-143">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="ddeec-143">See Also</span></span>

- [<span data-ttu-id="ddeec-144">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="ddeec-144">about_Profiles</span></span>](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [<span data-ttu-id="ddeec-145">Apresentando o ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ddeec-145">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)