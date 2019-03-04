---
title: Como adicionar Links relacionados a um tópico de ajuda | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5aadb730-4eb7-4936-b8df-3b0c0ca04fd5
caps.latest.revision: 5
ms.openlocfilehash: aa46cbc5bfcfdfec9fcf9d2581ff641baa532860
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855392"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>Como adicionar links relacionados a um tópico de ajuda do cmdlet

Esta seção descreve como adicionar referências a outros tipos de conteúdo que está relacionado a um tópico de ajuda Windows PowerShell®. Como essas referências são exibidos em uma janela de comando, elas não vinculam diretamente para o conteúdo referenciado.

Nos tópicos da Ajuda de cmdlet estão incluídos no Windows PowerShell®, esses links de referência outros cmdlets, conteúdo conceitual ("About _") e outros documentos e arquivos de Ajuda que não estão relacionados ao Windows PowerShell®.

O XML a seguir mostra como adicionar um nó de RelatedLinks que contém duas referências para tópicos relacionados.

```xml
<maml:relatedLinks>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
</ maml:relatedLinks >
```



