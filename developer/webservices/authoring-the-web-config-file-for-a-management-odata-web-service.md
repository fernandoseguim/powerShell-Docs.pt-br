---
title: Cria o arquivo Web. config para um serviço da web OData de gerenciamento | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569f5d5-9746-40c0-be5e-f218bc4560f7
caps.latest.revision: 4
ms.openlocfilehash: f52953ee091f05df5f355719ecba788d3d5ee055
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856712"
---
# <a name="authoring-the-webconfig-file-for-a-management-odata-web-service"></a><span data-ttu-id="c55b6-102">Criação do arquivo Web.config para um serviço Web OData de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="c55b6-102">Authoring the Web.config file for a Management OData web service</span></span>

<span data-ttu-id="c55b6-103">Antes de implantar o serviço web de OData de gerenciamento, você deve configurar o arquivo Web. config para apontar para os arquivos de esquema XML e as DLLs que implementam o [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) e [ Casse](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) interfaces.</span><span class="sxs-lookup"><span data-stu-id="c55b6-103">Before you can deploy your Management OData web service, you must configure the web.config file to point to the XML schema files and the DLLs that implement the [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) and  [System.Management.Automation.Remoting.Pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) interfaces.</span></span>

## <a name="sample-config-file"></a><span data-ttu-id="c55b6-104">Arquivo de configuração de exemplo</span><span class="sxs-lookup"><span data-stu-id="c55b6-104">Sample config file</span></span>

<span data-ttu-id="c55b6-105">O exemplo a seguir é um exemplo da aparência do arquivo Web. config para o serviço web.</span><span class="sxs-lookup"><span data-stu-id="c55b6-105">The following is an example of what the web.config file for your web service looks like.</span></span>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
   <configSections>
      <section name="managementOdata" type="Microsoft.Management.Odata.Core.DSConfiguration, Microsoft.Management.OData, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL" />
   </configSections>
   <managementOdata schemaFileName="Schema.mof" resourceMappingFileName="Schema.xml">
      <customAuthorization type="Microsoft.Samples.Management.OData.RoleBasedPlugins.CustomAuthorization" assembly=".\Microsoft.Samples.Management.OData.RoleBasedPlugins.dll" />
      <powershell>
         <sessionConfiguration type="Microsoft.Samples.Management.OData.RoleBasedPlugins.SessionConfiguration" assembly=".\Microsoft.Samples.Management.OData.RoleBasedPlugins.dll" />
      </powershell>
      <commandInvocation enabled="true" />
      <wcfDataServicesConfig>
      </wcfDataServicesConfig>
   </managementOdata>
   <system.serviceModel>
      <behaviors>
         <serviceBehaviors>
            <behavior>
                  <serviceAuthorization serviceAuthorizationManagerType="Microsoft.Management.Odata.Core.CustomAuthorizationManager, Microsoft.Management.OData, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
            </behavior>
         </serviceBehaviors>
      </behaviors>
      <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
   </system.serviceModel>
   <system.webServer>
      <security>
         <authentication>
            <anonymousAuthentication enabled="false" />
            <basicAuthentication enabled="true" />
            <windowsAuthentication enabled="false" />
         </authentication>
      </security>
  </system.webServer>
</configuration>

```

## <a name="see-also"></a><span data-ttu-id="c55b6-106">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="c55b6-106">See Also</span></span>

[<span data-ttu-id="c55b6-107">Implementar a autorização de personalizado para um serviço da web OData de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="c55b6-107">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

[<span data-ttu-id="c55b6-108">Implementando SessionConfiguration para um serviço da web OData de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="c55b6-108">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

[<span data-ttu-id="c55b6-109">O arquivo de esquema MOF para um serviço da web OData de gerenciamento de criação</span><span class="sxs-lookup"><span data-stu-id="c55b6-109">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="c55b6-110">O arquivo de esquema XML para um serviço da web OData de gerenciamento de criação</span><span class="sxs-lookup"><span data-stu-id="c55b6-110">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="c55b6-111">Criando um serviço Web OData de gerenciamento</span><span class="sxs-lookup"><span data-stu-id="c55b6-111">Creating a Management OData Web Service</span></span>](./creating-a-management-odata-web-service.md)