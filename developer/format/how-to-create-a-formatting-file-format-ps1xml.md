---
title: Como criar um arquivo de formatação (. ps1xml) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862962"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a>Como criar um arquivo de formatação (.format.ps1xml)

Este tópico descreve como criar um arquivo de formatação (. ps1xml).

> [!NOTE]
> Você também pode criar um arquivo de formatação, fazendo uma cópia de um dos arquivos fornecidos pelo Windows PowerShell. Se você fizer uma cópia de um arquivo existente, exclua a assinatura digital existente e adicionar sua própria assinatura para o novo arquivo.

### <a name="to-create-a-formatps1xml-file"></a>Para criar um. arquivo format.ps1xml.

1. Crie um arquivo de texto (. txt) usando um texto de editor como o bloco de notas.

2. Copie as seguintes linhas para o arquivo de formatação.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - O \<Configuration >\</Configuração > marcas definem raiz `Configuration` nó. Todas as marcas XML adicionais serão incluídas dentro desse nó.

   - O <ViewDefinitions> </ViewDefinitions> definem marcas de `ViewDefinitions` nó. Todas as exibições são definidas dentro deste nó.

3. Salve o arquivo para a pasta de instalação do Windows PowerShell, para a pasta de módulo ou em uma subpasta da pasta do módulo. Use o seguinte formato de nome quando você salva o arquivo: `MyFile.format.ps1xml`. Arquivos de formatação devem usar o `.format.ps1xml` extensão.

   Agora você está pronto para adicionar modos de exibição para o arquivo de formatação. Não há nenhum limite para o número de exibições que podem ser definidas em um arquivo de formatação. Você pode adicionar uma exibição única para cada objeto, vários modos de exibição para o mesmo objeto ou uma única exibição que é usada por vários objetos.

## <a name="see-also"></a>Consulte Também

[Escrevendo um formatação do Windows PowerShell e tipos de arquivo](./writing-a-powershell-formatting-file.md)
