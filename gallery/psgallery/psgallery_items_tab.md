---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet, galeria
ms.date: 2016-10-14
contributor: manikb
title: psgallery_items_tab
ms.technology: powershell
ms.openlocfilehash: 32f28df7318472f34f79c61f19f33016cf73f517
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
<a name="items-tab"></a>Guia Itens
==========

A Guia Itens exibe todos os itens disponíveis na Galeria do PowerShell.

Para ver somente os Módulos na Galeria do PowerShell, clique em Módulos no menu suspenso da Guia Itens.  De forma semelhante, para ver somente os Scripts na Galeria do PowerShell, clique em Scripts no menu suspenso da Guia Itens.  

Para ver mais detalhes sobre um item específico, clique no item.

Há várias maneiras de classificar os itens:

##<a name="filter-by"></a>Filtrar Por##
A seção Filtrar Por permite que os usuários filtrem os resultados por:
* Tipo de Item:
    * Módulos
    * Scripts
* Categoria:
    * Cmdlet
    * Recurso de DSC
    * Função
    * Fluxo de Trabalho

Observação: os filtros são inclusivos.  
Exemplo: um item que contém Cmdlets e Funções será exibido se um Cmdlet ou Função (ou ambos) for selecionada.  Se nenhum dos dois for selecionado, o item não será exibido.  
De forma semelhante, se todas as categorias forem selecionadas, apenas itens que contêm uma dessas categorias serão exibidos. **Itens que não pertencem a nenhuma dessas categorias não serão exibidos.**

##<a name="sort-by"></a>Classificar Por## 
O menu suspenso Classificar Por permite aos usuários classificar os resultados por:
* Popularidade – a popularidade é determinada pela Contagem de Download.
* A-Z – em ordem alfabética por nome do item.
* Recentes – os itens aparecem na ordem da data de publicação.


##<a name="search-box"></a>Caixa de Pesquisa##
A Caixa de Pesquisa permite que os usuários pesquisem itens por palavras-chave.  
Consulte [Sintaxe de Pesquisa](./psgallery_search_syntax.md) para obter mais detalhes.

