---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Visão Geral da Configuração de Estado Desejado para Tomadores de Decisão"
ms.openlocfilehash: 1800acfa9edae4f65e34db380ff719ad4c034921
ms.sourcegitcommit: 60f06a06c2fce63024f3f4cbd7657b1dfe7fcb1a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2018
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>Visão Geral da Configuração de Estado Desejado para Tomadores de Decisão

Este documento descreve os benefícios comerciais do uso da Configuração de Estado Desejado (DSC) do PowerShell. Não é um guia técnico.

## <a name="what-is-desired-state-configuration"></a>Qual é a Configuração de Estado Desejado?

A DSC (Configuração de Estado Desejado) do Windows PowerShell fornece uma plataforma de gerenciamento de configuração integrada no Windows que se baseia em padrões abertos. A DSC é flexível o suficiente para funcionar de maneira confiável e consistente em cada estágio do ciclo de vida de implantação (desenvolvimento, teste, pré-produção, produção), bem como durante a expansão. 

A DSC gira em torno de "[configurações](https://msdn.microsoft.com/en-us/powershell/dsc/configurations)".
Uma configuração é um documento fácil de ler que descreve um ambiente composto por computadores ("nós") com características específicas. Essas características podem ser tão simples quanto assegurar que um recurso específico do Windows esteja habilitado ou tão complexas quanto a implantação do SharePoint. 

A DSC também tem monitoramento e emissão de relatórios internos. Se um sistema não for mais compatível, a DSC poderá gerar um alerta e agir para corrigir o sistema. 

## <a name="benefits-of-using-desired-state-configuration"></a>Benefícios do Uso da Configuração de Estado Desejado

As configurações são concebidas para serem fáceis de ler, armazenar e atualizar. As configurações declaram o estado em que os dispositivos de destino devem estar, em vez de escrever instruções de como usá-los nesse estado. Assim, fica mais barato aprender, adotar, implementar e manter a configuração por meio da DSC. 

A criação de configurações significa que etapas complexas de implantação são capturadas como uma "única fonte da verdade" em um único local. Isso diminui a probabilidade de erros em implantações repetidas de um conjunto específico de máquinas. Por sua vez, agiliza e torna as implantações mais confiáveis, o que permite um retorno rápido em implantações complexas.

As configurações também podem ser compartilhadas por meio da [Galeria do PowerShell](https://powershellgallery.com), o que significa que cenários comuns e práticas recomendadas talvez já existam para o trabalho necessário.


## <a name="desired-state-configuration-and-devops"></a>Configuração de Estado Desejado e DevOps

[DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) é uma combinação de pessoas, processos e ferramentas que permitem uma rápida implantação e iteração concentradas em proporcionar vantagens para os usuários finais internos ou externos. A DSC foi concebida pensando em DevOps. Ter uma única configuração definindo um ambiente significa que os desenvolvedores podem codificar seus requisitos em uma configuração, verificar essa configuração no controle do código-fonte e as equipes de operações podem implantar facilmente o código sem precisar passar por processos manuais propensos a erro. 

As configurações também são [orientadas a dados](https://msdn.microsoft.com/en-us/powershell/dsc/configdata), o que ajuda as equipes de operações a identificar e alterar os ambientes sem a intervenção do desenvolvedor. 

## <a name="desired-state-configuration-on--and-off-premises"></a>Desired State Configuration local e externo

A DSC pode ser usada para gerenciar implantações locais e externas. Para soluções locais, a DSC tem um [servidor pull](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver) que pode ser usado para centralizar o gerenciamento de máquinas e relatar seus status. Para soluções de nuvem, a DSC é útil onde quer que o Windows seja utilizável. Também há ofertas específicas do Azure integradas na Configuração de Estado Desejado, como a [Automação do Azure](https://azure.microsoft.com/en-us/documentation/services/automation/), que centraliza os relatórios de DSC. 

## <a name="dsc-and-compatibility"></a>DSC e Compatibilidade

Embora a DSC tenha sido introduzida no Windows Server 2012 R2, está disponível para sistemas operacionais de nível inferior por meio do pacote do Windows Management Framework (WMF). Mais informações sobre o WMF podem ser encontradas na [home page do PowerShell](https://msdn.microsoft.com/en-us/powershell/). 

A DSC também pode ser usada para gerenciar o Linux. Para saber mais, veja [Introdução à DSC para Linux](https://msdn.microsoft.com/en-us/powershell/dsc/lnxgettingstarted).

