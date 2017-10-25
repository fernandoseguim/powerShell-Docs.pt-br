---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Recursos Internos de Configuração de Estado Desejado para Linux"
ms.openlocfilehash: b85f32f7559d89bda566d35462cc613d73424c50
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
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
  
