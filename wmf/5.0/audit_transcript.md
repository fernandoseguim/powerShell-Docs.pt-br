---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: 5e17b0a78f6e860c6144d2e81c426bb26126a85f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="enhanced-transcription-options"></a>Opções de transcrição avançada

A transcrição do Windows PowerShell foi aperfeiçoada para ser aplicada a todos os aplicativos de hospedagem (como o ISE do Windows PowerShell) em vez de apenas ao host do console (powershell.exe).

Além de se estender para a transcrição, a própria funcionalidade de transcrição foi atualizada para dar suporte ao aninhamento arbitrário de transcrições, metadados adicionais no cabeçalho da transcrição resultante, bem como a definição de um diretório de saída da transcrição (para dar suporte à coleta de log centralizada).

As opções de transcrição (incluindo a habilitação de uma transcrição geral do sistema) podem ser definidas com a configuração **Ativar Transcrição do PowerShell** Política de Grupo (em Modelos Administrativos -> Componentes do Windows -> Windows PowerShell).
