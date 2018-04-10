---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: psget_cmdlets_troubleshooting
ms.openlocfilehash: bc49dc78b8205d1194ddfe4bdca98b3e681860bd
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
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