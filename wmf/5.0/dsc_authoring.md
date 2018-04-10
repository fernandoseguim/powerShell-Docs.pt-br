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
# <a name="authoring-improvements-using-powershell-ise"></a><span data-ttu-id="08006-102">Criando melhorias usando o ISE do PowerShell</span><span class="sxs-lookup"><span data-stu-id="08006-102">Authoring Improvements using PowerShell ISE</span></span>

<span data-ttu-id="08006-103">Criar configurações DSC no ISE do Windows PowerShell ficou muito mais fácil, graças às seguintes melhorias:</span><span class="sxs-lookup"><span data-stu-id="08006-103">Authoring DSC configurations in Windows PowerShell ISE is much easier, thanks to the following improvements:</span></span>

- <span data-ttu-id="08006-104">Liste todos os recursos DSC dentro de um bloco de **configuração** ou de **nó** inserindo **Ctrl+Espaço** em uma linha em branco nele.</span><span class="sxs-lookup"><span data-stu-id="08006-104">List all DSC resources within a **configuration** block or **node** block by entering **Ctrl+Space** on a blank line within it.</span></span>
- <span data-ttu-id="08006-105">O preenchimento automático das propriedades de recurso é do tipo **enumeração**.</span><span class="sxs-lookup"><span data-stu-id="08006-105">Automatic completion on resource properties that are of the **enumeration** type.</span></span>
- <span data-ttu-id="08006-106">O preenchimento automático da propriedade **DependsOn** dos recursos DSC baseia-se em outras instâncias de recurso na configuração.</span><span class="sxs-lookup"><span data-stu-id="08006-106">Automatic completion on the **DependsOn** property of DSC resources, based on other resource instances in the configuration.</span></span>
- <span data-ttu-id="08006-107">Um melhor preenchimento de tabulação dos valores de propriedade de recurso.</span><span class="sxs-lookup"><span data-stu-id="08006-107">Better tab completion of resource property values.</span></span>

<span data-ttu-id="08006-108">**Observação:** é necessário ter uma cadeia de caracteres vazia para valores de propriedade de recurso antes que seja possível usar Ctrl+Espaço para listar as opções.</span><span class="sxs-lookup"><span data-stu-id="08006-108">**Note:** You must have an empty string for resource property values before you can use Ctrl+Space to list the options.</span></span> <span data-ttu-id="08006-109">Pressionar **Tab** percorrerá as opções.</span><span class="sxs-lookup"><span data-stu-id="08006-109">Pressing **Tab** cycles through options.</span></span>