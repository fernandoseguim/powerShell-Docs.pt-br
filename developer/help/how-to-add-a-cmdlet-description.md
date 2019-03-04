---
title: Como adicionar uma descrição do Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862592"
---
# <a name="how-to-add-a-cmdlet-description"></a>Como adicionar uma descrição do cmdlet

Esta seção descreve como adicionar conteúdo que é exibido na seção de descrição do cmdlet Help. No arquivo de Ajuda, esse conteúdo é adicionado para o nó de comando para cada cmdlet.

> [!NOTE]
> Para obter uma visão completa de um arquivo de Ajuda, abra um dos arquivos dll Help.xml localizado no diretório de instalação do Windows PowerShell. Por exemplo, o arquivo de Microsoft.PowerShell.Commands.Management.dll Help.xml contém conteúdo para vários dos cmdlets do Windows PowerShell.

### <a name="to-add-a-description"></a>Para adicionar uma descrição

- Comece explicando os recursos básicos do cmdlet em mais detalhes. Em muitos casos, você pode explicar os termos usados no nome do cmdlet e ilustrar conceitos familiarizados com um exemplo. Por exemplo, se o cmdlet acrescenta dados a um arquivo, explique que ele adiciona dados ao final de um arquivo existente.

- Para localizar todos os recursos do cmdlet, examine a lista de parâmetros. Descrever a função primária do cmdlet e, em seguida, incluir outras funções e recursos. Por exemplo, se a função principal do cmdlet é alterar uma propriedade, mas o cmdlet pode alterar todas as propriedades, que isso na descrição detalhada. Se os parâmetros do cmdlet permitem que os usuários solicitam informações de maneiras diferentes, explique-lo.

- Inclua informações sobre as maneiras que os usuários podem usar o cmdlet, além do óbvio usa. Por exemplo, você pode usar o objeto que o `Get-Host` cmdlet recupera para alterar a cor do texto na janela de comando do Windows PowerShell.

  Exemplo:  "O `Get-Acl` cmdlet obtém os objetos que representam o descritor de segurança de um arquivo ou recurso. O descritor de segurança contém as listas de controle de acesso (ACLs) do recurso. A ACL especifica as permissões que os usuários e grupos de usuários têm acesso ao recurso."

- A descrição detalhada deve descrever o cmdlet, mas ele não deve descrever os conceitos que usa o cmdlet. Colocar definições de conceito em observações adicionais.

## <a name="see-also"></a>Consulte Também

[SDK do Windows PowerShell](../windows-powershell-reference.md)
