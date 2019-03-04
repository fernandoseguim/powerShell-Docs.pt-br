---
title: Como adicionar tipos de entrada para um tópico de ajuda | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: f213605dda0132051d983f8608515325e815c455
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860802"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>Como adicionar tipos de entrada a um tópico de ajuda do cmdlet

Esta seção descreve como adicionar uma seção de ENTRADAS para um tópico de Ajuda do cmdlet Windows PowerShell®. A seção de ENTRADAS lista as classes do .NET de objetos que o cmdlet aceita como entrada do pipeline, por valor ou pelo nome da propriedade.

Não há nenhum limite para o número de classes que podem ser adicionados a uma seção de ENTRADAS. Os tipos de entrada são colocados em um \<inputTypes: comando > nó, com cada classe entre um \<inputType: comando > elemento.

O esquema inclui dois \<maml:description > elementos em cada \<inputType: comando > elemento. No entanto, o `Get-Help` cmdlet exibe somente o conteúdo do \<comando: tipo de entrada > /\<maml:description >) elemento.

A partir do Windows PowerShell 3.0, o `Get-Help` cmdlet exibe o conteúdo do \<NavigationLink > elemento. Esse elemento permite direcionar os usuários para tópicos que descrevem a classe do .NET.

O XML a seguir mostra o \<maml:inputTypes > nó.

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> Class name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Brief description </maml:para>
    </maml:description>
  </command:inputType>
</command:inputTypes>
```

O XML a seguir mostra um exemplo de como usar o \<maml:inputTypes > nó para documentar um tipo de entrada.

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```