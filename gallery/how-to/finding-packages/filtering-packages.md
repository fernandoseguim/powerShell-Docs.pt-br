---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery
title: Filtrando resultados da pesquisa
ms.openlocfilehash: 13270a310613a974e1588a9f56d443a936cfebb8
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003657"
---
# <a name="filtering-search-results"></a>Filtrando resultados da pesquisa

A [guia Pacotes](https://www.powershellgallery.com/packages) exibe todos os pacotes disponíveis na Galeria do PowerShell.

Há várias maneiras de filtrar, classificar e pesquisar os pacotes.
Para ver mais detalhes sobre um pacote específico, clique nele.

## <a name="filter-by"></a>Filtrar Por

O menu suspenso em "Filtrar Por" permite aos usuários filtrar os resultados por:
- Incluir pré-lançamento
- Apenas estável

Para saber mais sobre itens de "pré-lançamento" e "estáveis", confira o artigo [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) (Controle de versão de pré-lançamento adicionado ao PowerShellGet e à Galeria do PowerShell), no blog da equipe do PowerShell.

Com as caixas de seleção no menu suspenso, os usuários podem filtrar os resultados por:
- Tipos de Pacote
  - Módulo
  - script
- Categorias
  - Cmdlet
  - Recurso de DSC
  - Função
  - Capacidade da função
  - Fluxo de Trabalho

Para ver somente módulos na Galeria do PowerShell, marque a opção Módulo nos Tipos de Pacote.
Da mesma forma, para ver somente scripts na Galeria do PowerShell, marque a opção Script nos Tipos de Pacote.

> [!NOTE]
> Os filtros são inclusivos.
> Exemplo: um pacote que contém cmdlets e funções será exibido se Cmdlet ou Função (ou ambos) estiverem marcados.
> Se nenhum dos dois for selecionado, o pacote não será exibido.
> De forma semelhante, se todas as categorias forem selecionadas, apenas pacotes que contêm uma dessas categorias serão exibidos.
> **Pacotes que não pertencem a nenhuma dessas categorias não serão exibidos.**

## <a name="sort-by"></a>Classificar Por

O menu suspenso Classificar Por permite aos usuários classificar os resultados por:
- Popularidade – a popularidade é determinada pela Contagem de Downloads
- A a Z – em ordem alfabética por nome do pacote
- Recentes – os pacotes aparecem na ordem da data de publicação

## <a name="search-box"></a>Caixa de Pesquisa

A Caixa de Pesquisa permite que os usuários pesquisem pacotes por palavras-chave.
Para saber mais, confira [Sintaxe de Pesquisa da Galeria](search-syntax.md).
