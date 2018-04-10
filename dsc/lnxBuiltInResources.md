---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC,powershell,configuração,instalação
title: Recursos Internos de Configuração de Estado Desejado para Linux
ms.openlocfilehash: 77617b72584f39c46fc4b9eb67235378bbfc19aa
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a><span data-ttu-id="3c60b-103">Recursos Internos de Configuração de Estado Desejado para Linux</span><span class="sxs-lookup"><span data-stu-id="3c60b-103">Built-In Desired State Configuration Resources for Linux</span></span>

<span data-ttu-id="3c60b-104">Os recursos são blocos de construção que você pode usar para escrever um script de Configuração de Estado Desejado (DSC) do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3c60b-104">Resources are building blocks that you can use to write a PowerShell Desired State Configuration (DSC) script.</span></span> <span data-ttu-id="3c60b-105">A DSC para Linux vem com um conjunto de funcionalidade interna para configurar recursos, como arquivos e pastas, pacotes, variáveis de ambiente, serviços e processos.</span><span class="sxs-lookup"><span data-stu-id="3c60b-105">DSC for Linux comes with a set of built-in functionality for configuring resources such as files and folders, packages, environment variables, and services and processes.</span></span>

## <a name="built-in-resources"></a><span data-ttu-id="3c60b-106">Recursos internos</span><span class="sxs-lookup"><span data-stu-id="3c60b-106">Built-in resources</span></span>

<span data-ttu-id="3c60b-107">A tabela a seguir fornece uma lista desses recursos e links para tópicos que os descrevem detalhadamente.</span><span class="sxs-lookup"><span data-stu-id="3c60b-107">The following table provides a list of these resources and links to topics that describe them in detail.</span></span>

* <span data-ttu-id="3c60b-108">[Recurso nxArchive](lnxArchiveResource.md) — fornece um mecanismo para descompactar arquivos mortos (. tar,. zip) em um caminho específico.</span><span class="sxs-lookup"><span data-stu-id="3c60b-108">[nxArchive Resource](lnxArchiveResource.md)--Provides a mechanism to unpack archive (.tar, .zip) files at a specific path.</span></span>
* <span data-ttu-id="3c60b-109">[Recurso nxEnvironment](lnxEnvironmentResource.md) — gerencia as variáveis de ambiente em nós de destino.</span><span class="sxs-lookup"><span data-stu-id="3c60b-109">[nxEnvironment Resource](lnxEnvironmentResource.md)--Manages environment variables on target nodes.</span></span>
* <span data-ttu-id="3c60b-110">[Recurso nxFile](lnxFileResource.md) — gerencia arquivos e diretórios do Linux.</span><span class="sxs-lookup"><span data-stu-id="3c60b-110">[nxFile Resource](lnxFileResource.md)--Manages Linux files and directories.</span></span>
* <span data-ttu-id="3c60b-111">[Recurso nxFileLine](lnxFileLineResource.md) — gerencia linhas individuais em um arquivo do Linux.</span><span class="sxs-lookup"><span data-stu-id="3c60b-111">[nxFileLine Resource](lnxFileLineResource.md)--Manages individual lines in a Linux file.</span></span>
* <span data-ttu-id="3c60b-112">[Recurso nxGroup](lnxGroupResource.md) — gerencia grupos locais do Linux.</span><span class="sxs-lookup"><span data-stu-id="3c60b-112">[nxGroup Resource](lnxGroupResource.md)--Manages local Linux groups.</span></span>
* <span data-ttu-id="3c60b-113">[nxPackage Resource](lnxPackageResource.md) — gerencia pacotes em nós Linux.</span><span class="sxs-lookup"><span data-stu-id="3c60b-113">[nxPackage Resource](lnxPackageResource.md)--Manages packages on Linux nodes.</span></span>
* <span data-ttu-id="3c60b-114">[Recurso nxScript](lnxScriptResource.md) — executa scripts em nós de destino.</span><span class="sxs-lookup"><span data-stu-id="3c60b-114">[nxScript Resource](lnxScriptResource.md)--Runs scripts on target nodes.</span></span>
* <span data-ttu-id="3c60b-115">[Recurso nxService](lnxServiceResource.md) — gerencia serviços do Linux (daemons).</span><span class="sxs-lookup"><span data-stu-id="3c60b-115">[nxService Resource](lnxServiceResource.md)--Manages Linux services (daemons).</span></span>
* <span data-ttu-id="3c60b-116">[Recurso nxSshAuthorizedKeys](lnxSshAuthorizedKeysResource.md) — gerencia chaves ssh públicas para um usuário do Linux.</span><span class="sxs-lookup"><span data-stu-id="3c60b-116">[nxSshAuthorizedKeys Resource](lnxSshAuthorizedKeysResource.md)--Manages public ssh keys for a Linux user.</span></span>
* <span data-ttu-id="3c60b-117">[Recurso nxUser](lnxUserResource.md) — gerencia usuários locais do Linux.</span><span class="sxs-lookup"><span data-stu-id="3c60b-117">[nxUser Resource](lnxUserResource.md)--Manages local Linux users.</span></span>