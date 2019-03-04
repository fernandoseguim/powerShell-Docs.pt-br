---
title: Como adicionar um, consulte também seção um tópico de Ajuda do provedor | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858342"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>Como adicionar uma seção “veja também” a um tópico de ajuda do provedor

Esta seção explica como popular o **Consulte também** seção de um tópico de Ajuda do provedor.

O **Consulte também** seção consiste em uma lista de tópicos relacionados ao provedor ou pode ajudar o usuário a entender melhor e usar o provedor. A lista de tópicos pode incluir a Ajuda do cmdlet, Ajuda do provedor e tópicos de Ajuda no Windows PowerShell ("sobre"). Ele também pode incluir referências a livros, papel e tópicos online, incluindo uma versão online do tópico da Ajuda de provedor atual.

Ao fazer referência a tópicos online, forneça o URI ou um termo de pesquisa em texto sem formatação. O `Get-Help` cmdlet não vincular ou redirecionar para qualquer um dos tópicos na lista. Além disso, o `Online` parâmetro do `Get-Help` cmdlet não funciona com a Ajuda do provedor.

A seção Consulte também é criada a partir de `RelatedLinks` elemento e as marcas que ele contém. O XML a seguir mostra como adicionar as marcas.

### <a name="to-add-see-also-topics"></a>Para adicionar tópicos "Consulte também"

1. No *AssemblyName*help.xml. dll do arquivo, dentro de `providerHelp` elemento, adicionar um `RelatedLinks` elemento. O `RelatedLinks` elemento deve ser o último elemento no `providerHelp` elemento. Apenas um `RelatedLinks` elemento é permitido em cada tópico de Ajuda do provedor.

   Por exemplo:

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. Para cada tópico na **Consulte também** seção, dentro de `RelatedLinks` elemento, adicionar um `navigationLink` elemento. Em seguida, dentro de cada `navigationLink` elemento, adicione uma `linkText` e um elemento `uri` elemento. Se você não estiver usando o `uri` elemento, você pode adicioná-lo como um elemento vazio (\<uri / >).

   Por exemplo:

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> </linkText>
                <uri> </uri>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```

3. Digite o nome do tópico entre o `linkText` marcas. Se você estiver fornecendo um URI, digite-a entre o `uri` marcas. Para indicar a versão online do tópico de ajuda de provedor atual, entre o `linkText` marcas, tipo de "versão Online:" em vez do nome do tópico. Normalmente, a "versão Online:" link é o primeiro tópico na lista de tópico Consulte também.

   O exemplo a seguir incluem três tópicos Consulte também. O primeiro consulte a versão online do tópico atual. O segundo refere-se a um tópico de ajuda de cmdlet do Windows PowerShell. O terceiro refere-se para outro tópico on-line.

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> Online version: </linkText>
                <uri>http://www.fabrikam.com/help/myFunction.htm</uri>
            </navigationLink>
            <navigationLink>
                <linkText> about_functions </linkText>
                <uri/>
            </navigationLink>
            <navigationLink>
                <linkText> Windows PowerShell Getting Started Guide </linkText>
                <uri>http://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```