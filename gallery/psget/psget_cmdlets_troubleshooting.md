---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet, galeria
ms.date: 2016-10-14
contributor: manikb
title: psget_cmdlets_troubleshooting
ms.technology: powershell
ms.openlocfilehash: 4758c650933b082f467c66ad4accb4c8a1fb514e
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Como resolver o problema “AVISO: falha ao baixar o Pacote 'nome do pacote'”?




Foi relatado que Install-Module ou Update-Module às vezes falha em alguns computadores.
Com base em nossa investigação, isso está relacionado à conexão de rede.
Recentemente, atualizamos o provedor do NuGet para que ele possa baixar pacotes de forma confiável.
Siga as instruções abaixo para instalar o build mais recente do provedor do NuGet e instalar ou atualizar seu módulo.
Vamos usar o módulo “Azure” como o exemplo abaixo.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

