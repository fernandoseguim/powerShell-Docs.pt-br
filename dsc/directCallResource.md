---
title: "Chamando métodos do recurso DSC diretamente"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 1fe624c2532e44ed675762f3c141934fb4f0b60d

---

# Chamando métodos do recurso DSC diretamente

>Aplica-se a: Windows PowerShell 5.0

Você pode usar o cmdlet [Invoke-DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx) para chamar diretamente as funções ou os métodos de um recurso DSC (As funções **Get-TargetResource**, **Set-TargetResource** e **Test-TargetResource** de um recurso baseado em MOF ou os métodos **Get**, **Set** e **Test** de um recurso baseado em classe). Isso pode ser usado por terceiros que querem usar recursos DSC, ou como uma ferramenta útil ao desenvolver recursos. 

Geralmente, esse cmdlet é usado em combinação com uma propriedade de metaconfiguração `refreshMode = 'Disabled'`, mas pode ser usado, independentemente do **refreshMode** para o qual está definido.

Ao chamar o cmdlet **Invoke-DscResource**, você especifica qual método ou função chamar usando o parâmetro **Method**. Especifique as propriedades do recurso passando uma tabela de hash como o valor do parâmetro **Property**.

A seguir, exemplos de chamada direta aos métodos do recurso:

## Certificar-se de que um arquivo está presente

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## Testar se um arquivo está presente

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## Obter o conteúdo do arquivo

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

>**Observação:** não é permitido chamar diretamente métodos de recurso de composição. Em vez disso, chame os métodos de recursos subjacentes que compõem o recurso de composição.

## Consulte Também
- [Escrevendo um recurso personalizado de DSC com MOF](authoringResourceMOF.md) 
- [Escrevendo um recurso personalizado de DSC com classes do PowerShell](authoringResourceClass.md)
- [Depurando os recursos de DSC](debugResource.md)




<!--HONumber=Jun16_HO4-->


