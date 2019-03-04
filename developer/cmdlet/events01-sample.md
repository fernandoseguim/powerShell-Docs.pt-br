---
title: Exemplo de Events01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27d0ee5e-2589-4530-92ef-c09996b80994
caps.latest.revision: 10
ms.openlocfilehash: 3edbcabeff0c8d84831823df11749d152b347566
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863332"
---
# <a name="events01-sample"></a>Amostra Events01

Este exemplo mostra como criar um cmdlet que permite ao usuário para se registrar para eventos que são gerados por [FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher). Com esse cmdlet, os usuários podem registrar uma ação a ser executada quando um arquivo é criado em um diretório específico. Neste exemplo deriva de [Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) classe base.

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>Como criar o exemplo usando o Visual Studio.

1. Com o Windows PowerShell 2.0 do SDK instalado, navegue até a pasta Events01. O local padrão é C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01.

2. Clique duas vezes no ícone para o arquivo de solução (. sln). Isso abre o projeto de exemplo no Microsoft Visual Studio.

3. No **construir** menu, selecione **compilar solução**.

    A biblioteca para o exemplo será compilada nas pastas padrão \bin ou \bin\debug.

### <a name="how-to-run-the-sample"></a>Como executar o exemplo

1. Crie a seguinte pasta de módulo:

    `[user]/documents/windowspowershell/modules/events01`

2. Copie o arquivo de biblioteca para o exemplo para a pasta de módulo.

3. Inicie o Windows PowerShell.

4. Execute o seguinte comando para carregar o cmdlet no Windows PowerShell:

    ```powershell
    import-module events01
    ```

5. Use o cmdlet Register-FileSystemEvent para registrar uma ação que gravará uma mensagem quando um arquivo é criado sob o diretório TEMP.

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. Crie um arquivo no diretório TEMP e observe que a ação é executada (a mensagem é exibida).

Isso é um exemplo de saída que resulta seguindo estas etapas.

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

Este exemplo requer o Windows PowerShell 2.0.

## <a name="demonstrates"></a>Demonstra

Este exemplo demonstra o seguinte.

- Como gravar um cmdlet de registro de eventos. O cmdlet deriva de [Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) classe, que fornece suporte para os parâmetros comuns para registrar-* cmdlets do evento. Os cmdlets que são derivados de [Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) só precisa definir seus parâmetros específicos e substituir o `GetSourceObject` e `GetSourceObjectEventName` métodos abstratos.

## <a name="example"></a>Exemplo

Este exemplo mostra como se registrar para eventos gerados pelo [FileSystemWatcher](https://msdn.microsoft.com/en-us/library/system.io.filesystemwatcher\(v=vs.110\).aspx).

```csharp
namespace Sample
{
    using System;
    using System.IO;
    using System.Management.Automation;
    using System.Management.Automation.Runspaces;
    using Microsoft.PowerShell.Commands;

    [Cmdlet(VerbsLifecycle.Register, "FileSystemEvent")]
    public class RegisterObjectEventCommand : ObjectEventRegistrationBase
    {
        /// <summary>The FileSystemWatcher that exposes the events.</summary>
        private FileSystemWatcher fileSystemWatcher = new FileSystemWatcher();

        /// <summary>Name of the event to which the cmdlet registers.</summary>
        private string eventName = null;

        /// <summary>
        /// Gets or sets the path that will be monitored by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = true, Position = 0)]
        public string Path
        {
            get
            {
                return this.fileSystemWatcher.Path;
            }

            set
            {
                this.fileSystemWatcher.Path = value;
            }
        }

        /// <summary>
        /// Gets or sets the name of the event to which the cmdlet registers.
        /// <para>
        /// Currently System.IO.FileSystemWatcher exposes 6 events: Changed, Created,
        /// Deleted, Disposed, Error, and Renamed. Check the MSDN documentation of
        /// FileSystemWatcher for details on each event.
        /// </para>
        /// </summary>
        [Parameter(Mandatory = true, Position = 1)]
        public string EventName
        {
            get
            {
                return this.eventName;
            }

            set
            {
                this.eventName = value;
            }
        }

        /// <summary>
        /// Gets or sets the filter that will be user by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = false)]
        public string Filter
        {
            get
            {
                return this.fileSystemWatcher.Filter;
            }

            set
            {
                this.fileSystemWatcher.Filter = value;
            }
        }

        /// <summary>
        /// Derived classes must implement this method to return the object that generates
        /// the events to be monitored.
        /// </summary>
        /// <returns> This sample returns an instance of System.IO.FileSystemWatcher</returns>
        protected override object GetSourceObject()
        {
            return this.fileSystemWatcher;
        }

        /// <summary>
        /// Derived classes must implement this method to return the name of the event to
        /// be monitored. This event must be exposed by the input object.
        /// </summary>
        /// <returns> This sample returns the event specified by the user with the -EventName parameter.</returns>
        protected override string GetSourceObjectEventName()
        {
            return this.eventName;
        }
    }
}
```

## <a name="see-also"></a>Consulte Também

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)