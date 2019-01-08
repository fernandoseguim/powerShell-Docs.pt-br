---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Visão Geral da Desired State Configuration para Tomadores de Decisão
ms.openlocfilehash: ce554d4bb994d4b1816d9d9c24599e4ef0e1c593
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400178"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>Visão Geral da Desired State Configuration para Tomadores de Decisão

Este documento descreve os benefícios comerciais do uso da DSC (Desired State Configuration) do Windows PowerShell. Não é um guia técnico.

## <a name="what-is-desired-state-configuration"></a>Qual é a Desired State Configuration?

A Desired State Configuration do PowerShell é uma plataforma de gerenciamento de configuração interna do Windows que se baseia em padrões abertos. A DSC é flexível o suficiente para funcionar de maneira confiável e consistente em cada estágio do ciclo de vida de implantação (desenvolvimento, teste, pré-produção, produção), bem como durante a expansão.

A DSC concentra-se em [configurações](../configurations/configurations.md).
Uma configuração é um documento fácil de ler que descreve um ambiente composto por computadores ("nós") com características específicas.
Essas características podem ser tão simples quanto assegurar que um recurso específico do Windows esteja habilitado ou tão complexas quanto a implantação do SharePoint.

A DSC também tem monitoramento e emissão de relatórios internos.
Se um sistema não for mais compatível, a DSC poderá gerar um alerta e agir para corrigir o sistema.

## <a name="benefits-of-using-desired-state-configuration"></a>Benefícios do Uso da Configuração de Estado Desejado

As configurações são concebidas para serem fáceis de ler, armazenar e atualizar.
As configurações declaram o estado em que os dispositivos de destino devem estar, em vez de escrever instruções de como usá-los nesse estado.
Assim, fica mais barato aprender, adotar, implementar e manter a configuração por meio da DSC.

A criação de configurações significa que etapas complexas de implantação são capturadas como uma "única fonte da verdade" em um único local.
Isso diminui a probabilidade de erros em implantações repetidas de um conjunto específico de máquinas.
Por sua vez, agiliza e torna as implantações mais confiáveis, o que permite um retorno rápido em implantações complexas.

As configurações também podem ser compartilhadas por meio da [Galeria do PowerShell](https://powershellgallery.com), o que significa que talvez já existam cenários comuns e práticas recomendadas para o trabalho necessário.


## <a name="desired-state-configuration-and-devops"></a>Desired State Configuration e DevOps

A DSC foi projetada com [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) em mente, uma combinação de pessoas, processos e ferramentas que permitem implantar e iterar rapidamente visando fornecer valor a usuários finais internos ou externos.
Com uma única configuração definindo um ambiente, os desenvolvedores podem codificar seus requisitos em uma única configuração e verificar essa configuração no controle do código-fonte. Assim, as equipes de operações podem implantar facilmente o código sem precisar realizar processos manuais propensos a erro.

As configurações também são [controladas por dados](../configurations/configData.md), o que ajuda as equipes de operações a identificar e alterar os ambientes sem a intervenção do desenvolvedor.

## <a name="desired-state-configuration-on-premises-and-off-premises"></a>Desired State Configuration local e externamente
A DSC pode ser usada para gerenciar implantações locais e externas.
Para soluções locais, a DSC tem um [servidor pull](../pull-server/pullServer.md) que pode ser utilizado para centralizar o gerenciamento de máquinas e relatar seu status.
Para soluções de nuvem, a DSC é útil onde quer que o Windows seja utilizável.
Também há ofertas específicas do Azure integradas na Configuração de Estado Desejado, como a [Automação do Azure](https://azure.microsoft.com/en-us/documentation/services/automation/), que centraliza os relatórios de DSC.

## <a name="dsc-and-compatibility"></a>DSC e Compatibilidade

Embora a DSC tenha sido introduzida no Windows Server 2012 R2, ela está disponível para sistemas operacionais de nível inferior por meio do pacote do WMF (Windows Management Framework).
Mais informações sobre o WMF podem ser encontradas na [home page do PowerShell](/powershell/).

A DSC também pode ser usada para gerenciar o Linux. Para saber mais, veja [Introdução à DSC para Linux](../getting-started/lnxGettingStarted.md).
