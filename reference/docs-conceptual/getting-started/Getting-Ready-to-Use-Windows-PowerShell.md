---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Preparando-se para usar o Windows PowerShell
ms.assetid: 6dc7052d-cc5a-4220-950f-98f963a2b587
ms.openlocfilehash: 5e095984286ff89958dc0a4e3d27e40eae5b2c5e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="getting-ready-to-use-windows-powershell"></a>Preparando-se para usar o Windows PowerShell
Quando o Windows PowerShell estiver instalado e iniciado, considere as seguintes opções de configuração. Você pode executar essas tarefas a qualquer momento.

- **Instale os arquivos de Ajuda.** Os cmdlets que estão incluídos no Windows PowerShell 3.0 não vêm com arquivos de ajuda. No entanto, você pode usar o cmdlet [Update-Help](/powershell/module/microsoft.powershell.core/update-help) para baixar e instalar os arquivos de ajuda mais recentes no seu computador. Depois de os arquivos serem instalados, você pode usar o cmdlet [Get-Help](/powershell/module/microsoft.powershell.core/get-help) para exibi-los diretamente na linha de comando. Para obter mais informações, consulte [about_Updatable_Help](/powershell/module/microsoft.powershell.core/about/about_updatable_help).

    Se você decidir não instalar os arquivos de Ajuda, ainda poderá ler os tópicos da Ajuda online. Para abrir a versão online de qualquer tópico de Ajuda de cmdlet, digite: `Get-Help <CmdletName> -Online`. Para pesquisar os tópicos de ajuda do Windows PowerShell, consulte a [documentação do PowerShell](/powershell/scripting).

- **Execute os Scripts.** Para manter o Windows PowerShell seguro, a política de execução padrão no Windows PowerShell é **Restrita**. Essa política permite executar os cmdlets, mas não em scripts. Para executar scripts, use o cmdlet [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) para alterar a política de execução para **AllSigned** ou **RemoteSigned**. Somente os membros do grupo Administradores no computador podem executar este cmdlet. Para obter mais informações, consulte [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

- **Habilite a comunicação remota.** O sistema já está configurado para executar comandos remotos em outros computadores. No Windows Server 2012 R2 e Windows Server 2012, o sistema também está configurado para receber comandos remotos, ou seja, para permitir que outros computadores executem comandos remotos no computador local. Para permitir que os computadores que executam outras versões do Windows recebam comandos remotos, execute o cmdlet [Enable-PSRemoting](/powershell/module/microsoft.powershell.core/enable-psremoting) no computador que você deseja gerenciar remotamente. Somente os membros do grupo Administradores no computador podem executar este cmdlet. Para obter mais informações, consulte [about_Remote](/powershell/module/microsoft.powershell.core/about/about_remote).

    OBSERVAÇÃO: se a comunicação remota estiver habilitada em um computador que executa o Windows PowerShell 2.0, a comunicação remota ainda estará habilitada após a instalação do Windows Management Framework 3.0. No entanto, no Windows Server 2008 (não no Windows Server 2008 R2), você deve habilitar novamente a comunicação remota após instalar o Windows Management Framework 3.0.

## <a name="see-also"></a>Consulte Também
- [Instalar o Windows PowerShell](../setup/Installing-Windows-PowerShell.md)
- [Iniciando o Windows PowerShell](/powershell/scripting/setup/starting-windows-powershell)