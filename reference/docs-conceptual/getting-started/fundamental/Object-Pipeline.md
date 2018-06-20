---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Pipeline de objeto
ms.assetid: 523d8ae4-d743-47a4-b79a-806130ca688a
ms.openlocfilehash: 6102ec6e8fbf38fdc2bc5fa9c583244ef639dec8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30948203"
---
# <a name="object-pipeline"></a>Pipeline de objeto
Pipelines atuam como uma série de segmentos conectados do pipe. Itens que se movem pelo pipeline passam por cada segmento. Para criar um pipeline no Windows PowerShell, você conectar comandos com o operador de barra vertical "|". A saída de cada comando é usada como entrada para o próximo comando.

Pipelines são possivelmente o conceito mais valioso usado nas interfaces de linha de comando. Quando usados corretamente, os pipelines não apenas reduzem o esforço envolvido no fornecimento de comandos complexos, mas também tornam mais fácil ver o fluxo de trabalho nos comandos. Uma característica útil relacionada aos pipelines é que, como eles operam em cada item separadamente, você não precisa modificá-las com base em se terá zero, um ou muitos itens no pipeline. Além disso, cada comando em um pipeline (chamado de um elemento de pipeline) geralmente passa sua saída para o próximo comando no item a item do pipeline. Isso geralmente reduz a demanda de recursos de comandos complexos e permite que você comece obtendo saída imediatamente.

Neste capítulo, descreveremos como o pipeline do Windows PowerShell difere de pipelines dos shells mais populares e demonstraremos algumas ferramentas básicas que você pode usar para ajudar controlar a saída do pipeline, bem como para ver como o pipeline funciona.