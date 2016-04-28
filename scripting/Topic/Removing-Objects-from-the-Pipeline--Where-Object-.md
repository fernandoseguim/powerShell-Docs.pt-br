---
title: Removendo objetos do pipeline (Where-Object)
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 01df8b22-2d22-4e2c-a18d-c004cd3cc284
---
# Removendo objetos do pipeline (Where-Object)
No Windows PowerShell, você muitas vezes gera e passa mais objetos em um pipeline do que deseja. Você pode especificar as propriedades de determinados objetos para exibição usando os cmdlets **Format**, mas isso não ajuda em problemas de remoção de objetos inteiros da exibição. Talvez você queira filtrar objetos antes do final de um pipeline para poder executar ações em apenas um subconjunto dos objetos gerados inicialmente.

O Windows PowerShell inclui um cmdlet **Where-Object** que permite testar cada objeto no pipeline e apenas passá-lo pelo pipeline caso ele atenda a uma certa condição de teste específica. Objetos que não passarem no teste são removidos do pipeline. Forneça a condição de teste como o valor do parâmetro **Where-ObjectFilterScript**.

### Executar testes simples com Where-Object
O valor de **FilterScript** é um *bloco de script* (um ou mais comandos do Windows PowerShell cercados por chaves {}) que é avaliado como verdadeiro ou falso. Esses blocos de script podem ser muito simples, mas criá-los requer conhecimento sobre outro conceito do Windows PowerShell, os operadores de comparação. Um operador de comparação compara os itens que aparecem em cada lado dela. Operadores de comparação começam com um caractere “-” caracteres e são seguidos por um nome. Operadores de comparação básicos funcionam em praticamente qualquer tipo de objeto. Os operadores de comparação mais avançados podem funcionar apenas em texto ou matrizes.

> [!NOTE]
> Por padrão, ao trabalhar com texto, os operadores de comparação do Windows PowerShell não diferenciam maiúsculas de minúsculas.

Devido a considerações de análise, símbolos como <, > e = não são usados como operadores de comparação. Em vez disso, os operadores de comparação são compostos por letras. Os operadores de comparação básicos estão listados na tabela a seguir.

|Operador de Comparação|Significado|Exemplo (returna true)|
|-----------------------|-----------|--------------------------|
|-eq|é igual a|1 -eq 1|
|-ne|Não é igual a|1 -ne 2|
|-lt|É menor que|1 -lt 2|
|-le|É menor ou igual a|1 -le 2|
|-gt|É maior que|2 -gt 1|
|-ge|É maior ou igual a|2 -ge 1|
|-like|É como (curinga de comparação para texto)|"file.doc" -like "f*.do?"|
|-notlike|Não é como (curinga de comparação para texto)|"file.doc" -notlike "p*.doc"|
|-contains|Contém|1,2,3 -contains 1|
|-notcontains|Não contém|1,2,3 -notcontains 4|

Blocos de script Where-Object usam a variável especial “$_” para fazer referência ao objeto atual no pipeline. Veja um exemplo de como isso funciona. Se tiver uma lista de números e só quiser retornar aqueles inferiores a três, você poderá usar Where-Object para filtrar os números digitando:

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

### Filtragem com base nas propriedades de objeto
Como $_ refere-se ao objeto atual do pipeline, podemos acessar suas propriedades para nossos testes.

Por exemplo, podemos ver a classe Win32_SystemDriver no WMI. Pode haver centenas de drivers do sistema em um determinado sistema, mas você pode só estar interessado em um determinado conjunto de drivers do sistema, como aqueles que estão sendo executados. Se você usar Get-Member para exibir os membros de Win32_SystemDriver (**Get-WmiObject -Class Win32_SystemDriver | Get-Member -MemberType Property**), verá que a propriedade relevante é State e que ela tem um valor "Running" (Em execução) quando o driver está sendo executado. Você pode filtrar os drivers do sistema selecionando apenas aqueles em execução digitando:

```
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"}
```

Isso ainda produz uma longa lista. Você pode desejar filtrar para selecionar apenas os drivers definidos para iniciar automaticamente testando também o valor de StartMode:

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Auto"}

DisplayName : RAS Asynchronous Media Driver
Name        : AsyncMac
State       : Running
Status      : OK
Started     : True

DisplayName : Audio Stub Driver
Name        : audstub
State       : Running
Status      : OK
Started     : True
```

Isso nos fornece muitas informações que já não precisamos mais porque sabemos que os drivers estão sendo executados. Na verdade, a única informação que é provavelmente precisamos neste ponto é o nome e o nome de exibição. O comando a seguir inclui somente essas duas propriedades, resultando em uma saída muito mais simples:

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Manual"} | Format-Table -Property Name,DisplayName

Name                                    DisplayName
----                                    -----------
AsyncMac                                RAS Asynchronous Media Driver
Fdc                                     Floppy Disk Controller Driver
Flpydisk                                Floppy Disk Driver
Gpc                                     Generic Packet Classifier
IpNat                                   IP Network Address Translator
mouhid                                  Mouse HID Driver
MRxDAV                                  WebDav Client Redirector
mssmbios                                Microsoft System Management BIOS Driver
```

Há dois elementos Where-Object no comando acima, mas pode eles podem ser expressos em um único elemento Where-Object usando o operador lógico -and, desta forma:

```
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq "Running") -and ($_.StartMode -eq "Manual") } | Format-Table -Property Name,DisplayName
```

Os operadores lógicos padrão são listados na tabela a seguir.

|Operador Lógico|Significado|Exemplo (returna true)|
|--------------------|-----------|--------------------------|
|-and|E lógico; verdadeiro se ambos os lados forem verdadeiros|(1 -eq 1) -and (2 -eq 2)|
|-or|Ou lógico; verdadeiro se um dos lados for verdadeiro|(1 -eq 1) -or (1 -eq 2)|
|-not|Não lógico; inverte o verdadeiro e o falso|-not (1 -eq 2)|
|\!|Não lógico; inverte o verdadeiro e o falso|!(1 -eq 2)|



<!--HONumber=Apr16_HO1-->


