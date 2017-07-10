---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
ms.openlocfilehash: d40e5475c4132d6377c9a4559262a41b4842180a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
<a id="class-based-dsc-resources" class="xliff"></a>
# Recursos DSC baseados em classe

<a id="defining-dsc-resources-with-classes" class="xliff"></a>
## Definindo recursos DSC com classes

Com base nos comentários, tornamos a criação de recursos DSC baseados em classe mais simples e mais fácil de entender. As principais diferenças entre um recurso DSC baseado em classe e um provedor de recursos DSC de cmdlet são:

* Um arquivo MOF para o esquema não é necessário.
* Uma subpasta **DSCResource** na pasta do módulo não é necessária.
* Um arquivo de módulo do PowerShell pode conter várias classes de recursos DSC.

Para obter mais informações, veja [Escrevendo um recurso personalizado de DSC com classes do PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).

