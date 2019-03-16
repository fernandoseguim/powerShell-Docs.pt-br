---
title: Atributos de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.assetid: d3f4f652-d929-4c27-9358-9baa390a094c
caps.latest.revision: 14
ms.openlocfilehash: 326cd408e86402974569fc76d5e473be5a56f0b6
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055165"
---
# <a name="cmdlet-attributes"></a><span data-ttu-id="4b0de-102">Atributos de cmdlet</span><span class="sxs-lookup"><span data-stu-id="4b0de-102">Cmdlet Attributes</span></span>

<span data-ttu-id="4b0de-103">Windows PowerShell define vários atributos que você pode usar para adicionar funcionalidade comum para seus cmdlets sem implementar essa funcionalidade em seu próprio código.</span><span class="sxs-lookup"><span data-stu-id="4b0de-103">Windows PowerShell defines several attributes that you can use to add common functionality to your cmdlets without implementing that functionality within your own code.</span></span> <span data-ttu-id="4b0de-104">Isso inclui o atributo de Cmdlet que identifica uma classe do Microsoft .NET Framework como uma classe do cmdlet, o atributo de tipo de saída que especifica os tipos do .NET Framework retornados pelo cmdlet, o atributo de parâmetro que identifica as propriedades públicas como o cmdlet parâmetros e muito mais.</span><span class="sxs-lookup"><span data-stu-id="4b0de-104">This includes the Cmdlet attribute that identifies a Microsoft .NET Framework class as a cmdlet class, the OutputType attribute that specifies the .NET Framework types returned by the cmdlet, the Parameter attribute that identifies public properties as cmdlet parameters, and more.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="4b0de-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="4b0de-105">In This Section</span></span>

<span data-ttu-id="4b0de-106">[Atributos no código do Cmdlet](./attributes-in-cmdlet-code.md) descreve a vantagem de usar atributos no código do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4b0de-106">[Attributes in Cmdlet Code](./attributes-in-cmdlet-code.md) Describes the benefit of using attributes in cmdlet code.</span></span>

<span data-ttu-id="4b0de-107">[Tipos de atributo](./attribute-types.md) descreve os atributos diferentes que podem decorar uma classe cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4b0de-107">[Attribute Types](./attribute-types.md) Describes the different attributes that can decorate a cmdlet class.</span></span>

<span data-ttu-id="4b0de-108">[Declaração de atributo de alias](./alias-attribute-declaration.md) descreve como definir aliases para um nome de parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4b0de-108">[Alias Attribute Declaration](./alias-attribute-declaration.md) Describes how to define aliases for a cmdlet parameter name.</span></span>

<span data-ttu-id="4b0de-109">[Declaração de atributo do cmdlet](./cmdlet-attribute-declaration.md) descreve como definir uma classe do .NET Framework como um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4b0de-109">[Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md) Describes how to define a .NET Framework class as a cmdlet.</span></span>

<span data-ttu-id="4b0de-110">[Declaração de atributo de credencial](./credential-attribute-declaration.md) descreve como adicionar suporte para converter a entrada de cadeia de caracteres em um [pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto.</span><span class="sxs-lookup"><span data-stu-id="4b0de-110">[Credential Attribute Declaration](./credential-attribute-declaration.md) Describes how to add support for converting string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span>

<span data-ttu-id="4b0de-111">[Atributo OutputType declaração](./outputtype-attribute-declaration.md) descreve como especificar tipos do .NET Framework retornados pelo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4b0de-111">[OutputType attribute Declaration](./outputtype-attribute-declaration.md) Describes how to specify the .NET Framework types returned by the cmdlet.</span></span>

<span data-ttu-id="4b0de-112">[Declaração de atributo de parâmetro](./parameter-attribute-declaration.md) descreve como definir os parâmetros de um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4b0de-112">[Parameter Attribute Declaration](./parameter-attribute-declaration.md) Describes how to define the parameters of a cmdlet.</span></span>

<span data-ttu-id="4b0de-113">[Declaração de atributo ValidateCount](./validatecount-attribute-declaration.md) descreve como definir quantos argumentos são permitidos para um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4b0de-113">[ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md) Describes how to define how many arguments are allowed for a parameter.</span></span>

<span data-ttu-id="4b0de-114">[Declaração de atributo ValidateLength](./validatelength-attribute-declaration.md) descreve como definir o comprimento (em caracteres) de um argumento do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4b0de-114">[ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md) Describes how to define the length (in characters) of a parameter argument.</span></span>

<span data-ttu-id="4b0de-115">[Declaração de atributo ValidatePattern](./validatepattern-attribute-declaration.md) descreve como definir os padrões de válido para um argumento de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4b0de-115">[ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md) Describes how to define the valid patterns for a parameter argument.</span></span>

<span data-ttu-id="4b0de-116">[Declaração de atributo ValidateRange](./validaterange-attribute-declaration.md) descreve como definir o intervalo válido para um argumento de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4b0de-116">[ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md) Describes how to define the valid range for a parameter argument.</span></span>

<span data-ttu-id="4b0de-117">[Declaração de atributo ValidateSet](./validateset-attribute-declaration.md) descreve como definir os valores possíveis para um argumento de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4b0de-117">[ValidateSet Attribute Declaration](./validateset-attribute-declaration.md) Describes how to define the possible values for a parameter argument.</span></span>

## <a name="reference"></a><span data-ttu-id="4b0de-118">Referência</span><span class="sxs-lookup"><span data-stu-id="4b0de-118">Reference</span></span>

<span data-ttu-id="4b0de-119">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="4b0de-119">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
