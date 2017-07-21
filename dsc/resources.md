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
# <a name="dsc-resources"></a><span data-ttu-id="e63f3-103">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="e63f3-103">DSC Resources</span></span>

><span data-ttu-id="e63f3-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e63f3-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="e63f3-105">Os Recursos de Configuração de Estado Desejado (DSC) fornecem os blocos de construção para uma configuração DSC.</span><span class="sxs-lookup"><span data-stu-id="e63f3-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="e63f3-106">Um recurso expõe propriedades que podem ser configuradas (esquema) e contém as funções de script do PowerShell que o Gerenciador de Configurações Local (LCM) chama de "realizar".</span><span class="sxs-lookup"><span data-stu-id="e63f3-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="e63f3-107">Um recurso pode modelar algo tão genérico quanto um arquivo ou tão específico quanto uma configuração de servidor do IIS.</span><span class="sxs-lookup"><span data-stu-id="e63f3-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="e63f3-108">Grupos de recursos semelhantes são combinados em um Módulo de DSC, que organiza todos os arquivos necessários em uma estrutura que é portátil e inclui metadados para identificar como os recursos devem ser usados.</span><span class="sxs-lookup"><span data-stu-id="e63f3-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>  

<span data-ttu-id="e63f3-109">Os tópicos a seguir descrevem os recursos de DSC:</span><span class="sxs-lookup"><span data-stu-id="e63f3-109">The following topics describe DSC resources:</span></span>

- [<span data-ttu-id="e63f3-110">Recursos internos de DSC</span><span class="sxs-lookup"><span data-stu-id="e63f3-110">Built-In DSC resources</span></span>](builtInResource.md)
- [<span data-ttu-id="e63f3-111">Criar recursos personalizados de DSC</span><span class="sxs-lookup"><span data-stu-id="e63f3-111">Build custom DSC resources</span></span>](authoringResource.md)
- [<span data-ttu-id="e63f3-112">Recursos internos de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="e63f3-112">Built-In DSC resources for Linux</span></span>](lnxBuiltInResources.md)

