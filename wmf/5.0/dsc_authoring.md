---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
ms.openlocfilehash: 555e01e88647b40717417360fb74bb6554a9c122
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="authoring-improvements-using-powershell-ise"></a>Criando melhorias usando o ISE do PowerShell

Criar configurações DSC no ISE do Windows PowerShell ficou muito mais fácil, graças às seguintes melhorias:

- Liste todos os recursos DSC dentro de um bloco de **configuração** ou de **nó** inserindo **Ctrl+Espaço** em uma linha em branco nele.
- O preenchimento automático das propriedades de recurso é do tipo **enumeração**.
- O preenchimento automático da propriedade **DependsOn** dos recursos DSC baseia-se em outras instâncias de recurso na configuração.
- Um melhor preenchimento de tabulação dos valores de propriedade de recurso.

**Observação:** é necessário ter uma cadeia de caracteres vazia para valores de propriedade de recurso antes que seja possível usar Ctrl+Espaço para listar as opções. Pressionar **Tab** percorrerá as opções.

