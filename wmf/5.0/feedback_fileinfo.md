---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
ms.openlocfilehash: 587f3f592f4aab53c95bbc6d37ea37d7f2364aec
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="updates-to-fileinfo-object"></a><span data-ttu-id="a1f0c-102">Atualizações ao objeto FileInfo</span><span class="sxs-lookup"><span data-stu-id="a1f0c-102">Updates to FileInfo object</span></span>
<span data-ttu-id="a1f0c-103">Informações de versão do arquivo podem ser confusas, especialmente nos casos em que foi aplicado patch ao arquivo.</span><span class="sxs-lookup"><span data-stu-id="a1f0c-103">File version information can be misleading, particularly in cases where the file was patched.</span></span> <span data-ttu-id="a1f0c-104">Esta versão do WMF 5.0 adiciona novas propriedades de script **FileVersionRaw** e **ProductVersionRaw** a objetos FileInfo.</span><span class="sxs-lookup"><span data-stu-id="a1f0c-104">This release of WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to FileInfo objects.</span></span> <span data-ttu-id="a1f0c-105">Aqui estão as propriedades conforme exibidas para powershell.exe (supondo que $pid é a ID do processo do PowerShell):</span><span class="sxs-lookup"><span data-stu-id="a1f0c-105">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117

