---
title: Configurar a autorização baseada em função | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2933a6ca-fe92-4ba2-97ee-ef0f0d5fdfcf
caps.latest.revision: 8
ms.openlocfilehash: b73284adb4bf228510bf8134aa4c6a10561b7ea2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859592"
---
# <a name="configuring-role-based-authorization"></a>Configurar a autorização baseada em função

Este tópico demonstra como configurar a política de autorização baseada em função para a implementação de exemplo do [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interface descrita em [personalizado implementando Autorização para a extensão IIS OData de gerenciamento](./implementing-custom-authorization-for-a-management-odata-web-service.md).

Neste exemplo, você irá configurar um arquivo XML que é usado pelo aplicativo de OData de gerenciamento de exemplo para definir a política de autorização. Você criará duas funções e associar diferentes módulos do Windows PowerShell que contêm fluxos de trabalho com essas funções. O esquema que define o arquivo XML é listado no [esquema de configuração de autorização baseado em função](./role-based-authorization-configuration-schema.md).

## <a name="modifying-the-rbacconfigurationxml-file"></a>Modificando o arquivo RBacConfiguration.xml

Esse arquivo define a política de autorização para o aplicativo. As funções são definidas usando `Group` nós. Um `Group` nó define os comandos do Windows PowerShell que podem ser executados por usuários atribuídos a esse grupo. Os usuários são atribuídos a grupos usando `User` nós.

Nestes exemplos, você irá adicionar um módulo para o administrador `Group` nó, e adicionar um usuário a cada grupo.

#### <a name="adding-a-module-to-a-group-node"></a>Adicionar um módulo a um nó de grupo

1. Crie um arquivo chamado **RBacConfiguration.xml** em um editor de texto. Esse arquivo deve ser salvo para o diretório principal do aplicativo para o serviço web. Insira o seguinte texto no arquivo.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <RbacConfiguration>
     <Groups>
       <!--Group consists of the following:
         Name:  Name of the group
         UserName (Optional): Windows Identity user name
         Password (Optional): Password of the Windows user name
         DomainName (Optional): Domain for the user. For local machine account either do not include them or give the machine name. Do not give empty string
         MapIncomingUser (Optional): Boolean value indicating whether to execute cmdlet in the context of network client.

         User credentials and MapIncomingUser=true are exclusive.
       -->
       <Group Name="NonAdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Set-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
       </Group>
       <Group Name="AdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
         <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
       </Group>
     </Groups>
     <Users>
       <!-- User consists of the following :
         Name: Name of the user. If a user is from a cer
         AuthenticationType: Authentication type used.
         DomainName (Optional): Domain for the user
       -->
       <User Name="localNonAdmin" AuthenticationType="Basic" GroupName="NonAdminGroup" />
       <User Name="localAdmin" AuthenticationType="Basic" GroupName="AdminGroup" />
     </Users>
   </RbacConfiguration>
   ```

2. O arquivo contém dois `Group` nós. Elas representam as duas funções usadas neste exemplo, o `NonAdminGroup` e o `AdminGroup` funções.

   Diretamente após o fechamento `Cmdlets` marca no primeiro `Group` nó, adicione o seguinte XML:

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a>Adicionar um usuário a um nó de grupo

1. Abra o **RBacConfiguration.xml** em um editor de texto. Esse arquivo está localizado na pasta c:\\\inetpub\wwwroot\Modata se você não alterou o nome do ponto de extremidade antes da instalação.

2. Diretamente após a marca de fechamento no `Users` nó, adicione o seguinte XML:

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. Diretamente após o XML adicionado na etapa anterior, adicione o seguinte XML:

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```