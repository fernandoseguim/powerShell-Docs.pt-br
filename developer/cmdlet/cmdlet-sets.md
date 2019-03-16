---
title: Conjuntos de cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bcf0739e-920e-4dd8-afca-2c6d6927bc2a
caps.latest.revision: 10
ms.openlocfilehash: ef3b5bab5dcafc578397bcb4f071776bbdeaced1
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058259"
---
# <a name="cmdlet-sets"></a>Conjuntos de cmdlets

Quando você projeta seus cmdlets, você poderá encontrar casos em que você precisa executar várias ações nessa mesma parte dos dados. Por exemplo, talvez você precise obter e definir os dados ou iniciar e interromper um processo. Embora você precisará criar cmdlets separados para executar cada ação, o design do cmdlet deve incluir uma classe base da qual são derivadas as classes para os cmdlets individuais.

Mantenha o seguinte em mente ao implementar uma classe base.

- Declare nenhum parâmetro comum usado por todos os cmdlets derivados da classe base.

- Adicione parâmetros específicos do cmdlet à classe cmdlet apropriado.

- Substitua a método na classe base de processamento de entrada apropriada.

- Declare a [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) de atributo em todas as classes de cmdlet, mas não o declare na classe base.

- Implementar uma [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) ou [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) cujo nome de classe e a descrição reflita o conjunto de cmdlets.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra a implementação de uma classe base que é usado pelo Get-Proc e o cmdlet Stop-Proc que derivam da mesma classe base.

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace.

namespace Microsoft.Samples.PowerShell.Commands
{

  #region ProcessCommands

  /// <summary>
  /// This class implements a Stop-Proc cmdlet. The parameters
  /// for this cmdlet are defined by the BaseProcCommand class.
  /// </summary>
  [Cmdlet(VerbsLifecycle.Stop, "Proc", SupportsShouldProcess = true)]
  public class StopProcCommand : BaseProcCommand
  {
    public override void ProcessObject(Process process)
    {
      if (ShouldProcess(process.ProcessName, "Stop-Proc"))
      {
        process.Kill();
      }
    }
  }

  /// <summary>
  /// This class implements a Get-Proc cmdlet. The parameters
  /// for this cmdlet are defined by the BaseProcCommand class.
  /// </summary>

  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : BaseProcCommand
  {
    public override void ProcessObject(Process process)
    {
      WriteObject(process);
    }
  }

  /// <summary>
  /// This class is the base class that defines the common
  /// functionality used by the Get-Proc and Stop-Proc
  /// cmdlets.
  /// </summary>
  public class BaseProcCommand : Cmdlet
  {
    #region Parameters

    // Defines the Name parameter that is used to
    // specify a process by its name.
    [Parameter(
               Position = 0,
               Mandatory = true,
               ValueFromPipeline = true,
               ValueFromPipelineByPropertyName = true
    )]
    public string[] Name
    {
      get { return processNames; }
      set { processNames = value; }
    }
    private string[] processNames;

    // Defines the Exclude parameter that is used to
    // specify which processes should be excluded when
    // the cmdlet performs its action.
    [Parameter()]
    public string[] Exclude
    {
      get { return excludeNames; }
      set { excludeNames = value; }
    }
    private string[] excludeNames = new string[0];
    #endregion Parameters

    public virtual void ProcessObject(Process process)
    {
      throw new NotImplementedException("This method should be overridden.");
    }

    #region Cmdlet Overrides
    // <summary>
    // For each of the requested process names, retrieve and write
    // the associated processes.
    // </summary>
    protected override void ProcessRecord()
    {
      // Set up the wildcard characters used in resolving
      // the process names.
      WildcardOptions options = WildcardOptions.IgnoreCase |
                                WildcardOptions.Compiled;

      WildcardPattern[] include = new WildcardPattern[Name.Length];
      for (int i = 0; i < Name.Length; i++)
      {
        include[i] = new WildcardPattern(Name[i], options);
      }

      WildcardPattern[] exclude = new WildcardPattern[Exclude.Length];
      for (int i = 0; i < Exclude.Length; i++)
      {
        exclude[i] = new WildcardPattern(Exclude[i], options);
      }

      foreach (Process p in Process.GetProcesses())
      {
        foreach (WildcardPattern wIn in include)
        {
          if (wIn.IsMatch(p.ProcessName))
          {
            bool processThisOne = true;
            foreach (WildcardPattern wOut in exclude)
            {
              if (wOut.IsMatch(p.ProcessName))
              {
                processThisOne = false;
                break;
              }
            }
            if (processThisOne)
            {
              ProcessObject(p);
            }
            break;
          }
        }
      }
    }
    #endregion Cmdlet Overrides
  }
    #endregion ProcessCommands
}
```

## <a name="see-also"></a>Consulte Também

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
