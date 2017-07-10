---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
title: Melhorias do Mecanismo do PowerShell no WMF 5.1
ms.openlocfilehash: 6c8000ccfc59ab46de95dc4f67161e12a5a41199
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
<a id="powershell-engine-improvements" class="xliff"></a>
#Melhorias ao Mecanismo do PowerShell

As seguintes melhorias ao mecanismo principal do PowerShell foram implementadas no WMF 5.1:


<a id="performance" class="xliff"></a>
## Desempenho ##

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

