---
title: Melhorias do Mecanismo do PowerShell no WMF 5.1
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: c8ad4ac8f3c7bf705114edc06c1b85846336dfff
ms.sourcegitcommit: f75fc25411ce6a768596d3438e385c43c4f0bf71
translationtype: HT
---
#<a name="powershell-engine-improvements"></a>Melhorias ao Mecanismo do PowerShell

As seguintes melhorias ao mecanismo principal do PowerShell foram implementadas no WMF 5.1:


## <a name="performance"></a>Desempenho ##

O desempenho melhorou em algumas áreas importantes:

- Inicialização
- O pipelining para cmdlets como ForEach-Object e Where-Object é aproximadamente 50% mais rápido 

Alguns exemplos de melhorias (os resultados podem variar dependendo do hardware): 

| Cenário | Tempo de 5,0 (ms) | Tempo de 5,1 (ms) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| Primeira execução do PowerShell: `powershell -command "Unknown-Command"` | 30000 | 13000 |
| Built do cache de análise de comando: `powershell -command "Unknown-Command"` | 7000 | 520 |
| <code>1..1000000 &#124; % { }</code> | 1400 | 750 |
  
> Observação: uma alteração relacionada à inicialização pode afetar alguns cenários sem suporte. 
> O PowerShell não lê mais os arquivos `$pshome\*.ps1xml` – esses arquivos foram convertidos para C# para evitar sobrecarga de arquivo e CPU do processamento dos arquivos XML. 
Os arquivos ainda existem para dar suporte à V2 lado a lado; portanto, se você alterar o conteúdo do arquivo, ele não terá qualquer efeito na V5, apenas na V2. 
Observe que alterar os conteúdos desses arquivos nunca foi um cenário com suporte.

Outra alteração visível é como o PowerShell armazena em cache os comandos exportados e outras informações para módulos instalados em um sistema. Antes, esse cache era armazenado no diretório `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`. No WMF 5.1, o cache é um único arquivo `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Veja [Cache de análise do módulo](scenarios-features.md#module-analysis-cache) para obter mais detalhes.
