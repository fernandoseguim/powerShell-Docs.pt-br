---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
ms.openlocfilehash: 269f4112704067f291728e4c1d745d68ec6ccd6f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="register-a-powershell-repository"></a>Registrar um repositório do PowerShell
É possível configurar o PowerShellGet operar em repositórios internos. Isso é feito usando as seguintes adições:
- Register-PSRepository: registra um repositório para o usuário atual.
- Unregister-PSRepository: remove um repositório registrado para o usuário atual.
- Set-PSRepository: define valores para um repositório registrado.
- Get-PSRepository: obtém todos os repositórios registrados para o usuário atual.

Depois que um repositório for registrado, será possível usar Find-Module e Install-Module para funcionar com ele.

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