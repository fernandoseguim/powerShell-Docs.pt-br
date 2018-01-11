---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: galeria,powershell,cmdlet,psgallery
title: psgallery_items_tab
ms.openlocfilehash: 8704091542de5c19817ab0b4f77fd98987084b5d
ms.sourcegitcommit: 1a0a0928c1e3cae4e8df8d79b0737bd7ed6b4e47
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="items-tab"></a>Guia Itens

A [guia Itens](https://www.powershellgallery.com/items) exibe todos os itens disponíveis na Galeria do PowerShell.

Há várias maneiras de filtrar, classificar e pesquisar os itens.
Para ver mais detalhes sobre um item específico, clique no item.

## <a name="filter-by"></a>Filtrar Por

O menu suspenso em "Filtrar Por" permite aos usuários filtrar os resultados por:
* Incluir pré-lançamento
* Apenas estável

Para saber mais sobre itens de "pré-lançamento" e "estáveis", confira o artigo [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) (Controle de versão de pré-lançamento adicionado ao PowerShellGet e à Galeria do PowerShell), no blog da equipe do PowerShell.

Com as caixas de seleção no menu suspenso, os usuários podem filtrar os resultados por:
* Tipos de item
  - Módulo
  - script
* Categorias
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
* Popularidade – a popularidade é determinada pela Contagem de Downloads
* A a Z – em ordem alfabética por nome do item
* Recentes – os itens aparecem na ordem da data de publicação

## <a name="search-box"></a>Caixa de Pesquisa

A Caixa de Pesquisa permite que os usuários pesquisem itens por palavras-chave.
Para saber mais, confira [Sintaxe de Pesquisa da Galeria](psgallery_search_syntax.md).
