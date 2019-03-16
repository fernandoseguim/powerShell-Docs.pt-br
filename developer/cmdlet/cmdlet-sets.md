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
# <a name="cmdlet-sets"></a><span data-ttu-id="bc469-102">Conjuntos de cmdlets</span><span class="sxs-lookup"><span data-stu-id="bc469-102">Cmdlet Sets</span></span>

<span data-ttu-id="bc469-103">Quando você projeta seus cmdlets, você poderá encontrar casos em que você precisa executar várias ações nessa mesma parte dos dados.</span><span class="sxs-lookup"><span data-stu-id="bc469-103">When you design your cmdlets, you might encounter cases in which you need to perform several actions on the same piece of data.</span></span> <span data-ttu-id="bc469-104">Por exemplo, talvez você precise obter e definir os dados ou iniciar e interromper um processo.</span><span class="sxs-lookup"><span data-stu-id="bc469-104">For example, you might need to get and set data or start and stop a process.</span></span> <span data-ttu-id="bc469-105">Embora você precisará criar cmdlets separados para executar cada ação, o design do cmdlet deve incluir uma classe base da qual são derivadas as classes para os cmdlets individuais.</span><span class="sxs-lookup"><span data-stu-id="bc469-105">Although you will need to create separate cmdlets to perform each action, your cmdlet design should include a base class from which the classes for the individual cmdlets are derived.</span></span>

<span data-ttu-id="bc469-106">Mantenha o seguinte em mente ao implementar uma classe base.</span><span class="sxs-lookup"><span data-stu-id="bc469-106">Keep the following things in mind when implementing a base class.</span></span>

- <span data-ttu-id="bc469-107">Declare nenhum parâmetro comum usado por todos os cmdlets derivados da classe base.</span><span class="sxs-lookup"><span data-stu-id="bc469-107">Declare any common parameters used by all the derived cmdlets in the base class.</span></span>

- <span data-ttu-id="bc469-108">Adicione parâmetros específicos do cmdlet à classe cmdlet apropriado.</span><span class="sxs-lookup"><span data-stu-id="bc469-108">Add cmdlet-specific parameters to the appropriate cmdlet class.</span></span>

- <span data-ttu-id="bc469-109">Substitua a método na classe base de processamento de entrada apropriada.</span><span class="sxs-lookup"><span data-stu-id="bc469-109">Override the appropriate input processing method in the base class.</span></span>

- <span data-ttu-id="bc469-110">Declare a [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) de atributo em todas as classes de cmdlet, mas não o declare na classe base.</span><span class="sxs-lookup"><span data-stu-id="bc469-110">Declare the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute on all cmdlet classes, but do not declare it on the base class.</span></span>

- <span data-ttu-id="bc469-111">Implementar uma [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) ou [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) cujo nome de classe e a descrição reflita o conjunto de cmdlets.</span><span class="sxs-lookup"><span data-stu-id="bc469-111">Implement a [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class whose name and description reflects the set of cmdlets.</span></span>

## <a name="example"></a><span data-ttu-id="bc469-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bc469-112">Example</span></span>

<span data-ttu-id="bc469-113">O exemplo a seguir mostra a implementação de uma classe base que é usado pelo Get-Proc e o cmdlet Stop-Proc que derivam da mesma classe base.</span><span class="sxs-lookup"><span data-stu-id="bc469-113">The following example shows the implementation of a base class that is used by Get-Proc and Stop-Proc cmdlet that derive from the same base class.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="bc469-114">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="bc469-114">See Also</span></span>

<span data-ttu-id="bc469-115">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="bc469-115">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
