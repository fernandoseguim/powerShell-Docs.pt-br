---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Chamando métodos do recurso DSC diretamente"
ms.openlocfilehash: ab00e66d526eda244500a41e450c56b0151274ee
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
<a id="calling-dsc-resource-methods-directly" class="xliff"></a>
# Chamando métodos do recurso DSC diretamente

>Aplica-se a: Windows PowerShell 5.0

Você pode usar o cmdlet [Invoke-DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx) para chamar diretamente as funções ou os métodos de um recurso DSC (As funções **Get-TargetResource**, **Set-TargetResource** e **Test-TargetResource** de um recurso baseado em MOF ou os métodos **Get**, **Set** e **Test** de um recurso baseado em classe). Isso pode ser usado por terceiros que querem usar recursos DSC, ou como uma ferramenta útil ao desenvolver recursos. 

Geralmente, esse cmdlet é usado em combinação com uma propriedade de metaconfiguração `refreshMode = 'Disabled'`, mas pode ser usado, independentemente do **refreshMode** para o qual está definido.

Ao chamar o cmdlet **Invoke-DscResource**, você especifica qual método ou função chamar usando o parâmetro **Method**. Especifique as propriedades do recurso passando uma tabela de hash como o valor do parâmetro **Property**.

A seguir, exemplos de chamada direta aos métodos do recurso:

<a id="ensure-a-file-is-present" class="xliff"></a>
## Certificar-se de que um arquivo está presente

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

<a id="test-that-a-file-is-present" class="xliff"></a>
## Testar se um arquivo está presente

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

<a id="get-the-contents-of-file" class="xliff"></a>
## Obter o conteúdo do arquivo

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

>**Observação:** não é permitido chamar diretamente métodos de recurso de composição. Em vez disso, chame os métodos de recursos subjacentes que compõem o recurso de composição.

<a id="see-also" class="xliff"></a>
## Consulte Também
- [Escrevendo um recurso personalizado de DSC com MOF](authoringResourceMOF.md) 
- [Escrevendo um recurso personalizado de DSC com classes do PowerShell](authoringResourceClass.md)
- [Depurando os recursos de DSC](debugResource.md)

