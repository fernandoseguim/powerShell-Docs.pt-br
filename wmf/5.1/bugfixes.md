---
title: "Correções de Bug no WMF 5.1"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: 09316fef0594697a60a1bd4acabf39588f75edc2
ms.sourcegitcommit: f75fc25411ce6a768596d3438e385c43c4f0bf71
translationtype: HT
---
# <a name="bug-fixes-in-wmf-51"></a>Correções de Bug no WMF 5.1#

## <a name="bug-fixes"></a>Correções de bug ##

Os seguintes bugs importantes foram corrigidos no WMF 5.1:

### <a name="module-auto-discovery-fully-honors-envpsmodulepath"></a>A descoberta automática do módulo honra totalmente `$env:PSModulePath` ###

A descoberta automática do módulo (carregando módulos automaticamente sem um Import-Module explícito ao chamar um comando) foi introduzida no WMF 3. Quando introduzido, o PowerShell verificava comandos no `$PSHome\Modules` antes de usar `$env:PSModulePath`.

O WMF 5.1 altera esse comportamento para honrar `$env:PSModulePath` completamente. Isso permite que um módulo de autoria do usuário que define comandos fornecidos pelo PowerShell (por exemplo, `Get-ChildItem`) seja carregado automaticamente, substituindo corretamente o comando interno.

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a>Redirecionamento de arquivos não embute mais `-Encoding Unicode` ###

Em versões anteriores do PowerShell, era impossível controlar a codificação do arquivo usada pelo operador de redirecionamento de arquivo, por exemplo, `Get-ChildItem > out.txt`, porque o PowerShell adicionava `-Encoding Unicode`.

Do WMF 5.1 em diante, agora é possível alterar a codificação do arquivo de redirecionamento configurando `$PSDefaultParameterValues`:

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a>Corrigida uma regressão no acesso a membros do `System.Reflection.TypeInfo` ###

Uma regressão introduzida no WMF 5.0 se rompeu ao acessar membros de `System.Reflection.RuntimeType`, por exemplo, `[int].ImplementedInterfaces`.
Esse bug foi corrigido no WMF 5.1.


### <a name="fixed-some-issues-with-com-objects"></a>Corrigidos alguns problemas com objetos COM ###

O WMF 5.0 introduziu um novo associador de COM para chamar métodos em objetos COM e o acesso às propriedades de objetos COM. Esse novo associador melhorou consideravelmente o desempenho, mas também introduziu alguns bugs que foram corrigidos no WMF 5.1.

#### <a name="argument-conversions-were-not-always-performed-correctly"></a>Conversões de argumento não eram sempre executadas corretamente ####

No exemplo a seguir:

```
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

O método SendKeys espera uma cadeia de caracteres, mas o PowerShell não converteu o caractere para uma cadeia de caracteres, adiando a conversão para IDispatch::Invoke, que usa VariantChangeType para fazer a conversão, que, neste exemplo, resultou em enviar as chaves “1”, “7” e “3”, em vez da chave Volume.Mute esperada.

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a>Objetos COM enumeráveis nem sempre eram tratados corretamente ####

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

### <a name="ordered-was-not-allowed-inside-classes"></a>`[ordered]` não era permitido dentro de classes ###

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


### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a>A ajuda em tópicos “Sobre” com várias versões não funciona ###

Antes do WMF 5.1, se houvesse várias versões de um módulo instaladas e elas compartilhassem um tópico de ajuda, por exemplo, about_PSReadline, `help about_PSReadline` retornaria vários tópicos sem uma maneira óbvia de exibir a ajuda real.

O WMF 5.1 corrige isso retornando a ajuda para a versão mais recente do tópico.

`Get-Help` não oferece uma maneira de especificar para qual versão você quer obter ajuda. Para solucionar esse problema, navegue até o diretório de módulos e exibir a ajuda diretamente com uma ferramenta como seu editor favorito. 
