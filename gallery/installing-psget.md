---
ms.date: 06/12/2017
contributor: manikb
keywords: galeria,powershell,cmdlet,psget
title: Instalando o PowerShellGet
ms.openlocfilehash: c385f7fbf6b688a11face9c3ebf4e6475a7b4c33
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893953"
---
# <a name="installing-powershellget"></a><span data-ttu-id="c9b70-103">Instalando o PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="c9b70-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="c9b70-104">PowerShellGet é um módulo nativo nas seguintes versões</span><span class="sxs-lookup"><span data-stu-id="c9b70-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="c9b70-105">[Windows 10](https://www.microsoft.com/en-us/windows) ou mais recente</span><span class="sxs-lookup"><span data-stu-id="c9b70-105">[Windows 10](https://www.microsoft.com/en-us/windows) or newer</span></span>
- <span data-ttu-id="c9b70-106">[Windows Server 2016](/windows-server/windows-server) ou mais recente</span><span class="sxs-lookup"><span data-stu-id="c9b70-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="c9b70-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) ou mais recente</span><span class="sxs-lookup"><span data-stu-id="c9b70-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="c9b70-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="c9b70-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a><span data-ttu-id="c9b70-109">Módulo Get PowerShellGet para o PowerShell versões 3.0 e 4.0</span><span class="sxs-lookup"><span data-stu-id="c9b70-109">Get PowerShellGet module for PowerShell versions 3.0 and 4.0</span></span>

- [<span data-ttu-id="c9b70-110">MSI do PackageManagement</span><span class="sxs-lookup"><span data-stu-id="c9b70-110">PackageManagement MSI</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="c9b70-111">Obter a versão mais recente da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="c9b70-111">Get the latest version from PowerShell Gallery</span></span>

- <span data-ttu-id="c9b70-112">Antes de atualizar o PowerShellGet, você sempre deve instalar o provedor do Nuget mais recente.</span><span class="sxs-lookup"><span data-stu-id="c9b70-112">Before updating PowerShellGet, you should always install the latest Nuget provider.</span></span> <span data-ttu-id="c9b70-113">Para fazer isso, execute o seguinte em uma sessão do PowerShell com privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="c9b70-113">To do that, run the following in an elevated PowerShell session.</span></span>

  ```powershell
  Install-PackageProvider Nuget –Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="c9b70-114">Para sistemas com o PowerShell 5.0 (ou mais recente), você pode instalar o PowerShellGet mais recente</span><span class="sxs-lookup"><span data-stu-id="c9b70-114">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

- <span data-ttu-id="c9b70-115">Para fazer isso no Windows 10, no Windows Server 2016, em qualquer sistema com o WMF 5.0 ou 5.1 instalado ou em qualquer sistema com o PowerShell 6, execute os seguintes comandos em uma sessão do PowerShell com privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="c9b70-115">To do this on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

  ```powershell
  Install-Module –Name PowerShellGet –Force
  Exit
  ```

- <span data-ttu-id="c9b70-116">Use o `Update-Module` para obter versões mais recentes.</span><span class="sxs-lookup"><span data-stu-id="c9b70-116">Use `Update-Module` to get newer versions.</span></span>

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomen-usdownloaddetailsaspxid51451"></a><span data-ttu-id="c9b70-117">Para sistemas que executam o PowerShell 3 ou o PowerShell 4 que têm o [MSI do PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=51451) instalado</span><span class="sxs-lookup"><span data-stu-id="c9b70-117">For systems running PowerShell 3 or PowerShell 4, that have installed the [PackageManagement MSI](https://www.microsoft.com/en-us/download/details.aspx?id=51451)</span></span>

- <span data-ttu-id="c9b70-118">Use o cmdlet do PowerShellGet abaixo em uma sessão do PowerShell com privilégios elevados para salvar os módulos em um diretório local</span><span class="sxs-lookup"><span data-stu-id="c9b70-118">Use below PowerShellGet cmdlet from an elevated PowerShell session to save the modules to a local directory</span></span>

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- <span data-ttu-id="c9b70-119">Verifique se os módulos PowerShellGet e PackageManagment não estão carregados em nenhum outro processo.</span><span class="sxs-lookup"><span data-stu-id="c9b70-119">Ensure that PowerShellGet and PackageManagment modules are not loaded in any other processes.</span></span>
- <span data-ttu-id="c9b70-120">Exclua o conteúdo das pastas `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` e `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span><span class="sxs-lookup"><span data-stu-id="c9b70-120">Delete contents of `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and  `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folders.</span></span>
- <span data-ttu-id="c9b70-121">Reabra o Console do PS com permissões elevadas e execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="c9b70-121">Re-open the PS Console with elevated permissions then run the following commands.</span></span>

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```