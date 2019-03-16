---
title: Elemento DefaultSettings (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059058"
---
# <a name="defaultsettings-element-format"></a>Elemento DefaultSettings (formato)

Define as configurações comuns que se aplicam a todas as exibições do arquivo de formatação. Configurações comuns incluem a exibição de erros, quebra automática de texto em tabelas, definindo como coleções são expandidas e muito mais.

Elemento de DefaultSettings (formato) do elemento de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e o elemento pai do `DefaultSettings` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos filhos

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento DisplayError (formato)](./displayerror-element-format.md)|Elemento opcional.<br /><br /> Especifica que a cadeia de caracteres #ERR é exibida quando ocorre um erro ao exibir uma parte dos dados.|
|[Elemento EnumerableExpansions (formato)](./enumerableexpansions-element-format.md)|Elemento opcional.<br /><br /> Define as diferentes maneiras em que os objetos do .NET são expandidas quando eles são exibidos em uma exibição.|
|[PropertyCountForTable (formato)](./propertycountfortable-element-format.md)|Elemento opcional.<br /><br /> Especifica o número mínimo de propriedades de um objeto deve ter para exibir o objeto em uma exibição de tabela.|
|[Elemento ShowError (formato)](./showerror-element-format.md)|Elemento opcional.<br /><br /> Especifica que o registro completo de erro é exibido quando ocorre um erro ao exibir uma parte dos dados.|
|[Elemento WrapTables (formato)](./wraptables-element-format.md)|Elemento opcional.<br /><br /> Especifica que os dados em uma tabela são movidos para a próxima linha se ela não se ajustam a largura da coluna.|

### <a name="parent-elements"></a>Elementos pais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de configuração](./configuration-element-format.md)|Representa o elemento de nível superior de um arquivo de formatação.|

## <a name="remarks"></a>Comentários

## <a name="see-also"></a>Consulte Também

[Elemento de configuração](./configuration-element-format.md)

[Elemento DisplayError (formato)](./displayerror-element-format.md)

[Elemento EnumerableExpansions (formato)](./enumerableexpansions-element-format.md)

[PropertyCountForTable (formato)](./propertycountfortable-element-format.md)

[Elemento ShowError (formato)](./showerror-element-format.md)

[Elemento WrapTables (formato)](./wraptables-element-format.md)

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
