---
title: Como adicionar anotações a um tópico de ajuda | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862262"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>Como adicionar notas a um tópico de ajuda do cmdlet

Esta seção descreve como adicionar uma seção de notas a um tópico de ajuda Windows PowerShell®. A seção Observações é usada para explicar os detalhes que não se encaixam facilmente em outras seções estruturadas, como uma explicação mais detalhada de um parâmetro. Esse conteúdo pode incluir comentários em como o cmdlet funciona com um provedor específico, alguns usos exclusivos, embora importantes, do cmdlet ou maneiras de evitar possíveis condições de erro.

Não há nenhum limite para o número de observações que você pode adicionar uma seção de anotações. Para cada nota, adicione um par de \<maml:alert > marcas para o \<maml:alertset > nó. O conteúdo de cada nota é adicionado em um conjunto de \<MAML: para > marcas. Espaço em branco de uso \<MAML: para > marcas para espaçamento.

O XML a seguir mostra um \<maml:alertset > nó com duas anotações. Observe que cada Observação tem um recurso opcional \<MAML: Title > marca (títulos podem ser usados para agrupar qualquer conjunto de \<maml:alert > marcas), e se cada Observação tem uma linha em branco após o conteúdo para espaçamento.

```xml
<maml:alertSet>
  <maml:title>title for Note 1</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
  <maml:title>title for Note 2</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
</maml:alertSet>
```



