---
title: Instalando um módulo do PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: f7899713dd273b793017adfa0a20b3ff3352b62a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862162"
---
# <a name="installing-a-powershell-module"></a><span data-ttu-id="a4d60-102">Instalar um módulo do PowerShell</span><span class="sxs-lookup"><span data-stu-id="a4d60-102">Installing a PowerShell Module</span></span>

<span data-ttu-id="a4d60-103">Depois de criar o módulo do PowerShell, você provavelmente desejará instalar o módulo em um sistema, para que você ou outras pessoas podem usá-lo.</span><span class="sxs-lookup"><span data-stu-id="a4d60-103">After you have created your PowerShell module, you will likely want to install the module on a system, so that you or others may use it.</span></span> <span data-ttu-id="a4d60-104">Em termos gerais, isso simplesmente consiste em copiar os arquivos de módulo (ou seja, a. psm1, ou o assembly binário, o manifesto de módulo e quaisquer outros arquivos associados) em um diretório no computador em questão.</span><span class="sxs-lookup"><span data-stu-id="a4d60-104">Generally speaking, this simply consists of copying the module files (ie, the .psm1, or the binary assembly, the module manifest, and any other associated files) onto a directory on that computer.</span></span> <span data-ttu-id="a4d60-105">Para um projeto muito pequeno, isso pode ser tão simple quanto copiar e colar os arquivos com o Windows Explorer em um único computador remoto. No entanto, para grandes soluções você poderá usar um processo de instalação mais sofisticado.</span><span class="sxs-lookup"><span data-stu-id="a4d60-105">For a very small project, this may be as simple as copying and pasting the files with Windows Explorer onto a single remote computer; however, for larger solutions you may wish to use a more sophisticated installation process.</span></span> <span data-ttu-id="a4d60-106">Independentemente de como você pode obter seu módulo no sistema, o PowerShell pode usar várias técnicas que permitirá que os usuários localizar e usar seus módulos.</span><span class="sxs-lookup"><span data-stu-id="a4d60-106">Regardless of how you get your module onto the system, PowerShell can use a number of techniques that will let users find and use your modules.</span></span> <span data-ttu-id="a4d60-107">(Para obter mais informações, consulte [importação de um módulo do PowerShell](./importing-a-powershell-module.md).) Portanto, o principal problema para a instalação é garantir que o PowerShell será capaz de encontrar seu módulo.</span><span class="sxs-lookup"><span data-stu-id="a4d60-107">(For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).) Therefore, the main issue for installation is ensuring that PowerShell will be able to find your module.</span></span>

<span data-ttu-id="a4d60-108">Este tópico contém as seguintes seções:</span><span class="sxs-lookup"><span data-stu-id="a4d60-108">This topic contains the following sections:</span></span>

- <span data-ttu-id="a4d60-109">Regras para instalar os módulos</span><span class="sxs-lookup"><span data-stu-id="a4d60-109">Rules for Installing Modules</span></span>

- <span data-ttu-id="a4d60-110">Onde instalar os módulos</span><span class="sxs-lookup"><span data-stu-id="a4d60-110">Where to Install Modules</span></span>

- <span data-ttu-id="a4d60-111">Instalando várias versões de um módulo</span><span class="sxs-lookup"><span data-stu-id="a4d60-111">Installing Multiple Versions of a Module</span></span>

- <span data-ttu-id="a4d60-112">Tratamento de conflitos de nome de comando</span><span class="sxs-lookup"><span data-stu-id="a4d60-112">Handling Command Name Conflicts</span></span>

## <a name="rules-for-installing-modules"></a><span data-ttu-id="a4d60-113">Regras para instalar os módulos</span><span class="sxs-lookup"><span data-stu-id="a4d60-113">Rules for Installing Modules</span></span>

<span data-ttu-id="a4d60-114">As informações a seguir se refere a todos os módulos, incluindo os módulos que você cria para seu próprio uso, os módulos que você obteve de outras partes e módulos que você distribuir para outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="a4d60-114">The following information pertains to all modules, including modules that you create for your own use, modules that you get from other parties, and modules that you distribute to others.</span></span>

### <a name="install-modules-in-psmodulepath"></a><span data-ttu-id="a4d60-115">Instalar os módulos no PSModulePath</span><span class="sxs-lookup"><span data-stu-id="a4d60-115">Install Modules in PSModulePath</span></span>

<span data-ttu-id="a4d60-116">Sempre que possível, instale todos os módulos em um caminho que está listado na **PSModulePath** variável de ambiente ou adicione o caminho do módulo para o **PSModulePath** valor de variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="a4d60-116">Whenever possible, install all modules in a path that is listed in the **PSModulePath** environment variable or add the module path to the **PSModulePath** environment variable value.</span></span>

<span data-ttu-id="a4d60-117">O **PSModulePath** variável de ambiente ($Env: PSModulePath) contém os locais dos módulos do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a4d60-117">The **PSModulePath** environment variable ($Env:PSModulePath) contains the locations of Windows PowerShell modules.</span></span> <span data-ttu-id="a4d60-118">Cmdlets contam com o valor dessa variável de ambiente para localizar os módulos.</span><span class="sxs-lookup"><span data-stu-id="a4d60-118">Cmdlets rely on the value of this environment variable to find modules.</span></span>

<span data-ttu-id="a4d60-119">Por padrão, o **PSModulePath** valor de variável de ambiente contém o sistema a seguir e os diretórios de módulo de usuário, mas você pode adicionar a e edite o valor.</span><span class="sxs-lookup"><span data-stu-id="a4d60-119">By default, the **PSModulePath** environment variable value contains the following system and user module directories, but you can add to and edit the value.</span></span>

- <span data-ttu-id="a4d60-120">$PSHome\Modules (% Windir%\System32\WindowsPowerShell\v1.0\Modules)</span><span class="sxs-lookup"><span data-stu-id="a4d60-120">$PSHome\Modules (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span></span>

  > [!WARNING]
  > <span data-ttu-id="a4d60-121">Esse local é reservado para os módulos que acompanham o Windows.</span><span class="sxs-lookup"><span data-stu-id="a4d60-121">This location is reserved for modules that ship with Windows.</span></span> <span data-ttu-id="a4d60-122">Não instale os módulos neste local.</span><span class="sxs-lookup"><span data-stu-id="a4d60-122">Do not install modules to this location.</span></span>

- <span data-ttu-id="a4d60-123">$Home\Documents\WindowsPowerShell\Modules (%UserProfile%\Documents\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="a4d60-123">$Home\Documents\WindowsPowerShell\Modules (%UserProfile%\Documents\WindowsPowerShell\Modules)</span></span>

- <span data-ttu-id="a4d60-124">$Env: ProgramFiles\WindowsPowerShell\Modules (% ProgramFiles%\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="a4d60-124">$Env:ProgramFiles\WindowsPowerShell\Modules (%ProgramFiles%\WindowsPowerShell\Modules)</span></span>

  <span data-ttu-id="a4d60-125">Para obter o valor da **PSModulePath** variável de ambiente, use um dos comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="a4d60-125">To get the value of the **PSModulePath** environment variable, use either of the following commands.</span></span>

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  <span data-ttu-id="a4d60-126">Para adicionar um caminho de módulo como valor da **PSModulePath** variável de ambiente valor, use o seguinte formato de comando.</span><span class="sxs-lookup"><span data-stu-id="a4d60-126">To add a module path to value of the **PSModulePath** environment variable value, use the following command format.</span></span> <span data-ttu-id="a4d60-127">Esse formato usa o **SetEnvironmentVariable** método o **System. Environment** classe para fazer uma alteração de sessão independente para o **PSModulePath** ambiente variável.</span><span class="sxs-lookup"><span data-stu-id="a4d60-127">This format uses the **SetEnvironmentVariable** method of the **System.Environment** class to make a session-independent change to the **PSModulePath** environment variable.</span></span>

  ```powershell

  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > <span data-ttu-id="a4d60-128">Depois de adicionar o caminho para **PSModulePath**, você deve transmitir uma mensagem sobre a alteração de ambiente.</span><span class="sxs-lookup"><span data-stu-id="a4d60-128">Once you have added the path to **PSModulePath**, you should broadcast an environment message about the change.</span></span> <span data-ttu-id="a4d60-129">Transmitindo a alteração permite que outros aplicativos, como o shell acompanhar a alteração.</span><span class="sxs-lookup"><span data-stu-id="a4d60-129">Broadcasting the change allows other applications, such as the shell, to pick up the change.</span></span> <span data-ttu-id="a4d60-130">Para transmitir a alteração, que seu código de instalação de produto envie um **WM_SETTINGCHANGE** da mensagem com `lParam` definido como a cadeia de caracteres "Ambiente".</span><span class="sxs-lookup"><span data-stu-id="a4d60-130">To broadcast the change, have your product installation code send a **WM_SETTINGCHANGE** message with `lParam` set to the string "Environment".</span></span> <span data-ttu-id="a4d60-131">Certifique-se de enviar a mensagem depois que seu código de instalação do módulo atualizou **PSModulePath**.</span><span class="sxs-lookup"><span data-stu-id="a4d60-131">Be sure to send the message after your module installation code has updated **PSModulePath**.</span></span>

### <a name="use-the-correct-module-directory-name"></a><span data-ttu-id="a4d60-132">Use o nome de diretório do módulo correto</span><span class="sxs-lookup"><span data-stu-id="a4d60-132">Use the Correct Module Directory Name</span></span>

<span data-ttu-id="a4d60-133">Um "bem-formado" é um módulo que é armazenado em um diretório que tem o mesmo nome que o nome base de pelo menos um arquivo no diretório do módulo.</span><span class="sxs-lookup"><span data-stu-id="a4d60-133">A "well-formed" module is a module that is stored in a directory that has the same name as the base name of at least one file in the module directory.</span></span> <span data-ttu-id="a4d60-134">Se um módulo não está bem formado, o Windows PowerShell não reconhecê-lo como um módulo.</span><span class="sxs-lookup"><span data-stu-id="a4d60-134">If a module is not well-formed, Windows PowerShell does not recognize it as a module.</span></span>

<span data-ttu-id="a4d60-135">O "nome base" de um arquivo é o nome sem a extensão de nome de arquivo.</span><span class="sxs-lookup"><span data-stu-id="a4d60-135">The "base name" of a file is the name without the file name extension.</span></span> <span data-ttu-id="a4d60-136">Em um módulo bem formado, o nome do diretório que contém os arquivos de módulo deve corresponder ao nome de base pelo menos um arquivo no módulo.</span><span class="sxs-lookup"><span data-stu-id="a4d60-136">In a well-formed module, the name of the directory that contains the module files must match the base name of at least one file in the module.</span></span>

<span data-ttu-id="a4d60-137">Por exemplo, no módulo exemplo Fabrikam, o diretório que contém os arquivos de módulo é denominado "Fabrikam" e pelo menos um arquivo com o nome de base "Fabrikam".</span><span class="sxs-lookup"><span data-stu-id="a4d60-137">For example, in the sample Fabrikam module, the directory that contains the module files is named "Fabrikam" and at least one file has the "Fabrikam" base name.</span></span> <span data-ttu-id="a4d60-138">Nesse caso, Fabrikam.psd1 e Fabrikam.dll tem o nome de base "Fabrikam".</span><span class="sxs-lookup"><span data-stu-id="a4d60-138">In this case, both Fabrikam.psd1 and Fabrikam.dll have the "Fabrikam" base name.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a><span data-ttu-id="a4d60-139">Efeito da instalação incorreta</span><span class="sxs-lookup"><span data-stu-id="a4d60-139">Effect of Incorrect Installation</span></span>

<span data-ttu-id="a4d60-140">Se o módulo não está bem formado e sua localização não está incluída no valor de **PSModulePath** variável de ambiente, recursos de descoberta básico do Windows PowerShell, como a seguir, não funcionam.</span><span class="sxs-lookup"><span data-stu-id="a4d60-140">If the module is not well-formed and its location is not included in the value of the **PSModulePath** environment variable, basic discovery features of Windows PowerShell, such as the following, do not work.</span></span>

- <span data-ttu-id="a4d60-141">O recurso de carregamento automático do módulo não é possível importar o módulo automaticamente.</span><span class="sxs-lookup"><span data-stu-id="a4d60-141">The Module Auto-Loading feature cannot import the module automatically.</span></span>

- <span data-ttu-id="a4d60-142">O `ListAvailable` parâmetro do [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet não é possível localizar o módulo.</span><span class="sxs-lookup"><span data-stu-id="a4d60-142">The `ListAvailable` parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet cannot find the module.</span></span>

- <span data-ttu-id="a4d60-143">O [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet não é possível localizar o módulo.</span><span class="sxs-lookup"><span data-stu-id="a4d60-143">The [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet cannot find the module.</span></span> <span data-ttu-id="a4d60-144">Para importar o módulo, você deve fornecer o caminho completo para o arquivo de módulo raiz ou o arquivo de manifesto de módulo.</span><span class="sxs-lookup"><span data-stu-id="a4d60-144">To import the module, you must provide the full path to the root module file or module manifest file.</span></span>

  <span data-ttu-id="a4d60-145">Recursos adicionais, como a seguir, não funcionam, a menos que o módulo é importado para a sessão.</span><span class="sxs-lookup"><span data-stu-id="a4d60-145">Additional features, such as the following, do not work unless the module is imported into the session.</span></span> <span data-ttu-id="a4d60-146">Em módulos bem-formados a **PSModulePath** variável de ambiente, esses recursos funcionam, mesmo quando o módulo não será importado para a sessão.</span><span class="sxs-lookup"><span data-stu-id="a4d60-146">In well-formed modules in the **PSModulePath** environment variable, these features work even when the module is not imported into the session.</span></span>

- <span data-ttu-id="a4d60-147">O [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet não é possível localizar os comandos no módulo.</span><span class="sxs-lookup"><span data-stu-id="a4d60-147">The [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet cannot find commands in the module.</span></span>

- <span data-ttu-id="a4d60-148">O [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets não podem atualizar ou salvar ajuda para o módulo.</span><span class="sxs-lookup"><span data-stu-id="a4d60-148">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets cannot update or save help for the module.</span></span>

- <span data-ttu-id="a4d60-149">O [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet não pode localizar e exibir os comandos no módulo.</span><span class="sxs-lookup"><span data-stu-id="a4d60-149">The [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet cannot find and display the commands in the module.</span></span>

  <span data-ttu-id="a4d60-150">Os comandos no módulo estão ausentes do `Show-Command` janela no Windows PowerShell Integrated Scripting ISE (ambiente).</span><span class="sxs-lookup"><span data-stu-id="a4d60-150">The commands in the module are missing from the `Show-Command` window in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="where-to-install-modules"></a><span data-ttu-id="a4d60-151">Onde instalar os módulos</span><span class="sxs-lookup"><span data-stu-id="a4d60-151">Where to Install Modules</span></span>

<span data-ttu-id="a4d60-152">Esta seção explica onde no sistema de arquivos para instalar os módulos do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a4d60-152">This section explains where in the file system to install Windows PowerShell modules.</span></span> <span data-ttu-id="a4d60-153">O local depende de como o módulo é usado.</span><span class="sxs-lookup"><span data-stu-id="a4d60-153">The location depends on how the module is used.</span></span>

### <a name="installing-modules-for-a-specific-user"></a><span data-ttu-id="a4d60-154">Instalar os módulos para um usuário específico</span><span class="sxs-lookup"><span data-stu-id="a4d60-154">Installing Modules for a Specific User</span></span>

<span data-ttu-id="a4d60-155">Se você cria seu próprio módulo ou obter um módulo de terceiros, como um site da comunidade do Windows PowerShell, e você deseja que o módulo estejam disponíveis para sua conta de usuário, instale o módulo em seu diretório de módulos específicos do usuário.</span><span class="sxs-lookup"><span data-stu-id="a4d60-155">If you create your own module or get a module from another party, such as a Windows PowerShell community website, and you want the module to be available for your user account only, install the module in your user-specific Modules directory.</span></span>

```
$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

<span data-ttu-id="a4d60-156">O diretório de módulos específicos do usuário é adicionado ao valor de **PSModulePath** variável de ambiente, por padrão.</span><span class="sxs-lookup"><span data-stu-id="a4d60-156">The user-specific Modules directory is added to the value of the **PSModulePath** environment variable by default.</span></span>

### <a name="installing-modules-for-all-users-in-program-files"></a><span data-ttu-id="a4d60-157">Instalar os módulos para todos os usuários em arquivos de programa</span><span class="sxs-lookup"><span data-stu-id="a4d60-157">Installing Modules for all Users in Program Files</span></span>

<span data-ttu-id="a4d60-158">Se você quiser um módulo estejam disponíveis para todas as contas de usuário no computador, instale o módulo no local dos arquivos de programa.</span><span class="sxs-lookup"><span data-stu-id="a4d60-158">If you want a module to be available to all user accounts on the computer, install the module in the Program Files location.</span></span>

```
$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

> [!NOTE]
> <span data-ttu-id="a4d60-159">Por padrão no Windows PowerShell 4.0 e posterior, o local dos arquivos de programa é adicionado ao valor da variável de ambiente PSModulePath.</span><span class="sxs-lookup"><span data-stu-id="a4d60-159">The Program Files location is added to the value of the PSModulePath environment variable by default in Windows PowerShell 4.0 and later.</span></span> <span data-ttu-id="a4d60-160">Para versões anteriores do Windows PowerShell, você pode manualmente os arquivos de programa local ((%ProgramFiles%\WindowsPowerShell\Modules) de criar e adicionar este caminho à variável de ambiente PSModulePath, conforme descrito acima.</span><span class="sxs-lookup"><span data-stu-id="a4d60-160">For earlier versions of Windows PowerShell, you can manually create the Program Files location ((%ProgramFiles%\WindowsPowerShell\Modules) and add this path to your PSModulePath environment variable as described above.</span></span>

### <a name="installing-modules-in-a-product-directory"></a><span data-ttu-id="a4d60-161">Instalar os módulos em um diretório de produto</span><span class="sxs-lookup"><span data-stu-id="a4d60-161">Installing Modules in a Product Directory</span></span>

<span data-ttu-id="a4d60-162">Se você estiver distribuindo o módulo a outras partes, use o local dos arquivos de programa padrão descrito acima, ou crie seu próprio subdiretório específico da empresa ou produto específico do diretório % ProgramFiles %.</span><span class="sxs-lookup"><span data-stu-id="a4d60-162">If you are distributing the module to other parties, use the default Program Files location described above, or create your own company-specific or product-specific subdirectory of the %ProgramFiles% directory.</span></span>

<span data-ttu-id="a4d60-163">Por exemplo, as tecnologias da Fabrikam, uma empresa fictícia, está enviando um módulo do Windows PowerShell para seu produto Gerenciador da Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="a4d60-163">For example, Fabrikam Technologies, a fictitious company, is shipping a Windows PowerShell module for their Fabrikam Manager product.</span></span> <span data-ttu-id="a4d60-164">Seu instalador de módulos cria um subdiretório de módulos no subdiretório de produto Gerenciador da Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="a4d60-164">Their module installer creates a Modules subdirectory in the Fabrikam Manager product subdirectory.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

<span data-ttu-id="a4d60-165">Para habilitar os recursos de descoberta do módulo Windows PowerShell encontrar o módulo de Fabrikam, o instalador do módulo Fabrikam adiciona o local de módulo para o valor da **PSModulePath** variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="a4d60-165">To enable the Windows PowerShell module discovery features to find the Fabrikam module, the Fabrikam module installer adds the module location to the value of the **PSModulePath** environment variable.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += "C:\Program Files\Fabrikam Technolgies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a><span data-ttu-id="a4d60-166">Instalar os módulos no diretório de arquivos comuns</span><span class="sxs-lookup"><span data-stu-id="a4d60-166">Installing Modules in the Common Files Directory</span></span>

<span data-ttu-id="a4d60-167">Se um módulo é usado por vários componentes de um produto ou por várias versões de um produto, instale o módulo em um subdiretório específico do módulo do subdiretório Files\Modules %ProgramFiles%\Common.</span><span class="sxs-lookup"><span data-stu-id="a4d60-167">If a module is used by multiple components of a product or by multiple versions of a product, install the module in a module-specific subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span>

<span data-ttu-id="a4d60-168">No exemplo a seguir, o módulo da Fabrikam é instalado em um subdiretório de Fabrikam do subdiretório Files\Modules %ProgramFiles%\Common.</span><span class="sxs-lookup"><span data-stu-id="a4d60-168">In the following example, the Fabrikam module is installed in a Fabrikam subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span> <span data-ttu-id="a4d60-169">Observe que cada módulo reside em seu próprio subdiretório no subdiretório de módulos.</span><span class="sxs-lookup"><span data-stu-id="a4d60-169">Note that each module resides in its own subdirectory in the Modules subdirectory.</span></span>

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)

```

<span data-ttu-id="a4d60-170">Em seguida, o instalador garante que o valor de **PSModulePath** variável de ambiente inclui o caminho do subdiretório comum de módulos de arquivos.</span><span class="sxs-lookup"><span data-stu-id="a4d60-170">Then, the installer assures the value of the **PSModulePath** environment variable includes the path of the common files modules subdirectory.</span></span>

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a><span data-ttu-id="a4d60-171">Instalando várias versões de um módulo</span><span class="sxs-lookup"><span data-stu-id="a4d60-171">Installing Multiple Versions of a Module</span></span>

<span data-ttu-id="a4d60-172">Para instalar várias versões do mesmo módulo, use o procedimento a seguir.</span><span class="sxs-lookup"><span data-stu-id="a4d60-172">To install multiple versions of the same module, use the following procedure.</span></span>

1. <span data-ttu-id="a4d60-173">Crie um diretório para cada versão do módulo.</span><span class="sxs-lookup"><span data-stu-id="a4d60-173">Create a directory for each version of the module.</span></span> <span data-ttu-id="a4d60-174">Inclua o número de versão no nome do diretório.</span><span class="sxs-lookup"><span data-stu-id="a4d60-174">Include the version number in the directory name.</span></span>

2. <span data-ttu-id="a4d60-175">Crie um manifesto de módulo para cada versão do módulo.</span><span class="sxs-lookup"><span data-stu-id="a4d60-175">Create a module manifest for each version of the module.</span></span> <span data-ttu-id="a4d60-176">O valor da **ModuleVersion** da chave no manifesto, insira o número de versão do módulo.</span><span class="sxs-lookup"><span data-stu-id="a4d60-176">In the value of the **ModuleVersion** key in the manifest, enter the module version number.</span></span> <span data-ttu-id="a4d60-177">Salve o arquivo de manifesto (. psd1) no diretório específico da versão do módulo.</span><span class="sxs-lookup"><span data-stu-id="a4d60-177">Save the manifest file (.psd1) in the version-specific directory for the module.</span></span>

3. <span data-ttu-id="a4d60-178">Adicionar o caminho de pasta do módulo raiz para o valor de **PSModulePath** variável de ambiente, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="a4d60-178">Add the module root folder path to the value of the **PSModulePath** environment variable, as shown in the following examples.</span></span>

<span data-ttu-id="a4d60-179">Para importar uma versão específica do módulo, o usuário final pode usar o `MinimumVersion` ou `RequiredVersion` parâmetros da [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a4d60-179">To import a particular version of the module, the end-user can use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="a4d60-180">Por exemplo, se o módulo de Fabrikam está disponível nas versões 8.0 e 9.0, a estrutura de diretório do módulo Fabrikam pode se parecer com o seguinte.</span><span class="sxs-lookup"><span data-stu-id="a4d60-180">For example, if the Fabrikam module is available in versions 8.0 and 9.0, the Fabrikam module directory structure might resemble the following.</span></span>

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

<span data-ttu-id="a4d60-181">O instalador adiciona ambos os caminhos de módulo para o **PSModulePath** valor de variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="a4d60-181">The installer adds both of the module paths to the **PSModulePath** environment variable value.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

<span data-ttu-id="a4d60-182">Quando essas etapas forem concluídas, o **ListAvailable** parâmetro do [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet obtém a ambos os módulos da Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="a4d60-182">When these steps are complete, the **ListAvailable** parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet gets both of the Fabrikam modules.</span></span> <span data-ttu-id="a4d60-183">Para importar um módulo específico, use o `MiminumVersion` ou `RequiredVersion` parâmetros da [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a4d60-183">To import a particular module, use the `MiminumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="a4d60-184">Se ambos os módulos são importados para a mesma sessão, e os módulos contêm cmdlets com os mesmos nomes, os cmdlets que são importados pela última vez são eficazes na sessão.</span><span class="sxs-lookup"><span data-stu-id="a4d60-184">If both modules are imported into the same session, and the modules contain cmdlets with the same names, the cmdlets that are imported last are effective in the session.</span></span>

## <a name="handling-command-name-conflicts"></a><span data-ttu-id="a4d60-185">Tratamento de conflitos de nome de comando</span><span class="sxs-lookup"><span data-stu-id="a4d60-185">Handling Command Name Conflicts</span></span>

<span data-ttu-id="a4d60-186">Conflitos de nome de comando podem ocorrer quando os comandos que exporta um módulo tem o mesmo nome de comandos na sessão do usuário.</span><span class="sxs-lookup"><span data-stu-id="a4d60-186">Command name conflicts can occur when the commands that a module exports have the same name as commands in the user's session.</span></span>

<span data-ttu-id="a4d60-187">Quando uma sessão contém dois comandos que têm o mesmo nome, o Windows PowerShell executa o tipo de comando que tem precedência.</span><span class="sxs-lookup"><span data-stu-id="a4d60-187">When a session contains two commands that have the same name, Windows PowerShell runs the command type that takes precedence.</span></span> <span data-ttu-id="a4d60-188">Quando uma sessão contém dois comandos que têm o mesmo nome e o mesmo tipo, o Windows PowerShell executa o comando que foi adicionado à sessão mais recentemente.</span><span class="sxs-lookup"><span data-stu-id="a4d60-188">When a session contains two commands that have the same name and the same type, Windows PowerShell runs the command that was added to the session most recently.</span></span> <span data-ttu-id="a4d60-189">Para executar um comando que não é executado por padrão, os usuários podem qualificar o nome de comando com o nome do módulo.</span><span class="sxs-lookup"><span data-stu-id="a4d60-189">To run a command that is not run by default, users can qualify the command name with the module name.</span></span>

<span data-ttu-id="a4d60-190">Por exemplo, se a sessão contém um `Get-Date` função e o `Get-Date` , Windows PowerShell executa a função por padrão.</span><span class="sxs-lookup"><span data-stu-id="a4d60-190">For example, if the session contains a `Get-Date` function and the `Get-Date` cmdlet, Windows PowerShell runs the function by default.</span></span> <span data-ttu-id="a4d60-191">Para executar o cmdlet, preceda o comando com o nome do módulo, como:</span><span class="sxs-lookup"><span data-stu-id="a4d60-191">To run the cmdlet, preface the command with the module name, such as:</span></span>

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

<span data-ttu-id="a4d60-192">Para evitar conflitos de nome, os autores de módulo podem usar o **DefaultCommandPrefix** chave no manifesto do módulo para especificar um prefixo ao substantivo para todos os comandos exportados do módulo.</span><span class="sxs-lookup"><span data-stu-id="a4d60-192">To prevent name conflicts, module authors can use the **DefaultCommandPrefix** key in the module manifest to specify a noun prefix for all commands exported from the module.</span></span>

<span data-ttu-id="a4d60-193">Os usuários podem usar o **prefixo** parâmetro do `Import-Module` cmdlet para usar um prefixo alternativo.</span><span class="sxs-lookup"><span data-stu-id="a4d60-193">Users can use the **Prefix** parameter of the `Import-Module` cmdlet to use an alternate prefix.</span></span> <span data-ttu-id="a4d60-194">O valor da **prefixar** parâmetro tem precedência sobre o valor da **DefaultCommandPrefix** chave.</span><span class="sxs-lookup"><span data-stu-id="a4d60-194">The value of the **Prefix** parameter takes precedence over the value of the **DefaultCommandPrefix** key.</span></span>

## <a name="see-also"></a><span data-ttu-id="a4d60-195">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="a4d60-195">See Also</span></span>

[<span data-ttu-id="a4d60-196">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="a4d60-196">about_Command_Precedence</span></span>](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[<span data-ttu-id="a4d60-197">Escrevendo um módulo do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a4d60-197">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
