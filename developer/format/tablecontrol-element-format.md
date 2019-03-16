---
title: Elemento TableControl (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054570"
---
# <a name="tablecontrol-element-format"></a>Elemento TableControl (formato)

Define um formato de tabela para um modo de exibição.

Elemento ViewDefinitions (formato) modo de exibição (formato) TableControl elemento (formato)

## <a name="syntax"></a>Sintaxe

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `TableControl` elemento. Você deve especificar as linhas da tabela. Todos os outros elementos filho são opcionais.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento AutoSize para TableControl (formato)](./autosize-element-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica se o tamanho da coluna e o número de colunas são ajustados com base no tamanho dos dados.|
|[Elemento HideTableHeaders para TableControl (formato)](./hidetableheaders-element-format.md)|Elemento opcional.<br /><br /> Indica se o cabeçalho da tabela não é exibido.|
|[Elemento TableHeaders para TableControl (formato)](./tableheaders-element-format.md)|Elemento necessário.<br /><br /> Define os rótulos, as larguras e o alinhamento dos dados para as colunas da exibição de tabela.|
|[Elemento TableRowEntries para TableControl (formato)](./tablerowentries-element-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Fornece as definições da exibição de tabela.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de exibição (formato)](./view-element-format.md)|Define uma exibição que é usada para exibir os membros de um ou mais objetos.|

## <a name="remarks"></a>Comentários

Para obter mais informações sobre os componentes de uma exibição de tabela, consulte [criando uma exibição de tabela](./creating-a-table-view.md).

## <a name="example"></a>Exemplo

Este exemplo mostra uma `TableControl` que é usado para exibir as propriedades do elemento de [ServiceProcess](/dotnet/api/System.ServiceProcess.ServiceController) objeto.

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>...</TableHeaders>
    <TableRowEntries>...</TableRowEntries>
  </TableControl>
</View>

```

## <a name="see-also"></a>Consulte Também

[Criando uma exibição de tabela](./creating-a-table-view.md)

[Elemento de exibição (formato)](./view-element-format.md)

[Elemento AutoSize para TableControl (formato)](./autosize-element-for-tablecontrol-format.md)

[Elemento HideTableHeaders (formato)](./hidetableheaders-element-format.md)

[Elemento TableHeaders (formato)](./tableheaders-element-format.md)

[Elemento TableRowEntries (formato)](./tablerowentries-element-for-tablecontrol-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
