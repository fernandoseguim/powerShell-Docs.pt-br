---
title: Métodos de processamento de entrada do cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- virtual methods (PowerShell SDK]
ms.assetid: b0bb8172-c9fa-454b-9f1b-57c3fe60671b
caps.latest.revision: 12
ms.openlocfilehash: 7f8d25e03707052b1d5b62e245caae360da11d0b
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794936"
---
# <a name="cmdlet-input-processing-methods"></a>Métodos de processamento de entrada de cmdlet

Cmdlets deve substituir um ou mais dos métodos descritos neste tópico para realizar seu trabalho de processamento de entrada. Esses métodos permitem que o cmdlet executar pré-processando operações de entrada operações de processamento e pós-processamento de operações. Esses métodos também permitem que você parar o processamento de cmdlet.

## <a name="pre-processing-tasks"></a>Tarefas de pré-processamento

Cmdlets deve substituir o [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) método para adicionar quaisquer operações de pré-processamento são válidas para todos os registros que serão processados posteriormente pelo cmdlet. Quando o Windows PowerShell processa um pipeline de comando, o Windows PowerShell chama esse método uma vez para cada instância do cmdlet no pipeline. Para obter mais informações sobre como o Windows PowerShell invoca o pipeline de comando, consulte [ciclo de vida de processamento do Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

O código a seguir mostra uma implementação do [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) método.

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the BeginProcessing template."
  WriteObject("This is a test of the BeginProcessing template.");
}
```

Para obter um exemplo mais detalhado de como usar o [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) método, consulte [SelectStr Tutorial](./selectstr-tutorial.md). Neste tutorial, o **Str Select** cmdlet usa o [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) método para gerar a expressão regular que é usada para pesquisar os registros de processamento de entrada.

## <a name="input-processing-tasks"></a>Tarefas de processamento de entrada

Cmdlets pode substituir o [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método para processar a entrada que é enviada para o cmdlet. Quando o Windows PowerShell processa um pipeline de comando, o Windows PowerShell chama esse método para cada registro de entrada é processado pelo cmdlet. Para obter mais informações sobre como o Windows PowerShell invoca o pipeline de comando, consulte [ciclo de vida de processamento do Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

O código a seguir mostra uma implementação do [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método.

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the ProcessRecord template."
  WriteObject("This is a test of the ProcessRecord template.");
}
```

Para obter um exemplo mais detalhado de como usar o [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método, consulte [SelectStr Tutorial](./selectstr-tutorial.md).

## <a name="post-processing-tasks"></a>Tarefas de pós-processamento

Cmdlets deve substituir o [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) método para adicionar qualquer pós-processamento operações que são válidas para todos os registros que foram processados pelo cmdlet. Por exemplo, o cmdlet pode ter que limpar as variáveis de objeto depois que ele é concluído de processamento.

Quando o Windows PowerShell processa um pipeline de comando, o Windows PowerShell chama esse método uma vez para cada instância do cmdlet no pipeline. No entanto, é importante lembrar-se de que o tempo de execução do Windows PowerShell não chamará o [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) método se o cmdlet foi cancelado no Centro por meio de seu processamento de entrada ou se um encerramento ocorrerá erro em qualquer parte do cmdlet. Por esse motivo, um cmdlet que requer a limpeza do objeto deve implementar completo [System. IDisposable](/dotnet/api/System.IDisposable) padrão, incluindo um finalizador, para que o tempo de execução possa chamar ambos o [ System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) e [System.Idisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) métodos no final do processamento. Para obter mais informações sobre como o Windows PowerShell invoca o pipeline de comando, consulte [ciclo de vida de processamento do Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

O código a seguir mostra uma implementação do [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método.

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the EndProcessing template."
  WriteObject("This is a test of the EndProcessing template.");
}
```

Para obter um exemplo mais detalhado de como usar o [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método, consulte [SelectStr Tutorial](./selectstr-tutorial.md).

## <a name="see-also"></a>Consulte Também

[System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)

[System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)

[System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)

[System.Idisposable](/dotnet/api/System.IDisposable)

[Shell do Windows PowerShell do SDK](../windows-powershell-reference.md)
