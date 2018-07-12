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
# <a name="installing-powershellget"></a>Instalando o PowerShellGet

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet é um módulo nativo nas seguintes versões

- [Windows 10](https://www.microsoft.com/en-us/windows) ou mais recente
- [Windows Server 2016](/windows-server/windows-server) ou mais recente
- [Windows Management Framework (WMF) 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) ou mais recente
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a>Módulo Get PowerShellGet para o PowerShell versões 3.0 e 4.0

- [MSI do PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a>Obter a versão mais recente da Galeria do PowerShell

- Antes de atualizar o PowerShellGet, você sempre deve instalar o provedor do Nuget mais recente. Para fazer isso, execute o seguinte em uma sessão do PowerShell com privilégios elevados.

  ```powershell
  Install-PackageProvider Nuget –Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>Para sistemas com o PowerShell 5.0 (ou mais recente), você pode instalar o PowerShellGet mais recente

- Para fazer isso no Windows 10, no Windows Server 2016, em qualquer sistema com o WMF 5.0 ou 5.1 instalado ou em qualquer sistema com o PowerShell 6, execute os seguintes comandos em uma sessão do PowerShell com privilégios elevados.

  ```powershell
  Install-Module –Name PowerShellGet –Force
  Exit
  ```

- Use o `Update-Module` para obter versões mais recentes.

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomen-usdownloaddetailsaspxid51451"></a>Para sistemas que executam o PowerShell 3 ou o PowerShell 4 que têm o [MSI do PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=51451) instalado

- Use o cmdlet do PowerShellGet abaixo em uma sessão do PowerShell com privilégios elevados para salvar os módulos em um diretório local

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- Verifique se os módulos PowerShellGet e PackageManagment não estão carregados em nenhum outro processo.
- Exclua o conteúdo das pastas `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` e `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.
- Reabra o Console do PS com permissões elevadas e execute os comandos a seguir.

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```