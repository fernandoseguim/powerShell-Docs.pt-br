---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: 9a9bdac652512640209c20e3deb20d7abc0142c6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219524"
---
# <a name="register-a-powershell-repository"></a><span data-ttu-id="c9a51-102">Registrar um repositório do PowerShell</span><span class="sxs-lookup"><span data-stu-id="c9a51-102">Register a PowerShell Repository</span></span>
<span data-ttu-id="c9a51-103">É possível configurar o PowerShellGet operar em repositórios internos.</span><span class="sxs-lookup"><span data-stu-id="c9a51-103">You can configure PowerShellGet to operate against internal repositories.</span></span> <span data-ttu-id="c9a51-104">Isso é feito usando as seguintes adições:</span><span class="sxs-lookup"><span data-stu-id="c9a51-104">This is done by using the following additions:</span></span>
- <span data-ttu-id="c9a51-105">Register-PSRepository: registra um repositório para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="c9a51-105">Register-PSRepository: Registers a repository for the current user.</span></span>
- <span data-ttu-id="c9a51-106">Unregister-PSRepository: remove um repositório registrado para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="c9a51-106">Unregister-PSRepository: Removes a registered repository for the current user.</span></span>
- <span data-ttu-id="c9a51-107">Set-PSRepository: define valores para um repositório registrado.</span><span class="sxs-lookup"><span data-stu-id="c9a51-107">Set-PSRepository: Set values for a registered repository.</span></span>
- <span data-ttu-id="c9a51-108">Get-PSRepository: obtém todos os repositórios registrados para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="c9a51-108">Get-PSRepository: Get all registered repositories for the current user.</span></span>

<span data-ttu-id="c9a51-109">Depois que um repositório for registrado, será possível usar Find-Module e Install-Module para funcionar com ele.</span><span class="sxs-lookup"><span data-stu-id="c9a51-109">After a repository is registered, you can use Find-Module and Install-Module to work with it.</span></span>

```powershell
\#Register a default repository
Register-PSRepository –Name DemoRepo –SourceLocation “https://www.myget.org/F/powershellgetdemo/api/v2” –PublishLocation “<https://www.myget.org/F/powershellgetdemo/api/v2>/package” –InstallationPolicy –Trusted

\#Get all of the registered repositories
Get-PSRepository
Name SourceLocation
---- --------------
PSGallery https://msconfiggallery.cloudapp...
DemoRepo https://www.myget.org/F/powershe...

\#Search only the new repository for modules
Find-Module -Repository DemoRepo
Repository Version Name
---------- ------- ----
DemoRepo 1.0.1 xActiveDirectory
DemoRepo 1.1.1 SomeModule

\#By default, PowerShellGet operates against all registered repositories when none is specified. In this example, the “SomeModule” module is installed from the DemoRepo.
Install-Module SomeModule

\#Removing a repository
Unregister-PSRepository DemoRepo
```
