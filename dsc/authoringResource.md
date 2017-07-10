---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Criar recursos personalizados de configuração de estado desejado do Windows PowerShell"
ms.openlocfilehash: 75b494db4ee6e381491decb11d35b60105217a0f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
<a id="build-custom-windows-powershell-desired-state-configuration-resources" class="xliff"></a>
# Criar recursos personalizados de configuração de estado desejado do Windows PowerShell

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

A Configuração de Estado Desejado (DSC) do Windows PowerShell tem recursos internos que podem ser usados para configurar seu ambiente. (Para obter mais informações, consulte [Recursos Internos de Configuração de Estado Desejado do Windows PowerShell](builtInResource.md).) Este tópico fornece uma visão geral do desenvolvimento de recursos e links para tópicos com exemplos e informações específicas.

<a id="dsc-resource-components" class="xliff"></a>
## Componentes de recursos de DSC

Um recurso de DSC é um módulo do Windows PowerShell. O módulo contém o esquema (a definição das propriedades configuráveis) e a implementação (o código que faz o trabalho real especificado por uma configuração) do recurso. Um esquema de recursos de DSC pode ser definido em um arquivo MOF e a implementação é executada por um módulo de script. Começando com o suporte das classes do PowerShell na versão 5, o esquema e a implementação podem ser definidos em uma classe. Os tópicos a seguir descrevem detalhadamente como criar recursos de DSC.

* [Escrevendo um recurso personalizado de DSC com MOF](authoringResourceMOF.md) 
* [Implementando um recurso de DSC em C#](authoringResourceMofCS.md) 
* [Escrevendo um recurso personalizado de DSC com classes do PowerShell](authoringResourceClass.md) 
* [Recursos de composição: usando uma configuração DSC como um recurso](authoringResourceComposite.md) 
* [Usando a ferramenta Designer de Recursos](authoringResourceMofDesigner.md) 

