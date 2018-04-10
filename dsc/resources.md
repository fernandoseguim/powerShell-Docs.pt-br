---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC,powershell,configuração,instalação
title: Recursos de DSC
ms.openlocfilehash: e393c8fe2e1ba8d68ba9aa1b656d1e5ebfad30e8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-resources"></a>Recursos de DSC

>Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

Os Recursos de Configuração de Estado Desejado (DSC) fornecem os blocos de construção para uma configuração DSC. Um recurso expõe propriedades que podem ser configuradas (esquema) e contém as funções de script do PowerShell que o Gerenciador de Configurações Local (LCM) chama de "realizar".

Um recurso pode modelar algo tão genérico quanto um arquivo ou tão específico quanto uma configuração de servidor do IIS.  Grupos de recursos semelhantes são combinados em um Módulo de DSC, que organiza todos os arquivos necessários em uma estrutura que é portátil e inclui metadados para identificar como os recursos devem ser usados.

Os tópicos a seguir descrevem os recursos de DSC:

- [Recursos internos de DSC](builtInResource.md)
- [Criar recursos personalizados de DSC](authoringResource.md)
- [Recursos internos de DSC para Linux](lnxBuiltInResources.md)