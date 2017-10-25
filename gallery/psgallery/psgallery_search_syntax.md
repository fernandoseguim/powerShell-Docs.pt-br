---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: galeria,powershell,cmdlet,psgallery
title: psgallery_search_syntax
ms.openlocfilehash: 409ae607557af760f9cec4e3c54f39e51b5fac18
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="gallery-search-syntax"></a>Sintaxe de pesquisa da Galeria

A Galeria do PowerShell oferece uma caixa de pesquisa de texto em que você pode usar palavras, frases e expressões de palavra-chave para refinar os resultados da pesquisa.

## <a name="search-by-keywords"></a>Pesquisa com palavras-chave

    dsc azure sql

A pesquisa fará seu melhor esforço para encontrar documentos relevantes contendo as três palavras-chave e retornar os documentos correspondentes.

## <a name="search-using-phrases-and-keywords"></a>Pesquisa usando frases e palavras-chave

    "azure sql" deployment

Inserir uma frase entre aspas ("") altera a pesquisa para procurar pela frase específica, em vez de palavras-chave separadas.
Documentos correspondentes normalmente devem conter exatamente a frase "azure sql", incluindo variações nas maiúsculas e minúsculas, como "Azure SQL" e geralmente também contêm a palavra “deployment".

## <a name="filtering-on-fields"></a>Filtrando pelos campos

Você pode pesquisar pela ID de um item específico (ou "Id" ou "id") ou por alguns outros campos prefixando os termos de pesquisa com o nome do campo.

Atualmente, os campos pesquisáveis são "Id", "Version", "Tags", "Author", "Owner", "Functions", "Cmdlets", "DscResources" e "PowerShellVersion".

[Qual é a diferença entre o título e a ID? ID é o nome que você usa no console. O título é mostrado na parte superior da página do item nos resultados da pesquisa.]

## <a name="examples"></a>Exemplos

    ID:"PSReadline"
    id:"AzureRM.Profile"

localiza itens com "PSReadline" ou "AzureRM.Profile" no campo de ID, respectivamente.

    Id:"AzureRM.Profile"

é outra maneira de localizar itens com "AzureRM.Profile" no campo de ID.

O filtro "Id" é correspondente a uma subcadeia, de modo que se pesquisar pelo seguinte:

    Id:"azure"
    
Você obterá resultados como "AzureRM.Profile" e "Azure.Storage".

Você também pode pesquisar por várias palavras-chave em um único campo. Ou misturar e combinar os campos.

    id:azure tags:intellisense
    id:azure id:storage

E você pode fazer pesquisas por frase:

    id:"azure.storage"


Para pesquisar todos os itens com a marca DSC.

    Tags:"DSC"

Para pesquisar todos os itens com a função especificada.

    Functions:"Update-AzureRM"

Para pesquisar todos os itens com o cmdlet especificado.
    
    Cmdlets:"Get-AzureRmEnvironment"

Para pesquisar todos os itens com o nome do Recurso de DCS especificado.

    DscResources:"xArchive"

Para pesquisar todos os itens com o PowerShellVersion especificado

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


Por fim, se você usar um campo para o qual não há suporte, como "commands", vamos ignorá-lo e pesquisar em todos os campos. Sendo assim, a seguinte consulta

    commands:blobs storage
    
É interpretada exatamente como esta consulta:

    blobs storage

