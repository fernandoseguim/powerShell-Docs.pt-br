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
# <a name="getprocesssample02-sample"></a><span data-ttu-id="eeae6-102">Amostra GetProcessSample02</span><span class="sxs-lookup"><span data-stu-id="eeae6-102">GetProcessSample02 Sample</span></span>

<span data-ttu-id="eeae6-103">Este exemplo mostra como gravar um cmdlet que recupere os processos no computador local.</span><span class="sxs-lookup"><span data-stu-id="eeae6-103">This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="eeae6-104">Ele fornece um `Name` parâmetro que pode ser usado para especificar os processos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="eeae6-104">It provides a `Name` parameter that can be used to specify the processes to be retrieved.</span></span> <span data-ttu-id="eeae6-105">Esse cmdlet é uma versão simplificada do `Get-Process` cmdlet fornecido pelo Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="eeae6-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="eeae6-106">Como criar o exemplo usando o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="eeae6-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="eeae6-107">Com o Windows PowerShell 2.0 do SDK instalado, navegue até a pasta GetProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="eeae6-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample02 folder.</span></span> <span data-ttu-id="eeae6-108">O local padrão é C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="eeae6-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span></span>

2. <span data-ttu-id="eeae6-109">Clique duas vezes no ícone para o arquivo de solução (. sln).</span><span class="sxs-lookup"><span data-stu-id="eeae6-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="eeae6-110">Isso abre o projeto de exemplo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="eeae6-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="eeae6-111">No **construir** menu, selecione **compilar solução**.</span><span class="sxs-lookup"><span data-stu-id="eeae6-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="eeae6-112">A biblioteca para o exemplo será compilada nas pastas padrão \bin ou \bin\debug.</span><span class="sxs-lookup"><span data-stu-id="eeae6-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="eeae6-113">Como executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="eeae6-113">How to run the sample</span></span>

1. <span data-ttu-id="eeae6-114">Crie a seguinte pasta de módulo:</span><span class="sxs-lookup"><span data-stu-id="eeae6-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. <span data-ttu-id="eeae6-115">Copie o assembly de exemplo para a pasta de módulo.</span><span class="sxs-lookup"><span data-stu-id="eeae6-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="eeae6-116">Inicie o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eeae6-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="eeae6-117">Execute o seguinte comando para carregar o assembly no Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="eeae6-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module getprossessample02`

5. <span data-ttu-id="eeae6-118">Execute o seguinte comando para executar o cmdlet:</span><span class="sxs-lookup"><span data-stu-id="eeae6-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="eeae6-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eeae6-119">Requirements</span></span>

<span data-ttu-id="eeae6-120">Este exemplo requer o Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="eeae6-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="eeae6-121">Demonstra</span><span class="sxs-lookup"><span data-stu-id="eeae6-121">Demonstrates</span></span>

<span data-ttu-id="eeae6-122">Este exemplo demonstra o seguinte.</span><span class="sxs-lookup"><span data-stu-id="eeae6-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="eeae6-123">Declarando uma classe cmdlet usando o atributo de Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eeae6-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="eeae6-124">Declarar um parâmetro de cmdlet usando o atributo de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="eeae6-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="eeae6-125">Especifica a posição do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="eeae6-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="eeae6-126">Declarando um atributo de validação para o parâmetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="eeae6-126">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="eeae6-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eeae6-127">Example</span></span>

<span data-ttu-id="eeae6-128">Este exemplo mostra uma implementação do cmdlet Get-Proc que inclui um `Name` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="eeae6-128">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="eeae6-129">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="eeae6-129">See Also</span></span>

<span data-ttu-id="eeae6-130">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="eeae6-130">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
