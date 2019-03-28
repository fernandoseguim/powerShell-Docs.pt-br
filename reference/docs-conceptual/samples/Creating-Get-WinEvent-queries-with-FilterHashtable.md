---
ms.date: 3/18/2019
title: Criando consultas Get-WinEvent com FilterHashtable
ms.openlocfilehash: fae01cc8be5c1805e2aae008e1f21ed387efa325
ms.sourcegitcommit: 396509cd0d415acc306b68758b6f833406e26bf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2019
ms.locfileid: "58320451"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a>Criando consultas Get-WinEvent com FilterHashtable

Para ler a postagem de blog original do **Scripting Guy** de 3 de junho de 2014, confira [Use o FilterHashTable para filtrar log de eventos com o PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).

Este artigo é um trecho da postagem do blog original e explica como usar o parâmetro **FilterHashtable** do cmdlet `Get-WinEvent` para filtrar logs de eventos. O cmdlet `Get-WinEvent` do PowerShell é um método poderoso de filtragem de logs de eventos e diagnósticos do Windows. Quando uma consulta `Get-WinEvent` usa o parâmetro **FilterHashtable**, seu desempenho é aprimorado.

Quando você trabalha com grandes logs de eventos, não é eficiente enviar objetos pelo pipeline para um comando `Where-Object`. Antes do PowerShell 6, o cmdlet `Get-EventLog` era outra opção para obter dados de log. Por exemplo, os comandos a seguir são ineficientes para filtrar os logs **Microsoft-Windows-Defrag**:

`Get-EventLog -LogName Application | Where-Object Source -Match defrag`

`Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }`

O comando a seguir usa uma tabela de hash que melhora o desempenho:

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

### <a name="blog-posts-about-enumeration"></a>Postagens no blog sobre enumeração

Este artigo apresenta informações sobre como usar os valores enumerados em uma tabela de hash. Para obter mais informações sobre a enumeração, leia as postagens de blog de **Scripting Guy**. Para criar uma função que retorne valores enumerados, confira [Enumerações e valores](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).
Para obter mais informações, confira [a série de postagens de blog sobre enumeração de Scripting Guy](https://devblogs.microsoft.com/scripting/?s=about+enumeration).

### <a name="hash-table-keyvalue-pairs"></a>Pares chave-valor da tabela de hash

Para criar consultas eficientes, use o cmdlet `Get-WinEvent` com o parâmetro **FilterHashtable**.
O **FilterHashtable** aceita uma tabela de hash como filtro para obter informações específicas de logs de eventos do Windows. Uma tabela de hash usa pares **chave-valor**. Para obter informações sobre tabelas de hash, confira [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).

Se os pares **chave-valor** estiverem na mesma linha, eles deverão ser separados por um ponto e vírgula. Se cada par **chave-valor** estiver em uma linha separada, o ponto e vírgula não será necessário. Por exemplo, este artigo coloca pares **chave-valor**  em linhas separadas e não usa ponto e vírgula.

Este exemplo usa vários parâmetros **FilterHashtable** dos pares **chave-valor**. A consulta completa inclui **LogName**, **ProviderName**, **Palavras-chave**, **ID** e **Nível**.

Os pares **chave-valor** aceitos são mostrados na tabela a seguir e incluídos na documentação do parâmetro [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable **.

A tabela a seguir exibe os nomes de chave, os tipos de dados e se os caracteres curinga são aceitos para um valor de dados.

| Nome da chave     | Tipo de dados de valor    | Aceita caracteres curinga? |
|------------- | ------------------ | ---------------------------- |
| LogName      | `<String[]>`       | Sim |
| ProviderName | `<String[]>`       | Sim |
| Caminho         | `<String[]>`       | Não  |
| Palavras-chave     | `<Long[]>`         | Não  |
| ID           | `<Int32[]>`        | Não  |
| Nível        | `<Int32[]>`        | Não  |
| StartTime    | `<DateTime>`       | Não  |
| EndTime      | `<DateTime>`       | Não  |
| UserID       | `<SID>`            | Não  |
| Dados         | `<String[]>`       | Não  |
| *            | `<String[]>`       | Não  |

### <a name="building-a-query-with-a-hash-table"></a>Como criar uma consulta com uma tabela de hash

Para verificar os resultados e solucionar problemas, convém criar a tabela de hash com um par **chave-valor** de cada vez. A consulta obtém dados de log do **Aplicativo**. A tabela de hash é equivalente a `Get-WinEvent –LogName Application`.

Para começar, crie uma consulta `Get-WinEvent`. Use o par **chave-valor** do parâmetro **FilterHashtable** com a chave **LogName** e o valor **Aplicativo**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

Continue a criar a tabela de hash com a chave **ProviderName**. O **ProviderName** é o nome exibido no campo **Fonte** no **Visualizador de Eventos do Windows**. Por exemplo, **Tempo de execução do .NET** na captura de tela a seguir:

![Imagem das fontes do Visualizador de Eventos do Windows.](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

Atualize a tabela de hash e inclua o par **chave-valor** com a chave **ProviderName e o valor **Tempo de execução do .NET**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

Se sua consulta precisar obter dados de logs de eventos arquivados, use a chave **Caminho**. O valor **Caminho** especifica o caminho completo para o arquivo de log. Para obter mais informações, confira a postagem no blog do **Scripting Guy**, [Use o PowerShell para analisar erros de log de eventos salvos](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).

### <a name="using-enumerated-values-in-a-hash-table"></a>Usando valores enumerados em uma tabela de hash

A chave **Palavras-chave** é a próxima na tabela de hash. O tipo de dados **Palavras-chave** é uma matriz do tipo de valor `[long]` que contém um número grande. Use o seguinte comando para encontrar o valor máximo de `[long]`:

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

Para a chave **Palavras-chave**, o PowerShell usa um número, não uma cadeia de caracteres, como **Segurança**. Embora sejam valores enumerados, o **Visualizador de Eventos do Windows** exibe as **Palavras-chave** como cadeias de caracteres. Na tabela de hash, se você usar a chave **Palavras-chave** com um valor de cadeia de caracteres, será exibida uma mensagem de erro.

Abra o **Visualizador de Eventos do Windows** e, no painel **Ações**, clique em **Filtrar o registro atual**.
O menu suspenso **Palavras-chave** exibe as palavras-chave disponíveis, conforme mostrado na captura de tela a seguir:

![Imagem de palavras-chave do Visualizador de Eventos do Windows.](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

Use o seguinte comando para exibir os nomes das propriedades `StandardEventKeywords`.

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventKeywords] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventKeywords
Name             MemberType Definition
—-             ———- ———-
AuditFailure     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
AuditSuccess     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint2 Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
EventLogClassic  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
None             Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
ResponseTime     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
Sqm              Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiContext       Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiDiagnostic    Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
```

Os valores enumerados estão documentados no **.NET Framework**. Para obter mais informações, confira [Enumeração StandardEventKeywords](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).

Os nomes e valores enumerados das **Palavras-chave** são os seguintes:

| Nome             |  Valor            |
| ---------------- | ------------------|
| AuditFailure     | 4503599627370496  |
| AuditSuccess     | 9007199254740992  |
| CorrelationHint2 | 18014398509481984 |
| EventLogClassic  | 36028797018963968 |
| Sqm              | 2251799813685248  |
| WdiDiagnostic    | 1125899906842624  |
| WdiContext       | 562949953421312   |
| ResponseTime     | 281474976710656   |
| Não             | 0                 |

Atualize a tabela de hash e inclua o par **chave-valor** com a chave **Palavras-chave** e o valor de enumeração **EventLogClassic**, **36028797018963968**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

#### <a name="keywords-static-property-value-optional"></a>Valor da propriedade estática das palavras-chave (opcional)

A chave **Palavras-chave** é enumerada, mas é possível usar um nome de propriedade estático na consulta da tabela de hash.
Em vez de usar a cadeia de caracteres retornada, o nome da propriedade deve ser convertido em um valor com a propriedade **Value__**.

Por exemplo, o script a seguir usa a propriedade **Value__**.

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

### <a name="filtering-by-event-id"></a>Filtragem por ID do evento

Para obter dados mais específicos, os resultados da consulta são filtrados por **ID do evento**. O **ID do evento** é referenciado na tabela de hash como o **ID** chave e o valor é um **ID de evento** específico. O **Visualizador de Eventos do Windows** exibe o **ID do evento**. Este exemplo usa o **ID do evento 1023**.

Atualize a tabela de hash e inclua o par **chave-valor** com a chave, **ID** e o valor **1023**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

### <a name="filtering-by-level"></a>Filtragem por nível

Para refinar ainda mais os resultados e incluir apenas os eventos de erros, use a chave **Nível**.
Embora seja um valor enumerado, o **Visualizador de Eventos do Windows** exibe o **Nível** como valores de cadeias de caracteres. Na tabela de hash, se você usar a chave **Nível** com um valor de cadeia de caracteres, será exibida uma mensagem de erro.

O **Nível** tem valores como **Erro**, **Aviso** ou **Informativo**. Use o seguinte comando para exibir os nomes das propriedades `StandardEventLevel`.

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventLevel] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventLevel

Name          MemberType Definition
----          ---------- ----------
Critical      Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Critical {get;}
Error         Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Error {get;}
Informational Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Informational {get;}
LogAlways     Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel LogAlways {get;}
Verbose       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Verbose {get;}
Warning       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Warning {get;}
```

Os valores enumerados estão documentados no **.NET Framework**. Para obter mais informações, confira [Enumeração de StandardEventKeywords](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).

Os nomes e valores enumerados de **Nível** são os seguintes:

| Nome           | Valor |
| -------------- | ----- |
| Verbose        |   5   |
| Informativo  |   4   |
| Aviso        |   3   |
| Erro do          |   2   |
| Crítico       |   1   |
| LogAlways      |   0   |

A tabela de hash para a consulta completa inclui a chave do **Nível** e o valor **2**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

#### <a name="level-static-property-in-enumeration-optional"></a>Propriedade estática de nível na enumeração (opcional)

A chave do **Nível** é enumerada, mas você pode usar um nome de propriedade estático na consulta da tabela de hash.
Em vez de usar a cadeia de caracteres retornada, o nome da propriedade deve ser convertido em um valor com a propriedade **Value__**.

Por exemplo, o script a seguir usa a propriedade **Value__**.

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventLevel]::Informational
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=$C.Value__
}
```