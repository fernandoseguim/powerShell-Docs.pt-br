---
title: Escrever ajuda para Cmdlets do PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857852"
---
# <a name="writing-help-for-powershell-cmdlets"></a>Escrevendo ajuda para Cmdlets do PowerShell

Cmdlets do PowerShell pode ser útil, mas a menos que seus tópicos da Ajuda explicar claramente que o cmdlet faz e como usá-lo, o cmdlet não pode ser usado ou, pior ainda, ela pode frustrar os usuários.
O formato de arquivo de Ajuda do cmdlet baseado em XML melhora a consistência, mas grande ajuda requer muito mais.

Se você nunca escreveu a Ajuda de cmdlet, examine as diretrizes a seguir.
O esquema XML necessário para criar o tópico de Ajuda do cmdlet é descrito na seção a seguir.
Iniciar com [criando o arquivo de Ajuda do Cmdlet](./how-to-create-the-cmdlet-help-file.md).
Esse tópico inclui uma descrição de nós XML de nível superior.

## <a name="writing-guidelines-for-cmdlet-help"></a>Diretrizes de gravação para a Ajuda do Cmdlet

### <a name="write-well"></a>Grave
Nada substitui um tópico bem escrito.
Se você não for um escritor profissional, encontre um editor ou o gravador para ajudá-lo.
Outra alternativa é copiar o texto de ajuda para o Microsoft Word e usar a gramática e ortografia verifica para melhorar o seu trabalho.

### <a name="write-simply"></a>Simplesmente escrever
Use frases e palavras simples.
Evite jargão.
Considere a possibilidade de que muitos leitores são equipados somente com um dicionário de idioma estrangeiro e seu tópico de Ajuda.

### <a name="write-consistently"></a>Gravar de forma consistente
A Ajuda para cmdlets relacionados devem ser semelhantes (por exemplo, get-x e set-x).
Usar as descrições padrão para os parâmetros padrão, como **Force** e **InputObject**.
(Copiá-los da Ajuda para os cmdlets de núcleo.) Use condições padrão.
Por exemplo, use "parâmetro", não "argument" e use "cmdlet" não "comando" ou "command-let".

### <a name="start-the-synopsis-with-a-verb"></a>Inicie a Sinopse com um verbo
O campo Sinopse informa ao usuário que o cmdlet não, o que é ou como ele funciona.
Verbos de criar uma instrução baseado em tarefas que informam os usuários se esse cmdlet atende às suas necessidades.
Use verbos simples como "get", "criar" e "alterar".
Evite "set", que pode ser vagas e sofisticadas palavras como "modificar".

### <a name="focus-on-objects"></a>Concentre-se em objetos
A maioria "get" exibição de cmdlets algo, mas sua função principal é obter um objeto.
Sua ajuda nos concentrar no objeto, para que os usuários compreendam que a exibição padrão é uma das muitas e que eles podem usar os métodos e propriedades do objeto que você recuperou para eles de maneiras diferentes.

### <a name="write-detailed-descriptions"></a>Descrições detalhadas de gravação
Liste brevemente tudo o que o cmdlet pode fazer na descrição detalhada.
Se a função principal é alterar uma propriedade, mas o cmdlet pode alterar todas as propriedades, liste isso na descrição detalhada.

### <a name="use-conventional-syntax"></a>Use uma sintaxe convencional
Use o formato Backus-Naur padrão que é comum para obter ajuda de linha de comando do UNIX e Windows.

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a>Usar tipos do Microsoft .NET Framework para valores de parâmetro
Os espaços reservados para valores de parâmetro (nas descrições de sintaxe e parâmetro) mostram os tipos do .NET Framework dos objetos que o parâmetro aceitará.
A equipe do PowerShell desenvolveu essa convenção para ajudar a ensinar os usuários sobre o .NET Framework.

### <a name="write-complete-parameter-descriptions"></a>Descrições de parâmetro completa de gravação
Descrições de parâmetro devem informar os usuários de duas coisas: qual o parâmetro faz (seu efeito) e o que eles devem digitar os valores de parâmetro.

### <a name="write-practical-examples"></a>Exemplos práticos de gravação
Os exemplos devem mostram como usar todos os parâmetros, mas o mais importante é mostrar como usar o cmdlet em tarefas do mundo real.
Começar com um exemplo simple e exemplos de cada vez mais complexos de gravação.
No exemplo final, mostram como usar o cmdlet em um pipeline.

### <a name="use-the-notes-field"></a>Use o campo notas
Use o campo notas para explicar conceitos que os usuários precisam entender o cmdlet.
Você também pode usar anotações para ajudar os usuários a evitar erros comuns.
Evite URLs conforme mudam.
Em vez disso, forneça os termos de usuários a ser pesquisado.

### <a name="test-your-help"></a>Teste a sua ajuda.
Teste a Ajuda, exatamente como você testar seu código.
Tenho amigos e colegas ler seu conteúdo da Ajuda e fornecerem comentários.
Você também pode solicitar comentários dos grupos de notícias.

## <a name="see-also"></a>Consulte Também

 [Como criar o arquivo de Ajuda do Cmdlet](./how-to-create-the-cmdlet-help-file.md)

 [Como adicionar o nome do Cmdlet e a Sinopse a um tópico de ajuda](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Como adicionar a descrição detalhada para um tópico de Ajuda do Cmdlet](./how-to-add-a-cmdlet-description.md)

 [Como adicionar uma sintaxe para um tópico de Ajuda do Cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Como adicionar parâmetros a um tópico de ajuda](./how-to-add-parameter-information.md)

 [Como adicionar tipos de entrada para um tópico de Ajuda do Cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Como adicionar valores de retorno para um tópico de Ajuda do Cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Como adicionar notas a um tópico de Ajuda do Cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Como adicionar exemplos para um tópico de ajuda](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Como adicionar Links relacionados a um tópico de ajuda](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [SDK do Windows PowerShell](../windows-powershell-reference.md)