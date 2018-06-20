---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: 42f323590609319388e9a0a2c7c305dfa80c2d49
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221843"
---
# <a name="class-based-dsc-resources"></a>Recursos DSC baseados em classe

## <a name="defining-dsc-resources-with-classes"></a>Definindo recursos DSC com classes

Com base nos comentários, tornamos a criação de recursos DSC baseados em classe mais simples e mais fácil de entender.
As principais diferenças entre um recurso DSC baseado em classe e um provedor de recursos DSC de cmdlet são:

* Um arquivo MOF para o esquema não é necessário.
* Uma subpasta **DSCResource** na pasta do módulo não é necessária.
* Um arquivo de módulo do PowerShell pode conter várias classes de recursos DSC.

Para obter mais informações, veja [Escrevendo um recurso personalizado de DSC com classes do PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).
