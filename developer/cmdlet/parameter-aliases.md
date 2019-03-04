---
title: Aliases de parâmetro | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853312"
---
# <a name="parameter-aliases"></a><span data-ttu-id="b7f5f-102">Aliases de parâmetro</span><span class="sxs-lookup"><span data-stu-id="b7f5f-102">Parameter Aliases</span></span>

<span data-ttu-id="b7f5f-103">Os parâmetros de cmdlets também podem ter aliases.</span><span class="sxs-lookup"><span data-stu-id="b7f5f-103">Cmdlet parameters can also have aliases.</span></span> <span data-ttu-id="b7f5f-104">Você pode usar os aliases em vez dos nomes de parâmetro, quando você digita ou especifica o parâmetro em um comando.</span><span class="sxs-lookup"><span data-stu-id="b7f5f-104">You can use the aliases instead of the parameter names when you type or specify the parameter in a command.</span></span>

## <a name="benefits-of-using-aliases"></a><span data-ttu-id="b7f5f-105">Benefícios do uso de Aliases</span><span class="sxs-lookup"><span data-stu-id="b7f5f-105">Benefits of Using Aliases</span></span>

<span data-ttu-id="b7f5f-106">A adição de aliases para parâmetros fornece os seguintes benefícios.</span><span class="sxs-lookup"><span data-stu-id="b7f5f-106">Adding aliases to parameters provides the following benefits.</span></span>

- <span data-ttu-id="b7f5f-107">Você pode fornecer um atalho para que o usuário não precisa usar o nome de parâmetro completa quando o cmdlet for chamado.</span><span class="sxs-lookup"><span data-stu-id="b7f5f-107">You can provide a shortcut so that the user does not have to use the complete parameter name when the cmdlet is called.</span></span> <span data-ttu-id="b7f5f-108">Por exemplo, você pode usar o alias "CN" em vez do nome do parâmetro "NomeDoComputador".</span><span class="sxs-lookup"><span data-stu-id="b7f5f-108">For example, you could use the "CN" alias instead of the parameter name "ComputerName".</span></span>

- <span data-ttu-id="b7f5f-109">Se você quiser fornecer nomes diferentes para o mesmo parâmetro, você pode definir vários aliases.</span><span class="sxs-lookup"><span data-stu-id="b7f5f-109">You can define multiple aliases if you want to provide different names for the same parameter.</span></span> <span data-ttu-id="b7f5f-110">Você talvez queira definir vários aliases, se você tiver que trabalhar com vários grupos de usuários que se referem aos mesmos dados de maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="b7f5f-110">You might want to define multiple aliases if you have to work with multiple user groups that refer to the same data in different ways.</span></span>

- <span data-ttu-id="b7f5f-111">Você pode fornecer com versões anteriores compatibilidade para os scripts existentes se o nome de um parâmetro for alterado.</span><span class="sxs-lookup"><span data-stu-id="b7f5f-111">You can provide backwards compatibility for existing scripts if the name of a parameter changes.</span></span>

- <span data-ttu-id="b7f5f-112">Usando o atributo de Alias, juntamente com o atributo ValueFromPipelineByName, você pode definir um parâmetro que permite que seu cmdlet associar a diferentes tipos de objeto.</span><span class="sxs-lookup"><span data-stu-id="b7f5f-112">By using the Alias attribute along with the ValueFromPipelineByName attribute, you can define a parameter that allows your cmdlet to bind to different object types.</span></span> <span data-ttu-id="b7f5f-113">Por exemplo, digamos que você tinha dois objetos de tipos diferentes e o primeiro objeto tinha uma propriedade de gravador e o segundo objeto tinha uma propriedade do editor.</span><span class="sxs-lookup"><span data-stu-id="b7f5f-113">For example, say you had two objects of different types and the first object had a writer property and the second object had an editor property.</span></span> <span data-ttu-id="b7f5f-114">Se seu cmdlet tinha um parâmetro que tinha aliases escritor e editor e o cmdlet aceita entrada do pipeline com base em nomes de propriedade, seu cmdlet pôde ligar aos dois objetos usando dois aliases de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b7f5f-114">If your cmdlet had a parameter that had writer and editor aliases and the cmdlet accepted pipeline input based in property names, your cmdlet could bind to both objects using the two parameter aliases.</span></span>

<span data-ttu-id="b7f5f-115">Para obter mais informações sobre aliases que podem ser usados com parâmetros específicos, consulte [nomes de parâmetro comuns](./common-parameter-names.md).</span><span class="sxs-lookup"><span data-stu-id="b7f5f-115">For more information about aliases that can be used with specific parameters, see [Common Parameter Names](./common-parameter-names.md).</span></span>

## <a name="defining-parameter-aliases"></a><span data-ttu-id="b7f5f-116">Definir Aliases de parâmetro</span><span class="sxs-lookup"><span data-stu-id="b7f5f-116">Defining Parameter Aliases</span></span>

<span data-ttu-id="b7f5f-117">Para definir um alias para um parâmetro, declare o atributo de Alias, conforme mostrado na seguinte declaração de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b7f5f-117">To define an alias for a parameter, declare the Alias attribute, as shown in the following parameter declaration.</span></span> <span data-ttu-id="b7f5f-118">Neste exemplo, vários aliases são definidos para o mesmo parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b7f5f-118">In this example, multiple aliases are defined for the same parameter.</span></span> <span data-ttu-id="b7f5f-119">(Para obter mais informações, consulte[como declarar parâmetros de Cmdlet](./how-to-declare-cmdlet-parameters.md).)</span><span class="sxs-lookup"><span data-stu-id="b7f5f-119">(For more information, see[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).)</span></span>

```csharp
[Alias("UN","Writer","Editor")]
[Parameter()]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="see-also"></a><span data-ttu-id="b7f5f-120">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="b7f5f-120">See Also</span></span>

[<span data-ttu-id="b7f5f-121">Nomes de parâmetro comuns</span><span class="sxs-lookup"><span data-stu-id="b7f5f-121">Common Parameter Names</span></span>](./common-parameter-names.md)

[<span data-ttu-id="b7f5f-122">Como declarar parâmetros de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b7f5f-122">How to Declare Cmdlet Parameters</span></span>](./how-to-declare-cmdlet-parameters.md)

<span data-ttu-id="b7f5f-123">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="b7f5f-123">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
