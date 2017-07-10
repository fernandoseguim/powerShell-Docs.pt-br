---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
title: "Correções de Bug no WMF 5.1"
ms.openlocfilehash: 137095f50f9f926d3488ff9c1ce8270ddbda63eb
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
<a id="bug-fixes-in-wmf-51" class="xliff"></a>
# Correções de bug no WMF 5.1#

<a id="bug-fixes" class="xliff"></a>
## Correções de bug ##

Os seguintes bugs importantes foram corrigidos no WMF 5.1:

<a id="module-auto-discovery-fully-honors-envpsmodulepath" class="xliff"></a>
### A descoberta automática do módulo honra totalmente `$env:PSModulePath` ###

A descoberta automática do módulo (carregando módulos automaticamente sem um Import-Module explícito ao chamar um comando) foi introduzida no WMF 3. Quando introduzido, o PowerShell verificava comandos no `$PSHome\Modules` antes de usar `$env:PSModulePath`.

O WMF 5.1 altera esse comportamento para honrar `$env:PSModulePath` completamente. Isso permite que um módulo de autoria do usuário que define comandos fornecidos pelo PowerShell (por exemplo, `Get-ChildItem`) seja carregado automaticamente, substituindo corretamente o comando interno.

<a id="file-redirection-no-longer-hard-codes--encoding-unicode" class="xliff"></a>
### Redirecionamento de arquivos não embute mais `-Encoding Unicode` ###

Em versões anteriores do PowerShell, era impossível controlar a codificação do arquivo usada pelo operador de redirecionamento de arquivo, por exemplo, `Get-ChildItem > out.txt`, porque o PowerShell adicionava `-Encoding Unicode`.

Do WMF 5.1 em diante, agora é possível alterar a codificação do arquivo de redirecionamento configurando `$PSDefaultParameterValues`:

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

<a id="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo" class="xliff"></a>
### Corrigida uma regressão no acesso a membros do `System.Reflection.TypeInfo` ###

Uma regressão introduzida no WMF 5.0 se rompeu ao acessar membros de `System.Reflection.RuntimeType`, por exemplo, `[int].ImplementedInterfaces`.
Esse bug foi corrigido no WMF 5.1.


<a id="fixed-some-issues-with-com-objects" class="xliff"></a>
### Corrigidos alguns problemas com objetos COM ###

O WMF 5.0 introduziu um novo associador de COM para chamar métodos em objetos COM e o acesso às propriedades de objetos COM. Esse novo associador melhorou consideravelmente o desempenho, mas também introduziu alguns bugs que foram corrigidos no WMF 5.1.

<a id="argument-conversions-were-not-always-performed-correctly" class="xliff"></a>
#### Conversões de argumento não eram sempre executadas corretamente ####

No exemplo a seguir:

```
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

O método SendKeys espera uma cadeia de caracteres, mas o PowerShell não converteu o caractere para uma cadeia de caracteres, adiando a conversão para IDispatch::Invoke, que usa VariantChangeType para fazer a conversão, que, neste exemplo, resultou em enviar as chaves “1”, “7” e “3”, em vez da chave Volume.Mute esperada.

<a id="enumerable-com-objects-not-always-handled-correctly" class="xliff"></a>
#### Objetos COM enumeráveis nem sempre eram tratados corretamente ####

O PowerShell normalmente enumera a maioria dos objetos enumeráveis, mas uma regressão introduzida no WMF 5.0 impedia a enumeração de objetos COM que implementam IEnumerable.  Por exemplo:

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

No exemplo acima, o WMF 5.0 gravou incorretamente Scripting.Dictionary no pipeline, em vez de enumerar os pares chave-valor.

Esta alteração também aborda o [problema 1752224 no Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)

<a id="ordered-was-not-allowed-inside-classes" class="xliff"></a>
### `[ordered]` não era permitido dentro de classes ###

O WMF 5.0 introduziu classes com validação de literais de tipo usados em classes.  
`[ordered]` parece um literal de tipo, mas não é um tipo .NET verdadeiro. O WMF 5.0 relatou incorretamente um erro no `[ordered]` dentro de uma classe:

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


<a id="help-on-about-topics-with-multiple-versions-does-not-work" class="xliff"></a>
### A ajuda em tópicos “Sobre” com várias versões não funciona ###

Antes do WMF 5.1, se houvesse várias versões de um módulo instaladas e elas compartilhassem um tópico de ajuda, por exemplo, about_PSReadline, `help about_PSReadline` retornaria vários tópicos sem uma maneira óbvia de exibir a ajuda real.

O WMF 5.1 corrige isso retornando a ajuda para a versão mais recente do tópico.

`Get-Help` não oferece uma maneira de especificar para qual versão você quer obter ajuda. Para solucionar esse problema, navegue até o diretório de módulos e exibir a ajuda diretamente com uma ferramenta como seu editor favorito. 

<a id="powershellexe-reading-from-stdin-stopped-working" class="xliff"></a>
### A leitura do powershell.exe do STDIN parou de funcionar

Os clientes usam o `powershell -command -` de aplicativos nativos para executar o PowerShell passando o script por meio do STDIN, mas infelizmente isso não está funcionando devido a outras alterações no host do console.

https://windowsserver.uservoice.com/forums/301869-powershell/suggestions/15854689-powershell-exe-command-is-broken-on-windows-10

<a id="powershellexe-creates-spike-in-cpu-usage-on-startup" class="xliff"></a>
### O powershell.exe cria um pico no uso da CPU durante a inicialização

O PowerShell usa uma consulta de WMI para verificar se ele foi iniciado por meio de Política de Grupo para evitar um atraso no logon.
A consulta de WMI acaba injetando o tzres.mui.dll em cada processo no sistema, uma vez que a classe Win32_Process de WMI tenta recuperar informações do fuso horário local.
Isso resulta em um grande aumento no uso da CPU no wmiprvse (o host de provedor de WMI).
A correção é usar chamadas de API do Win32 para obter as mesmas informações em vez de usar o WMI.

