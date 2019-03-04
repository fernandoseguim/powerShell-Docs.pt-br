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
# <a name="cmdlet-dynamic-parameters"></a>Parâmetros dinâmicos de cmdlet

Cmdlets pode definir os parâmetros que estão disponíveis para o usuário sob condições especiais, como quando o argumento de outro parâmetro é um valor específico. Esses parâmetros são adicionados em tempo de execução e são denominados *parâmetros dinâmicos* porque eles são adicionados apenas quando eles forem necessários. Por exemplo, você pode criar um cmdlet que adiciona vários parâmetros somente quando um parâmetro de opção específico é especificado.

> [!NOTE]
> Provedores e funções do Windows PowerShell também podem definir parâmetros dinâmicos.

## <a name="dynamic-parameters-in-windows-powershell-cmdlets"></a>Parâmetros dinâmicos nos Cmdlets do Windows PowerShell

Windows PowerShell usa os parâmetros dinâmicos em vários dos seus cmdlets do provedor. Por exemplo, o `Get-Item` e `Get-ChildItem` adicionar cmdlets uma `CodeSigningCert` parâmetro em tempo de execução quando o `Path` parâmetro do cmdlet especifica o caminho do provedor de certificado. Se o `Path` parâmetro do cmdlet especifica um caminho para um provedor diferente, o `CodeSigningCert` parâmetro não está disponível.

Os exemplos a seguir mostram como o `CodeSigningCert` parâmetro é adicionado em tempo de execução quando o `Get-Item` cmdlet é executado.

No primeiro exemplo, o tempo de execução do Windows PowerShell tiver adicionado o parâmetro e o cmdlet é bem-sucedida.

```powershell
Get-Item -Path cert:\CurrentUser -codesigningcert
```

```output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

No segundo exemplo, uma unidade de sistema de arquivos for especificada e um erro será retornado. A mensagem de erro indica que o `CodeSigningCert` parâmetro não pode ser encontrado.

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

## <a name="support-for-dynamic-parameters"></a>Suporte para parâmetros dinâmicos

Para dar suporte a parâmetros dinâmicos, o código do cmdlet deve incluir os seguintes elementos.

[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) essa interface fornece o método que recupera os parâmetros dinâmicos.

Exemplo:

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) esse método recupera o objeto que contém as definições de parâmetro dinâmico.

Exemplo:

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

Classe de parâmetro dinâmico essa classe define os parâmetros a serem adicionados. Essa classe deve incluir um atributo de parâmetro para cada parâmetro e os atributos opcionais de Alias e de validação que são necessários para o cmdlet.

Exemplo:

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

Para obter um exemplo completo de um cmdlet que dá suporte a parâmetros dinâmicos, consulte [como declarar parâmetros dinâmicos](./how-to-declare-dynamic-parameters.md).

## <a name="see-also"></a>Consulte Também

[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters)

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Como declarar parâmetros dinâmicos](./how-to-declare-dynamic-parameters.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
