---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery
title: Sintaxe de pesquisa da Galeria
ms.openlocfilehash: 9aadb6771c85845cc3fa05cb56f0194b060d1c1b
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003635"
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

Você pode pesquisar pela ID de um pacote específico (ou "Id" ou "id") ou por alguns outros campos, prefixando os termos de pesquisa com o nome do campo.

Atualmente, os campos pesquisáveis são "Id", "Version", "Tags", "Author", "Owner", "Functions", "Cmdlets", "DscResources" e "PowerShellVersion".

[Qual é a diferença entre o título e a ID? ID é o nome que você usa no console. O título é mostrado na parte superior da página do pacote nos resultados da pesquisa.]

## <a name="examples"></a>Exemplos

    ID:"PSReadline"
    id:"AzureRM.Profile"

localiza pacotes com "PSReadline" ou "AzureRM.Profile" no campo de ID, respectivamente.

    Id:"AzureRM.Profile"

é outra maneira de localizar pacotes com "AzureRM.Profile" no campo de ID.

O filtro "Id" é correspondente a uma subcadeia, de modo que se pesquisar pelo seguinte:

    Id:"azure"

Você obterá resultados como "AzureRM.Profile" e "Azure.Storage".

Você também pode pesquisar por várias palavras-chave em um único campo. Ou misturar e combinar os campos.

    id:azure tags:intellisense
    id:azure id:storage

E você pode fazer pesquisas por frase:

    id:"azure.storage"


Para pesquisar todos os pacotes com a marca DSC.

    Tags:"DSC"

Para pesquisar todos os pacotes com a função especificada.

    Functions:"Update-AzureRM"

Para pesquisar todos os pacotes com o cmdlet especificado.

    Cmdlets:"Get-AzureRmEnvironment"

Para pesquisar todos os pacotes com o nome do Recurso de DSC especificado.

    DscResources:"xArchive"

Para pesquisar todos os pacotes com o PowerShellVersion especificado

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


Por fim, se você usar um campo para o qual não há suporte, como "commands", vamos ignorá-lo e pesquisar em todos os campos. Sendo assim, a seguinte consulta

    commands:blobs storage

É interpretada exatamente como esta consulta:

    blobs storage
