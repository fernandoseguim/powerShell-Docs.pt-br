---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: 7a1725e3858c59a6d31699add22b042359c48463
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675797"
---
# <a name="separation-of-node-and-configuration-ids"></a>Separação de IDs de nó e de configuração

## <a name="overview"></a>Visão geral

Para proporcionar uma experiência mais flexível e simplificada ao usar o DSC no modo Pull, adicionamos uma série de recursos nesta versão. Esses recursos destinam-se a permitir que você tenha a flexibilidade de configurar e implantar configurações em vários nós com facilidade, ao mesmo tempo que acompanha as informações de status e relatório de cada nó individualmente.
Esses recursos são os seguintes:

* Um nome de configuração que identifica a configuração de um computador. Esse nome pode ser compartilhado por vários nós de destino
* Uma ID de agente que identifica exclusivamente um único nó
* Uma etapa de registro que ocorre apenas na primeira vez em que um nó de destino se conecta a um servidor de recepção

**Observação:** esses recursos e funcionalidades foram adicionados e não substituem os conceitos e recursos existentes de pull. É possível usar esses novos recursos ou os antigos com o novo servidor de recepção fornecido nesta versão.

Para obter mais informações, veja [Configurando um cliente de pull usando nomes de configuração](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)
