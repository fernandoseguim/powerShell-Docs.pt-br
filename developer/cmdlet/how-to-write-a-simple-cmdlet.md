---
title: Como escrever um Simple Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 01/15/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137543d8-0012-4cba-bcd6-98b25aac83bb
caps.latest.revision: 9
ms.openlocfilehash: 8271512d06047f3ff5e45f81d971ffe2c1f6afd7
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251448"
---
# <a name="how-to-write-a-cmdlet"></a>Como gravar um cmdlet

Este artigo mostra como gravar um cmdlet. O `Send-Greeting` cmdlet usa um nome de usuário único como entrada e, em seguida, grava uma saudação ao usuário. Embora o cmdlet não faz muito trabalho, este exemplo demonstra as principais seções de um cmdlet.

## <a name="steps-to-write-a-cmdlet"></a>Etapas para gravar um cmdlet

1. Para declarar a classe como um cmdlet, use o **Cmdlet** atributo. O **Cmdlet** atributo especifica o verbo e substantivo para o nome do cmdlet.

   Para obter mais informações sobre o **Cmdlet** atributo, consulte [declaração CmdletAttribute](cmdlet-attribute-declaration.md).

2. Especifique o nome da classe.

3. Especifique que o cmdlet deriva de qualquer uma das seguintes classes:

   * [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)
   * [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

4. Para definir os parâmetros para o cmdlet, use o **parâmetro** atributo. Nesse caso, apenas um necessário o parâmetro é especificado.

   Para obter mais informações sobre o **parâmetro** atributo, consulte [ParameterAttribute declaração](parameter-attribute-declaration.md).

5. Substitua a método que processa a entrada de processamento de entrada. Nesse caso, o [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método é substituído.

6. Para gravar a saudação, use o método [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).
   A saudação será exibida no seguinte formato:

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a>Exemplo

```csharp
using System.Management.Automation;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify the
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory=true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a>Consulte também

[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)

[System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[Declaração CmdletAttribute](cmdlet-attribute-declaration.md)

[Declaração de ParameterAttribute](parameter-attribute-declaration.md)

[Writing a Windows PowerShell Cmdlet](writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)