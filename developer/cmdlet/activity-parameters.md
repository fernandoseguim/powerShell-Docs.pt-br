---
title: Parâmetros de atividade | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4e0cf6-19e0-44b8-8b40-d6f6075276cf
caps.latest.revision: 5
ms.openlocfilehash: 489d8bcdabe904d6a3d2bc6cdb9d7e23d09cbef2
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251210"
---
# <a name="activity-parameters"></a>Parâmetros de atividade

A tabela a seguir lista os nomes recomendados e a funcionalidade para os parâmetros de atividade.

|Parâmetro|Funcionalidade|
|---|---|
|**Acrescentar**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que o usuário pode adicionar conteúdo ao final de um recurso quando o parâmetro for especificado.|
|**CaseSensitive**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que o usuário pode exigir a diferenciação de maiusculas quando o parâmetro for especificado.|
|**Comando**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar uma cadeia de caracteres de comando para executar.|
|**CompatibleVersion**<br>Tipo de dados: Objeto Version|Implemente esse parâmetro para que o usuário pode especificar a semântica que o cmdlet deve ser compatível com para compatibilidade com versões anteriores.|
|**Compactar**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que a compactação de dados é usada quando o parâmetro for especificado.|
|**Compactar**<br>Tipo de dados: Palavra-chave|Implemente esse parâmetro para que o usuário pode especificar o algoritmo para compactação de dados.|
|**contínua**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que os dados são processados até que o usuário encerra o cmdlet, quando o parâmetro for especificado. Se o parâmetro não for especificado, o cmdlet processa uma quantidade predefinida de dados e, em seguida, encerra a operação.|
|**criar**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para indicar que um recurso é criado se ainda não existir quando o parâmetro for especificado.|
|**Delete**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que os recursos serão excluídos quando o cmdlet concluiu sua operação quando o parâmetro for especificado.|
|**Esvaziar**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para indicar que os itens de trabalho pendentes sejam processados antes que o cmdlet processa os novos dados quando o parâmetro for especificado. Se o parâmetro não for especificado, os itens de trabalho são processados imediatamente.|
|**Erase**<br>Tipo de dados: Int32|Implemente esse parâmetro para que o usuário pode especificar o número de vezes que um recurso é apagado antes de ser excluído.|
|**ErrorLevel**<br>Tipo de dados: Int32|Implemente esse parâmetro para que o usuário pode especificar o nível de erro para relatar.|
|**Excluir**<br>Tipo de dados: String[]|Implemente esse parâmetro para que o usuário pode excluir algo de uma atividade. Para obter mais informações sobre como usar filtros de entrada, consulte [parâmetros de filtro de entrada](input-filter-parameters.md).|
|**filtro**<br>Tipo de dados: Palavra-chave|Implemente esse parâmetro para que o usuário pode especificar um filtro que seleciona os recursos no qual executar a ação de cmdlet. Para obter mais informações sobre como usar filtros de entrada, consulte [parâmetros de filtro de entrada](./input-filter-parameters.md).|
|**Siga**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que o progresso é controlado quando o parâmetro for especificado.|
|**Force**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para indicar que o usuário pode executar uma ação, mesmo se as restrições forem encontradas quando o parâmetro for especificado. O parâmetro não permite a segurança de comprometimento. Por exemplo, este parâmetro permite ao usuário substituir um arquivo somente leitura.|
|**Incluir**<br>Tipo de dados: String[]|Implemente esse parâmetro para que o usuário possa incluir algo em uma atividade. Para obter mais informações sobre como usar filtros de entrada, consulte [parâmetros de filtro de entrada](input-filter-parameters.md).|
|**Incremental**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para indicar que o processamento é realizado incrementalmente quando o parâmetro for especificado. Por exemplo, este parâmetro permite ao usuário executar backups incrementais e fazer backup de arquivos somente desde o último backup.|
|**InputObject**<br>Tipo de dados: Objeto|Implemente esse parâmetro quando o cmdlet obtém a entrada de outros cmdlets. Quando você define uma **InputObject** parâmetro, sempre especifique a **ValueFromPipeline** palavra-chave quando você declara o **parâmetro** atributo. Para obter mais informações sobre como usar filtros de entrada, consulte [parâmetros de filtro de entrada](./input-filter-parameters.md).|
|**Inserir**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que o cmdlet insere um item quando o parâmetro for especificado.|
|**Interativo**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que o cmdlet interativamente funciona com o usuário quando o parâmetro for especificado.|
|**intervalo**<br>Tipo de dados: HashTable|Implemente esse parâmetro para que o usuário pode especificar uma tabela de hash de palavras-chave que contém os valores. O exemplo a seguir mostra os valores de exemplo para o **intervalo** parâmetro: `-interval @{ResumeScan=15; Retry=3}`.|
|**Log**<br>Tipo de dados: SwitchParameter|Implemente essa auditoria de parâmetro as ações do cmdlet, quando o parâmetro for especificado.|
|**NoClobber**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que o recurso não será substituído quando o parâmetro for especificado. Este parâmetro geralmente se aplica aos cmdlets que criam objetos novos, de modo que eles podem ser impedidos de substituir os objetos existentes com o mesmo nome.|
|**Notificar**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que o usuário será notificado de que a atividade é concluída quando o parâmetro for especificado.|
|**NotifyAddress**<br>Tipo de dados: Endereço de email|Implemente esse parâmetro para que o usuário pode especificar o endereço de email a ser usado para enviar uma notificação quando o **notificar** parâmetro for especificado.|
|**Substituir**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que o cmdlet substitui quaisquer dados existentes quando o parâmetro for especificado.|
|**Solicitar**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar um prompt para o cmdlet.|
|**Silencioso**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que o cmdlet suprime comentários do usuário durante a suas ações quando o parâmetro for especificado.|
|**Recurse**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que recursivamente o cmdlet executa suas ações em recursos e o parâmetro for especificado.|
|**Repair**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que o cmdlet tentará corrigir algo em um estado interrompido quando o parâmetro for especificado.|
|**RepairString**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar uma cadeia de caracteres para utilizar quando o **reparo** parâmetro for especificado.|
|**Tente novamente**<br>Tipo de dados: Int32|Implemente esse parâmetro para que o usuário pode especificar o número de vezes que o cmdlet tentará realizar uma ação.|
|**Select**<br>Tipo de dados: Matriz de palavra-chave|Implemente esse parâmetro para que o usuário pode especificar uma matriz dos tipos de itens.|
|**fluxo**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que o usuário pode transmitir vários objetos de saída por meio do pipeline quando o parâmetro for especificado.|
|**Estrito**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que todos os erros são tratados como erros de finalização quando o parâmetro for especificado.|
|**TempLocation**<br>Tipo de dados: Cadeia de caracteres|Implemente esse parâmetro para que o usuário pode especificar o local de dados temporários que são usados durante a operação do cmdlet.|
|**tempo limite**<br>Tipo de dados: Int32|Implemente esse parâmetro para que o usuário pode especificar o intervalo de tempo limite (em milissegundos).|
|**Truncar**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que o cmdlet irá truncar suas ações quando o parâmetro for especificado. Se o parâmetro não for especificado, o cmdlet realiza outra ação.|
|**Verifique se**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que o cmdlet será testado para determinar se uma ação ocorreu quando o parâmetro for especificado.|
|**Wait**<br>Tipo de dados: SwitchParameter|Implemente esse parâmetro para que o cmdlet irá esperar para entrada do usuário antes de continuar quando o parâmetro for especificado.
|**WaitTime**<br>Tipo de dados: Int32|Implemente esse parâmetro para que o usuário pode especificar a duração (em segundos) que o cmdlet irá esperar para o usuário de entrada quando o **esperar** parâmetro for especificado.|

## <a name="see-also"></a>Consulte Também

[Parâmetros do cmdlet](./cmdlet-parameters.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
