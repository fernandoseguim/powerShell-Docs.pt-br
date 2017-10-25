---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
ms.openlocfilehash: 3261e5a07b8181190a04de3f210da50f23bb2953
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>Suporte ao controle de versão do módulo lado a lado para recursos DSC

Os módulos que contêm recursos DSC podem ser instalados lado a lado, e as configurações DSC podem usar uma versão específica do recurso instalado no sistema.

Para obter mais informações, veja [Usando recursos com várias versões](https://msdn.microsoft.com/powershell/dsc/sxsresource).

## <a name="known-issues"></a>Problemas conhecidos

Nesta versão, os seguintes problemas são problemas conhecidos da instalação lado a lado:

-   Não há suporte para o uso de duas versões diferentes do recurso DSC na mesma configuração.

