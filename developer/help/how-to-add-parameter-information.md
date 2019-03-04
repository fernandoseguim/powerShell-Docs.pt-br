---
title: Como adicionar informações de parâmetro | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf6c1442-60aa-477a-8f30-ab02b1b11039
caps.latest.revision: 7
ms.openlocfilehash: d4a5fc934a41b00f89862674e44e4540680674f7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863322"
---
# <a name="how-to-add-parameter-information"></a>Como adicionar informações de parâmetro

Esta seção descreve como adicionar conteúdo que é exibido na seção de parâmetros do tópico da Ajuda de cmdlet. A seção de parâmetros do tópico da Ajuda lista cada um dos parâmetros do cmdlet e fornece uma descrição detalhada de cada parâmetro.

O conteúdo da seção de parâmetros deve ser consistente com o conteúdo da seção de sintaxe do tópico da Ajuda. É responsabilidade do autor da Ajuda para certificar-se de que o nó de sintaxe e os parâmetros contêm elementos XML semelhantes.

> [!NOTE]
> Para obter uma visão completa de um arquivo de Ajuda, abra um dos arquivos dll Help.xml localizado no diretório de instalação do Windows PowerShell. Por exemplo, o arquivo de Microsoft.PowerShell.Commands.Management.dll Help.xml contém conteúdo para vários dos cmdlets do Windows PowerShell.

### <a name="to-add-parameters"></a>Para adicionar parâmetros

1. Abra o arquivo de Ajuda do cmdlet e localize o nó de comando para o cmdlet que você está documentando. Se você estiver adicionando um novo cmdlet, você precisará criar um novo nó de comando. Contém um nó de comando para cada cmdlet que você está fornecendo o conteúdo da Ajuda para seu arquivo de Ajuda. Aqui está um exemplo de um nó de comando em branco.

    ```xml
    <command:command>
    </command:command>
    ```

2. Dentro do nó de comando, localize o nó de descrição e adicione um nó de parâmetros, conforme mostrado abaixo. Apenas um nó de parâmetros é permitido, e você deve seguir imediatamente o nó de sintaxe.

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. Dentro do nó de parâmetros, adicione um nó de parâmetro para cada parâmetro do cmdlet, conforme mostrado abaixo.

   Neste exemplo, um nó de parâmetro é adicionado para três parâmetros.

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   Como essas são as mesmas marcas XML que são usadas no nó da sintaxe e porque os parâmetros especificados aqui devem coincidir com os parâmetros especificados pelo nó de sintaxe, você pode copiar os nós de parâmetro a partir do nó de sintaxe e cole-o nó parâmetros. No entanto, certifique-se de copiar apenas uma instância de um nó de parâmetro, mesmo se o parâmetro for especificado no parâmetro de vários define na sintaxe.

4. Para cada nó de parâmetro, defina os valores de atributo que definem as características de cada parâmetro. Esses atributos incluem o seguinte: necessária, o recurso de curinga, pipelineinput e posição.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named" ></command:parameter>
    </command:Parameters>
    ```

5. Para cada nó de parâmetro, adicione o nome do parâmetro. Aqui está um exemplo do nome do parâmetro adicionado para o nó de parâmetro.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. Para cada nó de parâmetro, adicione a descrição do parâmetro. Aqui está um exemplo de como a descrição do parâmetro adicionado para o nó de parâmetro.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
      </command:parameter>
    </command:parameters>
    ```

7. Para cada nó de parâmetro, adicione o tipo do .NET Framework do parâmetro. O tipo de parâmetro é exibido junto com o nome do parâmetro.

   Aqui está um exemplo de tipo do .NET Framework parâmetro adicionado para o nó de parâmetro.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
      </command:parameter>
    </command:parameters>
    ```

8. Para cada nó de parâmetro, adicione o valor padrão do parâmetro. A seguinte sentença é adicionada à descrição do parâmetro quando o conteúdo é exibido: "DefaultValue" é o padrão.

   Aqui está um exemplo de valor padrão do parâmetro é adicionado ao nó de parâmetro.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
        <dev:defaultvalue> Add default value...</dev:defaultvalue>
      </command:parameter>
    </command:parameters>
    ```

9. Para cada parâmetro que tenha vários valores, adicione um nó de valores possíveis.

   Aqui está um exemplo de como o de um nó de valores possíveis que define dois valores possíveis para o parâmetro

    ```xml
    <dev:possiblevalues>
      <dev:possiblevalue>
        <dev:value>Unknown</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      /dev:possiblevalue>
      <dev:possiblevalue>
        <dev:value>String</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possibleValue>
    </dev:possiblevalues>
    ```

Aqui estão algumas coisas para se lembrar ao adicionar parâmetros.

- Os atributos do parâmetro não são exibidos em todas as exibições do tópico da Ajuda de cmdlet. No entanto, eles são exibidos em uma tabela de descrição do parâmetro a seguir quando o usuário solicita o completo (Get-Help \<cmdletname >-completo) ou um parâmetro (Get-Help \<cmdletname >-parâmetro) modo de exibição do tópico.

- A descrição do parâmetro é uma das partes mais importantes de um tópico de Ajuda do cmdlet. A descrição deve ser breve, bem como completa. Além disso, lembre-se de que, se a descrição do parâmetro torna-se muito longa, como quando os dois parâmetros interagem entre si, você pode adicionar mais conteúdo na seção Observações do tópico da Ajuda de cmdlet.

  A descrição do parâmetro fornece dois tipos de informações.

- O que o cmdlet faz quando o parâmetro é usado.

- É o que é um valor válido para o parâmetro.

- Porque os valores de parâmetro são expressos como objetos do .NET Framework, os usuários precisam saber mais sobre esses valores do que em uma ajuda de linha de comando tradicional. Informar ao usuário qual tipo de dados para o parâmetro é projetado para aceitar e incluem exemplos.

O valor padrão do parâmetro é o valor que é usado se o parâmetro não for especificado na linha de comando. Observe que o valor padrão é opcional e não é necessária para alguns parâmetros, como os parâmetros necessários. No entanto, você deve especificar um valor padrão para a maioria dos parâmetros opcionais.

O valor padrão ajuda o usuário a entender o efeito de não usar o parâmetro. Descreva o valor padrão, especificamente, como "diretório atual" ou o "Windows PowerShell diretório de instalação ($pshome)" para um caminho opcional. Você também pode escrever uma frase que descreve o padrão, como a seguinte sentença usada para o `PassThru` parâmetro: "Se PassThru não for especificado, o cmdlet não passa objetos pelo pipeline."  Além disso, porque o valor é exibido oposta o nome do campo "**valor padrão**", você não precisa incluir o termo "valor padrão" na entrada.

O valor padrão do parâmetro não é exibido em todas as exibições do tópico da Ajuda de cmdlet. No entanto, ele é exibido em uma tabela (juntamente com os atributos de parâmetro) seguindo a descrição do parâmetro quando o usuário solicita o completo (Get-Help \<cmdletname >-completo) ou um parâmetro (Get-Help \<cmdletname >-parâmetro) modo de exibição o tópico.

O XML a seguir mostra um par de `<dev:defaultValue>` marcas adicionadas ao `<command:parameter>` nó. Observe que o valor padrão que segue imediatamente após o fechamento `</command:parameterValue>` marca (quando o valor do parâmetro for especificado) ou o fechamento `</maml:description>` marca da descrição do parâmetro. Nome.

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
  </command:parameter>
</command:parameters>
```

Adicionar valores para os tipos enumerados

Se o parâmetro tem vários valores ou valores de um tipo enumerado, você pode usar um recurso opcional \<dev:possibleValues > nó. Este nó permite que você especifique um nome e uma descrição para vários valores.

Lembre-se de que as descrições dos valores enumerados não aparecem em qualquer um dos padrão modos de exibição de ajuda exibidos pelo `Get-Help` cmdlet, mas outros visualizadores de Ajuda podem exibir esse conteúdo em suas exibições.

O XML a seguir mostra um `<dev:possibleValues>` nó com dois valores especificados.

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
    <dev:possibleValues>
      <dev:possibleValue>
        <dev:value> Value 1 </dev:value>
        <maml:description>
          <maml:para> Description 1 </maml:para>
        </maml:description>
      <dev:possibleValue>
      <dev:possibleValue>
        <dev:value> Value 2 </dev:value>
        <maml:description>
          <maml:para> Description 2 </maml:para>
        </maml:description>
      <dev:possibleValue>
    </dev:possibleValues>
  </command:parameter>
</command:parameters>
```