---
title: Adicionar Aliases, expansão de curinga e ajudar a parâmetros de Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: 0f025213087e6f308adf8e597fc01c1320251f76
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859322"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a>Adicionar aliases, expansão de curinga e ajuda a parâmetros de cmdlet

Esta seção descreve como adicionar aliases, expansão de curinga, e mensagens de ajuda para os parâmetros do cmdlet Stop-Proc (descrito na [criação de um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md)).

Esse cmdlet Stop-Proc tenta interromper os processos que são recuperados usando o cmdlet Get-Proc (descrito na [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md)).

Os tópicos nesta seção incluem o seguinte:

- [Definindo o Cmdlet](#Defining-the-Cmdlet)

- [Definir parâmetros para modificação do sistema](#Defining-Parameters-for-System-Modification)

- [Definir um Alias de parâmetro](#Defining-a-Parameter-Alias)

- [Ajuda para os parâmetros de criação](#Creating-Help-for-Parameters)

- [Substituindo uma método de processamento de entrada](#Overriding-an-Input-Processing-Method)

- [Suporte à expansão de curinga](#Supporting-Wildcard-Expansion)

- [Exemplo de código](#Defining-a-Parameter-Alias)

- [Definindo tipos de objeto e formatação](#Define-Object-Types-and-Formatting)

- [Criando o Cmdlet](#Building-the-Cmdlet)

- [Testando o Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Definindo o Cmdlet

A primeira etapa na criação de cmdlet sempre é o cmdlet de nomenclatura e declarar a classe .NET que implementa o cmdlet. Porque você está escrevendo um cmdlet para alterar o sistema, ele deve ser nomeado adequadamente. Como este cmdlet interrompe os processos do sistema, ele usa o verbo "Stop", definido pela [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) classe, com o substantivo "Processo" para indicar o processo. Para obter mais informações sobre os verbos aprovados do cmdlet, consulte [nomes de verbos de Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

O código a seguir é a definição de classe para esse cmdlet Stop-Proc.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Definir parâmetros para modificação do sistema

O cmdlet precisa definir os parâmetros que modificações no sistema de suporte e comentários do usuário. O cmdlet deve definir um `Name` parâmetro ou equivalente para que o cmdlet será capaz de modificar o sistema por algum tipo de identificador. Além disso, o cmdlet deve definir a `Force` e `PassThru` parâmetros. Para obter mais informações sobre esses parâmetros, consulte [criação de um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="defining-a-parameter-alias"></a>Definir um Alias de parâmetro

Um alias de parâmetro pode ser um nome alternativo ou bem-definidos 1 ou 2 letras nome curto para um parâmetro de cmdlet. Em ambos os casos, o objetivo de usar aliases é simplificar a entrada do usuário na linha de comando. Windows PowerShell dá suporte a aliases de parâmetro por meio de [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) atributo, que usa a sintaxe de declaração [Alias()].

O código a seguir mostra como um alias é adicionado para o `Name` parâmetro.

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
[Alias("ProcessName")]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

Além de usar o [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) atributo, o tempo de execução do Windows PowerShell executa a correspondência de nome parcial, mesmo se nenhum alias for especificadas. Por exemplo, se seu cmdlet possui um `FileName` parâmetro e que é o único parâmetro que começa com `F`, o usuário poderia digitar `Filename`, `Filenam`, `File`, `Fi`, ou `F` e ainda reconhecer a entrada, como o `FileName` parâmetro.

## <a name="creating-help-for-parameters"></a>Ajuda para os parâmetros de criação

Windows PowerShell permite que você crie a Ajuda para os parâmetros de cmdlet. Faça isso para qualquer parâmetro usado para comentários de usuário e a modificação do sistema. Para cada parâmetro dar suporte à Ajuda, você pode definir as `HelpMessage` palavra-chave de atributo o [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) declaração do atributo. Essa palavra-chave define o texto a ser exibido ao usuário para assistência usando o parâmetro. Você também pode definir o `HelpMessageBaseName` palavra-chave para identificar o nome de base de um recurso a ser usado para a mensagem. Se você definir essa palavra-chave, você também deve definir o `HelpMessageResourceId` palavra-chave para especificar o identificador de recurso.

O código a seguir desse cmdlet Stop-Proc define o `HelpMessage` atributo a palavra-chave para o `Name` parâmetro.

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
```

## <a name="overriding-an-input-processing-method"></a>Substituindo uma método de processamento de entrada

O cmdlet deve substituir uma método de processamento de entrada, mais frequentemente, isso será [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Ao modificar o sistema, o cmdlet deve chamar o [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos que permitem a usuário para fornecer comentários antes que uma alteração é feita. Para obter mais informações sobre esses métodos, consulte [criação de um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="supporting-wildcard-expansion"></a>Suporte à expansão de curinga

Para permitir que a seleção de vários objetos, o cmdlet pode usar o [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) e [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes para fornecer suporte de expansão de curinga para o parâmetro de entrada. São exemplos de padrões de curinga de lsa * \*. txt e [a-c]\*. Use o caractere de acento (') como um caractere de escape quando o padrão contém um caractere que deve ser usado literalmente.

Expansões de curinga de nomes de arquivo e caminho são exemplos de cenários comuns em que o cmdlet talvez queira permitir que o suporte para entradas de caminho quando a seleção de vários objetos é necessária. Um caso comum é no sistema de arquivos, em que um usuário quiser ver todos os arquivos que residem na pasta atual.

Você precisa apenas raramente uma implementação de correspondência de padrão de curinga personalizados. Nesse caso, seu cmdlet deve dar suporte a 1003.2 POSIX completa, especificação 3.13 para expansão de curinga ou o subconjunto simplificado a seguir:

- **Ponto de interrogação (?).** Corresponde a qualquer caractere no local especificado.

- **Asterisco (\*).** Corresponde a zero ou mais caracteres começando no local especificado.

- **Colchete de abertura ([]).** Apresenta uma expressão entre colchetes padrão que pode conter caracteres ou um intervalo de caracteres. Se um intervalo for necessário, um hífen (-) é usado para indicar o intervalo.

- **Colchete de fechamento (]).** Termina uma expressão entre colchetes de padrão.

- **Acento caractere de escape (').** Indica que o próximo caractere deve ser interpretado literalmente. Lembre-se de que ao especificar o caractere de acento da linha de comando (em vez de especificá-lo por meio de programação), o caractere de escape de acento deve ser especificado duas vezes.

> [!NOTE]
> Para obter mais informações sobre padrões de curinga, consulte [que dão suporte a curingas nos parâmetros de Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).

O código a seguir mostra como definir opções de curinga e definir o padrão de curinga usado para resolver o `Name` parâmetro desse cmdlet.

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

O código a seguir mostra como testar se o nome do processo corresponde ao padrão de curinga definido. Observe que, nesse caso, se o nome do processo não coincide com o padrão, o cmdlet continua em obter o próximo nome de processo.

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a>Exemplo de código

Para o completo C# exemplos de código, consulte [StopProcessSample03 amostra](./stopprocesssample03-sample.md).

## <a name="define-object-types-and-formatting"></a>Definir tipos de objeto e formatação

Windows PowerShell passa informações entre cmdlets usando objetos .net. Consequentemente, talvez seja necessário definir seu próprio tipo de um cmdlet ou o cmdlet talvez precise estender um tipo existente fornecido pelo outro cmdlet. Para obter mais informações sobre como definir novos tipos ou estender os tipos existentes, consulte [estendendo tipos de objeto e formatação](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Criando o Cmdlet

Depois de implementar um cmdlet, ele deve ser registrado com o Windows PowerShell por meio de um snap-in do Windows PowerShell. Para obter mais informações sobre como registrar cmdlets, consulte [como registrar Cmdlets, provedores e aplicativos Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testando o Cmdlet

Quando seu cmdlet tiver sido registrado com o Windows PowerShell, você pode testá-lo executando-o na linha de comando. Vamos testar o exemplo de cmdlet Stop-Proc. Para obter mais informações sobre como usar os cmdlets da linha de comando, consulte o [Introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Inicie o Windows PowerShell e use Proc Stop para interromper um processo usando o alias ProcessName para o `Name` parâmetro.

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

A seguinte saída é exibida.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Verifique a entrada a seguir na linha de comando. Como o parâmetro de nome é obrigatório, você será solicitado para ele. Inserir "!?" Exibe o texto de ajuda associado ao parâmetro.

    ```powershell
    PS> stop-proc
    ```

A seguinte saída é exibida.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- Agora, verifique a seguinte entrada para interromper todos os processos que correspondem ao padrão de curinga "* Observação\*". Você será solicitado antes de parar a cada processo que corresponde ao padrão.

    ```powershell
    PS> stop-proc -Name *note*
    ```

A seguinte saída é exibida.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

A seguinte saída é exibida.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

A seguinte saída é exibida.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Consulte Também

[Criar um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md)

[Como criar um Cmdlet do Windows PowerShell](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Estendendo tipos de objeto e formatação](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Como registrar Cmdlets, provedores e aplicativos de Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Suporte a curingas nos parâmetros do Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
