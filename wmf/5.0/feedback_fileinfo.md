---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: 63c3b8237a9883b147380dfe9cb173107cea9aa9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="updates-to-fileinfo-object"></a><span data-ttu-id="add1e-102">Atualizações ao objeto FileInfo</span><span class="sxs-lookup"><span data-stu-id="add1e-102">Updates to FileInfo object</span></span>
<span data-ttu-id="add1e-103">Informações de versão do arquivo podem ser confusas, especialmente nos casos em que foi aplicado patch ao arquivo.</span><span class="sxs-lookup"><span data-stu-id="add1e-103">File version information can be misleading, particularly in cases where the file was patched.</span></span> <span data-ttu-id="add1e-104">Esta versão do WMF 5.0 adiciona novas propriedades de script **FileVersionRaw** e **ProductVersionRaw** a objetos FileInfo.</span><span class="sxs-lookup"><span data-stu-id="add1e-104">This release of WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to FileInfo objects.</span></span> <span data-ttu-id="add1e-105">Aqui estão as propriedades conforme exibidas para powershell.exe (supondo que $pid é a ID do processo do PowerShell):</span><span class="sxs-lookup"><span data-stu-id="add1e-105">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117
