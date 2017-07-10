---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: Recursos de DSC
ms.openlocfilehash: 62bf352b929d661e585e145e5aab0f44f13010a1
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
<a id="dsc-resources" class="xliff"></a>
# Recursos de DSC

>Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

Os Recursos de Configuração de Estado Desejado (DSC) fornecem os blocos de construção para uma configuração DSC. Um recurso expõe propriedades que podem ser configuradas (esquema) e contém as funções de script do PowerShell que o Gerenciador de Configurações Local (LCM) chama de "realizar".

Um recurso pode modelar algo tão genérico quanto um arquivo ou tão específico quanto uma configuração de servidor do IIS.  Grupos de recursos semelhantes são combinados em um Módulo de DSC, que organiza todos os arquivos necessários em uma estrutura que é portátil e inclui metadados para identificar como os recursos devem ser usados.  

Os tópicos a seguir descrevem os recursos de DSC:

- [Recursos internos de DSC](builtInResource.md)
- [Criar recursos personalizados de DSC](authoringResource.md)
- [Recursos internos de DSC para Linux](lnxBuiltInResources.md)

