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
# <a name="built-in-desired-state-configuration-resources-for-linux"></a>Recursos Internos de Configuração de Estado Desejado para Linux

Os recursos são blocos de construção que você pode usar para escrever um script de Configuração de Estado Desejado (DSC) do PowerShell. A DSC para Linux vem com um conjunto de funcionalidade interna para configurar recursos, como arquivos e pastas, pacotes, variáveis de ambiente, serviços e processos.

## <a name="built-in-resources"></a>Recursos internos

A tabela a seguir fornece uma lista desses recursos e links para tópicos que os descrevem detalhadamente.

* [Recurso nxArchive](lnxArchiveResource.md) — fornece um mecanismo para descompactar arquivos mortos (. tar,. zip) em um caminho específico.
* [Recurso nxEnvironment](lnxEnvironmentResource.md) — gerencia as variáveis de ambiente em nós de destino.
* [Recurso nxFile](lnxFileResource.md) — gerencia arquivos e diretórios do Linux.
* [Recurso nxFileLine](lnxFileLineResource.md) — gerencia linhas individuais em um arquivo do Linux.
* [Recurso nxGroup](lnxGroupResource.md) — gerencia grupos locais do Linux.
* [nxPackage Resource](lnxPackageResource.md) — gerencia pacotes em nós Linux.
* [Recurso nxScript](lnxScriptResource.md) — executa scripts em nós de destino.
* [Recurso nxService](lnxServiceResource.md) — gerencia serviços do Linux (daemons).
* [Recurso nxSshAuthorizedKeys](lnxSshAuthorizedKeysResource.md) — gerencia chaves ssh públicas para um usuário do Linux.
* [Recurso nxUser](lnxUserResource.md) — gerencia usuários locais do Linux.