---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
ms.openlocfilehash: 3b2c268cd10d7c421b3d1fc73a7bbeaa4714f5fc
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="authoring-improvements-using-powershell-ise"></a>Criando melhorias usando o ISE do PowerShell

Criar configurações DSC no ISE do Windows PowerShell ficou muito mais fácil, graças às seguintes melhorias:

- Liste todos os recursos DSC dentro de um bloco de **configuração** ou de **nó** inserindo **Ctrl+Espaço** em uma linha em branco nele.
- O preenchimento automático das propriedades de recurso é do tipo **enumeração**.
- O preenchimento automático da propriedade **DependsOn** dos recursos DSC baseia-se em outras instâncias de recurso na configuração.
- Um melhor preenchimento de tabulação dos valores de propriedade de recurso.

**Observação:** é necessário ter uma cadeia de caracteres vazia para valores de propriedade de recurso antes que seja possível usar Ctrl+Espaço para listar as opções. Pressionar **Tab** percorrerá as opções.