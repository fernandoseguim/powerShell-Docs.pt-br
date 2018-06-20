---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: f929ce4684bb53c3039238ecd465f1c0e432f741
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225667"
---
# <a name="deliver-a-configuration-document-without-applying"></a>Entregar um documento de configuração sem aplicação

O cmdlet [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) faz uma cópia de um arquivo MOF de configuração e a cola em um nó de destino, mas não aplica a configuração.
Essa configuração é aplicada durante a próxima passagem de consistência ou ao executar o cmdlet [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx).
