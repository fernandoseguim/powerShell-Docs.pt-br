---
ms.date: 06/12/2017
keywords: jea,powershell,segurança
title: Pré-requisitos do JEA
ms.openlocfilehash: a5cf5519b30b24d44c12bdeedcf4cd763e2edbde
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189764"
---
# <a name="prerequisites"></a><span data-ttu-id="2786f-103">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="2786f-103">Prerequisites</span></span>

> <span data-ttu-id="2786f-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2786f-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="2786f-105">O Just Enough Administration é um recurso incluído com o Windows PowerShell 5.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="2786f-105">Just Enough Administration is a feature included with Windows PowerShell 5.0 and higher.</span></span>
<span data-ttu-id="2786f-106">Este tópico descreve os pré-requisitos que devem ser atendidos para começar a usar o JEA.</span><span class="sxs-lookup"><span data-stu-id="2786f-106">This topic describes the prerequisites that must be satisfied in order to start using JEA.</span></span>

## <a name="install-jea"></a><span data-ttu-id="2786f-107">Instalar o JEA</span><span class="sxs-lookup"><span data-stu-id="2786f-107">Install JEA</span></span>

<span data-ttu-id="2786f-108">O JEA está disponível com o Windows PowerShell 5.0 e posteriores, mas para a funcionalidade completa é recomendado que você instale a versão mais recente do PowerShell disponível para o seu sistema.</span><span class="sxs-lookup"><span data-stu-id="2786f-108">JEA is available with Windows PowerShell 5.0 and higher, but for full functionality it is recommended that you install the latest version of PowerShell available for your system.</span></span>
<span data-ttu-id="2786f-109">A tabela a seguir descreve a disponibilidade do JEA no Windows Server:</span><span class="sxs-lookup"><span data-stu-id="2786f-109">The following table describes JEA's availability on Windows Server:</span></span>

<span data-ttu-id="2786f-110">Sistema operacional de servidor</span><span class="sxs-lookup"><span data-stu-id="2786f-110">Server Operating System</span></span>   | <span data-ttu-id="2786f-111">Disponibilidade do JEA</span><span class="sxs-lookup"><span data-stu-id="2786f-111">JEA Availability</span></span>
--------------------------|--------------------------------
<span data-ttu-id="2786f-112">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="2786f-112">Windows Server 2016</span></span>       | <span data-ttu-id="2786f-113">Pré-instalado</span><span class="sxs-lookup"><span data-stu-id="2786f-113">Preinstalled</span></span>
<span data-ttu-id="2786f-114">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="2786f-114">Windows Server 2012 R2</span></span>    | <span data-ttu-id="2786f-115">Funcionalidade completa com o WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="2786f-115">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="2786f-116">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="2786f-116">Windows Server 2012</span></span>       | <span data-ttu-id="2786f-117">Funcionalidade completa com o WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="2786f-117">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="2786f-118">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="2786f-118">Windows Server 2008 R2</span></span>    | <span data-ttu-id="2786f-119">Funcionalidade reduzida<sup>1</sup> com WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="2786f-119">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="2786f-120">Você também pode usar o JEA no seu computador residencial ou do trabalho:</span><span class="sxs-lookup"><span data-stu-id="2786f-120">You can also use JEA on your home or work computer:</span></span>

<span data-ttu-id="2786f-121">Sistema Operacional do Cliente</span><span class="sxs-lookup"><span data-stu-id="2786f-121">Client Operating System</span></span>   | <span data-ttu-id="2786f-122">Disponibilidade do JEA</span><span class="sxs-lookup"><span data-stu-id="2786f-122">JEA Availability</span></span>
--------------------------|-----------------------------------------------------
<span data-ttu-id="2786f-123">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="2786f-123">Windows 10 1607+</span></span>          | <span data-ttu-id="2786f-124">Pré-instalado</span><span class="sxs-lookup"><span data-stu-id="2786f-124">Preinstalled</span></span>
<span data-ttu-id="2786f-125">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="2786f-125">Windows 10 1603, 1511</span></span>     | <span data-ttu-id="2786f-126">Pré-instalado, com funcionalidade reduzida<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="2786f-126">Preinstalled, with reduced functionality<sup>2</sup></span></span>
<span data-ttu-id="2786f-127">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="2786f-127">Windows 10 1507</span></span>           | <span data-ttu-id="2786f-128">Não disponível</span><span class="sxs-lookup"><span data-stu-id="2786f-128">Not available</span></span>
<span data-ttu-id="2786f-129">Windows 8, 8.1</span><span class="sxs-lookup"><span data-stu-id="2786f-129">Windows 8, 8.1</span></span>            | <span data-ttu-id="2786f-130">Funcionalidade completa com o WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="2786f-130">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="2786f-131">Windows 7</span><span class="sxs-lookup"><span data-stu-id="2786f-131">Windows 7</span></span>                 | <span data-ttu-id="2786f-132">Funcionalidade reduzida<sup>1</sup> com WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="2786f-132">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="2786f-133"><sup>1</sup> O JEA não pode ser configurado para usar contas de serviço gerenciado por grupo no Windows Server 2008 R2 ou Windows 7.</span><span class="sxs-lookup"><span data-stu-id="2786f-133"><sup>1</sup> JEA cannot be configured to use group managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span>
<span data-ttu-id="2786f-134">*Há suporte* para contas virtuais e outros recursos de JEA.</span><span class="sxs-lookup"><span data-stu-id="2786f-134">Virtual accounts and other JEA features *are* supported.</span></span>

<span data-ttu-id="2786f-135"><sup>2</sup> As versões 1511 e 1603 do Windows 10 não oferecem suporte aos seguintes recursos do JEA: execução como uma conta de serviço gerenciado de grupo, regras de acesso condicional nas configurações de sessão, a unidade do usuário e a concessão de acesso a contas de usuário local.</span><span class="sxs-lookup"><span data-stu-id="2786f-135"><sup>2</sup> Windows 10 versions 1511 and 1603 do not support the following JEA features: running as a group managed service account, conditional access rules in session configurations, the user drive, and granting access to local user accounts.</span></span>
<span data-ttu-id="2786f-136">Para obter suporte para esses recursos, atualize o Windows para a versão 1607 (Atualização de Aniversário) ou superior.</span><span class="sxs-lookup"><span data-stu-id="2786f-136">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="2786f-137">Verificar qual versão do PowerShell que está instalada</span><span class="sxs-lookup"><span data-stu-id="2786f-137">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="2786f-138">Para verificar qual a versão do PowerShell que está instalada em seu sistema, verifique a variável `$PSVersionTable` em um prompt do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2786f-138">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
PS C:\> $PSVersionTable.PSVersion

Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="2786f-139">Você está pronto para usar o JEA se a versão *Principal* for maior ou igual a **5**.</span><span class="sxs-lookup"><span data-stu-id="2786f-139">You are ready to use JEA if the *Major* version is equal to or greater than **5**.</span></span>
<span data-ttu-id="2786f-140">Para obter a melhor experiência e ter acesso a todos os recursos mais recentes, é recomendável que você atualize para a versão **5.1** do PowerShell assim que possível.</span><span class="sxs-lookup"><span data-stu-id="2786f-140">For the best experience, and to have access to all the latest features, it is recommended that you upgrade to PowerShell version **5.1** when possible.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="2786f-141">Instalar o Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="2786f-141">Install Windows Management Framework</span></span>

<span data-ttu-id="2786f-142">Se estiver executando uma versão mais antiga do PowerShell, você precisará atualizar o sistema com a atualização mais recente do WMF (Windows Management Framework).</span><span class="sxs-lookup"><span data-stu-id="2786f-142">If you are running an older version of PowerShell, you will need to update your system with the latest Windows Management Framework (WMF) update.</span></span>
<span data-ttu-id="2786f-143">Os pacotes de atualização e um link para as notas de versão mais recentes do WMF estão disponíveis no [Centro de Download](https://aka.ms/WMF5).</span><span class="sxs-lookup"><span data-stu-id="2786f-143">Update packages and a link to the latest WMF release notes are available in the [Download Center](https://aka.ms/WMF5).</span></span>

<span data-ttu-id="2786f-144">É altamente recomendável que você teste a compatibilidade da sua carga de trabalho com WMF antes de atualizar todos os seus servidores.</span><span class="sxs-lookup"><span data-stu-id="2786f-144">It is strongly recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="2786f-145">Os usuários do Windows 10 devem instalar as atualizações mais recentes do recurso para obter a versão atual do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2786f-145">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="2786f-146">Habilitar a Comunicação Remota do PowerShell</span><span class="sxs-lookup"><span data-stu-id="2786f-146">Enable PowerShell Remoting</span></span>

<span data-ttu-id="2786f-147">A Comunicação Remota do PowerShell fornece a base na qual o JEA é criado.</span><span class="sxs-lookup"><span data-stu-id="2786f-147">PowerShell Remoting provides the foundation on which JEA is built.</span></span>
<span data-ttu-id="2786f-148">Portanto, é necessário garantir que a comunicação remota do PowerShell esteja habilitada e [devidamente protegida](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity) em seu sistema antes de usar o JEA.</span><span class="sxs-lookup"><span data-stu-id="2786f-148">It is therefore necessary to ensure PowerShell Remoting is enabled and [properly secured](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity) on your system before you can use JEA.</span></span>

<span data-ttu-id="2786f-149">A Comunicação Remota do PowerShell é habilitada por padrão no Windows Server 2012, 2012 R2 e 2016.</span><span class="sxs-lookup"><span data-stu-id="2786f-149">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span>
<span data-ttu-id="2786f-150">Você pode habilitar a Comunicação Remota do PowerShell executando o seguinte comando em uma janela elevada do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2786f-150">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="2786f-151">Habilitar o módulo do PowerShell e o registro em log de bloco de script (opcional)</span><span class="sxs-lookup"><span data-stu-id="2786f-151">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="2786f-152">As etapas a seguir habilitam o log para todas as ações do PowerShell em seu sistema.</span><span class="sxs-lookup"><span data-stu-id="2786f-152">The following steps enable logging for all PowerShell actions on your system.</span></span>
<span data-ttu-id="2786f-153">O registro em log do Módulo do PowerShell não é necessário para o JEA, no entanto é altamente recomendável que você o ative para garantir que os comandos que os usuários executam sejam registrados em um local central.</span><span class="sxs-lookup"><span data-stu-id="2786f-153">PowerShell Module Logging is not required for JEA, however it is strongly recommended that you turn it on to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="2786f-154">Você pode configurar a política de Registro em Log do Módulo do PowerShell usando a Política de Grupo.</span><span class="sxs-lookup"><span data-stu-id="2786f-154">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="2786f-155">Abra o Editor de Política de Grupo Local em uma estação de trabalho ou um Objeto de Política de Grupo no Console de Gerenciamento de Política de Grupo em um Controlador de Domínio do Active Directory</span><span class="sxs-lookup"><span data-stu-id="2786f-155">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="2786f-156">Navegue até **Configuração do Computador\\Modelos Administrativos\\Componentes do Windows\\Windows PowerShell**</span><span class="sxs-lookup"><span data-stu-id="2786f-156">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="2786f-157">Clique duas vezes em **Habilitar o Log de Módulo**</span><span class="sxs-lookup"><span data-stu-id="2786f-157">Double click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="2786f-158">Clique em **Habilitado**</span><span class="sxs-lookup"><span data-stu-id="2786f-158">Click **Enabled**</span></span>
5. <span data-ttu-id="2786f-159">Na seção Opções, clique em **Mostrar** ao lado dos Nomes de Módulo</span><span class="sxs-lookup"><span data-stu-id="2786f-159">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="2786f-160">Digite "**\***" na janela pop-up.</span><span class="sxs-lookup"><span data-stu-id="2786f-160">Type "**\***" in the pop up window.</span></span> <span data-ttu-id="2786f-161">Isso instrui o PowerShell a registrar comandos de todos os módulos.</span><span class="sxs-lookup"><span data-stu-id="2786f-161">This instructs PowerShell to log commands from all modules.</span></span>
7. <span data-ttu-id="2786f-162">Clique em **OK** para definir a política</span><span class="sxs-lookup"><span data-stu-id="2786f-162">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="2786f-163">Clique duas vezes em **Ativar Registro de Bloco de Script do PowerShell**</span><span class="sxs-lookup"><span data-stu-id="2786f-163">Double click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="2786f-164">Clique em **Habilitado**</span><span class="sxs-lookup"><span data-stu-id="2786f-164">Click **Enabled**</span></span>
10. <span data-ttu-id="2786f-165">Clique em **OK** para definir a política</span><span class="sxs-lookup"><span data-stu-id="2786f-165">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="2786f-166">(Somente em computadores ingressados no domínio) Execute **gpupdate** ou aguarde a Política de Grupo processar a política atualizada e aplicar as configurações</span><span class="sxs-lookup"><span data-stu-id="2786f-166">(On domain-joined machines only) Run **gpupdate** or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="2786f-167">Você também pode habilitar transcrição do PowerShell de todo o sistema por meio da Política de Grupo.</span><span class="sxs-lookup"><span data-stu-id="2786f-167">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2786f-168">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="2786f-168">Next steps</span></span>

- [<span data-ttu-id="2786f-169">Criar um arquivo de capacidade de função</span><span class="sxs-lookup"><span data-stu-id="2786f-169">Create a role capability file</span></span>](role-capabilities.md)
- [<span data-ttu-id="2786f-170">Criar um arquivo de configuração de sessão</span><span class="sxs-lookup"><span data-stu-id="2786f-170">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="2786f-171">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2786f-171">See also</span></span>

- [<span data-ttu-id="2786f-172">Informações adicionais sobre a Comunicação Remota do PowerShell e segurança do WinRM</span><span class="sxs-lookup"><span data-stu-id="2786f-172">Additional information about PowerShell Remoting and WinRM security</span></span>](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity)
- [<span data-ttu-id="2786f-173">*Postagem no blog sobre segurança* PowerShell ♥ the Blue Team</span><span class="sxs-lookup"><span data-stu-id="2786f-173">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)