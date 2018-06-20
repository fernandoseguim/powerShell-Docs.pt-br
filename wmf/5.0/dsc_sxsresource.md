---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: 0543afbc72148b1ba713e59655126c069b16ef33
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218426"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>Suporte ao controle de versão do módulo lado a lado para recursos DSC

Os módulos que contêm recursos DSC podem ser instalados lado a lado, e as configurações DSC podem usar uma versão específica do recurso instalado no sistema.

Para obter mais informações, veja [Usando recursos com várias versões](https://msdn.microsoft.com/powershell/dsc/sxsresource).

## <a name="known-issues"></a>Problemas conhecidos

Nesta versão, os seguintes problemas são problemas conhecidos da instalação lado a lado:

-   Não há suporte para o uso de duas versões diferentes do recurso DSC na mesma configuração.
