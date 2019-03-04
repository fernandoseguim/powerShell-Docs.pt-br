---
title: Como adicionar o nome do Cmdlet e a Sinopse a um tópico de ajuda | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861822"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a>Como adicionar a sinopse e o nome do cmdlet a um tópico de ajuda do cmdlet

Esta seção descreve como adicionar conteúdo que é exibido nas seções de nome e a Sinopse da Ajuda do cmdlet. No arquivo de Ajuda, esse conteúdo é adicionado para o nó de comando para cada cmdlet.

> [!NOTE]
> Para obter uma visão completa de um arquivo de Ajuda, abra um dos arquivos dll Help.xml localizado no diretório de instalação do Windows PowerShell. Por exemplo, o arquivo de Microsoft.PowerShell.Commands.Management.dll Help.xml contém conteúdo para vários dos cmdlets do Windows PowerShell.

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a>Para adicionar o nome do Cmdlet e uma sinopse

- O cmdlet Help pode exibir duas descrições para o cmdlet. A descrição a primeira é uma breve descrição que é conhecida como a Sinopse. A segunda descrição é uma descrição mais detalhada que é abordada [adicionando a descrição detalhada para um tópico de Ajuda do Cmdlet](./how-to-add-a-cmdlet-description.md). Ambas as essas descrições devem ser gravadas como um único parágrafo.

- Na Sinopse não se repetem o nome do cmdlet. Informando ao usuário que o cmdlet Get-Server obtém um servidor é breve, mas não informativos. Em vez disso, usar sinônimos e adicionar detalhes à descrição.

  Exemplo: "Obtém um objeto que representa um computador local ou remoto."

- Use verbos simples como "get", "criar" e "alterar" a Sinopse. Evite usar "set" porque é vaga e palavras bonitas como "modificam."

  Exemplo: "Obtém informações sobre a assinatura Authenticode em um arquivo".

- Gravar em voz ativa. Por exemplo, "usar o objeto TimeSpan..." é bem mais claro de "objeto TimeSpan pode ser usado para..."

- Evite o verbo "display" ao descrever os cmdlets que obter objetos. Embora o Windows PowerShell exibe dados de cmdlet, é importante apresentar a usuários o conceito de que o cmdlet retorna objetos do .NET Framework cujos dados podem não ser exibidos. Se você enfatizar a exibição, o usuário talvez não tenha percebido que o cmdlet pode ter retornado muitas outras propriedades e métodos úteis que não são exibidos.

## <a name="see-also"></a>Consulte Também

 [SDK do Windows PowerShell](../windows-powershell-reference.md)