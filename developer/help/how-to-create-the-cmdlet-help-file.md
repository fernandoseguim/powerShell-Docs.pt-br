---
title: Como criar o arquivo de Ajuda do Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858972"
---
# <a name="how-to-create-the-cmdlet-help-file"></a>Como criar o arquivo de ajuda do cmdlet

Esta seção descreve como criar um arquivo XML válido que contém o conteúdo para tópicos de ajuda de cmdlet do Windows PowerShell. Esta seção discute como nomear o arquivo de Ajuda, como adicionar os cabeçalhos apropriados de XML e como adicionar nós que conterá as diferentes seções do conteúdo da Ajuda do cmdlet.

> [!NOTE]
> Para obter uma visão completa de um arquivo de Ajuda, abra um dos arquivos dll Help.xml localizado no diretório de instalação do Windows PowerShell. Por exemplo, o arquivo de Microsoft.PowerShell.Commands.Management.dll Help.xml contém conteúdo para vários dos cmdlets do Windows PowerShell.

### <a name="how-to-create-a-cmdlet-help-file"></a>Como criar um arquivo de Ajuda do Cmdlet

1. Crie um arquivo de texto e salvá-lo usando a codificação UTF8. O nome do arquivo deve ter o seguinte formato para que o Windows PowerShell pode detectá-lo como um arquivo de Ajuda do cmdlet.

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. Adicione os seguintes cabeçalhos XML ao arquivo de texto. Lembre-se de que o arquivo será validado em relação ao esquema de linguagem de modelagem de vários agentes (MAML). Atualmente, o Windows PowerShell não oferece nenhuma ferramenta para validar o arquivo.

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. Adicione um nó de comando para o arquivo de Ajuda do cmdlet para cada cmdlet no assembly. Cada nó dentro do nó de comando se relaciona com as diferentes seções do tópico da Ajuda de cmdlet.

   A tabela a seguir lista o elemento XML para cada nó, seguido por um descrições de cada nó.

   |Nó|Descrição|
   |----------|-----------------|
   |`<details>`|Adiciona o conteúdo para os nome e a Sinopse seções do tópico da Ajuda de cmdlet. Para obter mais informações, consulte [como adicionar o nome do Cmdlet e a Sinopse](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).|
   |`<maml:description>`|Adiciona o conteúdo para a seção de descrição do tópico da Ajuda de cmdlet. Para obter mais informações, consulte [como adicionar a descrição detalhada para um tópico de Ajuda do Cmdlet](./how-to-add-a-cmdlet-description.md).|
   |`<command:syntax>`|Adiciona o conteúdo para a seção de sintaxe do tópico da Ajuda de cmdlet. Para obter mais informações, consulte [como adicionar a sintaxe para um tópico de Ajuda do Cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md).|
   |`<command:parameters>`|Adiciona o conteúdo para a seção de parâmetros do tópico da Ajuda de cmdlet. Para obter mais informações, consulte [como adicionar parâmetros para um tópico de Ajuda do Cmdlet](./how-to-add-parameter-information.md).|
   |`<command:inputTypes>`|Adiciona o conteúdo para a seção de ENTRADAS do tópico da Ajuda de cmdlet. Para obter mais informações, consulte [como adicionar tipos de entrada para um tópico de Ajuda do Cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md).|
   |`<command:returnValues>`|Adiciona o conteúdo da seção de SAÍDAS do tópico da Ajuda de cmdlet. Para obter mais informações, consulte [como adicionar valores de retorno para um tópico de Ajuda do Cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md).|
   |`<maml:alertset>`|Adiciona o conteúdo para a seção Observações do tópico da Ajuda de cmdlet. Para obter mais informações, consulte [como adicionar notas a um tópico de Ajuda do Cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md).|
   |`<command:examples>`|Adiciona o conteúdo para a seção de exemplos do tópico da Ajuda de cmdlet. Para obter mais informações, consulte [como exemplos de adicionar um tópico de Ajuda do Cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md).|
   |`<maml:relatedLinks>`|Adiciona o conteúdo para a seção de LINKS relacionados do tópico da Ajuda de cmdlet. Para obter mais informações, consulte [como adicionar Links relacionados a um tópico de Ajuda do Cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md).|

## <a name="example"></a>Exemplo

 Aqui está um exemplo de um nó de comando que inclui os nós para as várias seções do tópico da Ajuda de cmdlet.

```xml
<command:command
  xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
  xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
  <command:details>
    <!--Add name an synopsis here-->
  </command:details>
  <maml:description>
    <!--Add detailed description here-->
  </maml:description>
  <command:syntax>
    <!--Add syntax information here-->
  </command:syntax>
  <command:parameters>
    <!--Add parameter information here-->
  </command:parameters>
  <command:inputTypes>
    <!--Add input type information here-->
  </command:inputTypes>
  <command:returnValues>
    <!--Add return value information here-->
  </command:returnValues>
  <maml:alertSet>
    <!--Add Note information here-->
  </maml:alertSet>
  <command:examples>
    <!--Add cmdlet examples here-->
  </command:examples>
  <maml:relatedLinks>
    <!--Add links to related content here-->
  </maml:relatedLinks>
</command:command>
```

## <a name="see-also"></a>Consulte Também

 [Como adicionar o nome do Cmdlet e a Sinopse](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Como adicionar a descrição detalhada para um tópico de Ajuda do Cmdlet](./how-to-add-a-cmdlet-description.md)

 [Como adicionar uma sintaxe para um tópico de Ajuda do Cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Como adicionar parâmetros a um tópico de ajuda](./how-to-add-parameter-information.md)

 [Como adicionar tipos de entrada para um tópico de Ajuda do Cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Como adicionar valores de retorno para um tópico de Ajuda do Cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Como adicionar notas a um tópico de Ajuda do Cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Como adicionar exemplos para um tópico de ajuda](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Como adicionar Links relacionados a um tópico de ajuda](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [SDK do Windows PowerShell](../windows-powershell-reference.md)