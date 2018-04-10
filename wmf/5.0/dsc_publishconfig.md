---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
ms.openlocfilehash: 136e16ae74e54f3bc9d0623178257df1e9104aac
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="deliver-a-configuration-document-without-applying"></a>Entregar um documento de configuração sem aplicação

O cmdlet [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) faz uma cópia de um arquivo MOF de configuração e a cola em um nó de destino, mas não aplica a configuração.
Essa configuração é aplicada durante a próxima passagem de consistência ou ao executar o cmdlet [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx).