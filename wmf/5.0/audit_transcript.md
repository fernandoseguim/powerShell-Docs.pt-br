---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
ms.openlocfilehash: 814b1172505e1bac59a75fee494e9741f7d1f820
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="enhanced-transcription-options"></a>Opções de transcrição avançada

A transcrição do Windows PowerShell foi aperfeiçoada para ser aplicada a todos os aplicativos de hospedagem (como o ISE do Windows PowerShell) em vez de apenas ao host do console (powershell.exe).

Além de se estender para a transcrição, a própria funcionalidade de transcrição foi atualizada para dar suporte ao aninhamento arbitrário de transcrições, metadados adicionais no cabeçalho da transcrição resultante, bem como a definição de um diretório de saída da transcrição (para dar suporte à coleta de log centralizada).

As opções de transcrição (incluindo a habilitação de uma transcrição geral do sistema) podem ser definidas com a configuração **Ativar Transcrição do PowerShell** Política de Grupo (em Modelos Administrativos -> Componentes do Windows -> Windows PowerShell).