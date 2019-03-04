---
title: Como atualizar os arquivos de ajuda | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855522"
---
# <a name="how-to-update-help-files"></a>Como atualizar os arquivos de ajuda

Este tópico explica como atualizar os arquivos de ajuda para um módulo que dá suporte à Ajuda atualizável.

## <a name="updating-help-files"></a>Atualizando arquivos de ajuda

Há muitas razões para atualizar os arquivos de Ajuda, como corrigir erros, esclarecendo um conceito, responder a uma pergunta frequentes, adicionando novos arquivos ou adicionando novos e melhores exemplos.

Para atualizar um arquivo de Ajuda:

1. Altere os arquivos.

2. Converta os arquivos em outras culturas de interface do usuário.

3. Colete todos os arquivos de Ajuda (novos, alterados e inalterados) para o módulo de cada cultura de interface do usuário.

4. Valide os arquivos em relação ao esquema XML.

5. Recompile os arquivos CAB para cada cultura de interface do usuário.

6. No arquivo XML HelpInfo, incremente os números de versão do arquivo CAB para cada cultura de interface do usuário.

7. Carregar os novos arquivos CAB para o local que é especificado pelo valor de **HelpContentUri** elemento no arquivo XML HelpInfo. Substitua os arquivos mais antigos do CAB com os novos arquivos CAB.

8. Carregar o arquivo XML HelpInfo atualizado para o local especificado pelo **HelpInfoUri** chave no manifesto de módulo. Substitua o arquivo XML HelpInfo mais antigo com o novo arquivo.