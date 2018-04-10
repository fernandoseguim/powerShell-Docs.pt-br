---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
ms.openlocfilehash: baa35e9acd24d6f6155acf617a0d2c2210742af7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="detailed-information-about-lcm-state"></a>Informações detalhadas sobre o estado do LCM

Fizemos melhorias na exposição de detalhes sobre o estado do LCM. O LCMState retornado por Get-DscLocalConfigurationManager agora pode conter os seguintes valores:

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

Também adicionamos uma propriedade de LCMStateDetail que contém mais informações sobre o estado.