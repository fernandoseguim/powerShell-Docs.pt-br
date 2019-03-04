---
title: Como adicionar um retorno de valores para um tópico de ajuda | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52ab737-753c-4d04-8af7-758d5c805e18
caps.latest.revision: 7
ms.openlocfilehash: b21811e5a5a819c3d5c4a55fcbe685a84819b71d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859432"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>Como adicionar valores retornados a um tópico de ajuda do cmdlet

Esta seção descreve como adicionar uma seção de SAÍDAS para um tópico de Ajuda do cmdlet Windows PowerShell®. A seção de SAÍDAS lista as classes do .NET de objetos que o cmdlet retorna ou passa pelo pipeline.

Não há nenhum limite para o número de classes que podem ser adicionados à seção de SAÍDAS. Os tipos de retorno de um cmdlet são incluídos em uma \<returnValues: comando > nó, com cada classe entre um \<returnValue: comando > elemento.

Se um cmdlet não gera nenhuma saída, use esta seção para indicar que não há nenhuma saída. Por exemplo, no lugar do nome de classe, escrever "None" e forneça uma breve explicação. Se o cmdlet gera saída condicionalmente, use esse nó para explicar as condições e descrever a saída condicional.

O esquema inclui dois \<maml:description > elementos em cada \<returnValue: comando > elemento. No entanto, o `Get-Help` cmdlet exibe somente o conteúdo do \<returnValue: comando > /\<maml:description > elemento.

A partir do Windows PowerShell 3.0, o `Get-Help` cmdlet exibe o conteúdo do \<NavigationLink > elemento. Esse elemento permite direcionar os usuários para tópicos que descrevem a classe do .NET.

O XML a seguir mostra o \<maml:returnValues > nó.

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> Class Name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
       <maml:para> Brief description <maml:para>

</maml:description>
  </command: returnValue>
</command: returnValues>
```

O XML a seguir mostra um exemplo de como usar o \<maml:returnValues > nó para documentar um tipo de saída.

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```



