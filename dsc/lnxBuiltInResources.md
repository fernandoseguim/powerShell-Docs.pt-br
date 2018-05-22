---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recursos Internos de Configuração de Estado Desejado para Linux
ms.openlocfilehash: ea700d24c7ff4377af671944184abb3f201852e8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
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