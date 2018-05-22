---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: db9b48c188b3bfe2e20c06875606a285922f55a6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="detailed-information-about-lcm-state"></a>Informações detalhadas sobre o estado do LCM

Fizemos melhorias na exposição de detalhes sobre o estado do LCM. O LCMState retornado por Get-DscLocalConfigurationManager agora pode conter os seguintes valores:

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

Também adicionamos uma propriedade de LCMStateDetail que contém mais informações sobre o estado.
