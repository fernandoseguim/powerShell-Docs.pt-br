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
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="47be8-102">Como adicionar tipos de entrada a um tópico de ajuda do cmdlet</span><span class="sxs-lookup"><span data-stu-id="47be8-102">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="47be8-103">Esta seção descreve como adicionar uma seção de ENTRADAS para um tópico de Ajuda do cmdlet Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="47be8-103">This section describes how to add an INPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="47be8-104">A seção de ENTRADAS lista as classes do .NET de objetos que o cmdlet aceita como entrada do pipeline, por valor ou pelo nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="47be8-104">The INPUTS section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="47be8-105">Não há nenhum limite para o número de classes que podem ser adicionados a uma seção de ENTRADAS.</span><span class="sxs-lookup"><span data-stu-id="47be8-105">There is no limit to the number of classes that you can add to an INPUTS section.</span></span> <span data-ttu-id="47be8-106">Os tipos de entrada são colocados em um \<inputTypes: comando > nó, com cada classe entre um \<inputType: comando > elemento.</span><span class="sxs-lookup"><span data-stu-id="47be8-106">The input types are enclosed in a \<command:inputTypes> node, with each class enclosed in a  \<command:inputType> element.</span></span>

<span data-ttu-id="47be8-107">O esquema inclui dois \<maml:description > elementos em cada \<inputType: comando > elemento.</span><span class="sxs-lookup"><span data-stu-id="47be8-107">The schema includes two \<maml:description> elements in each \<command:inputType> element.</span></span> <span data-ttu-id="47be8-108">No entanto, o `Get-Help` cmdlet exibe somente o conteúdo do \<comando: tipo de entrada > /\<maml:description >) elemento.</span><span class="sxs-lookup"><span data-stu-id="47be8-108">However, the `Get-Help` cmdlet displays only the content of the \<command:inputType>/\<maml:description>) element.</span></span>

<span data-ttu-id="47be8-109">A partir do Windows PowerShell 3.0, o `Get-Help` cmdlet exibe o conteúdo do \<NavigationLink > elemento.</span><span class="sxs-lookup"><span data-stu-id="47be8-109">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="47be8-110">Esse elemento permite direcionar os usuários para tópicos que descrevem a classe do .NET.</span><span class="sxs-lookup"><span data-stu-id="47be8-110">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="47be8-111">O XML a seguir mostra o \<maml:inputTypes > nó.</span><span class="sxs-lookup"><span data-stu-id="47be8-111">The following XML shows the \<maml:inputTypes> node.</span></span>

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

<span data-ttu-id="47be8-112">O XML a seguir mostra um exemplo de como usar o \<maml:inputTypes > nó para documentar um tipo de entrada.</span><span class="sxs-lookup"><span data-stu-id="47be8-112">The following XML shows an example of using the \<maml:inputTypes> node to document an input type.</span></span>

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