---
title: Declaração de atributo de credenciais | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: 49a62ccb09f06f77862d4737199e58293e7fbe0a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059245"
---
# <a name="credential-attribute-declaration"></a><span data-ttu-id="dbd68-102">Declaração de atributo de credencial</span><span class="sxs-lookup"><span data-stu-id="dbd68-102">Credential Attribute Declaration</span></span>

<span data-ttu-id="dbd68-103">A credencial é um atributo opcional que pode ser usado com parâmetros de tipo de credencial [pscredential](/dotnet/api/System.Management.Automation.PSCredential) para que uma cadeia de caracteres também pode ser passada como um argumento para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="dbd68-103">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="dbd68-104">Quando esse atributo é adicionado a uma declaração de parâmetro, o Windows PowerShell converte a entrada de cadeia de caracteres em uma [pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto.</span><span class="sxs-lookup"><span data-stu-id="dbd68-104">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="dbd68-105">Por exemplo, o [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet usa esse atributo para o Windows PowerShell gerar as [pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto que é retornado pelo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dbd68-105">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="dbd68-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dbd68-106">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="dbd68-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="dbd68-107">Remarks</span></span>

- <span data-ttu-id="dbd68-108">Normalmente, esse atributo é usado pelos parâmetros do tipo [pscredential](/dotnet/api/System.Management.Automation.PSCredential) para que uma cadeia de caracteres também pode ser passada como um argumento para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="dbd68-108">Typically this attribute is used by parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="dbd68-109">Quando um [pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto é passado para o parâmetro, o Windows PowerShell não faz nada.</span><span class="sxs-lookup"><span data-stu-id="dbd68-109">When a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="dbd68-110">Ao criar o [pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto, o Windows PowerShell usa o Host atual para exibir os avisos apropriados para o usuário.</span><span class="sxs-lookup"><span data-stu-id="dbd68-110">When creating the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="dbd68-111">Por exemplo, o padrão Host exibe um prompt para um nome de usuário e uma senha quando esse atributo é usado.</span><span class="sxs-lookup"><span data-stu-id="dbd68-111">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="dbd68-112">No entanto, se um host personalizado estiver sendo usado que define um prompt de diferente e em seguida, esse prompt seria exibido.</span><span class="sxs-lookup"><span data-stu-id="dbd68-112">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="dbd68-113">Este atributo é usado com o atributo de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="dbd68-113">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="dbd68-114">Para obter mais informações sobre esse atributo, consulte [declaração de atributo de parâmetro](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="dbd68-114">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="dbd68-115">O atributo de credencial é definido pela [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="dbd68-115">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="dbd68-116">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="dbd68-116">See Also</span></span>

[<span data-ttu-id="dbd68-117">Aliases de parâmetro</span><span class="sxs-lookup"><span data-stu-id="dbd68-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="dbd68-118">Declaração de atributo de parâmetro</span><span class="sxs-lookup"><span data-stu-id="dbd68-118">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

<span data-ttu-id="dbd68-119">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="dbd68-119">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
