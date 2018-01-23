---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: Recursos de DSC
ms.openlocfilehash: 0994616673b5e447c69c09154bfdb9b9126a88c8
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-resources"></a><span data-ttu-id="48434-103">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="48434-103">DSC Resources</span></span>

><span data-ttu-id="48434-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="48434-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="48434-105">Os Recursos de Configuração de Estado Desejado (DSC) fornecem os blocos de construção para uma configuração DSC.</span><span class="sxs-lookup"><span data-stu-id="48434-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="48434-106">Um recurso expõe propriedades que podem ser configuradas (esquema) e contém as funções de script do PowerShell que o Gerenciador de Configurações Local (LCM) chama de "realizar".</span><span class="sxs-lookup"><span data-stu-id="48434-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="48434-107">Um recurso pode modelar algo tão genérico quanto um arquivo ou tão específico quanto uma configuração de servidor do IIS.</span><span class="sxs-lookup"><span data-stu-id="48434-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="48434-108">Grupos de recursos semelhantes são combinados em um Módulo de DSC, que organiza todos os arquivos necessários em uma estrutura que é portátil e inclui metadados para identificar como os recursos devem ser usados.</span><span class="sxs-lookup"><span data-stu-id="48434-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>  

<span data-ttu-id="48434-109">Os tópicos a seguir descrevem os recursos de DSC:</span><span class="sxs-lookup"><span data-stu-id="48434-109">The following topics describe DSC resources:</span></span>

- [<span data-ttu-id="48434-110">Recursos internos de DSC</span><span class="sxs-lookup"><span data-stu-id="48434-110">Built-In DSC resources</span></span>](builtInResource.md)
- [<span data-ttu-id="48434-111">Criar recursos personalizados de DSC</span><span class="sxs-lookup"><span data-stu-id="48434-111">Build custom DSC resources</span></span>](authoringResource.md)
- [<span data-ttu-id="48434-112">Recursos internos de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="48434-112">Built-In DSC resources for Linux</span></span>](lnxBuiltInResources.md)

