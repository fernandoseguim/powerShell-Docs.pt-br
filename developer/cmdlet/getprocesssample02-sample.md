---
title: GetProcessSample02 exemplo | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 481f557d-3344-4d33-b2da-4736a0165181
caps.latest.revision: 7
ms.openlocfilehash: fa4cd8a724793e71b615c84a5c5a833aa92c93fc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859852"
---
# <a name="getprocesssample02-sample"></a>Amostra GetProcessSample02

Este exemplo mostra como gravar um cmdlet que recupere os processos no computador local. Ele fornece um `Name` parâmetro que pode ser usado para especificar os processos a serem recuperados. Esse cmdlet é uma versão simplificada do `Get-Process` cmdlet fornecido pelo Windows PowerShell 2.0.

## <a name="how-to-build-the-sample-using-visual-studio"></a>Como criar o exemplo usando o Visual Studio.

1. Com o Windows PowerShell 2.0 do SDK instalado, navegue até a pasta GetProcessSample02. O local padrão é C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.

2. Clique duas vezes no ícone para o arquivo de solução (. sln). Isso abre o projeto de exemplo no Visual Studio.

3. No **construir** menu, selecione **compilar solução**.

    A biblioteca para o exemplo será compilada nas pastas padrão \bin ou \bin\debug.

### <a name="how-to-run-the-sample"></a>Como executar o exemplo

1. Crie a seguinte pasta de módulo:

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. Copie o assembly de exemplo para a pasta de módulo.

3. Inicie o Windows PowerShell.

4. Execute o seguinte comando para carregar o assembly no Windows PowerShell:

    `import-module getprossessample02`

5. Execute o seguinte comando para executar o cmdlet:

    `get-proc`

## <a name="requirements"></a>Requisitos

Este exemplo requer o Windows PowerShell 2.0.

## <a name="demonstrates"></a>Demonstra

Este exemplo demonstra o seguinte.

- Declarando uma classe cmdlet usando o atributo de Cmdlet.

- Declarar um parâmetro de cmdlet usando o atributo de parâmetro.

- Especifica a posição do parâmetro.

- Declarando um atributo de validação para o parâmetro de entrada.

## <a name="example"></a>Exemplo

Este exemplo mostra uma implementação do cmdlet Get-Proc que inclui um `Name` parâmetro.

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;     // Windows PowerShell namespace

  #region GetProcCommand

  /// <summary>
  /// This class implements the get-proc cmdlet.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Parameters

    /// <summary>
    /// The names of the processes retrieved by the cmdlet.
    /// </summary>
    private string[] processNames;

    /// <summary>
    /// Gets or sets the list of process names on which
    /// the Get-Proc cmdlet will work.
    /// </summary>
    [Parameter(Position = 0)]
    [ValidateNotNullOrEmpty]
    public string[] Name
    {
      get { return this.processNames; }
      set { this.processNames = value; }
    }

    #endregion Parameters

    #region Cmdlet Overrides

    /// <summary>
    /// The ProcessRecord method calls the Process.GetProcesses
    /// method to retrieve the processes specified by the Name
    /// parameter. Then, the WriteObject method writes the
    /// associated process objects to the pipeline.
    /// </summary>
    protected override void ProcessRecord()
    {
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames...).
    } // End ProcessRecord.
    #endregion Cmdlet Overrides
  } // End GetProcCommand class.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a>Consulte Também

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
