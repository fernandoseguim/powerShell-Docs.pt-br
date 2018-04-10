---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
ms.openlocfilehash: 4def20aa95f66ab23c9eee575150bc3db02541d8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="class-based-dsc-resources"></a>Recursos DSC baseados em classe

## <a name="defining-dsc-resources-with-classes"></a>Definindo recursos DSC com classes

Com base nos comentários, tornamos a criação de recursos DSC baseados em classe mais simples e mais fácil de entender.
As principais diferenças entre um recurso DSC baseado em classe e um provedor de recursos DSC de cmdlet são:

* Um arquivo MOF para o esquema não é necessário.
* Uma subpasta **DSCResource** na pasta do módulo não é necessária.
* Um arquivo de módulo do PowerShell pode conter várias classes de recursos DSC.

Para obter mais informações, veja [Escrevendo um recurso personalizado de DSC com classes do PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).