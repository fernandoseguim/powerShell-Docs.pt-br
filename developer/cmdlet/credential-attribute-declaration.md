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
ms.openlocfilehash: abdd6e915b768b8ac688b6fc8c3194723961765e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863392"
---
# <a name="credential-attribute-declaration"></a><span data-ttu-id="0fa04-102">Declaração de atributo de credencial</span><span class="sxs-lookup"><span data-stu-id="0fa04-102">Credential Attribute Declaration</span></span>

<span data-ttu-id="0fa04-103">A credencial é um atributo opcional que pode ser usado com parâmetros de tipo de credencial [pscredential](/dotnet/api/System.Management.Automation.PSCredential) para que uma cadeia de caracteres também pode ser passada como um argumento para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="0fa04-103">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="0fa04-104">Quando esse atributo é adicionado a uma declaração de parâmetro, o Windows PowerShell converte a entrada de cadeia de caracteres em uma [pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto.</span><span class="sxs-lookup"><span data-stu-id="0fa04-104">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="0fa04-105">Por exemplo, o [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet usa esse atributo para o Windows PowerShell gerar as [pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto que é retornado pelo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0fa04-105">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>
<span data-ttu-id="0fa04-106">A credencial é um atributo opcional que pode ser usado com parâmetros de tipo de credencial [pscredential](/dotnet/api/System.Management.Automation.PSCredential) para que uma cadeia de caracteres também pode ser passada como um argumento para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="0fa04-106">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="0fa04-107">Quando esse atributo é adicionado a uma declaração de parâmetro, o Windows PowerShell converte a entrada de cadeia de caracteres em uma [pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto.</span><span class="sxs-lookup"><span data-stu-id="0fa04-107">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="0fa04-108">Por exemplo, o [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet usa esse atributo para o Windows PowerShell gerar as [pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto que é retornado pelo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0fa04-108">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="0fa04-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0fa04-109">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="0fa04-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="0fa04-110">Remarks</span></span>

- <span data-ttu-id="0fa04-111">Normalmente, esse atributo é usado pelos parâmetros do tipo [pscredential](/dotnet/api/System.Management.Automation.PSCredential) para que uma cadeia de caracteres também pode ser passada como um argumento para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="0fa04-111">Typically this attribute is used by parameters of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="0fa04-112">Quando um [pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto é passado para o parâmetro, o Windows PowerShell não faz nada.</span><span class="sxs-lookup"><span data-stu-id="0fa04-112">When a [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="0fa04-113">Ao criar o [pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto, o Windows PowerShell usa o Host atual para exibir os avisos apropriados para o usuário.</span><span class="sxs-lookup"><span data-stu-id="0fa04-113">When creating the [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="0fa04-114">Por exemplo, o padrão Host exibe um prompt para um nome de usuário e uma senha quando esse atributo é usado.</span><span class="sxs-lookup"><span data-stu-id="0fa04-114">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="0fa04-115">No entanto, se um host personalizado estiver sendo usado que define um prompt de diferente e em seguida, esse prompt seria exibido.</span><span class="sxs-lookup"><span data-stu-id="0fa04-115">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="0fa04-116">Este atributo é usado com o atributo de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="0fa04-116">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="0fa04-117">Para obter mais informações sobre esse atributo, consulte [declaração de atributo de parâmetro](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0fa04-117">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="0fa04-118">O atributo de credencial é definido pela [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="0fa04-118">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="0fa04-119">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="0fa04-119">See Also</span></span>

[<span data-ttu-id="0fa04-120">Aliases de parâmetro</span><span class="sxs-lookup"><span data-stu-id="0fa04-120">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="0fa04-121">Declaração de atributo de parâmetro</span><span class="sxs-lookup"><span data-stu-id="0fa04-121">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

<span data-ttu-id="0fa04-122">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="0fa04-122">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
