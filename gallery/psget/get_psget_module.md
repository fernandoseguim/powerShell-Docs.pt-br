---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: "Módulo Get PowerShellGet"
ms.openlocfilehash: 7224cf5d71b98d51ca22c47a00ca382d34864bfb
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
<a name="get-powershellget-module"></a>Módulo Get PowerShellGet
========================

### <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet é um módulo nativo nas seguintes versões
- [Windows 10](https://www.microsoft.com/windows/get-windows-10) ou mais recente
- [Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/windows-server-2016) ou mais recente
- [Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) ou mais recente
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

### <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a>Módulo Get PowerShellGet para o PowerShell versões 3.0 e 4.0
- [MSI do PackageManagement](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409) 

### <a name="get-the-latest-version-from-powershell-gallery"></a>Obter a versão mais recente da Galeria do PowerShell

- Antes de atualizar o PowerShellGet, você sempre deve instalar o provedor do Nuget mais recente. Para fazer isso, execute o seguinte em uma sessão do PowerShell com privilégios elevados.
```powershell
Install-PackageProvider Nuget –Force
Exit
```

#### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>Para sistemas com o PowerShell 5.0 (ou mais recente), você pode instalar o PowerShellGet mais recente 
- Para fazer isso no Windows 10, no Windows Server 2016, em qualquer sistema com o WMF 5.0 ou 5.1 instalado ou em qualquer sistema com o PowerShell 6, execute os seguintes comandos em uma sessão do PowerShell com privilégios elevados.
```powershell
Install-Module –Name PowerShellGet –Force
Exit
```

- Use Update-Module para obter versões mais recentes.
```powershell
Update-Module -Name PowerShellGet
Exit
```

#### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpgomicrosoftcomfwlinklinkid746217clcid0x409"></a>Para sistemas que executam o PowerShell 3 ou o PowerShell 4 que têm o [MSI do PackageManagement](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409) instalado

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