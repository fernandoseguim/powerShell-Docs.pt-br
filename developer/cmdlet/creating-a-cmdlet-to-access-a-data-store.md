---
title: Criação de um Cmdlet para acessar uma Data Store | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea15e00e-20dc-4209-9e97-9ffd763e5d97
caps.latest.revision: 8
ms.openlocfilehash: 28d55874960f9a64b986204411d38319ef1d0da7
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059517"
---
# <a name="creating-a-cmdlet-to-access-a-data-store"></a>Criar um cmdlet para acessar um armazenamento de dados

Esta seção descreve como criar um cmdlet que acessa os dados armazenados por meio de um provedor do Windows PowerShell. Esse tipo de cmdlet usa a infraestrutura do provedor do Windows PowerShell do tempo de execução do Windows PowerShell e, portanto, a classe do cmdlet deve derivar de [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe base.

O cmdlet Select-Str descrito aqui pode localizar e selecionar cadeias de caracteres em um arquivo ou objeto. Os padrões usados para identificar a cadeia de caracteres podem ser especificados explicitamente por meio de `Path` parâmetro do cmdlet ou implicitamente por meio de `Script` parâmetro.

O cmdlet é projetado para usar qualquer provedor do Windows PowerShell que deriva [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider). Por exemplo, o cmdlet pode especificar o provedor do sistema de arquivos ou o provedor Variable que é fornecido pelo Windows PowerShell. Para obter mais informações aboutWindows provedores do PowerShell, consulte [provedor de projetar o Windows PowerShell](../prog-guide/designing-your-windows-powershell-provider.md).

Os tópicos nesta seção incluem o seguinte:

- [Definição da classe do Cmdlet](#Defining-the-Cmdlet-Class)

- [Definir parâmetros para acesso a dados](#Declaring-the-Path-Parameter)

- [Substituindo métodos de processamento de entrada](#Overriding-Input-Processing-Methods)

- [Acessar conteúdo](#Accessing-Content)

- [Exemplo de código](#Code-Sample)

- [Definindo tipos de objeto e formatação](#Declaring-Search-Support-Parameters)

- [Criando o Cmdlet](#Building-the-Cmdlet)

- [Testando o Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a>Definição da classe do Cmdlet

A primeira etapa na criação de cmdlet sempre é o cmdlet de nomenclatura e declarar a classe .NET que implementa o cmdlet. Esse cmdlet detecta determinadas cadeias de caracteres, portanto, o nome do verbo escolhido aqui é "Select", definido pela [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) classe. O nome de substantivo "Str" é usado porque o cmdlet age em cadeias de caracteres. Na declaração a seguir, observe que o nome do verbo e substantivo do cmdlet são refletidas no nome de classe do cmdlet. Para obter mais informações sobre os verbos aprovados do cmdlet, consulte [nomes de verbos de Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

A classe do .NET para esse cmdlet deve derivar de [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe base, pois ele fornece o suporte necessário no tempo de execução do Windows PowerShell para expor o provedor do Windows PowerShell infraestrutura. Observe que esse cmdlet também faz uso de classes de expressões regulares do .NET Framework, como [RegularExpressions](/dotnet/api/System.Text.RegularExpressions.Regex).

O código a seguir é a definição de classe para esse cmdlet Select-Str.

```csharp
[Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
public class SelectStringCommand : PSCmdlet
```

Esse cmdlet define um parâmetro padrão definido adicionando o `DefaultParameterSetName` palavra-chave de atributo à declaração de classe. O conjunto de parâmetros padrão `PatternParameterSet` é usado quando o `Script` parâmetro não for especificado. Para obter mais informações sobre este conjunto de parâmetros, consulte a `Pattern` e `Script` discussão de parâmetro na seção a seguir.

## <a name="defining-parameters-for-data-access"></a>Definir parâmetros para acesso a dados

Esse cmdlet define vários parâmetros que permitem ao usuário acessar e examinar os dados armazenados. Esses parâmetros incluem um `Path` parâmetro que indica o local do repositório de dados, um `Pattern` parâmetro que especifica o padrão a ser usado na pesquisa e vários outros parâmetros que dão suporte a como a pesquisa é executada.

> [!NOTE]
> Para obter mais informações sobre os conceitos básicos da definição de parâmetros, consulte [adicionando parâmetros essa entrada de linha de comando de processo](./adding-parameters-that-process-command-line-input.md).

### <a name="declaring-the-path-parameter"></a>Declarar o parâmetro Path

Para localizar o armazenamento de dados, esse cmdlet deve usar um caminho do Windows PowerShell para identificar o provedor do Windows PowerShell que foi projetado para acessar o armazenamento de dados. Portanto, ele define uma `Path` parâmetro da matriz de cadeia de caracteres de tipo para indicar o local do provedor.

```csharp
[Parameter(
           Position = 0,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
[Parameter(
           Position = 0,
           ParameterSetName = "PatternParameterSet",
           ValueFromPipeline = true,
           Mandatory = true)]
           [Alias("PSPath")]
public string[] Path
{
  get { return paths; }
  set { paths = value; }
}
private string[] paths;
```

Observe que esse parâmetro pertence a dois conjuntos de parâmetros diferentes e que tem um alias.

Duas [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) atributos declará-lo a `Path` parâmetro pertence a `ScriptParameterSet` e o `PatternParameterSet`. Para obter mais informações sobre conjuntos de parâmetros, consulte [adicionando conjuntos de parâmetro para um Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).

O [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) atributo declara um `PSPath` alias para o `Path` parâmetro. Declarar esse alias é altamente recomendável para manter a consistência com outros cmdlets que acessam provedores do Windows PowerShell. Para obter mais informações aboutWindows caminhos do PowerShell, consulte "Conceitos de caminho do PowerShell" em [como o Windows PowerShell funciona](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

### <a name="declaring-the-pattern-parameter"></a>Declarar o parâmetro padrão

Para especificar os padrões para pesquisar, esse cmdlet declara um `Pattern` parâmetro que é uma matriz de cadeias de caracteres. Um resultado positivo é retornado quando qualquer um dos padrões são encontrados no repositório de dados. Observe que esses padrões podem ser compilados em uma matriz de expressões regulares compiladas ou uma matriz de padrões de curinga usado para pesquisas de literais.

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "PatternParameterSet",
           Mandatory = true)]
public string[] Pattern
{
  get { return patterns; }
  set { patterns = value; }
}
private string[] patterns;
private Regex[] regexPattern;
private WildcardPattern[] wildcardPattern;
```

Quando esse parâmetro for especificado, o cmdlet usa o conjunto de parâmetros padrão `PatternParameterSet`. Nesse caso, o cmdlet usa os padrões especificados aqui para selecionar as cadeias de caracteres. Em contraste, o `Script` parâmetro também poderia ser usado para fornecer um script que contém os padrões. O `Script` e `Pattern` parâmetros definem dois conjuntos de parâmetros separados, portanto, eles são mutuamente exclusivos.

### <a name="declaring-search-support-parameters"></a>Declarando parâmetros de suporte de pesquisa

Esse cmdlet define os seguintes parâmetros de suporte que podem ser usados para modificar os recursos de pesquisa do cmdlet.

O `Script` parâmetro especifica um bloco de script que pode ser usado para fornecer um mecanismo de pesquisa alternativos para o cmdlet. O script deve conter os padrões usados para corresponder e retornar um [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objeto. Observe que esse parâmetro é também o parâmetro exclusivo que identifica o `ScriptParameterSet` conjunto de parâmetros. Quando o tempo de execução do Windows PowerShell vê esse parâmetro, ele usa apenas os parâmetros que pertencem ao `ScriptParameterSet` conjunto de parâmetros.

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
public ScriptBlock Script
{
  set { script = value; }
  get { return script; }
}
ScriptBlock script;
```

O `SimpleMatch` parâmetro é um parâmetro de opção que indica se o cmdlet deve ser explicitamente correspondam aos padrões, como eles são fornecidos. Quando o usuário Especifica o parâmetro na linha de comando (`true`), o cmdlet usa os padrões, como eles são fornecidos. Se o parâmetro não for especificado (`false`), o cmdlet usa expressões regulares. O padrão para esse parâmetro é `false`.

```csharp
[Parameter]
public SwitchParameter SimpleMatch
{
  get { return simpleMatch; }
  set { simpleMatch = value; }
}
private bool simpleMatch;
```

O `CaseSensitive` parâmetro é um parâmetro de opção que indica se a uma pesquisa diferencia maiusculas de minúsculas será executada. Quando o usuário Especifica o parâmetro na linha de comando (`true`), o cmdlet verifica as letras maiusculas e minúsculas de caracteres ao comparar os padrões. Se o parâmetro não for especificado (`false`), o cmdlet não faz distinção entre maiusculas e minúsculas. Por exemplo "MyFile" e "myfile" ambos retornariam como ocorrências positivas. O padrão para esse parâmetro é `false`.

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

O `Exclude` e `Include` parâmetros identificam os itens que são explicitamente excluídos ou incluídos na pesquisa. Por padrão, o cmdlet irá procurar todos os itens no armazenamento de dados. No entanto, para limitar a pesquisa executada pelo cmdlet, esses parâmetros podem ser usados para indicar explicitamente os itens a serem incluídos na pesquisa ou omitidos.

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

```csharp
[Parameter]
[ValidateNotNullOrEmpty]
public string[] Include
{
  get
  {
    return includeStrings;
  }
  set
  {
    includeStrings = value;

    this.include = new WildcardPattern[includeStrings.Length];
    for (int i = 0; i < includeStrings.Length; i++)
    {
      this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
    }
  }
}

internal string[] includeStrings = null;
internal WildcardPattern[] include = null;
```

### <a name="declaring-parameter-sets"></a>Declarando conjuntos de parâmetros

Esse cmdlet usa dois conjuntos de parâmetros (`ScriptParameterSet` e `PatternParameterSet`, que é o padrão) como os nomes dos dois conjuntos de parâmetros usados no acesso a dados. `PatternParameterSet` é o conjunto de parâmetros padrão e é usado quando o `Pattern` parâmetro for especificado. `ScriptParameterSet` é usado quando o usuário Especifica um mecanismo de pesquisa alternativos por meio de `Script` parâmetro. Para obter mais informações sobre conjuntos de parâmetros, consulte [adicionando conjuntos de parâmetro para um Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).

## <a name="overriding-input-processing-methods"></a>Substituindo métodos de processamento de entrada

Cmdlets deve substituir um ou mais da entrada de processamento de métodos para o [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe. Para obter mais informações sobre os métodos de processamento de entrada, consulte [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md).

Esse cmdlet substitui o [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) compilado de método para criar uma matriz de expressões regulares na inicialização. Isso aumenta o desempenho durante as pesquisas que não usam correspondência simples.

```csharp
protected override void BeginProcessing()
{
  WriteDebug("Validating patterns.");
  if (patterns != null)
  {
    foreach(string pattern in patterns)
    {
      if (pattern == null)
      ThrowTerminatingError(new ErrorRecord(
                            new ArgumentNullException(
                            "Search pattern cannot be null."),
                            "NullSearchPattern",
                            ErrorCategory.InvalidArgument,
                            pattern)
                            );
    }

    WriteVerbose("Search pattern(s) are valid.");

    // If a simple match is not specified, then
    // compile the regular expressions once.
    if (!simpleMatch)
    {
      WriteDebug("Compiling search regular expressions.");

      RegexOptions regexOptions = RegexOptions.Compiled;
      if (!caseSensitive)
         regexOptions |= RegexOptions.Compiled;
      regexPattern = new Regex[patterns.Length];

      for (int i = 0; i < patterns.Length; i++)
      {
        try
        {
          regexPattern[i] = new Regex(patterns[i], regexOptions);
        }
        catch (ArgumentException ex)
        {
          ThrowTerminatingError(new ErrorRecord(
                        ex,
                        "InvalidRegularExpression",
                        ErrorCategory.InvalidArgument,
                        patterns[i]
                     ));
        }
      } //Loop through patterns to create RegEx objects.

      WriteVerbose("Pattern(s) compiled into regular expressions.");
    }// If not a simple match.

    // If a simple match is specified, then compile the
    // wildcard patterns once.
    else
    {
      WriteDebug("Compiling search wildcards.");

      WildcardOptions wildcardOptions = WildcardOptions.Compiled;

      if (!caseSensitive)
      {
        wildcardOptions |= WildcardOptions.IgnoreCase;
      }

      wildcardPattern = new WildcardPattern[patterns.Length];
      for (int i = 0; i < patterns.Length; i++)
      {
        wildcardPattern[i] =
                     new WildcardPattern(patterns[i], wildcardOptions);
      }

      WriteVerbose("Pattern(s) compiled into wildcard expressions.");
    }// If match is a simple match.
  }// If valid patterns are available.
}// End of function BeginProcessing().
```

Esse cmdlet também substitui o [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método para processar as seleções de cadeia de caracteres que o usuário faz na linha de comando. Ele grava os resultados da seleção de cadeia de caracteres na forma de um objeto personalizado, chamando uma privada **MatchString** método.

```csharp
protected override void ProcessRecord()
{
  UInt64 lineNumber = 0;
  MatchInfo result;
  ArrayList nonMatches = new ArrayList();

  // Walk the list of paths and search the contents for
  // any of the specified patterns.
  foreach (string psPath in paths)
  {
    // Once the filepaths are expanded, we may have more than one
    // path, so process all referenced paths.
    foreach(PathInfo path in
            SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
           )
    {
      WriteVerbose("Processing path " + path.Path);

      // Check if the path represents one of the items to be
      // excluded. If so, continue to next path.
      if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
         continue;

      // Get the content reader for the item(s) at the
      // specified path.
      Collection<IContentReader> readerCollection = null;
      try
      {
        readerCollection =
                    this.InvokeProvider.Content.GetReader(path.Path);
      }
      catch (PSNotSupportedException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "ContentAccessNotSupported",
                    ErrorCategory.NotImplemented,
                    path.Path)
                   );
        return;
      }

      foreach(IContentReader reader in readerCollection)
      {
        // Reset the line number for this path.
        lineNumber = 0;

        // Read in a single block (line in case of a file)
        // from the object.
        IList items = reader.Read(1);

        // Read and process one block(line) at a time until
        // no more blocks(lines) exist.
        while (items != null && items.Count == 1)
        {
          // Increment the line number each time a line is
          // processed.
          lineNumber++;

          String message = String.Format("Testing line {0} : {1}",
                                        lineNumber, items[0]);

          WriteDebug(message);

          result = SelectString(items[0]);

          if (result != null)
          {
            result.Path = path.Path;
            result.LineNumber = lineNumber;

            WriteObject(result);
          }
          else
          {
            // Add the block(line) that did not match to the
            // collection of non matches , which will be stored
            // in the SessionState variable $NonMatches
            nonMatches.Add(items[0]);
          }

          // Get the next line from the object.
          items = reader.Read(1);

        }// While loop for reading one line at a time.
      }// Foreach loop for reader collection.
    }// Foreach loop for processing referenced paths.
  }// Foreach loop for walking of path list.

  // Store the list of non-matches in the
  // session state variable $NonMatches.
  try
  {
    this.SessionState.PSVariable.Set("NonMatches", nonMatches);
  }
  catch (SessionStateUnauthorizedAccessException ex)
  {
    WriteError(new ErrorRecord(ex,
               "CannotWriteVariableNonMatches",
               ErrorCategory.InvalidOperation,
               nonMatches)
              );
  }

}// End of protected override void ProcessRecord().
```

## <a name="accessing-content"></a>Acessar conteúdo

O cmdlet deve abrir o provedor indicado pelo caminho do Windows PowerShell para que ele pode acessar os dados. O [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) objeto para o espaço de execução é usado para acessar o provedor, enquanto o [System.Management.Automation.PSCmdlet.Invokeprovider*](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider) propriedade das cmdlet é usado para abrir o provedor. Acesso ao conteúdo é fornecido pela recuperação do [System.Management.Automation.Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics) abrir o objeto para o provedor.

Esse cmdlet Str Select de exemplo usa o [System.Management.Automation.Providerintrinsics.Content*](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content) propriedade para expor o conteúdo para fazer a varredura. Em seguida, ele pode chamar o [System.Management.Automation.Contentcmdletproviderintrinsics.Getreader*](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader) método, passando o caminho necessário do Windows PowerShell.

## <a name="code-sample"></a>Exemplo de código

O código a seguir mostra a implementação dessa versão desse cmdlet Select-Str. Observe que esse código inclui a classe do cmdlet, usados pelo cmdlet de métodos privados e o Windows PowerShell snap-in do código usado para registrar o cmdlet. Para obter mais informações sobre como registrar o cmdlet, consulte [Compilando o Cmdlet](#Building-the-Cmdlet).

```csharp
//
// Copyright (c) 2006 Microsoft Corporation. All rights reserved.
//
// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
// PARTICULAR PURPOSE.
//
using System;
using System.Text.RegularExpressions;
using System.Collections;
using System.Collections.ObjectModel;
using System.Management.Automation;
using System.Management.Automation.Provider;
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{
  #region SelectStringCommand
  /// <summary>
  /// This cmdlet searches through PSObjects for particular patterns.
  /// </summary>
  /// <remarks>
  /// This cmdlet can be used to search any object, such as a file or a
  /// variable, whose provider exposes methods for reading and writing
  /// content.
  /// </remarks>
  [Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
  public class SelectStringCommand : PSCmdlet
  {
    #region Parameters
    /// <summary>
    /// Declare a Path parameter that specifies where the data is stored.
    /// This parameter must specify a PowerShell that indicates the
    /// PowerShell provider that is used to access the objects to be
    /// searched for matching patterns. This parameter should also have
    /// a PSPath alias to provide consistency with other cmdlets that use
    /// PowerShell providers.
    /// </summary>
    /// <value>Path of the object(s) to search.</value>
    [Parameter(
               Position = 0,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    [Parameter(
               Position = 0,
               ParameterSetName = "PatternParameterSet",
               ValueFromPipeline = true,
               Mandatory = true)]
               [Alias("PSPath")]
    public string[] Path
    {
      get { return paths; }
      set { paths = value; }
    }
    private string[] paths;

    /// <summary>
    /// Declare a Pattern parameter that specifies the pattern(s)
    /// used to find matching patterns in the string representation
    /// of the objects. A positive result will be returned
    /// if any of the patterns are found in the objects.
    /// </summary>
    /// <remarks>
    /// The patterns will be compiled into an array of wildcard
    /// patterns for a simple match (literal string matching),
    /// or the patterns will be converted into an array of compiled
    /// regular expressions.
    /// </remarks>
    /// <value>Array of patterns to search.</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "PatternParameterSet",
               Mandatory = true)]
    public string[] Pattern
    {
      get { return patterns; }
      set { patterns = value; }
    }
    private string[] patterns;
    private Regex[] regexPattern;
    private WildcardPattern[] wildcardPattern;

    /// <summary>
    /// Declare a Script parameter that specifies a script block
    /// that is called to perform the matching operations
    /// instead of the matching performed by the cmdlet.
    /// </summary>
    /// <value>Script block that will be called for matching</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    public ScriptBlock Script
    {
      set { script = value; }
      get { return script; }
    }
    ScriptBlock script;

    /// <summary>
    /// Declare a switch parameter that specifies if the pattern(s) are used
    /// literally. If not (default), searching is
    /// done using regular expressions.
    /// </summary>
    /// <value>If True, a literal pattern is used.</value>
    [Parameter]
    public SwitchParameter SimpleMatch
    {
      get { return simpleMatch; }
      set { simpleMatch = value; }
    }
    private bool simpleMatch;

    /// <summary>
    /// Declare a switch parameter that specifies if a case-sensitive
    /// search is performed.  If not (default), a case-insensitive search
    /// is performed.
    /// </summary>
    /// <value>If True, a case-sensitive search is made.</value>
    [Parameter]
    public SwitchParameter CaseSensitive
    {
      get { return caseSensitive; }
      set { caseSensitive = value; }
    }
    private bool caseSensitive;

    /// <summary>
    /// Declare an Include parameter that species which
    /// specific items are searched.  When this parameter
    /// is used, items that are not listed here are omitted
    /// from the search.
    /// </summary>
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Include
    {
      get
      {
        return includeStrings;
      }
      set
      {
        includeStrings = value;

        this.include = new WildcardPattern[includeStrings.Length];
        for (int i = 0; i < includeStrings.Length; i++)
        {
          this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }

    internal string[] includeStrings = null;
    internal WildcardPattern[] include = null;

    /// <summary>
    /// Declare an Exclude parameter that species which
    /// specific items are omitted from the search.
    /// </summary>
    ///
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Exclude
    {
      get
      {
        return excludeStrings;
      }
      set
      {
        excludeStrings = value;

        this.exclude = new WildcardPattern[excludeStrings.Length];
        for (int i = 0; i < excludeStrings.Length; i++)
        {
          this.exclude[i] = new WildcardPattern(excludeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }
    internal string[] excludeStrings;
    internal WildcardPattern[] exclude;

    #endregion Parameters

    #region Overrides
    /// <summary>
    /// If regular expressions are used for pattern matching,
    /// then build an array of compiled regular expressions
    /// at startup. This increases performance during scanning
    /// operations when simple matching is not used.
    /// </summary>
    protected override void BeginProcessing()
    {
      WriteDebug("Validating patterns.");
      if (patterns != null)
      {
        foreach(string pattern in patterns)
        {
          if (pattern == null)
          ThrowTerminatingError(new ErrorRecord(
                                new ArgumentNullException(
                                "Search pattern cannot be null."),
                                "NullSearchPattern",
                                ErrorCategory.InvalidArgument,
                                pattern)
                                );
        }

        WriteVerbose("Search pattern(s) are valid.");

        // If a simple match is not specified, then
        // compile the regular expressions once.
        if (!simpleMatch)
        {
          WriteDebug("Compiling search regular expressions.");

          RegexOptions regexOptions = RegexOptions.Compiled;
          if (!caseSensitive)
             regexOptions |= RegexOptions.Compiled;
          regexPattern = new Regex[patterns.Length];

          for (int i = 0; i < patterns.Length; i++)
          {
            try
            {
              regexPattern[i] = new Regex(patterns[i], regexOptions);
            }
            catch (ArgumentException ex)
            {
              ThrowTerminatingError(new ErrorRecord(
                            ex,
                            "InvalidRegularExpression",
                            ErrorCategory.InvalidArgument,
                            patterns[i]
                         ));
            }
          } //Loop through patterns to create RegEx objects.

          WriteVerbose("Pattern(s) compiled into regular expressions.");
        }// If not a simple match.

        // If a simple match is specified, then compile the
        // wildcard patterns once.
        else
        {
          WriteDebug("Compiling search wildcards.");

          WildcardOptions wildcardOptions = WildcardOptions.Compiled;

          if (!caseSensitive)
          {
            wildcardOptions |= WildcardOptions.IgnoreCase;
          }

          wildcardPattern = new WildcardPattern[patterns.Length];
          for (int i = 0; i < patterns.Length; i++)
          {
            wildcardPattern[i] =
                         new WildcardPattern(patterns[i], wildcardOptions);
          }

          WriteVerbose("Pattern(s) compiled into wildcard expressions.");
        }// If match is a simple match.
      }// If valid patterns are available.
    }// End of function BeginProcessing().

    /// <summary>
    /// Process the input and search for the specified patterns.
    /// </summary>
    protected override void ProcessRecord()
    {
      UInt64 lineNumber = 0;
      MatchInfo result;
      ArrayList nonMatches = new ArrayList();

      // Walk the list of paths and search the contents for
      // any of the specified patterns.
      foreach (string psPath in paths)
      {
        // Once the filepaths are expanded, we may have more than one
        // path, so process all referenced paths.
        foreach(PathInfo path in
                SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
               )
        {
          WriteVerbose("Processing path " + path.Path);

          // Check if the path represents one of the items to be
          // excluded. If so, continue to next path.
          if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
             continue;

          // Get the content reader for the item(s) at the
          // specified path.
          Collection<IContentReader> readerCollection = null;
          try
          {
            readerCollection =
                        this.InvokeProvider.Content.GetReader(path.Path);
          }
          catch (PSNotSupportedException ex)
          {
            WriteError(new ErrorRecord(ex,
                       "ContentAccessNotSupported",
                        ErrorCategory.NotImplemented,
                        path.Path)
                       );
            return;
          }

          foreach(IContentReader reader in readerCollection)
          {
            // Reset the line number for this path.
            lineNumber = 0;

            // Read in a single block (line in case of a file)
            // from the object.
            IList items = reader.Read(1);

            // Read and process one block(line) at a time until
            // no more blocks(lines) exist.
            while (items != null && items.Count == 1)
            {
              // Increment the line number each time a line is
              // processed.
              lineNumber++;

              String message = String.Format("Testing line {0} : {1}",
                                            lineNumber, items[0]);

              WriteDebug(message);

              result = SelectString(items[0]);

              if (result != null)
              {
                result.Path = path.Path;
                result.LineNumber = lineNumber;

                WriteObject(result);
              }
              else
              {
                // Add the block(line) that did not match to the
                // collection of non matches , which will be stored
                // in the SessionState variable $NonMatches
                nonMatches.Add(items[0]);
              }

              // Get the next line from the object.
              items = reader.Read(1);

            }// While loop for reading one line at a time.
          }// Foreach loop for reader collection.
        }// Foreach loop for processing referenced paths.
      }// Foreach loop for walking of path list.

      // Store the list of non-matches in the
      // session state variable $NonMatches.
      try
      {
        this.SessionState.PSVariable.Set("NonMatches", nonMatches);
      }
      catch (SessionStateUnauthorizedAccessException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "CannotWriteVariableNonMatches",
                   ErrorCategory.InvalidOperation,
                   nonMatches)
                  );
      }

    }// End of protected override void ProcessRecord().
    #endregion Overrides

    #region PrivateMethods
    /// <summary>
    /// Check for a match using the input string and the pattern(s)
    /// specified.
    /// </summary>
    /// <param name="input">The string to test.</param>
    /// <returns>MatchInfo object containing information about
    /// result of a match</returns>
    private MatchInfo SelectString(object input)
    {
      string line = null;

      try
      {
        // Convert the object to a string type
        // safely using language support methods
        line = (string)LanguagePrimitives.ConvertTo(
                                                    input,
                                                    typeof(string)
                                                    );
        line = line.Trim(' ','\t');
      }
      catch (PSInvalidCastException ex)
      {
        WriteError(new ErrorRecord(
                   ex,
                   "CannotCastObjectToString",
                   ErrorCategory.InvalidOperation,
                   input)
                   );

        return null;
      }

      MatchInfo result = null;

      // If a scriptblock has been specified, call it
      // with the path for processing.  It will return
      // one object.
      if (script != null)
      {
        WriteDebug("Executing script block.");

        Collection<PSObject> psObjects =
                             script.Invoke(
                                           line,
                                           simpleMatch,
                                           caseSensitive
                                          );

        foreach (PSObject psObject in psObjects)
        {
          if (LanguagePrimitives.IsTrue(psObject))
          {
            result = new MatchInfo();
            result.Line = line;
            result.IgnoreCase = !caseSensitive;

            break;
          } //End of If.
        } //End ForEach loop.
      } // End of If if script exists.

      // If script block exists, see if this line matches any
      // of the match patterns.
      else
      {
        int patternIndex = 0;

        while (patternIndex < patterns.Length)
        {
          if ((simpleMatch &&
              wildcardPattern[patternIndex].IsMatch(line))
              || (regexPattern != null
              && regexPattern[patternIndex].IsMatch(line))
             )
          {
            result = new MatchInfo();
            result.IgnoreCase = !caseSensitive;
            result.Line = line;
            result.Pattern = patterns[patternIndex];

            break;
          }

          patternIndex++;

        }// While loop through patterns.
      }// Else for no script block specified.

      return result;

    }// End of SelectString

    /// <summary>
    /// Check whether the supplied name meets the include/exclude criteria.
    /// That is - it's on the include list if the include list was
    /// specified, and not on the exclude list if the exclude list was specified.
    /// </summary>
    /// <param name="path">path to validate</param>
    /// <returns>True if the path is acceptable.</returns>
    private bool MeetsIncludeExcludeCriteria(string path)
    {
      bool ok = false;

      // See if the file is on the include list.
      if (this.include != null)
      {
        foreach (WildcardPattern patternItem in this.include)
        {
          if (patternItem.IsMatch(path))
          {
            ok = true;
            break;
          }
        }
      }
      else
      {
        ok = true;
      }

      if (!ok)
         return false;

      // See if the file is on the exclude list.
      if (this.exclude != null)
      {
        foreach (WildcardPattern patternItem in this.exclude)
        {
          if (patternItem.IsMatch(path))
          {
            ok = false;
            break;
          }
        }
      }

      return ok;
    } //MeetsIncludeExcludeCriteria
    #endregion Private Methods

  }// class SelectStringCommand

  #endregion SelectStringCommand

  #region MatchInfo

  /// <summary>
  /// Class representing the result of a pattern/literal match
  /// that is passed through the pipeline by the Select-Str cmdlet.
  /// </summary>
  public class MatchInfo
  {
    /// <summary>
    /// Indicates if the match was done ignoring case.
    /// </summary>
    /// <value>True if case was ignored.</value>
    public bool IgnoreCase
    {
      get { return ignoreCase; }
      set { ignoreCase = value; }
    }
    private bool ignoreCase;

    /// <summary>
    /// Specifies the number of the matching line.
    /// </summary>
    /// <value>The number of the matching line.</value>
    public UInt64 LineNumber
    {
      get { return lineNumber; }
      set { lineNumber = value; }
    }
    private UInt64 lineNumber;

    /// <summary>
    /// Specifies the text of the matching line.
    /// </summary>
    /// <value>The text of the matching line.</value>
    public string Line
    {
      get { return line; }
      set { line = value; }
    }
    private string line;

    /// <summary>
    /// Specifies the full path of the object(file) containing the
    /// matching line.
    /// </summary>
    /// <remarks>
    /// It will be "inputStream" if the object came from the input
    /// stream.
    /// </remarks>
    /// <value>The path name</value>
    public string Path
    {
      get { return path; }
      set
      {
        pathSet = true;
        path = value;
      }
    }
    private string path;
    private bool pathSet;

    /// <summary>
    /// Specifies the pattern that was used in the match.
    /// </summary>
    /// <value>The pattern string</value>
    public string Pattern
    {
      get { return pattern; }
      set { pattern = value; }
    }
    private string pattern;

    private const string MatchFormat = "{0}:{1}:{2}";

    /// <summary>
    /// Returns the string representation of this object. The format
    /// depends on whether a path has been set for this object or
    /// not.
    /// </summary>
    /// <remarks>
    /// If the path component is set, as would be the case when
    /// matching in a file, ToString() returns the path, line
    /// number and line text.  If path is not set, then just the
    /// line text is presented.
    /// </remarks>
    /// <returns>The string representation of the match object.</returns>
    public override string ToString()
    {
      if (pathSet)
         return String.Format(
         System.Threading.Thread.CurrentThread.CurrentCulture,
         MatchFormat,
         this.path,
         this.lineNumber,
         this.line
         );
      else
         return this.line;
    }
  }// End class MatchInfo

  #endregion

  #region PowerShell snap-in

  /// <summary>
  /// Create a PowerShell snap-in for the Select-Str cmdlet.
  /// </summary>
  [RunInstaller(true)]
  public class SelectStringPSSnapIn : PSSnapIn
  {
    /// <summary>
    /// Create an instance of the SelectStrPSSnapin class.
    /// </summary>
    public SelectStringPSSnapIn()
           : base()
    {
    }

    /// <summary>
    /// Specify the name of the PowerShell snap-in.
    /// </summary>
    public override string Name
    {
      get
      {
        return "SelectStrPSSnapIn";
      }
    }

    /// <summary>
    /// Specify the vendor of the PowerShell snap-in.
    /// </summary>
    public override string Vendor
    {
      get
      {
        return "Microsoft";
      }
    }

    /// <summary>
    /// Specify the localization resource information for the vendor.
    /// Use the format: SnapinName,VendorName.
    /// </summary>
    public override string VendorResource
    {
      get
      {
        return "SelectStrSnapIn,Microsoft";
      }
    }

    /// <summary>
    /// Specify the description of the PowerShell snap-in.
    /// </summary>
    public override string Description
    {
      get
        {
          return "This is a PowerShell snap-in for the Select-Str cmdlet.";
        }
    }

    /// <summary>
    /// Specify the localization resource information for the description.
    /// Use the format: SnapinName,Description.

    /// </summary>
    public override string DescriptionResource
    {
      get
      {
          return "SelectStrSnapIn,This is a PowerShell snap-in for the Select-Str cmdlet.";
      }
    }
  }
  #endregion PowerShell snap-in

} //namespace Microsoft.Samples.PowerShell.Commands;
```

## <a name="building-the-cmdlet"></a>Criando o Cmdlet

Depois de implementar um cmdlet, você deve registrá-lo com o Windows PowerShell por meio de um snap-in do Windows PowerShell. Para obter mais informações sobre como registrar cmdlets, consulte [como registrar Cmdlets, provedores e aplicativos Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testando o Cmdlet

Quando seu cmdlet tiver sido registrado com o Windows PowerShell, você pode testá-lo executando-o na linha de comando. O procedimento a seguir pode ser usado para testar o exemplo de cmdlet Select Str.

1. Inicie o Windows PowerShell e procure o arquivo de notas para ocorrências de linhas com a expressão ".NET". Observe que as aspas ao redor do nome do caminho são necessárias apenas se o caminho consiste em mais de uma palavra.

    ```powershell
    select-str -Path "notes" -Pattern ".NET" -SimpleMatch=$false
    ```

    A seguinte saída é exibida.

    ```output
    IgnoreCase   : True
    LineNumber   : 8
    Line         : Because Windows PowerShell works directly with .NET objects, there is often a .NET object
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    IgnoreCase   : True
    LineNumber   : 21
    Line         : You should normally define the class for a cmdlet in a .NET namespace
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    ```

2. Procure o arquivo de notas para ocorrências de linhas com a palavra "por", seguido por qualquer outro texto. O `SimpleMatch` parâmetro está usando o valor padrão de `false`. A pesquisa diferencia maiusculas de minúsculas porque o `CaseSensitive` parâmetro é definido como `false`.

    ```powershell
    select-str -Path notes -Pattern "over*" -SimpleMatch -CaseSensitive:$false
    ```

    A seguinte saída é exibida.

    ```output
    IgnoreCase   : True
    LineNumber   : 45
    Line         : Override StopProcessing
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    IgnoreCase   : True
    LineNumber   : 49
    Line         : overriding the StopProcessing method
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    ```

3. O arquivo de notas usando uma expressão regular como o padrão de pesquisa. O cmdlet procura por caracteres alfabéticos e espaços em branco entre parênteses.

    ```powershell
    select-str -Path notes -Pattern "\([A-Za-z:blank:]" -SimpleMatch:$false
    ```

    A seguinte saída é exibida.

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : Advisory Guidelines (Consider Following)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    IgnoreCase   : True
    LineNumber   : 53
    Line         : If your cmdlet has objects that are not disposed of (written to the pipeline)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    ```

4. Realize uma pesquisa diferencia maiusculas de minúsculas do arquivo de notas para ocorrências da palavra "Parâmetro".

    ```powershell
    select-str -Path notes -Pattern Parameter -CaseSensitive
    ```

    A seguinte saída é exibida.

    ```output
    IgnoreCase   : False
    LineNumber   : 6
    Line         : Support an InputObject Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    IgnoreCase   : False
    LineNumber   : 30
    Line         : Support Force Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    ```

5. Pesquisa o provedor variable é fornecido com o Windows PowerShell para variáveis que têm valores numéricos de 0 a 9.

    ```powershell
    select-str -Path * -Pattern "[0-9]"
    ```

    A seguinte saída é exibida.

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : 64
    Path         : Variable:\MaximumHistoryCount
    Pattern      : [0-9]
    ```

6. Use um bloco de script para pesquisar o arquivo SelectStrCommandSample.cs para a cadeia de caracteres "Pos". O **cmatch** de função para o script realiza uma correspondência de padrão de maiusculas e minúsculas.

    ```powershell
    select-str -Path "SelectStrCommandSample.cs" -Script { if ($args[0] -cmatch "Pos"){ return $true } return $false }
    ```

    A seguinte saída é exibida.

    ```output
    IgnoreCase   : True
    LineNumber   : 37
    Line         :    Position = 0.
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\SelectStrCommandSample.cs
    Pattern      :
    ```

## <a name="see-also"></a>Consulte Também

[Como criar um Cmdlet do Windows PowerShell](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md)

[Criação de um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md)

[Projetar seu provedor do Windows PowerShell](../prog-guide/designing-your-windows-powershell-provider.md)

[Como funciona o Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Como registrar Cmdlets, provedores e aplicativos de Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
