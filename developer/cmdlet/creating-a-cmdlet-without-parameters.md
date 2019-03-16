---
title: Criação de um Cmdlet sem parâmetros | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmers Guide], creating
- cmdlets [PowerShell Programmers Guide], basic cmdlet
ms.assetid: 54236ef3-82db-45f8-9114-1ecb7ff65d3e
caps.latest.revision: 8
ms.openlocfilehash: c380b28570c955de6f41152fd617f5c1b0f9e4bd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054689"
---
# <a name="creating-a-cmdlet-without-parameters"></a>Criar um cmdlet sem parâmetros

Esta seção descreve como criar um cmdlet que recupera informações do computador local sem o uso de parâmetros e, em seguida, grava as informações para o pipeline. O cmdlet descrito aqui é um cmdlet Get-Proc que recupera informações sobre os processos do computador local e, em seguida, exibe essas informações na linha de comando.

Os tópicos nesta seção incluem o seguinte:

- [O Cmdlet de nomenclatura](#Naming-the-Cmdlet)

- [Definição da classe do Cmdlet](#Defining-the-Cmdlet-Class)

- [Substituindo uma método de processamento de entrada](#Overriding-an-Input-Processing-Method)

- [Exemplo de código](#Code-Sample)

- [Definindo tipos de objeto e formatação](#Defining-Object-Types-and-Formatting)

- [Criando o Cmdlet](#Building-the-Cmdlet)

- [Testando o Cmdlet](#Testing-the-Cmdlet)

> [!NOTE]
> Lembre-se de que ao gravar cmdlets, os assemblies de referência Windows PowerShell® são baixados para o disco (por padrão em C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0). Eles não estão instalados no Cache de Assembly Global (GAC).

## <a name="naming-the-cmdlet"></a>O Cmdlet de nomenclatura

Um nome de cmdlet consiste em um verbo que indica que a ação que o cmdlet usa e um substantivo que indica os itens que o cmdlet atua. Como esse exemplo de cmdlet Get-Proc recupera objetos de processo, ele usa o verbo "Get", definido pela [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeração e o substantivo "Processo" para indicar que o cmdlet funciona em itens de processo.

Ao nomear os cmdlets, não use nenhum dos seguintes caracteres: #, () {} [] & - / \ $;: "' <> &#124; ? @ ` .

### <a name="choosing-a-noun"></a>Escolhendo um substantivo

Você deve escolher um substantivo específico. É melhor usar um substantivo no singular prefixado com uma versão abreviada do nome do produto. Um nome de cmdlet de exemplo desse tipo é "`Get-SQLServer`".

### <a name="choosing-a-verb"></a>Escolhendo um verbo

Você deve usar um verbo do conjunto de nomes de verbos aprovados do cmdlet. Para obter mais informações sobre os verbos aprovados do cmdlet, consulte [nomes de verbos de Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

## <a name="defining-the-cmdlet-class"></a>Definição da classe do Cmdlet

Depois de escolher um nome de cmdlet, defina uma classe do .NET para implementar o cmdlet. Aqui está a definição de classe para esse cmdlet Get-Proc de exemplo:

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

Observe que o anterior para a definição de classe, o [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) atributo, com a sintaxe `[Cmdlet(verb, noun, ...)]`, é usado para identificar essa classe como um cmdlet. Isso é o único atributo obrigatório para todos os cmdlets e permite que o tempo de execução do Windows PowerShell chamá-los corretamente. Você pode definir palavras-chave de atributo adicional declarar a classe, se necessário. Lembre-se de que a declaração de atributo para nosso exemplo de classe GetProcCommand declara apenas os nomes de verbo e um substantivo para o cmdlet Get-Proc.

> [!NOTE]
> Para todas as classes de atributo do Windows PowerShell, as palavras-chave que você pode definir correspondem às propriedades da classe de atributo.

Ao nomear a classe do cmdlet, é uma boa prática para refletir o nome do cmdlet no nome da classe. Para fazer isso, use o formulário "VerbNounCommand" e substitua "Verbo" e "Substantivo" com o verbo e substantivo usado no nome do cmdlet. Conforme é mostrado na definição de classe anteriores, o cmdlet Get-Proc de exemplo define uma classe chamada GetProcCommand, que deriva de [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe base.

> [!IMPORTANT]
> Se você quiser definir um cmdlet que acessa o tempo de execução do Windows PowerShell diretamente, sua classe do .NET deve derivar de [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe base. Para obter mais informações sobre essa classe, consulte [criando um Cmdlet que conjuntos de parâmetros define](./adding-parameter-sets-to-a-cmdlet.md).

> [!NOTE]
> A classe para um cmdlet deve ser explicitamente marcada como pública. Classes que não são marcadas como públicos padrão serão interno e não serão encontradas pelo tempo de execução do Windows PowerShell.

O Windows PowerShell usa o [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace para suas classes de cmdlet. É recomendável colocar suas classes de cmdlet em um namespace de comandos do seu namespace de API, por exemplo, xxx.PS.Commands.

## <a name="overriding-an-input-processing-method"></a>Substituindo uma método de processamento de entrada

O [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe fornece três métodos de processamento de entrada principal, pelo menos um dos quais deve substituir seu cmdlet. Para obter mais informações sobre como o Windows PowerShell processa registros, consulte [como o Windows PowerShell funciona](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

Para todos os tipos de entrada, o tempo de execução do Windows PowerShell chama [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) para habilitar o processamento. Se seu cmdlet deve executar algum pré-processamento ou a instalação, ele pode fazer isso substituindo esse método.

> [!NOTE]
> Windows PowerShell usa o termo "Registro" para descrever o conjunto de valores de parâmetro fornecido quando um cmdlet é chamado.

Se seu cmdlet aceita entrada do pipeline, ele deve substituir a [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método e, opcionalmente, o [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)método. Por exemplo, um cmdlet pode substituir os dois métodos se ele reúne todas as entrada usando [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) e, em seguida, opera na entrada como um todo, em vez de um elemento por vez, como o `Sort-Object` cmdlet faz.

Se seu cmdlet não aceita entrada do pipeline, ele deve substituir a [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método. Lembre-se de que esse método é frequentemente usado no lugar de [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) quando o cmdlet não pode operar em um elemento por vez, como no caso de um cmdlet de classificação.

Como esse exemplo de cmdlet Get-Proc deve receber entrada do pipeline, ele substitui o [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método e usa as implementações padrão para [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) e [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing). O [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) substituição recupera processos e os grava em linha de comando usando o [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método.

```csharp
protected override void ProcessRecord()
{
  // Get the current processes
  Process[] processes = Process.GetProcesses();

  // Write the processes to the pipeline making them available
  // to the next cmdlet. The second parameter of this call tells
  // PowerShell to enumerate the array, and send one process at a
  // time to the pipeline.
  WriteObject(processes, true);
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ Get the current processes.
    Dim processes As Process()
    processes = Process.GetProcesses()

    '/ Write the processes to the pipeline making them available
    '/ to the next cmdlet. The second parameter of this call tells
    '/ PowerShell to enumerate the array, and send one process at a
    '/ time to the pipeline.
    WriteObject(processes, True)

End Sub 'ProcessRecord
```

#### <a name="things-to-remember-about-input-processing"></a>Coisas a serem lembrados sobre o processamento de entrada

- A fonte padrão para a entrada é um objeto explícito (por exemplo, uma cadeia de caracteres) fornecido pelo usuário na linha de comando. Para obter mais informações, consulte [criação de um Cmdlet para entrada de linha de comando de processo](./adding-parameters-that-process-command-line-input.md).

- Uma método de processamento de entrada também pode receber entrada de objeto de saída de um cmdlet upstream no pipeline. Para obter mais informações, consulte [criação de um Cmdlet para entrada de Pipeline de processo](./adding-parameters-that-process-pipeline-input.md). Lembre-se que seu cmdlet pode receber entrada de uma combinação de linha de comando e um pipeline de códigos-fonte.

- O cmdlet downstream pode não retornar por um longo tempo ou não. Por esse motivo, a método no seu cmdlet de processamento de entrada deve não mantenha bloqueios durante as chamadas para [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especialmente os bloqueios para a qual o escopo ultrapasse a instância do cmdlet.

> [!IMPORTANT]
> Cmdlets nunca deve chamar [System.Console.Writeline*](/dotnet/api/System.Console.WriteLine) ou seu equivalente.

- Seu cmdlet pode ter variáveis de objeto a ser limpo quando ele for concluído processamento (por exemplo, se ele é aberto em um identificador de arquivo a [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método e mantém o identificador aberto para uso pelo [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)). É importante lembrar-se de que o tempo de execução do Windows PowerShell não sempre chamar o [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método, que deve executar a limpeza do objeto.

Por exemplo, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) não poderá ser chamado se o cmdlet foi cancelado no centro ou se um encerramento ocorrerá erro em qualquer parte do cmdlet. Portanto, um cmdlet que requer a limpeza do objeto deve implementar completo [System. IDisposable](/dotnet/api/System.IDisposable) padrão, incluindo o finalizador, para que o tempo de execução possa chamar ambos [ System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) e [System.IDisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) no final do processamento.

## <a name="code-sample"></a>Exemplo de código

Para o completo C# exemplos de código, consulte [exemplo GetProcessSample01](./getprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definindo tipos de objeto e formatação

Windows PowerShell passa informações entre cmdlets usando objetos .NET. Consequentemente, talvez seja necessário definir seu próprio tipo de um cmdlet, ou o cmdlet talvez precise estender um tipo existente fornecido pelo outro cmdlet. Para obter mais informações sobre como definir novos tipos ou estender os tipos existentes, consulte [estendendo tipos de objeto e formatação](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Criando o Cmdlet

Depois de implementar um cmdlet, você deve registrá-lo com o Windows PowerShell por meio de um snap-in do Windows PowerShell. Para obter mais informações sobre como registrar cmdlets, consulte [como registrar Cmdlets, provedores e aplicativos Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testando o Cmdlet

Quando seu cmdlet tiver sido registrado com o Windows PowerShell, você pode testá-lo executando-o na linha de comando. O código para nosso exemplo de cmdlet Get-Proc é pequeno, mas ainda usa o tempo de execução do Windows PowerShell e um objeto existente do .NET, que é suficiente para torná-lo útil. Vamos testá-lo para entender melhor o que Get-Proc pode fazer e como sua saída pode ser usada. Para obter mais informações sobre como usar os cmdlets da linha de comando, consulte o [Introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

1. Inicie o Windows PowerShell e obter os processos atuais em execução no computador.

    ```powershell
    get-proc
    ```

    A seguinte saída é exibida.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. Atribua uma variável para os resultados do cmdlet para facilitar a manipulação.

    ```powershell
    $p=get-proc
    ```

3. Obtenha o número de processos.

    ```powershell
    $p.length
    ```

    A seguinte saída é exibida.

    ```output
    63
    ```

4. Recupere um processo específico.

    ```powershell
    $p[6]
    ```

    A seguinte saída é exibida.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. Obter a hora de início desse processo.

    ```powershell
    $p[6].starttime
    ```

    A seguinte saída é exibida.

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. Obter os processos para o qual a contagem de identificadores é maior que 500 e classificar o resultado.

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    A seguinte saída é exibida.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. Use o `Get-Member` cmdlet para listar as propriedades disponíveis para cada processo.

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    A seguinte saída é exibida.

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a>Consulte Também

[Criação de um Cmdlet para processar a entrada de linha de comando](./adding-parameters-that-process-command-line-input.md)

[Criação de um Cmdlet para processar a entrada de Pipeline](./adding-parameters-that-process-pipeline-input.md)

[Como criar um Cmdlet do Windows PowerShell](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Estendendo tipos de objeto e formatação](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Como funciona o Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Como registrar Cmdlets, provedores e aplicativos de Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Referência do Windows PowerShell](../windows-powershell-reference.md)

[Exemplos de cmdlet](./cmdlet-samples.md)