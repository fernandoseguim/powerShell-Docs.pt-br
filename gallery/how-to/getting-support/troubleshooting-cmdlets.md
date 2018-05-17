---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: galeria,powershell,cmdlet,psget
title: Cmdlets de solução de problemas
ms.openlocfilehash: 6295a5b99aa19db933569638d84e490ad81eedc7
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="troubleshooting-cmdlets"></a>Cmdlets de solução de problemas

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