---
title: Aprimoramentos do mecanismo do PowerShell
author: jasonsh
translationtype: Human Translation
ms.sourcegitcommit: 6813902aec214aee9ede27ff79dd291364e9f443
ms.openlocfilehash: f864850128f118704d7545b09110835ab1d51b8e

---

# Aprimoramentos do mecanismo do PowerShell #

Os seguintes aprimoramentos ao mecanismo principal do PowerShell foram implementados para o PowerShell 5.1:


## Desempenho ##

O desempenho melhorou em algumas áreas importantes:

1. Inicialização
2. O pipelining para cmdlets como ForEach-Object e Where-Object é aproximadamente 50% mais rápido 

Alguns exemplos de melhorias (os resultados podem variar dependendo de seu hardware): 

| Cenário | Tempo de 5,0 (ms) | Tempo de 5,1 (ms) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| Primeira execução do PowerShell: `powershell -command "Unknown-Command"` | 30000 | 13000 |
| Built do cache de análise de comando: `powershell -command "Unknown-Command"` | 7000 | 520 |
| <code>1..1000000 &#124; % { }</code> | 1400 | 750 |
  
Uma alteração relacionada à inicialização pode afetar alguns cenários (sem suporte). O PowerShell não lê mais os arquivos `$pshome\*.ps1xml` – esses arquivos foram convertidos para C# para evitar alguma sobrecarga de arquivo e CPU do processamento dos arquivos xml. Os arquivos ainda existem para dar suporte à V2 lado a lado; portanto, se você alterar o conteúdo do arquivo, ele não terá qualquer efeito na V5, apenas na V2. Observe que alterar os conteúdos desses arquivos nunca foi um cenário com suporte.

Outra alteração visível é como o PowerShell armazena em cache os comandos exportados e outras informações para módulos instalados em um sistema. Antes, esse cache era armazenado no diretório `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`. No WMF 5.1, o cache é um único arquivo `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Veja mais detalhes em [analysis_cache.md]().

Da versão 5.1 em diante, o PowerShell está disponível nas edições diferentes que denotam diferentes conjuntos de recursos e compatibilidade de plataforma.



## Correções de bug ##

Os seguintes bugs importantes foram corrigidos:

### A descoberta automática do módulo honra totalmente `$env:PSModulePath` ###

A descoberta automática do módulo (carregando módulos automaticamente sem um Import-Module explícito ao chamar um comando) foi introduzida no WMF3. Quando introduzido, o PowerShell verificava comandos no `$PSHome\Modules` antes de usar `$env:PSModulePath`.

O WMF 5.1 altera esse comportamento para honrar `$env:PSModulePath` completamente. Isso permite que um módulo de autoria do usuário que define comandos fornecidos pelo PowerShell (por exemplo, `Get-ChildItem`) seja carregado automaticamente, substituindo corretamente o comando interno.

### Redirecionamento de arquivos não embute mais `-Encoding Unicode` ###

Em versões anteriores do PowerShell, era impossível controlar a codificação do arquivo usada pelo operador de redirecionamento de arquivo, por exemplo, `get-childitem > out.txt`, porque o PowerShell adicionava `-Encoding Unicode`.

Do WMF 5.1 em diante, agora você pode alterar a codificação do arquivo de redirecionamento configurando `$PSDefaultParameterValues`, por exemplo,

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### Corrigida uma regressão no acesso a membros do `System.Reflection.TypeInfo` ###

Uma regressão introduzida no WMF5 se rompeu ao acessar membros de `System.Reflection.RuntimeType`, por exemplo, `[int].ImplementedInterfaces`.
Esse bug foi corrigido no WMF 5.1.


### Corrigidos alguns problemas com objetos COM ###

O WMF5 introduziu um novo associador de COM para chamar métodos em objetos COM e o acesso às propriedades de objetos COM.
Esse novo associador melhorou significativamente o desempenho, mas também introduziu alguns bugs que foram corrigidos no WMF 5.1.

#### Conversões de argumento não eram sempre executadas corretamente ####

No exemplo a seguir:

```
$obj = new-object -com wscript.shell
$obj.SendKeys([char]173)
```

O método SendKeys espera uma cadeia de caracteres, mas o PowerShell não converteu o caractere para uma cadeia de caracteres, adiando a conversão para IDispatch::Invoke, que usa VariantChangeType para fazer a conversão, que, neste exemplo, resultou em enviar as chaves “1”, “7” e “3”, em vez da chave Volume.Mute esperada.

#### Objetos COM enumeráveis nem sempre eram tratados corretamente ####

O PowerShell normalmente enumera a maioria dos objetos enumeráveis, mas uma regressão introduzida no WMF5 impedia a enumeração de objetos COM que implementam IEnumerable.  Por exemplo:

```
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

No exemplo acima, o WMF5 gravou incorretamente Scripting.Dictionary no pipeline, em vez de enumerar os pares de chave-valor.


### `[ordered]` não era permitido dentro de classes ###

O WMF5 introduziu classes com validação de literais de tipo usados em classes.  `[ordered]` parece um literal de tipo, mas não é um tipo .Net verdadeiro.  WMF5 relatou incorretamente um erro no `[ordered]` dentro de uma classe:

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### A ajuda em tópicos “Sobre” com várias versões não funciona ###

Antes do WMF 5.1, se houvesse várias versões de um módulo instaladas e se elas compartilhassem um tópico de ajuda, por exemplo, about_PSReadline, `help about_PSReadline` retornaria vários tópicos sem uma maneira óbvia de exibir a ajuda real.

O WMF 5.1 corrige isso retornando a ajuda para a versão mais recente do tópico.

Get-Help não oferece uma maneira de especificar para qual versão você deseja obter ajuda; a solução alternativa é navegar até o diretório de módulos e exibir a ajuda diretamente com uma ferramenta, como seu editor favorito. 



<!--HONumber=Jul16_HO2-->


