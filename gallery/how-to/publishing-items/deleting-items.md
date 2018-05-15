---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galeria,powershell,cmdlet,psgallery
title: Excluindo itens
ms.openlocfilehash: 5af66c5b7edf8f0d7049a98ed4dd10b13d4e9471
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="deleting-items"></a>Excluindo itens

A Galeria do PowerShell não dá suporte à exclusão permanente de itens, porque isso interromperia qualquer usuário que dependesse da disponibilidade desses itens.

Em vez disso, a Galeria de PowerShell dá suporte a uma maneira de “remover um item da lista”, que pode ser feito na página de gerenciamento dos itens no site.
Quando um item é removido da lista, ele não aparece mais na pesquisa e em nenhuma listagem de itens, tanto na Galeria do PowerShell quanto por meio dos comandos PowerShellGet.
No entanto, ele permanece disponível para download, pela especificação da versão exata, o que permite que os scripts automatizados continuem funcionando.

Se você estiver em uma situação excepcional em que acredita que um de seus itens precise ser excluído, isso poderá ser feito manualmente pela equipe da Galeria do PowerShell.
Por exemplo, se houver um problema de violação de direitos autorais ou conteúdo potencialmente perigoso, isso poderá ser um motivo válido para excluí-lo.
Nesse caso, você deve enviar uma solicitação de suporte por meio da [Galeria do PowerShell] (http://www.PowerShellGallery.com)).