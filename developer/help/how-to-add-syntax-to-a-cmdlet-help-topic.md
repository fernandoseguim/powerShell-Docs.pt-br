---
title: Como adicionar uma sintaxe para um tópico de ajuda | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 2e9dbc9ff8f9507f2008cd6e114ba6fec36b10bf
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054604"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a>Como adicionar sintaxe a um tópico de ajuda do cmdlet

- [Atributos de parâmetro](#Parameter-Attributes)

- [Atributos de valor de parâmetro](#Parameter-Value-Attributes)

- [Coletando informações de sintaxe](#Gathering-Syntax-Information)

- [O diagrama de sintaxe XML de codificação](#Coding-the-Syntax-Diagram-XML)

## <a name="things-to-know-about-the-syntax-diagram-in-cmdlet-help"></a>É importante saber sobre o diagrama de sintaxe na Ajuda do Cmdlet

Antes de começar a codificar o XML para o diagrama de sintaxe no arquivo de ajuda de cmdlet, leia esta seção para obter uma visão clara do tipo de dados que você precisa fornecer, como os atributos de parâmetro e como esses dados são exibidos no diagrama de sintaxe...

### <a name="parameter-attributes"></a>Atributos de parâmetro

- Necessária

  - Se for true, o parâmetro deve aparecer em todos os comandos que usam o conjunto de parâmetros.

  - Se for false, o parâmetro é opcional em todos os comandos que usam o conjunto de parâmetros.

- posição

  - Se o nome, o nome do parâmetro é necessário.

  - Se posicionais, o nome do parâmetro é opcional. Quando ele for omitido, o valor do parâmetro deve estar na posição especificada no comando. Por exemplo, se o valor é a posição = "1", o valor do parâmetro deve ser o primeiro ou o único valor de parâmetro no comando sem nome.

- Entrada de pipeline

  - Se for verdadeiro (ByValue), você pode redirecionar a entrada para o parâmetro. A entrada é associada com ("associado à") o parâmetro, mesmo se o nome da propriedade e o tipo de objeto não corresponde ao tipo esperado. O PowerShell do Windows? componentes de associação de parâmetro tentam converter a entrada para o tipo correto e não o comando somente quando o tipo não pode ser convertido. Pode ser associado a apenas um parâmetro em um conjunto de parâmetros por valor.

  - Se for true (ByPropertyName), você pode redirecionar a entrada para o parâmetro. No entanto, a entrada é associada ao parâmetro somente quando o nome do parâmetro corresponde ao nome de uma propriedade do objeto de entrada. Por exemplo, se o nome do parâmetro é `Path`, objetos canalizados para o cmdlet estão associados esse parâmetro somente quando o objeto tem uma propriedade chamada caminho.

  - Se verdadeiro (ByValue, ByPropertyName), você pode redirecionar a entrada para o parâmetro pelo nome da propriedade ou por valor. Pode ser associado a apenas um parâmetro em um conjunto de parâmetros por valor.

  - Se for false, você não pode redirecionar a entrada para esse parâmetro.

- Recurso de curinga

  - Se for true, o texto que o usuário digita o valor do parâmetro pode incluir caracteres curinga.

  - Se for false, o texto que o usuário digita o valor do parâmetro não pode incluir caracteres curinga.

### <a name="parameter-value-attributes"></a>Atributos de valor de parâmetro

- Necessária

  - Se for true, o valor especificado deve ser usado sempre que usar o parâmetro em um comando.

  - Se for false, o valor do parâmetro é opcional. Normalmente, um valor é opcional somente quando ele é um dos vários valores válidos para um parâmetro, como em um tipo enumerado.

O atributo necessário de um valor de parâmetro é diferente do atributo de um parâmetro obrigatório.

O atributo necessário de um parâmetro indica se o parâmetro (e seu valor) devem ser incluídos ao invocar o cmdlet. Em contraste, o atributo necessário de um valor de parâmetro é usado somente quando o parâmetro está incluído no comando. Indica se esse valor específico deve ser usado com o parâmetro.

Normalmente, os valores de parâmetro que são espaços reservados são necessários e os valores de parâmetro literais não são necessários, pois eles são um dos vários valores que podem ser usados com o parâmetro.

### <a name="gathering-syntax-information"></a>Coletando informações de sintaxe

1. Comece com o nome do cmdlet.

   ```
   SYNTAX
       Get-Tech
   ```

2. Liste todos os parâmetros do cmdlet. Digite um traço (também conhecido como "traço" ou "sinal de subtração" (ASCII 45) antes de cada nome de parâmetro. Separe os parâmetros em conjuntos de parâmetros (alguns cmdlets pode ter apenas um parâmetro definido). Neste exemplo, o Get-Tech cmdlet tem dois conjuntos de parâmetros.

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   Inicie cada parâmetro definido com o nome do cmdlet.

   Lista o parâmetro padrão definido pela primeira vez. O parâmetro padrão é especificado pela classe do cmdlet.

   Para cada conjunto de parâmetros, liste seu parâmetro exclusivo pela primeira vez, a menos que haja parâmetros posicionais devem aparecer primeiro. No exemplo anterior, os parâmetros de nome e ID são parâmetros exclusivos para os dois conjuntos de parâmetros (cada conjunto de parâmetros deve ter um parâmetro que seja exclusivo para esse conjunto de parâmetros). Isso torna mais fácil para os usuários a identificar quais eles precisarão fornecer para o parâmetro de parâmetro definido.

   Liste os parâmetros na ordem em que elas devem aparecer no comando. Se a ordem não importa, listar os parâmetros relacionados juntos ou lista os parâmetros usados com mais frequência pela primeira vez.

   Certifique-se de que lista os parâmetros WhatIf e confirmar se o cmdlet oferece suporte a ShouldProcess.

   Não liste os parâmetros comuns (como Verbose, Debug e ErrorAction) em seu diagrama de sintaxe. O `Get-Help` cmdlet adiciona essas informações para você quando ele exibe o tópico da Ajuda.

3. Adicione os valores de parâmetro. No Windows PowerShell?, valores de parâmetro são representados por tipo de .NET. No entanto, o nome do tipo pode ser abreviado, como "string" para System. String.

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   Abreviar tipos, desde que seu significado é claro, como "string" para System. String e "int" para System. Int32.

   Listar todos os valores de enumerações, como o parâmetro - type no exemplo anterior, que pode ser definido como "básico" ou "Avançado".

   Alternar parâmetros, como - lista no exemplo anterior, não têm valores.

4. Adicione os colchetes angulares para valores de parâmetros que são de espaço reservado, em comparação com os valores de parâmetros que são literais.

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. Coloque os parâmetros opcionais e seus valores entre colchetes.

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. Coloque os nomes de parâmetros opcionais (para parâmetros posicionais) entre colchetes. O nome para parâmetros posicionais, como o parâmetro Name no exemplo a seguir, é preciso ser incluído no comando.

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. Se um valor de parâmetro pode conter vários valores, como uma lista de nomes no parâmetro Name, adicione um par de colchetes diretamente após o valor do parâmetro.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. Se o usuário pode escolher parâmetros ou valores de parâmetro, como o parâmetro de tipo, coloque as escolhas em colchetes e separe-as com o symbol(;) OR exclusivo.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. Se o valor do parâmetro deve usar a formatação específica, como aspas ou parênteses, mostram o formato na sintaxe.

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a>O diagrama de sintaxe XML de codificação

O nó de sintaxe do XML começa imediatamente após o nó de descrição, que termina com o \</maml:description > marca. Para obter informações sobre a coleta de dados usados no diagrama de sintaxe, consulte [coleta informações sobre a sintaxe](#Gathering-Syntax-Information).

### <a name="adding-a-syntax-node"></a>Adicionando um nó de sintaxe

O diagrama de sintaxe exibido no tópico da Ajuda do cmdlet é gerado a partir de dados no nó da sintaxe do XML. O nó de sintaxe é colocado em um par se \<: sintaxe de comando > marcas. Com cada conjunto de parâmetros do cmdlet entre um par de \<syntaxitem: comando > marcas. Não há nenhum limite para o número de \<syntaxitem: comando > marcas que podem ser adicionados.

O exemplo a seguir mostra um nó de sintaxe que tem nós de item de sintaxe para dois conjuntos de parâmetros.

```xml
<command:syntax>
  <command:syntaxItem>
    ...
    <!--Parameter Set 1 (default parameter set) parameters go here-->
    ...
  </command:syntaxItem>
  <command:syntaxItem>
    ...
    <!--Parameter Set 2 parameters go here-->
    ...
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a>Adicionar o nome do Cmdlet para o parâmetro de conjunto de dados

Cada conjunto de parâmetros do cmdlet é especificado em um nó de item de sintaxe. Cada nó de item de sintaxe começa com um par de \<maml:name > marcas que incluem o nome do cmdlet.

O exemplo a seguir inclui um nó de sintaxe que tem nós de item de sintaxe para dois conjuntos de parâmetros.

```xml
<command:syntax>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-parameters"></a>Adicionando parâmetros

Cada parâmetro é adicionado ao nó de item de sintaxe é especificado dentro de um par de \<: parâmetro de comando > marcas. Você precisa de um par de \<: parâmetro de comando > marcas para cada parâmetro incluído no conjunto de parâmetros, com exceção dos parâmetros comuns que são fornecidos pelo Windows PowerShell?.

Os atributos da abertura \<: parâmetro de comando > marca determinar como o parâmetro aparece no diagrama de sintaxe. Para obter informações sobre atributos de parâmetro, consulte [atributos de parâmetro](#Parameter-Attributes).

> [!NOTE]
> O \<: parâmetro de comando > marca dá suporte a um elemento filho \<maml:description > cujo conteúdo nunca é exibido. As descrições de parâmetro são especificadas no nó de parâmetro do XML. Para evitar inconsistências entre as informações no item de sintaxe bodes e o nó de parâmetro, omita o (\<maml:description > ou deixá-lo vazio.

O exemplo a seguir inclui um nó de item de sintaxe para um parâmetro definido com dois parâmetros.

```xml
<command:syntaxItem>
  <maml:name>Cmdlet-Name</maml:name>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByValue)" position="1">
    <maml:name>ParameterName1</maml:name>
    <command:parameterValue required="true">
      string[]
    </command:parameterValue>
  </command:parameter>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByPropertyName)">
    <maml:name>ParameterName2</maml:name>
    <command:parameterValue required="true">
      int32[]
    </command:parameterValue>
  </command:parameter>
</command:syntaxItem>
```
