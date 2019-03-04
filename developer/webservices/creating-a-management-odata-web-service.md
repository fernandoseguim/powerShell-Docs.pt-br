---
title: Criando um serviço Web OData de gerenciamento | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06b1b050-0bf7-48f5-ba05-43f489d597c0
caps.latest.revision: 10
ms.openlocfilehash: 476fce9fc087b870bad93a9204a820c5a84df99e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856622"
---
# <a name="creating-a-management-odata-web-service"></a>Criar um serviço Web OData de gerenciamento

Extensão IIS do Management ODATA é uma infraestrutura para a criação de um ponto de extremidade de serviço web ASP.NET que expõe os dados de gerenciamento, acessados por meio de cmdlets do Windows PowerShell e scripts, como entidades de serviço OData Web. Ele faz isso processando solicitações de OData e convertendo-as em uma invocação do Windows PowerShell. As equipes de produto podem se basear nessa infra-estrutura para criar pontos de extremidade que expõem os conjuntos de dados de gerenciamento específicos.

Baixe e instale o [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) exemplo. Siga as instruções para implantar o serviço web. Este serviço web expõe os serviços e processos por meio de operações criar, ler, atualizar e excluir (CRUD). Solicitações CRUD feitas ao serviço web de chamam comandos do Windows PowerShell que executam as operações solicitadas. Um mapeamento entre as operações CRUD e os comandos do Windows PowerShell subjacentes é implementado por Schema. XML, MOF e arquivos de esquema de dois. O arquivo MOF usa o [Distributed Management Task Force](https://www.dmtf.org/) standard (DMTF) MOF (Managed Object). O arquivo Schema. XML usa um esquema XML que é descrito em [esquema de mapeamento de recursos](./resource-mapping-schema.md).

> [!IMPORTANT]
> Antes de habilitar a extensão IIS do Management ODATA no Windows Server 2008 R2 SP1, os recursos a seguir devem ser habilitados.
>
> 1.  IIS-WebServerRole
> 2.  IIS-WebServer
> 3.  IIS-HttpTracing
> 4.  IIS-ManagementOData

## <a name="steps-for-creating-a-management-odata-web-service"></a>Etapas para criar um serviço web de OData de gerenciamento

Os tópicos a seguir descrevem como criar e implantar um serviço web de OData de gerenciamento.

- [Adicionar recursos a um serviço Web OData de gerenciamento](./adding-resources-to-a-management-odata-web-service.md)

- [Implementar a autorização de personalizado para um serviço da web OData de gerenciamento](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [Implementando SessionConfiguration para um serviço da web OData de gerenciamento](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [O arquivo de esquema MOF para um serviço da web OData de gerenciamento de criação](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [O arquivo de esquema XML para um serviço da web OData de gerenciamento de criação](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [O arquivo Web. config para um serviço da web OData de gerenciamento de criação](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [Implantando um serviço web de OData de gerenciamento](./deploying-a-management-odata-web-service.md)

- [Associação de entidades de OData de gerenciamento](./associating-management-odata-entities.md)

## <a name="see-also"></a>Consulte Também

[Esquema de extensão IIS ODATA de gerenciamento de arquivos](./management-odata-iis-extension-schema-files.md)
