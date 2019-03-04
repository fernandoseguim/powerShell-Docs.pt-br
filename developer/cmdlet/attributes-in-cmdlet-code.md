---
title: Atributos no código do Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853782"
---
# <a name="attributes-in-cmdlet-code"></a><span data-ttu-id="6e628-102">Atributos no código do cmdlet</span><span class="sxs-lookup"><span data-stu-id="6e628-102">Attributes in Cmdlet Code</span></span>

<span data-ttu-id="6e628-103">Para usar a funcionalidade comum fornecida pelo Windows PowerShell, as classes e propriedades públicas definidas no código do cmdlet são decoradas com atributos.</span><span class="sxs-lookup"><span data-stu-id="6e628-103">To use the common functionality provided by Windows PowerShell, the classes and public properties defined in the cmdlet code are decorated with attributes.</span></span> <span data-ttu-id="6e628-104">Por exemplo, a definição de classe a seguir usa o atributo de Cmdlet para identificar a classe do Microsoft .NET Framework na qual o **Get-Proc** cmdlet é implementado.</span><span class="sxs-lookup"><span data-stu-id="6e628-104">For example, the following class definition uses the Cmdlet attribute to identify the Microsoft .NET Framework class in which the **Get-Proc** cmdlet is implemented.</span></span> <span data-ttu-id="6e628-105">(Esse cmdlet é usado como exemplo neste documento e é semelhante ao `Get-Process` cmdlet fornecido pelo Windows PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="6e628-105">(This cmdlet is used as an example in this document, and is similar to the `Get-Process` cmdlet provided by Windows PowerShell.)</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="6e628-106">Esses atributos são considerados metadados porque sua implementação é separada da implementação do código do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6e628-106">These attributes are considered metadata because their implementation is separate from the implementation of the cmdlet code.</span></span> <span data-ttu-id="6e628-107">Quando o tempo de execução do Windows PowerShell executa o cmdlet, ele reconhece os atributos e, em seguida, executa a ação apropriada para cada atributo.</span><span class="sxs-lookup"><span data-stu-id="6e628-107">When the Windows PowerShell runtime runs the cmdlet, it recognizes the attributes and then performs the appropriate action for each attribute.</span></span>

<span data-ttu-id="6e628-108">Embora você talvez queira implementar sua própria versão da funcionalidade fornecida por meio desses atributos, um cmdlet bom design usa essas funcionalidades comuns.</span><span class="sxs-lookup"><span data-stu-id="6e628-108">Although you might want to implement your own version of the functionality provided by these attributes, a good cmdlet design uses these common functionalities.</span></span>

<span data-ttu-id="6e628-109">Para obter mais informações sobre os diferentes atributos que podem ser declaradas em seus cmdlets, consulte [tipos de atributo](./attribute-types.md).</span><span class="sxs-lookup"><span data-stu-id="6e628-109">For more information about the different attributes that can be declared in your cmdlets, see [Attribute Types](./attribute-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6e628-110">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="6e628-110">See Also</span></span>

[<span data-ttu-id="6e628-111">Tipos de atributo</span><span class="sxs-lookup"><span data-stu-id="6e628-111">Attribute Types</span></span>](./attribute-types.md)

<span data-ttu-id="6e628-112">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="6e628-112">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
