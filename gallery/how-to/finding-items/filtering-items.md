---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery
title: Filtrando resultados da pesquisa
ms.openlocfilehash: eafbc993a37eaee7413102ef9d669a6b07d6ff6e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188801"
---
# <a name="filtering-search-results"></a>Filtrando resultados da pesquisa

A [guia Itens](https://www.powershellgallery.com/items) exibe todos os itens disponíveis na Galeria do PowerShell.

Há várias maneiras de filtrar, classificar e pesquisar os itens.
Para ver mais detalhes sobre um item específico, clique no item.

## <a name="filter-by"></a>Filtrar Por

O menu suspenso em "Filtrar Por" permite aos usuários filtrar os resultados por:
- Incluir pré-lançamento
- Apenas estável

Para saber mais sobre itens de "pré-lançamento" e "estáveis", confira o artigo [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) (Controle de versão de pré-lançamento adicionado ao PowerShellGet e à Galeria do PowerShell), no blog da equipe do PowerShell.

Com as caixas de seleção no menu suspenso, os usuários podem filtrar os resultados por:
- Tipos de item
  - Módulo
  - script
- Categorias
  - Cmdlet
  - Recurso de DSC
  - Função
  - Capacidade da função
  - Fluxo de Trabalho

Para ver somente módulos na Galeria do PowerShell, marque a opção Módulo nos Tipos de item.
Da mesma forma, para ver somente scripts na Galeria do PowerShell, marque a opção Script nos Tipos de item.

> [!NOTE]
> Os filtros são inclusivos.
> Exemplo: um item que contém cmdlets e funções será exibido se Cmdlet ou Função (ou ambos) estiverem marcados.
> Se nenhum dos dois for selecionado, o item não será exibido.
> De forma semelhante, se todas as categorias forem selecionadas, apenas itens que contêm uma dessas categorias serão exibidos.
> **Itens que não pertencem a nenhuma dessas categorias não serão exibidos.**

## <a name="sort-by"></a>Classificar Por

O menu suspenso Classificar Por permite aos usuários classificar os resultados por:
- Popularidade – a popularidade é determinada pela Contagem de Downloads
- A a Z – em ordem alfabética por nome do item
- Recentes – os itens aparecem na ordem da data de publicação

## <a name="search-box"></a>Caixa de Pesquisa

A Caixa de Pesquisa permite que os usuários pesquisem itens por palavras-chave.
Para saber mais, confira [Sintaxe de Pesquisa da Galeria](search-syntax.md).