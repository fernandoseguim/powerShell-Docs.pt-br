---
title: Como declarar conjuntos de parâmetros | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859692"
---
# <a name="how-to-declare-parameter-sets"></a><span data-ttu-id="1a44d-102">Como declarar conjuntos de parâmetros</span><span class="sxs-lookup"><span data-stu-id="1a44d-102">How to Declare Parameter Sets</span></span>

<span data-ttu-id="1a44d-103">Este exemplo mostra como definir dois conjuntos de parâmetros quando você declara os parâmetros para um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1a44d-103">This example shows how to define two parameter sets when you declare the parameters for a cmdlet.</span></span> <span data-ttu-id="1a44d-104">Cada conjunto de parâmetro tem um parâmetro exclusivo e um parâmetro compartilhado que é usado em ambos os conjuntos de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1a44d-104">Each parameter set has both a unique parameter and a shared parameter that is used by both parameter sets.</span></span> <span data-ttu-id="1a44d-105">Para obter mais informações sobre conjuntos de parâmetros, incluindo como especificar o conjunto de parâmetros padrão, consulte [conjuntos de parâmetros do Cmdlet](./cmdlet-parameter-sets.md).</span><span class="sxs-lookup"><span data-stu-id="1a44d-105">For more information about parameters sets, including how to specify the default parameter set, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1a44d-106">Sempre que possível, defina o parâmetro unique de um parâmetro definido como um parâmetro obrigatório.</span><span class="sxs-lookup"><span data-stu-id="1a44d-106">Whenever possible, define the unique parameter of a parameter set as a required parameter.</span></span> <span data-ttu-id="1a44d-107">No entanto, se você quiser que seu cmdlet para executar sem especificar nenhum parâmetro, o parâmetro unique pode ser um parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="1a44d-107">However, if you want your cmdlet to run without specifying any parameters, the unique parameter can be an optional parameter.</span></span> <span data-ttu-id="1a44d-108">Por exemplo, o parâmetro unique do `Get-Command` cmdlet é opcional.</span><span class="sxs-lookup"><span data-stu-id="1a44d-108">For example, the unique parameter of the `Get-Command` cmdlet is optional.</span></span>

## <a name="how-to-define-two-parameter-sets"></a><span data-ttu-id="1a44d-109">Como definir dois conjuntos de parâmetros</span><span class="sxs-lookup"><span data-stu-id="1a44d-109">How to Define Two Parameter Sets</span></span>

1. <span data-ttu-id="1a44d-110">Adicionar o `ParameterSet` palavra-chave para o atributo de parâmetro para o parâmetro unique do primeiro conjunto de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="1a44d-110">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the first parameter set.</span></span>

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test01")]
   public string UserName
   {
     get { return userName; }
     set { userName = value; }
   }
   private string userName;
   ```

2. <span data-ttu-id="1a44d-111">Adicionar o `ParameterSet` palavra-chave para o atributo de parâmetro para o parâmetro unique do segundo conjunto de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1a44d-111">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the second parameter set.</span></span>

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test02")]
   public string ComputerName
   {
     get { return computerName; }
     set { computerName = value; }
   }
   private string computerName;
   ```

3. <span data-ttu-id="1a44d-112">Para o parâmetro que pertence a ambos os conjuntos de parâmetros, adicione um atributo de parâmetro para cada conjunto de parâmetros e, em seguida, adicione o `ParameterSet` palavra-chave para cada conjunto.</span><span class="sxs-lookup"><span data-stu-id="1a44d-112">For the parameter that belongs to both parameter sets, add a Parameter attribute for each parameter set and then add the `ParameterSet` keyword to each set.</span></span> <span data-ttu-id="1a44d-113">Em cada atributo de parâmetro, você pode especificar como esse parâmetro é definido.</span><span class="sxs-lookup"><span data-stu-id="1a44d-113">In each Parameter attribute, you can specify how that parameter is defined.</span></span> <span data-ttu-id="1a44d-114">Um parâmetro pode ser opcional em um conjunto e obrigatórias em outro.</span><span class="sxs-lookup"><span data-stu-id="1a44d-114">A parameter can be optional in one set and mandatory in another.</span></span>

   ```csharp
   [Parameter(Mandatory= true, ParameterSetName = "Test01")]
   [Parameter(ParameterSetName = "Test02")]
   public string SharedParam
   {
       get { return sharedParam; }
       set { sharedParam = value; }
   }
   private string sharedParam;
   ```

## <a name="see-also"></a><span data-ttu-id="1a44d-115">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="1a44d-115">See Also</span></span>

[<span data-ttu-id="1a44d-116">Conjuntos de parâmetros do cmdlet</span><span class="sxs-lookup"><span data-stu-id="1a44d-116">Cmdlet Parameter Sets</span></span>](./cmdlet-parameter-sets.md)

<span data-ttu-id="1a44d-117">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="1a44d-117">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
