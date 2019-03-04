---
title: Parâmetros de cmdlet dinâmico | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 2fc73b6ef5a862fafb7a3c8fe3da19ac71bafc05
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853802"
---
# <a name="cmdlet-dynamic-parameters"></a><span data-ttu-id="9772d-102">Parâmetros dinâmicos de cmdlet</span><span class="sxs-lookup"><span data-stu-id="9772d-102">Cmdlet Dynamic Parameters</span></span>

<span data-ttu-id="9772d-103">Cmdlets pode definir os parâmetros que estão disponíveis para o usuário sob condições especiais, como quando o argumento de outro parâmetro é um valor específico.</span><span class="sxs-lookup"><span data-stu-id="9772d-103">Cmdlets can define parameters that are available to the user under special conditions, such as when the argument of another parameter is a specific value.</span></span> <span data-ttu-id="9772d-104">Esses parâmetros são adicionados em tempo de execução e são denominados *parâmetros dinâmicos* porque eles são adicionados apenas quando eles forem necessários.</span><span class="sxs-lookup"><span data-stu-id="9772d-104">These parameters are added at runtime and are referred to as *dynamic parameters* because they are added only when they are needed.</span></span> <span data-ttu-id="9772d-105">Por exemplo, você pode criar um cmdlet que adiciona vários parâmetros somente quando um parâmetro de opção específico é especificado.</span><span class="sxs-lookup"><span data-stu-id="9772d-105">For example, you can design a cmdlet that adds several parameters only when a specific switch parameter is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="9772d-106">Provedores e funções do Windows PowerShell também podem definir parâmetros dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="9772d-106">Providers and Windows PowerShell functions can also define dynamic parameters.</span></span>

## <a name="dynamic-parameters-in-windows-powershell-cmdlets"></a><span data-ttu-id="9772d-107">Parâmetros dinâmicos nos Cmdlets do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9772d-107">Dynamic Parameters in Windows PowerShell Cmdlets</span></span>

<span data-ttu-id="9772d-108">Windows PowerShell usa os parâmetros dinâmicos em vários dos seus cmdlets do provedor.</span><span class="sxs-lookup"><span data-stu-id="9772d-108">Windows PowerShell uses dynamic parameters in several of its provider cmdlets.</span></span> <span data-ttu-id="9772d-109">Por exemplo, o `Get-Item` e `Get-ChildItem` adicionar cmdlets uma `CodeSigningCert` parâmetro em tempo de execução quando o `Path` parâmetro do cmdlet especifica o caminho do provedor de certificado.</span><span class="sxs-lookup"><span data-stu-id="9772d-109">For example, the `Get-Item` and `Get-ChildItem` cmdlets add a `CodeSigningCert` parameter at runtime when the `Path` parameter of the cmdlet specifies the Certificate provider path.</span></span> <span data-ttu-id="9772d-110">Se o `Path` parâmetro do cmdlet especifica um caminho para um provedor diferente, o `CodeSigningCert` parâmetro não está disponível.</span><span class="sxs-lookup"><span data-stu-id="9772d-110">If the `Path` parameter of the cmdlet specifies a path for a different provider, the `CodeSigningCert` parameter is not available.</span></span>

<span data-ttu-id="9772d-111">Os exemplos a seguir mostram como o `CodeSigningCert` parâmetro é adicionado em tempo de execução quando o `Get-Item` cmdlet é executado.</span><span class="sxs-lookup"><span data-stu-id="9772d-111">The following examples show how the `CodeSigningCert` parameter is added at runtime when the `Get-Item` cmdlet is run.</span></span>

<span data-ttu-id="9772d-112">No primeiro exemplo, o tempo de execução do Windows PowerShell tiver adicionado o parâmetro e o cmdlet é bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="9772d-112">In the first example, the Windows PowerShell runtime has added the parameter, and the cmdlet is successful.</span></span>

```powershell
Get-Item -Path cert:\CurrentUser -codesigningcert
```

```output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

<span data-ttu-id="9772d-113">No segundo exemplo, uma unidade de sistema de arquivos for especificada e um erro será retornado.</span><span class="sxs-lookup"><span data-stu-id="9772d-113">In the second example, a FileSystem drive is specified, and an error is returned.</span></span> <span data-ttu-id="9772d-114">A mensagem de erro indica que o `CodeSigningCert` parâmetro não pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="9772d-114">The error message indicates that the `CodeSigningCert` parameter cannot be found.</span></span>

```powershell
Get-Item -Path C:\ -codesigningcert
```

```output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a><span data-ttu-id="9772d-115">Suporte para parâmetros dinâmicos</span><span class="sxs-lookup"><span data-stu-id="9772d-115">Support for Dynamic Parameters</span></span>

<span data-ttu-id="9772d-116">Para dar suporte a parâmetros dinâmicos, o código do cmdlet deve incluir os seguintes elementos.</span><span class="sxs-lookup"><span data-stu-id="9772d-116">To support dynamic parameters, the cmdlet code must include the following elements.</span></span>

<span data-ttu-id="9772d-117">[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) essa interface fornece o método que recupera os parâmetros dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="9772d-117">[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) This interface provides the method that retrieves the dynamic parameters.</span></span>

<span data-ttu-id="9772d-118">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="9772d-118">Example:</span></span>

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

<span data-ttu-id="9772d-119">[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) esse método recupera o objeto que contém as definições de parâmetro dinâmico.</span><span class="sxs-lookup"><span data-stu-id="9772d-119">[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) This method retrieves the object that contains the dynamic parameter definitions.</span></span>

<span data-ttu-id="9772d-120">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="9772d-120">Example:</span></span>

```csharp
 public object GetDynamicParameters()
 {
   if (employee)
   {
     context= new SendGreetingCommandDynamicParameters();
     return context;
   }
   return null;
}
private SendGreetingCommandDynamicParameters context;
```

<span data-ttu-id="9772d-121">Classe de parâmetro dinâmico essa classe define os parâmetros a serem adicionados.</span><span class="sxs-lookup"><span data-stu-id="9772d-121">Dynamic Parameter class This class defines the parameters to be added.</span></span> <span data-ttu-id="9772d-122">Essa classe deve incluir um atributo de parâmetro para cada parâmetro e os atributos opcionais de Alias e de validação que são necessários para o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9772d-122">This class must include a Parameter attribute for each parameter and any optional Alias and Validation attributes that are needed by the cmdlet.</span></span>

<span data-ttu-id="9772d-123">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="9772d-123">Example:</span></span>

```csharp
public class SendGreetingCommandDynamicParameters
{
  [Parameter]
  [ValidateSet ("Marketing", "Sales", "Development")]
  public string Department
  {
    get { return department; }
    set { department = value; }
  }
  private string department;
}
```

<span data-ttu-id="9772d-124">Para obter um exemplo completo de um cmdlet que dá suporte a parâmetros dinâmicos, consulte [como declarar parâmetros dinâmicos](./how-to-declare-dynamic-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="9772d-124">For a complete example of a cmdlet that supports dynamic parameters, see [How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9772d-125">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="9772d-125">See Also</span></span>

[<span data-ttu-id="9772d-126">System.Management.Automation.Idynamicparameters</span><span class="sxs-lookup"><span data-stu-id="9772d-126">System.Management.Automation.Idynamicparameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters)

[<span data-ttu-id="9772d-127">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span><span class="sxs-lookup"><span data-stu-id="9772d-127">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="9772d-128">Como declarar parâmetros dinâmicos</span><span class="sxs-lookup"><span data-stu-id="9772d-128">How to Declare Dynamic Parameters</span></span>](./how-to-declare-dynamic-parameters.md)

<span data-ttu-id="9772d-129">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="9772d-129">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
