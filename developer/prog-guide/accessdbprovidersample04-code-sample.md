---
title: Exemplo de código AccessDbProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: 43f01b9cd6af3ab6c26f88ee0c1e9269499b2bc3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853602"
---
# <a name="accessdbprovidersample04-code-sample"></a>Exemplo de código AccessDbProviderSample04

O código a seguir mostra a implementação do provedor do Windows PowerShell descrito em [criando um provedor de contêiner do Windows PowerShell](./creating-a-windows-powershell-container-provider.md). Esse provedor funciona em armazenamentos de dados de várias camadas. Para esse tipo de armazenamento de dados, do armazenamento de nível superior contém os itens de raiz e cada nível subsequente é conhecido como um nó de itens filho. Ao permitir que o usuário trabalhar em nós filho, um usuário pode interagir hierarquicamente por meio do armazenamento de dados.

## <a name="code-sample"></a>Exemplo de código

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>Consulte Também

[SDK do Windows PowerShell](../windows-powershell-reference.md)