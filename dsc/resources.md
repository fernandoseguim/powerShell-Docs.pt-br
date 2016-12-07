---
title: Recursos de DSC
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 0a27a40b995393c41f0496a5f7fa3f56fbd865dd
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="dsc-resources"></a>Recursos de DSC

>Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

Os Recursos de Configuração de Estado Desejado (DSC) fornecem os blocos de construção para uma configuração DSC. Um recurso expõe propriedades que podem ser configuradas (esquema) e contém as funções de script do PowerShell que o Gerenciador de Configurações Local (LCM) chama de "realizar".

Um recurso pode modelar algo tão genérico quanto um arquivo ou tão específico quanto uma configuração de servidor do IIS.  Grupos de recursos semelhantes são combinados em um Módulo de DSC, que organiza todos os arquivos necessários em uma estrutura que é portátil e inclui metadados para identificar como os recursos devem ser usados.  

Os tópicos a seguir descrevem os recursos de DSC:

- [Recursos internos de DSC](builtInResource.md)
- [Criar recursos personalizados de DSC](authoringResource.md)
- [Recursos internos de DSC para Linux](lnxBuiltInResources.md)

