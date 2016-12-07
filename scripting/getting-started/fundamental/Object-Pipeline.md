---
title: Pipeline de objeto
ms.date: 2016-05-11
keywords: PowerShell, cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 523d8ae4-d743-47a4-b79a-806130ca688a
ms.openlocfilehash: 570805d6ceb4613f0efc8095f08ce79d90514f62
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="object-pipeline"></a>Pipeline de objeto
Pipelines atuam como uma série de segmentos conectados do pipe. Itens que se movem pelo pipeline passam por cada segmento. Para criar um pipeline no Windows PowerShell, você conectar comandos com o operador de barra vertical "|". A saída de cada comando é usada como entrada para o próximo comando.

Pipelines são possivelmente o conceito mais valioso usado nas interfaces de linha de comando. Quando usados corretamente, os pipelines não apenas reduzem o esforço envolvido no fornecimento de comandos complexos, mas também tornam mais fácil ver o fluxo de trabalho nos comandos. Uma característica útil relacionada aos pipelines é que, como eles operam em cada item separadamente, você não precisa modificá-las com base em se terá zero, um ou muitos itens no pipeline. Além disso, cada comando em um pipeline (chamado de um elemento de pipeline) geralmente passa sua saída para o próximo comando no item a item do pipeline. Isso geralmente reduz a demanda de recursos de comandos complexos e permite que você comece obtendo saída imediatamente.

Neste capítulo, descreveremos como o pipeline do Windows PowerShell difere de pipelines dos shells mais populares e demonstraremos algumas ferramentas básicas que você pode usar para ajudar controlar a saída do pipeline, bem como para ver como o pipeline funciona.

