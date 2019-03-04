---
title: Como criar um arquivo XML HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853262"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a>Como criar um arquivo XML HelpInfo

Esse tópicos desta seção explica como criar e popular um arquivo de informações de Ajuda, normalmente conhecido como um "arquivo XML HelpInfo," para o recurso de ajuda atualizável do Windows PowerShell.

## <a name="helpinfo-xml-file-overview"></a>Visão geral do arquivo XML HelpInfo

O arquivo XML HelpInfo é a principal fonte de informações sobre a Ajuda atualizável para o módulo. Ele inclui o local dos arquivos de ajuda para os módulos, as culturas de interface do usuário com suporte e os números de versão que a Ajuda atualizável usa para determinar se o usuário tem os arquivos de ajuda mais recentes.

Cada módulo tem apenas um arquivo XML HelpInfo, mesmo se o módulo inclui vários arquivos de ajuda para várias culturas de interface do usuário. O autor de módulo cria o arquivo XML HelpInfo e o coloca no local de Internet que é especificado pela **HelpInfoUri** chave no manifesto de módulo. Quando os arquivos de Ajuda do módulo são atualizados e carregados, o autor do módulo atualiza o arquivo XML HelpInfo e substitui o arquivo XML HelpInfo original com a nova versão.

É essencial que o arquivo XML HelpInfo seja mantido com cuidado. Se você carregar novos arquivos, mas esquecer de incrementar os números de versão, a Ajuda atualizável não baixará os novos arquivos para os computadores dos usuários. Se você adicionar arquivos de ajuda para uma nova cultura de interface do usuário, mas não atualizar o arquivo XML HelpInfo ou colocá-lo no local correto, a Ajuda atualizável não baixará os novos arquivos.

## <a name="in-this-section"></a>Nesta seção

Esta seção inclui os seguintes tópicos.

- [Esquema XML HelpInfo](./helpinfo-xml-schema.md)

- [Arquivo de exemplo do XML HelpInfo](./helpinfo-xml-sample-file.md)

- [Como nomear um arquivo XML HelpInfo](./how-to-name-a-helpinfo-xml-file.md)

- [Como definir os números de versão XML HelpInfo](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a>Consulte Também

[Suporte à Ajuda atualizável](./supporting-updatable-help.md)