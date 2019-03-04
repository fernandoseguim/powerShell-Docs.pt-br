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
# <a name="creating-a-management-odata-web-service"></a><span data-ttu-id="1fbeb-102">Criar um serviço Web OData de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="1fbeb-102">Creating a Management OData Web Service</span></span>

<span data-ttu-id="1fbeb-103">Extensão IIS do Management ODATA é uma infraestrutura para a criação de um ponto de extremidade de serviço web ASP.NET que expõe os dados de gerenciamento, acessados por meio de cmdlets do Windows PowerShell e scripts, como entidades de serviço OData Web.</span><span class="sxs-lookup"><span data-stu-id="1fbeb-103">Management ODATA IIS Extension is an infrastructure for creating an ASP.NET web service end point that exposes your management data, accessed through Windows PowerShell cmdlets and scripts, as OData Web service entities.</span></span> <span data-ttu-id="1fbeb-104">Ele faz isso processando solicitações de OData e convertendo-as em uma invocação do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1fbeb-104">It does that by processing OData requests and converting them into a Windows PowerShell invocation.</span></span> <span data-ttu-id="1fbeb-105">As equipes de produto podem se basear nessa infra-estrutura para criar pontos de extremidade que expõem os conjuntos de dados de gerenciamento específicos.</span><span class="sxs-lookup"><span data-stu-id="1fbeb-105">Product teams can build on top of this infrastructure to create endpoints that expose specific sets of management data.</span></span>

<span data-ttu-id="1fbeb-106">Baixe e instale o [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) exemplo.</span><span class="sxs-lookup"><span data-stu-id="1fbeb-106">Download and install the [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) sample.</span></span> <span data-ttu-id="1fbeb-107">Siga as instruções para implantar o serviço web.</span><span class="sxs-lookup"><span data-stu-id="1fbeb-107">Follow the instructions to deploy the web service.</span></span> <span data-ttu-id="1fbeb-108">Este serviço web expõe os serviços e processos por meio de operações criar, ler, atualizar e excluir (CRUD).</span><span class="sxs-lookup"><span data-stu-id="1fbeb-108">This web service exposes Services and Processes through Create, Read, Update, and Delete (CRUD) operations.</span></span> <span data-ttu-id="1fbeb-109">Solicitações CRUD feitas ao serviço web de chamam comandos do Windows PowerShell que executam as operações solicitadas.</span><span class="sxs-lookup"><span data-stu-id="1fbeb-109">CRUD requests made to the web service invoke  Windows PowerShell commands that perform the requested operations.</span></span> <span data-ttu-id="1fbeb-110">Um mapeamento entre as operações CRUD e os comandos do Windows PowerShell subjacentes é implementado por Schema. XML, MOF e arquivos de esquema de dois.</span><span class="sxs-lookup"><span data-stu-id="1fbeb-110">A mapping between the CRUD operations and the underlying Windows PowerShell commands is implemented by two schema files, schema.mof and schema.xml.</span></span> <span data-ttu-id="1fbeb-111">O arquivo MOF usa o [Distributed Management Task Force](https://www.dmtf.org/) standard (DMTF) MOF (Managed Object).</span><span class="sxs-lookup"><span data-stu-id="1fbeb-111">The schema.mof file uses the [Distributed Management  Task Force](https://www.dmtf.org/) (DMTF) Managed Object (MOF) standard.</span></span> <span data-ttu-id="1fbeb-112">O arquivo Schema. XML usa um esquema XML que é descrito em [esquema de mapeamento de recursos](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="1fbeb-112">The schema.xml file uses an XML schema that is described in [Resource Mapping Schema](./resource-mapping-schema.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1fbeb-113">Antes de habilitar a extensão IIS do Management ODATA no Windows Server 2008 R2 SP1, os recursos a seguir devem ser habilitados.</span><span class="sxs-lookup"><span data-stu-id="1fbeb-113">Before you enabling Management ODATA IIS Extension on Windows Server 2008 R2 SP1, the following features must be enabled.</span></span>
>
> 1.  <span data-ttu-id="1fbeb-114">IIS-WebServerRole</span><span class="sxs-lookup"><span data-stu-id="1fbeb-114">IIS-WebServerRole</span></span>
> 2.  <span data-ttu-id="1fbeb-115">IIS-WebServer</span><span class="sxs-lookup"><span data-stu-id="1fbeb-115">IIS-WebServer</span></span>
> 3.  <span data-ttu-id="1fbeb-116">IIS-HttpTracing</span><span class="sxs-lookup"><span data-stu-id="1fbeb-116">IIS-HttpTracing</span></span>
> 4.  <span data-ttu-id="1fbeb-117">IIS-ManagementOData</span><span class="sxs-lookup"><span data-stu-id="1fbeb-117">IIS-ManagementOData</span></span>

## <a name="steps-for-creating-a-management-odata-web-service"></a><span data-ttu-id="1fbeb-118">Etapas para criar um serviço web de OData de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="1fbeb-118">Steps for creating a Management OData web service</span></span>

<span data-ttu-id="1fbeb-119">Os tópicos a seguir descrevem como criar e implantar um serviço web de OData de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="1fbeb-119">The following topics describe how to create and deploy a Management OData web service.</span></span>

- [<span data-ttu-id="1fbeb-120">Adicionar recursos a um serviço Web OData de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="1fbeb-120">Adding Resources to a Management OData Web Service</span></span>](./adding-resources-to-a-management-odata-web-service.md)

- [<span data-ttu-id="1fbeb-121">Implementar a autorização de personalizado para um serviço da web OData de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="1fbeb-121">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [<span data-ttu-id="1fbeb-122">Implementando SessionConfiguration para um serviço da web OData de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="1fbeb-122">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [<span data-ttu-id="1fbeb-123">O arquivo de esquema MOF para um serviço da web OData de gerenciamento de criação</span><span class="sxs-lookup"><span data-stu-id="1fbeb-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="1fbeb-124">O arquivo de esquema XML para um serviço da web OData de gerenciamento de criação</span><span class="sxs-lookup"><span data-stu-id="1fbeb-124">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="1fbeb-125">O arquivo Web. config para um serviço da web OData de gerenciamento de criação</span><span class="sxs-lookup"><span data-stu-id="1fbeb-125">Authoring the Web.config file for a Management OData web service</span></span>](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="1fbeb-126">Implantando um serviço web de OData de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="1fbeb-126">Deploying a Management OData web service</span></span>](./deploying-a-management-odata-web-service.md)

- [<span data-ttu-id="1fbeb-127">Associação de entidades de OData de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="1fbeb-127">Associating Management OData Entities</span></span>](./associating-management-odata-entities.md)

## <a name="see-also"></a><span data-ttu-id="1fbeb-128">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="1fbeb-128">See Also</span></span>

[<span data-ttu-id="1fbeb-129">Esquema de extensão IIS ODATA de gerenciamento de arquivos</span><span class="sxs-lookup"><span data-stu-id="1fbeb-129">Management ODATA IIS Extension Schema Files</span></span>](./management-odata-iis-extension-schema-files.md)
