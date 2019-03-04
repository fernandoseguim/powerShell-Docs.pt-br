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
# <a name="credential-attribute-declaration"></a>Declaração de atributo de credencial

A credencial é um atributo opcional que pode ser usado com parâmetros de tipo de credencial [pscredential](/dotnet/api/System.Management.Automation.PSCredential) para que uma cadeia de caracteres também pode ser passada como um argumento para o parâmetro. Quando esse atributo é adicionado a uma declaração de parâmetro, o Windows PowerShell converte a entrada de cadeia de caracteres em uma [pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto. Por exemplo, o [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet usa esse atributo para o Windows PowerShell gerar as [pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto que é retornado pelo cmdlet.
A credencial é um atributo opcional que pode ser usado com parâmetros de tipo de credencial [pscredential](/dotnet/api/System.Management.Automation.PSCredential) para que uma cadeia de caracteres também pode ser passada como um argumento para o parâmetro. Quando esse atributo é adicionado a uma declaração de parâmetro, o Windows PowerShell converte a entrada de cadeia de caracteres em uma [pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto. Por exemplo, o [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet usa esse atributo para o Windows PowerShell gerar as [pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto que é retornado pelo cmdlet.

## <a name="syntax"></a>Sintaxe

```csharp
[Credential]
```

## <a name="remarks"></a>Comentários

- Normalmente, esse atributo é usado pelos parâmetros do tipo [pscredential](/dotnet/api/System.Management.Automation.PSCredential) para que uma cadeia de caracteres também pode ser passada como um argumento para o parâmetro. Quando um [pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto é passado para o parâmetro, o Windows PowerShell não faz nada.

- Ao criar o [pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto, o Windows PowerShell usa o Host atual para exibir os avisos apropriados para o usuário. Por exemplo, o padrão Host exibe um prompt para um nome de usuário e uma senha quando esse atributo é usado. No entanto, se um host personalizado estiver sendo usado que define um prompt de diferente e em seguida, esse prompt seria exibido.

- Este atributo é usado com o atributo de parâmetro. Para obter mais informações sobre esse atributo, consulte [declaração de atributo de parâmetro](./parameter-attribute-declaration.md).

- O atributo de credencial é definido pela [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) classe.

## <a name="see-also"></a>Consulte Também

[Aliases de parâmetro](./parameter-aliases.md)

[Declaração de atributo de parâmetro](./parameter-attribute-declaration.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
