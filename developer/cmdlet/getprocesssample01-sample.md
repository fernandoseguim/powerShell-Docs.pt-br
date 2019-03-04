---
title: Exemplo GetProcessSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b48bf80-cbf0-4cb1-8d5b-3b8d06196598
caps.latest.revision: 10
ms.openlocfilehash: 00190c7350cb0f1cfc5c389b56e48e9397480446
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859832"
---
# <a name="getprocesssample01-sample"></a>Amostra GetProcessSample01

Este exemplo mostra como implementar um cmdlet que recupera os processos no computador local. Esse cmdlet é uma versão simplificada do `Get-Process` cmdlet que é fornecida pelo Windows PowerShell 2.0.

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>Como criar o exemplo usando o Visual Studio.

1. Com o Windows PowerShell 2.0 do SDK instalado, navegue até a pasta GetProcessSample01. O local padrão é C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.

2. Clique duas vezes no ícone para o arquivo de solução (. sln). Isso abre o projeto de exemplo no Microsoft Visual Studio.

3. No **construir** menu, selecione **compilar solução**.

  A biblioteca para o exemplo será compilada nas pastas padrão \bin ou \bin\debug.

### <a name="how-to-run-the-sample"></a>Como executar o exemplo

1. Abra uma janela de Prompt de Comando.

2. Navegue até o diretório que contém o arquivo. dll de exemplo.

3. Execute o installutil "GetProcessSample01.dll".

4. Inicie o Windows PowerShell.

5. Execute o seguinte comando para adicionar o snap-in para o shell.

   `Add-PSSnapin GetProcPSSnapIn01`

6. Digite o seguinte comando para executar o cmdlet. `get-proc`

   `get-proc`

   Isso é um exemplo de saída que resulta da seguindo estas etapas.

   ```output
   Id              Name            State      HasMoreData     Location             Command
   --              ----            -----      -----------     --------             -------
   1               26932870-d3b... NotStarted False                                 Write-Host "A f...

   ```

   ```powershell
   Set-Content $env:temp\test.txt "This is a test file"
   ```

   ```output
   A file was created in the TEMP directory
   ```

## <a name="requirements"></a>Requisitos

Este exemplo requer o Windows PowerShell 1.0 ou posterior.

## <a name="demonstrates"></a>Demonstra

Este exemplo demonstra o seguinte.

- Criando um exemplo básico de cmdlet.

- Definindo uma classe cmdlet usando o atributo de Cmdlet.

- Criando um snap-in que funciona com o Windows PowerShell 1.0 e o Windows PowerShell 2.0. Exemplos subsequentes usam módulos em vez de snap-ins para que eles exigem o Windows PowerShell 2.0.

## <a name="example"></a>Exemplo

Este exemplo mostra como criar um cmdlet simples e seu snap-in.

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{

   #region GetProcCommand

   /// <summary>
   /// This class implements the Get-Proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes of the local computer.
      /// Then, the WriteObject method writes the associated processes
      /// to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
         // Retrieve the current processes.
         Process[] processes = Process.GetProcesses();

         // Write the processes to the pipeline to make them available
         // to the next cmdlet. The second argument (true) tells Windows
         // PowerShell to enumerate the array and to send one process
         // object at a time to the pipeline.
         WriteObject(processes, true);
      }

      #endregion Overrides

   } //GetProcCommand

   #endregion GetProcCommand

   #region PowerShell snap-in

   /// <summary>
   /// Create this sample as an PowerShell snap-in
   /// </summary>
   [RunInstaller(true)]
   public class GetProcPSSnapIn01 : PSSnapIn
   {
       /// <summary>
       /// Create an instance of the GetProcPSSnapIn01
       /// </summary>
       public GetProcPSSnapIn01()
           : base()
       {
       }

       /// <summary>
       /// Get a name for this PowerShell snap-in. This name will be used in registering
       /// this PowerShell snap-in.
       /// </summary>
       public override string Name
       {
           get
           {
               return "GetProcPSSnapIn01";
           }
       }

       /// <summary>
       /// Vendor information for this PowerShell snap-in.
       /// </summary>
       public override string Vendor
       {
           get
           {
               return "Microsoft";
           }
       }

       /// <summary>
       /// Gets resource information for vendor. This is a string of format:
       /// resourceBaseName,resourceName.
       /// </summary>
       public override string VendorResource
       {
           get
           {
               return "GetProcPSSnapIn01,Microsoft";
           }
       }

       /// <summary>
       /// Description of this PowerShell snap-in.
       /// </summary>
       public override string Description
       {
           get
           {
               return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
           }
       }
   }

   #endregion PowerShell snap-in
}
```

## <a name="see-also"></a>Consulte Também

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)