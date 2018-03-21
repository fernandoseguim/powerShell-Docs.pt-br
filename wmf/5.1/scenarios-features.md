---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
title: "Novos cenários e recursos no WMF 5.1"
ms.openlocfilehash: da3dfb2243c00e3faf637d3dbcb70016cfabb011
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="new-scenarios-and-features-in-wmf-51"></a>Novos cenários e recursos no WMF 5.1 #

> Observação: essas informações são preliminares e estão sujeitas a alteração.

## <a name="powershell-editions"></a>Edições do PowerShell ##
A partir da versão 5.1, o PowerShell está disponível em diferentes edições que denotam os vários conjuntos de recursos e compatibilidades de plataforma.

- **Desktop Edition:** criada no .NET Framework e oferece compatibilidade com scripts e módulos destinados a versões do PowerShell em execução em edições de superfície completa do Windows, como Server Core e Área de Trabalho do Windows.
- **Core Edition:** criada no .NET Core e oferece compatibilidade com scripts e módulos destinados a versões do PowerShell executando em edições de superfície reduzida do Windows, como o Nano Server e Windows IoT.

**Saiba mais sobre como usar as edições do PowerShell**
- [Determinar a edição em execução do PowerShell]()
- [Declarar a compatibilidade de um módulo para versões específicas do PowerShell]()
- [Filtrar resultados de Get-Module por CompatiblePSEditions]()
- [Impedir a execução do script, a menos que seja ele executado em uma edição compatível do PowerShell]()

## <a name="catalog-cmdlets"></a>Cmdlets de Catálogo  

Dois novos cmdlets foram adicionados no módulo [Microsoft.PowerShell.Security](https://technet.microsoft.com/library/hh847877.aspx); eles geram e validam os arquivos de catálogo do Windows.  

###<a name="new-filecatalog"></a>New-FileCatalog 
--------------------------------

New-FileCatalog cria um arquivo de catálogo do Windows para o conjunto de arquivos e pastas. Este arquivo de catálogo contém hashes para todos os arquivos nos caminhos especificados. Os usuários podem distribuir o conjunto de pastas juntamente com o arquivo de catálogo correspondente que representa essas pastas. Essas informações são úteis para validar se as alterações foram feitas nas pastas desde a hora de criação do catálogo.    

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
Há suporte para as versões 1 e 2 do catálogo. A versão 1 usa o algoritmo de hash SHA1 para criar hashes de arquivo; a versão 2 usa SHA256. Não há suporte para a versão 2 do catálogo no *Windows Server 2008 R2* ou no *Windows 7*. Você deve usar a versão 2 do catálogo no *Windows 8*, no *Windows Server 2012* e nos sistemas operacionais posteriores.  

![](../images/NewFileCatalog.jpg)

Isso cria o arquivo de catálogo. 

![](../images/CatalogFile1.jpg)  

![](../images/CatalogFile2.jpg) 

Para verificar a integridade do arquivo de catálogo (Pester.cat, no exemplo acima), assine-o usando o cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx).   


###<a name="test-filecatalog"></a>Test-FileCatalog 
--------------------------------

Test-FileCatalog valida o catálogo que representa um conjunto de pastas. 

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

Este cmdlet compara todos os hashes de arquivos e seus caminhos relativos encontrados no *catálogo* com aqueles no *disco*. Se detectar qualquer incompatibilidade entre os hashes e os caminhos de arquivo, o status será retornado como *ValidationFailed*. Os usuários podem recuperar todas essas informações usando o parâmetro *-Detailed*. Ele também exibe o status da assinatura do catálogo na propriedade *Signature*, que é equivalente a chamar o cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) no arquivo de catálogo. Os usuários também podem ignorar qualquer arquivo durante a validação usando o parâmetro *-FilesToSkip*. 


## <a name="module-analysis-cache"></a>Cache de análise do módulo ##
Do WMF 5.1 em diante, o PowerShell fornece controle sobre o arquivo que é usado para cache de dados sobre um módulo, como os comandos que exporta.

Por padrão, esse cache é armazenado no arquivo `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
O cache normalmente é lido na inicialização ao procurar um comando e é gravado em um thread em segundo plano em algum momento após a importação de um módulo.

Para alterar o local padrão do cache, defina a variável de ambiente `$env:PSModuleAnalysisCachePath` antes de iniciar o PowerShell. As alterações a esta variável de ambiente afetarão apenas processos filhos. O valor deve nomear um caminho completo (incluindo nome do arquivo) em que o PowerShell tenha permissão para criar e gravar arquivos. Para desabilitar o cache de arquivo, defina esse valor para um local inválido, por exemplo:

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

Isso define o caminho para um dispositivo inválido. Se o PowerShell não conseguir gravar no caminho, nenhum erro será retornado, mas você poderá ver relatórios de erro usando um rastreamento:

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Ao gravar o cache, o PowerShell verificará se há módulos que não existem mais para evitar um cache desnecessariamente grande.
Às vezes, essas verificações não são desejáveis, o que, nesse caso, você pode desativá-las configurando:

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

Definir essa variável de ambiente entrará em vigor imediatamente no processo atual.

##<a name="specifying-module-version"></a>Especificando a versão do módulo

No WMF 5.1, o `using module` comporta-se da mesma maneira que outras construções relacionadas ao módulo no PowerShell. Anteriormente, não era possível especificar uma versão de módulo específica; se houvesse várias versões presentes, isso resultaria em um erro.


No WMF 5.1:

* Você pode usar o [Construtor ModuleSpecification (tabela de hash)](https://msdn.microsoft.com/library/jj136290). Essa tabela de hash tem o mesmo formato que `Get-Module -FullyQualifiedName`.

**Exemplo:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

* Se houver várias versões do módulo, o PowerShell usará a **mesma lógica de resolução** que `Import-Module` e não retornará um erro – o mesmo comportamento que `Import-Module` e `Import-DscResource`.


##<a name="improvements-to-pester"></a>Melhorias no Pester
No WMF 5.1, a versão do Pester fornecida com o PowerShell foi atualizada do 3.3.5 para 3.4.0, com a adição da confirmação https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, que permite um comportamento melhor do Pester no Nano Server. 

Você pode revisar as alterações nas versões 3.3.5 a 3.4.0 inspecionando o arquivo ChangeLog.md em: https://github.com/pester/Pester/blob/master/CHANGELOG.md

