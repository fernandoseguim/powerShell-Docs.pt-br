---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Criar recursos personalizados de configuração de estado desejado do Windows PowerShell"
ms.openlocfilehash: 4751bcaab1996ee3164bd2a2f430c3b188712860
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="b7688-103">Criar recursos personalizados de configuração de estado desejado do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b7688-103">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="b7688-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b7688-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b7688-105">A Configuração de Estado Desejado (DSC) do Windows PowerShell tem recursos internos que podem ser usados para configurar seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="b7688-105">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="b7688-106">(Para obter mais informações, consulte [Recursos Internos de Configuração de Estado Desejado do Windows PowerShell](builtInResource.md).) Este tópico fornece uma visão geral do desenvolvimento de recursos e links para tópicos com exemplos e informações específicas.</span><span class="sxs-lookup"><span data-stu-id="b7688-106">(For more information, see [Built-In Windows PowerShell Desired State Configuration Resources](builtInResource.md).) This topic provides an overview of developing resources and links to topics with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="b7688-107">Componentes de recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="b7688-107">DSC resource components</span></span>

<span data-ttu-id="b7688-108">Um recurso de DSC é um módulo do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b7688-108">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="b7688-109">O módulo contém o esquema (a definição das propriedades configuráveis) e a implementação (o código que faz o trabalho real especificado por uma configuração) do recurso.</span><span class="sxs-lookup"><span data-stu-id="b7688-109">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="b7688-110">Um esquema de recursos de DSC pode ser definido em um arquivo MOF e a implementação é executada por um módulo de script.</span><span class="sxs-lookup"><span data-stu-id="b7688-110">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="b7688-111">Começando com o suporte das classes do PowerShell na versão 5, o esquema e a implementação podem ser definidos em uma classe.</span><span class="sxs-lookup"><span data-stu-id="b7688-111">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="b7688-112">Os tópicos a seguir descrevem detalhadamente como criar recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="b7688-112">The following topics describe in more detail how to create DSC resources.</span></span>

* [<span data-ttu-id="b7688-113">Escrevendo um recurso personalizado de DSC com MOF</span><span class="sxs-lookup"><span data-stu-id="b7688-113">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="b7688-114">Implementando um recurso de DSC em C#</span><span class="sxs-lookup"><span data-stu-id="b7688-114">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
* [<span data-ttu-id="b7688-115">Escrevendo um recurso personalizado de DSC com classes do PowerShell</span><span class="sxs-lookup"><span data-stu-id="b7688-115">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
* [<span data-ttu-id="b7688-116">Recursos de composição: usando uma configuração DSC como um recurso</span><span class="sxs-lookup"><span data-stu-id="b7688-116">Composite resources: Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
* [<span data-ttu-id="b7688-117">Usando a ferramenta Designer de Recursos</span><span class="sxs-lookup"><span data-stu-id="b7688-117">Using the Resource Designer tool</span></span>](authoringResourceMofDesigner.md)

