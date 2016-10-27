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
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: 740c72620e1a5a114716f924f859c57cad125614

---

## Como resolver o problema “AVISO: falha ao baixar o Pacote 'nome do pacote'”?




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




<!--HONumber=Oct16_HO2-->


