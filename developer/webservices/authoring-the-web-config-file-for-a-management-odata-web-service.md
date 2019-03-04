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
# <a name="authoring-the-webconfig-file-for-a-management-odata-web-service"></a>Criação do arquivo Web.config para um serviço Web OData de gerenciamento

Antes de implantar o serviço web de OData de gerenciamento, você deve configurar o arquivo Web. config para apontar para os arquivos de esquema XML e as DLLs que implementam o [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) e [ Casse](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) interfaces.

## <a name="sample-config-file"></a>Arquivo de configuração de exemplo

O exemplo a seguir é um exemplo da aparência do arquivo Web. config para o serviço web.

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

## <a name="see-also"></a>Consulte Também

[Implementar a autorização de personalizado para um serviço da web OData de gerenciamento](./implementing-custom-authorization-for-a-management-odata-web-service.md)

[Implementando SessionConfiguration para um serviço da web OData de gerenciamento](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

[O arquivo de esquema MOF para um serviço da web OData de gerenciamento de criação](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[O arquivo de esquema XML para um serviço da web OData de gerenciamento de criação](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

[Criando um serviço Web OData de gerenciamento](./creating-a-management-odata-web-service.md)