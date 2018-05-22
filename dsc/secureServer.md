---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Práticas recomendadas do servidor de pull
ms.openlocfilehash: 1efc016df6882fa962f59dfd3e53eaa6d6b0c121
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="pull-server-best-practices"></a>Práticas recomendadas do servidor de pull

>Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> O Servidor de Recepção (Recurso do Windows *Serviço DSC*) é um componente compatível com o Windows Server, no entanto, não há planos de oferecer novos recursos ou funcionalidades. É recomendável começar a fazer a transição dos clientes gerenciados para o [DSC de Automação do Azure](/azure/automation/automation-dsc-getting-started) (inclui recursos além do Servidor de Recepção no Windows Server) ou para uma das soluções da comunidade listadas [aqui](pullserver.md#community-solutions-for-pull-service).

Resumo: este documento destina-se a incluir processo e extensibilidade para ajudar os engenheiros que estão se preparando para a solução. Os detalhes devem fornecer as práticas recomendadas, como identificadas por clientes e, em seguida, validadas pela equipe de produto para garantir que as recomendações sejam voltadas para o futuro e consideradas estáveis.

| |Informações do documento|
|:---|:---|
Autor | Michael Greene
Revisores | Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic
Publicado | Abril de 2015

## <a name="abstract"></a>Resumo

Este documento foi criado para fornecer diretrizes oficiais para qualquer pessoa que esteja planejando uma implementação de um servidor de pull de Configuração de Estado Desejado do Windows PowerShell. Um servidor de pull é um serviço simples que deve levar apenas alguns minutos para implantar. Embora ofereça diretrizes técnicas passo a passo que podem ser usadas em uma implantação, o valor desse documento está em servir como uma referência para as práticas recomendadas e no que se deve refletir antes da implantação.
Os leitores devem ter uma familiaridade básica com o DSC e com os termos usados para descrever os componentes que estão incluídos em uma implantação de DSC. Para obter mais informações, consulte o tópico [Visão Geral da Configuração de Estado Desejado do Windows PowerShell](https://technet.microsoft.com/library/dn249912.aspx).
Como é esperado que o DSC evolua em uma cadência de nuvem, espera-se também que a tecnologia subjacente, incluindo o servidor de pull, evolua e introduza novos recursos. Este documento inclui uma tabela de versão no apêndice que fornece referências a versões anteriores e referências a soluções futuras para incentivar designs inovadores.

As duas seções principais deste documento:

 - Planejamento de Configuração
 - Guia de instalação

### <a name="versions-of-the-windows-management-framework"></a>Versões do Windows Management Framework
As informações neste documento destinam-se ao Windows Management Framework 5.0. Embora o WMF 5.0 não seja necessário para a implantação e operação de um servidor de pull, o foco deste documento é a versão 5.0.

### <a name="windows-powershell-desired-state-configuration"></a>Configuração do Estado Desejado do Windows PowerShell
A DSC (Configuração do Estado Desejado) é uma plataforma de gerenciamento que habilita a implantação e gerenciamento de dados de configuração, usando uma sintaxe do setor chamada de MOF (Managed Object Format) para descrever o CIM (modelo CIM). Existe um projeto de software livre, o OMI (Open Management Infrastructure), para promover o desenvolvimento desses padrões entre plataformas, incluindo Linux e sistemas operacionais de hardware de rede. Para obter mais informações, consulte a [página DMTF com vínculo para as especificações de MOF](http://dmtf.org/standards/cim) e [Documentos e Fonte do OMI](https://collaboration.opengroup.org/omi/documents.php).

O Windows PowerShell fornece um conjunto de extensões de linguagem para a Configuração de Estado Desejado que podem ser usadas para criar e gerenciar configurações declarativas.

### <a name="pull-server-role"></a>Função de servidor de pull
Um servidor de pull oferece um serviço centralizado para armazenar configurações que estarão acessíveis aos nós de destino.

A função de servidor de pull pode ser implantada como uma instância de servidor Web ou um compartilhamento de arquivos SMB. A capacidade de servidor Web inclui uma interface de OData e, opcionalmente, pode incluir recursos para que os nós de destino reportem a confirmação de êxito ou de falha conforme as configurações são aplicadas. Essa funcionalidade é útil em ambientes em que há um grande número de nós de destino.
Depois de configurar um nó de destino (também conhecido como um cliente) para apontar para o servidor de pull, os dados de configuração mais recentes e os scripts necessários são baixados e aplicados. Isso pode ser feito como uma implantação única ou como um trabalho recorrente, o que também torna o servidor de pull um ativo importante para o gerenciamento de alteração em grande escala. Para obter mais informações, consulte [Servidores de Pull de Configuração de Estado Desejado do Windows PowerShell](https://technet.microsoft.com/library/dn249913.aspx) e [Modos de Configuração de Push e Pull](https://technet.microsoft.com/library/dn249913.aspx).

## <a name="configuration-planning"></a>Planejamento de configuração

Para qualquer implantação de software empresarial há informações que podem ser coletadas com antecedência para ajudar a planejar a arquitetura correta e se preparar para as etapas necessárias para concluir a implantação. As seções a seguir fornecem informações sobre como se preparar e as conexões organizacionais que provavelmente precisarão acontecer com antecedência.

### <a name="software-requirements"></a>Requisitos de software

A implantação de um servidor de pull requer o recurso de Serviço DSC do Windows Server. Esse recurso foi introduzido no Windows Server 2012 e foi atualizado por meio das versões em andamento do WMF (Windows Management Framework).

### <a name="software-downloads"></a>Downloads de software

Além de instalar o conteúdo mais recente do Windows Update, há dois downloads que são considerados como práticas recomendadas para implantar um servidor de pull de DSC: a versão mais recente do Windows Management Framework e um módulo de DSC para automatizar o provisionamento do servidor de pull.

### <a name="wmf"></a>WINDOWS MANAGEMENT FRAMEWORK

O Windows Server 2012 R2 inclui um recurso chamado de serviço DSC. O recurso de serviço DSC fornece a funcionalidade do servidor de pull, incluindo os binários que oferecem suporte ao ponto de extremidade OData.
O WMF está incluído no Windows Server e é atualizado em uma cadência ágil entre as versões do Windows Server. [Novas versões do WMF 5.0](http://aka.ms/wmf5latest) podem incluir atualizações do recurso de Serviço DSC. Por esse motivo, é uma prática recomendada baixar a versão mais recente do WMF e examinar as notas de versão para determinar se a versão inclui uma atualização do recurso de serviço DSC. Também é necessário examinar a seção das notas de versão que indica se o status de design para uma atualização ou cenário está listado como estável ou experimental.
Para permitir um ciclo de lançamento ágil, recursos individuais podem ser declarados estáveis, o que indica que o recurso está pronto para ser usado em um ambiente de produção ainda que o WMF esteja lançado como visualização.
Outros recursos que têm sido historicamente atualizados por versões do WMF (consulte as Notas de Versão do WMF para obter mais detalhes):

 - Windows PowerShell, ISE (Ambiente de Script Integrado) do Windows PowerShell
 - Serviços Web do Windows PowerShell (Extensão do IIS do Management OData)
 - DSC (Configuração de Estado Desejado) do Windows PowerShell
 - WinRM (Gerenciamento Remoto do Windows) WMI (Instrumentação de Gerenciamento do Windows)

### <a name="dsc-resource"></a>Recurso DSC

Uma implantação de servidor de pull pode ser simplificada através do provisionamento do serviço com o uso de um script de configuração DSC. Este documento inclui scripts de configuração que podem ser usados para implantar um nó de servidor pronto para produção. Para usar os scripts de configuração, é necessário um módulo de DSC que não está incluído no Windows Server. O nome do módulo necessário é **xPSDesiredStateConfiguration**, que inclui o recurso de DSC **xDscWebService**. O módulo xPSDesiredStateConfiguration pode ser baixado [aqui](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).

Use o cmdlet **Install-Module** do módulo **PowerShellGet**.

```powershell
Install-Module xPSDesiredStateConfiguration
```

O módulo **PowerShellGet** baixará o módulo em:

`C:\Program Files\Windows PowerShell\Modules`

Tarefa de planejamento|
---|
Você tem acesso aos arquivos de instalação do Windows Server 2012 R2?|
O ambiente de implantação terá acesso à Internet para baixar o módulo e o WMF da galeria online?|
Como você instalará as atualizações mais recentes de segurança depois de instalar o sistema operacional?|
O ambiente terá acesso à Internet para obter atualizações ou terá um servidor local do WSUS (Windows Server Update Services)?|
Você tem acesso aos arquivos de instalação do Windows Server que já contêm atualizações por meio de injeção offline?|

### <a name="hardware-requirements"></a>Requisitos de hardware

As implantações de servidor de pull têm suporte em servidores físicos e virtuais. Os requisitos de dimensionamento para o servidor de pull estão alinhados com os requisitos do Windows Server 2012 R2.

CPU: processador de 1,4 GHz e 64 bits, Memória: 512 MB, Espaço em disco: 32 GB, Rede: Adaptador Gigabit Ethernet

Tarefa de planejamento|
---|
Você implantará em hardware físico ou em uma plataforma de virtualização?|
Qual é o processo de solicitação de um novo servidor para seu ambiente de destino?|
Qual é o tempo médio de resposta para que um servidor fique disponível?|
Qual tamanho de servidor você solicitará?|

### <a name="accounts"></a>Contas

Não há nenhum requisito de conta de serviço para implantar uma instância de servidor de pull.
No entanto, há situações em que o site pode ser executado em um contexto de uma conta de usuário local.
Por exemplo, se houver a necessidade de acessar um compartilhamento de armazenamento de conteúdo do site e o Windows Server ou o dispositivo que hospeda o compartilhamento de armazenamento não estiverem associados ao domínio.

### <a name="dns-records"></a>Registros DNS

Será necessário um nome do servidor para ser usado durante a configuração de clientes para trabalhar com um ambiente de servidor de pull.
Em ambientes de teste, normalmente será usado o nome do host do servidor ou poderá ser usado o endereço IP para o servidor se a resolução de nomes DNS não estiver disponível.
Em ambientes de produção ou em um ambiente de laboratório que pretende representar uma implantação de produção, a prática recomendada é criar um registro DNS CNAME.

Um DNS CNAME permite a criação de um alias para se referir ao seu registro de host (A).
O objetivo do registro de nome adicional é o aumento da flexibilidade, caso uma alteração seja necessária no futuro.
Um CNAME pode ajudar a isolar a configuração do cliente de maneira que as alterações no ambiente de servidor, como a substituição de um servidor de pull ou adição de servidores de pull, não exijam uma alteração correspondente na configuração do cliente.

Ao escolher um nome para o registro DNS, lembre-se da arquitetura da solução.
Se estiver usando o balanceamento de carga, o certificado usado para proteger o tráfego por meio de HTTPS precisará compartilhar o mesmo nome do registro DNS.

Cenário |Prática recomendada
:---|:---
Ambiente de Teste |Reproduzir o ambiente de produção planejado, se possível. Um nome do host do servidor é adequado para configurações simples. Se o DNS não estiver disponível, um endereço IP poderá ser usado no lugar do nome do host.|
Implantação de Nó único |Criar um registro DNS CNAME que aponta para o nome do host do servidor.|

Para obter mais informações, consulte [Configuração de Round Robin de DNS no Windows Server](https://technet.microsoft.com/en-us/library/cc787484(v=ws.10).aspx).

Tarefa de planejamento|
---|
Você sabe quem contatar para que os registros DNS sejam criados e alterados?|
Qual é o tempo médio de resposta para uma solicitação de um registro DNS?|
Você precisa solicitar registros de nome do host (A) estáticos para servidores?|
O que você solicitará como um CNAME?|
Se necessário, qual tipo de solução de Balanceamento de Carga você utilizará? (consulte a seção intitulada Balanceamento de Carga para obter mais detalhes)|

### <a name="public-key-infrastructure"></a>Infraestrutura de chave pública

A maioria das organizações atuais exige que o tráfego de rede, especialmente o tráfego que inclui dados confidenciais como a maneira que os servidores são configurados, seja validado e/ou criptografado durante o trânsito.
Embora seja possível implantar um servidor de pull usando HTTP, o que facilita as solicitações de clientes em texto não criptografado, é uma prática recomendada proteger o tráfego usando HTTPS. O serviço pode ser configurado para usar HTTPS por meio de um conjunto de parâmetros no recurso de DSC **xPSDesiredStateConfiguration**.

Os requisitos de certificado para proteger o tráfego HTTPS do servidor de pull não são diferentes da proteção de qualquer outro site HTTPS. O modelo de **servidor Web** dos Serviços de Certificado do Windows Server satisfaz os recursos necessários.

Tarefa de planejamento|
---|
Se as solicitações de certificado não são automatizadas, quem você precisará contatar para solicitar um certificado?|
Qual é o tempo médio de resposta para a solicitação?|
Como o arquivo de certificado será transferido para você?|
Como a chave privada do certificado será transferida para você?|
Qual é o tempo de expiração padrão?|
Você estabeleceu um nome DNS para o ambiente de servidor de pull que pode ser usado para o nome do certificado?|

### <a name="choosing-an-architecture"></a>Escolha de uma arquitetura

Um servidor de pull pode ser implantado usando um serviço Web hospedado no IIS ou em um compartilhamento de arquivos SMB. Na maioria das situações, a opção de serviço Web fornecerá maior flexibilidade. Não é incomum que o tráfego HTTPS atravesse os limites da rede, enquanto que o tráfego SMB é geralmente filtrado ou bloqueado entre redes. O serviço Web também oferece a opção de incluir um Servidor de Conformidade ou um Reporting Manager da Web (esses dois tópicos serão abordados em uma versão futura deste documento) que fornecem um mecanismo para os clientes reportarem o status a um servidor para uma visibilidade centralizada.
O SMB fornece uma opção para ambientes em que a política determina que um servidor Web não deve ser utilizado e para outros requisitos de ambientes em que uma função de servidor Web não é desejada.
Em ambos os casos, lembre-se de avaliar os requisitos para assinatura e criptografia de tráfego. O HTTPS, a assinatura SMB e as políticas IPSEC são opções que vale a pena considerar.

#### <a name="load-balancing"></a>Balanceamento de carga
Os clientes interagindo com o serviço Web fazem uma solicitação de informações que é retornada em uma única resposta. Não são necessárias solicitações sequenciais, portanto, não é necessário que a plataforma de balanceamento de carga garanta que as sessões sejam mantidas em um único servidor em qualquer ponto no tempo.

Tarefa de planejamento|
---|
Qual solução será usada para o tráfego de balanceamento de carga entre servidores?|
Se estiver usando um balanceador de carga de hardware, quem receberá uma solicitação para adicionar uma nova configuração ao dispositivo?|
Qual é o tempo médio de resposta de uma solicitação para configurar um novo serviço Web com balanceamento de carga?|
Quais informações serão necessárias para a solicitação?|
Você precisará solicitar um IP adicional ou a equipe responsável pelo balanceamento de carga cuidará disso?|
Você tem os registros DNS necessários e isso será solicitado pela equipe responsável por configurar a solução de balanceamento de carga?|
A solução de balanceamento de carga necessita que o PKI seja manipulado pelo dispositivo ou ele pode balancear a carga de tráfego HTTPS desde que não haja requisitos de sessão?|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a>Configurações e módulos de preparo no servidor de pull

Como parte do planejamento da configuração, será necessário pensar sobre quais módulos de DSC e configurações serão hospedadas pelo servidor de pull. Para fins de planejamento de configuração, é importante ter um entendimento básico de como preparar e implantar conteúdo em um servidor de pull.

No futuro, esta seção será expandida e incluída em um Guia de Operações para Servidor de Pull da DSC.  O guia discutirá o processo diário do gerenciamento de módulos e das configurações ao longo do tempo, com automação.

#### <a name="dsc-modules"></a>Módulos de DSC
Os clientes que solicitam uma configuração precisarão dos módulos necessários de DSC. Automatizar a distribuição por demanda dos módulos de DSC para clientes é uma funcionalidade do servidor de pull. Se estiver implantando um servidor de pull pela primeira vez, talvez como um laboratório ou prova de conceito, você provavelmente vai depender de módulos de DSC que estão disponíveis em repositórios públicos, como a Galeria do PowerShell ou os repositórios PowerShell.org do GitHub para módulos de DSC.

É importante lembrar que mesmo para as fontes confiáveis online como a Galeria do PowerShell, qualquer módulo que é baixado de um repositório público deve ser revisado por alguém com experiência com PowerShell e conhecimento sobre o ambiente em que os módulos serão usados antes de serem usados em produção. Durante a conclusão dessa tarefa é um bom momento para verificar se há qualquer conteúdo adicional no módulo que pode ser removido, como documentação e scripts de exemplo. Isso reduz a largura de banda da rede por cliente em sua primeira solicitação, quando os módulos serão baixados do servidor para o cliente através da rede.

Cada módulo deve ser empacotado em um formato específico, um arquivo ZIP denominado ModuleName_Version.zip que contém o conteúdo do módulo. Depois que o arquivo for copiado para o servidor, um arquivo de soma de verificação deve ser criado. Quando os clientes se conectam ao servidor, a soma de verificação é usada para verificar se o conteúdo do módulo de DSC não foi alterado desde que foi publicado.

```powershell
New-DscCheckSum -ConfigurationPath .\ -OutPath .\
```

Tarefa de planejamento|
---|
Se você estiver planejando um ambiente de laboratório ou de teste, quais cenários serão fundamentais para validar?|
Há módulos disponíveis publicamente que contêm recursos para cobrir tudo o que é necessário ou você precisará criar seus próprios recursos?|
Seu ambiente terá acesso à Internet para recuperar os módulos públicos?|
Quem será responsável por examinar os módulos de DSC?|
Se você estiver planejando um ambiente de produção, o que será usado como repositório local para armazenar os módulos de DSC?|
Uma equipe central aceitará módulos de DSC das equipes de aplicativo? Qual será o processo?|
O empacotamento, a cópia e a criação do seu repositório de origem, de uma soma de verificação para módulos de DSC prontos para a produção no servidor, será automatizada?|
Sua equipe também será responsável pelo gerenciamento da plataforma de automação?|

#### <a name="dsc-configurations"></a>Configurações DSC

A finalidade de um servidor de pull é fornecer um mecanismo centralizado para a distribuição de configurações DSC aos nós de cliente. As configurações são armazenadas no servidor como documentos MOF.
Cada documento será nomeado com um GUID exclusivo. Quando os clientes são configurados para se conectar com um servidor de pull, também recebem o GUID para a configuração que devem solicitar. Esse sistema de referenciar configurações por GUID garante a exclusividade global e é flexível, de modo que uma configuração possa ser aplicada com granularidade por nó ou como uma configuração de função que abrange vários servidores que devem ter configurações idênticas.

#### <a name="guids"></a>GUIDs

O planejamento de GUIDs de configuração merece atenção adicional quando se pensa em uma implantação de servidor de pull. Não há nenhum requisito específico para manipular GUIDs e é provável que o processo seja exclusivo para cada ambiente. O processo pode variar de simples a complexo: um arquivo CSV armazenado centralmente, uma tabela SQL simples, um CMDB ou uma solução complexa que exige integração com outra solução de ferramenta ou de software. Há duas abordagens gerais:

 - **Atribuição de GUIDs por servidor** — Fornece uma medida de garantia de que todas as configurações de servidor sejam controladas individualmente. Isso fornece um nível de precisão em relação às atualizações e pode funcionar bem em ambientes com poucos servidores.
 - **Atribuição de GUIDs por função de servidor** — Todos os servidores que executam a mesma função, como servidores Web, usam o mesmo GUID para fazer referência aos dados de configuração necessários.  Lembre-se de que se vários servidores compartilham o mesmo GUID, todos eles serão atualizados simultaneamente quando as configurações forem alteradas.

O GUID é algo que deve ser considerado como dado confidencial, porque ele pode ser aproveitado por alguém mal-intencionado para obter informações sobre como os servidores estão implantados e configurados no seu ambiente. Para obter mais informações, consulte [Alocar GUIDs com segurança no Modo Pull da Configuração de Estado Desejado do PowerShell](http://blogs.msdn.com/b/powershell/archive/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode.aspx).

Tarefa de planejamento|
---|
Quem será responsável pela cópia de configurações na pasta do servidor de pull quando elas estiverem prontas?|
Se as configurações são criadas por uma equipe de aplicativos, qual será o processo para entregá-las?|
Você utilizará um repositório para armazenar configurações conforme elas são criadas entre as equipes?|
Você automatizará o processo de copiar as configurações para o servidor e criar uma soma de verificação quando estiverem prontas?|
Como você mapeará os GUIDs aos servidores ou às funções e onde isso será armazenado?|
O que será usado como processo para configurar computadores cliente e como isso se integrará ao seu processo de criação e armazenamento de GUIDs de Configuração?|

## <a name="installation-guide"></a>Guia de instalação

*Os scripts fornecidos neste documento são exemplos estáveis. Sempre examine os scripts cuidadosamente antes de executá-los em um ambiente de produção.*

### <a name="prerequisites"></a>Pré-requisitos

Para verificar a versão do PowerShell no seu servidor use o comando a seguir.

```powershell
$PSVersionTable.PSVersion
```

Se possível, atualize para a versão mais recente do Windows Management Framework.
Em seguida, baixe o módulo `xPsDesiredStateConfiguration` usando o comando a seguir.


```powershell
Install-Module xPSDesiredStateConfiguration
```

O comando solicitará sua aprovação antes de baixar o módulo.

### <a name="installation-and-configuration-scripts"></a>Scripts de instalação e configuração
-

O melhor método para implantar um servidor de pull de DSC é usar um script de configuração DSC. Este documento apresentará scripts que incluem as configurações básicas que configurariam apenas o serviço Web da DSC e as configurações avançadas, que configurariam um Windows Server de ponta a ponta, incluindo o serviço Web da DSC.

Observação: atualmente o módulo `xPSDesiredStateConfiguation` da DSC exige que o servidor seja de localidade EN-US.

### <a name="basic-configuration-for-windows-server-2012"></a>Configuração básica para Windows Server 2012
-------------------------------------------
```powershell
# This is a very basic Configuration to deploy a pull server instance in a lab environment on Windows Server 2012.

Configuration PullServer {
Import-DscResource -ModuleName xPSDesiredStateConfiguration

        # Load the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
          Ensure = 'Present'
          Name = 'DSC-Service'
        }

        # Use the DSC Resource to simplify deployment of the web service
        xDSCWebService PSDSCPullServer
        {
          Ensure = 'Present'
          EndpointName = 'PSDSCPullServer'
          Port = 8080
          PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
          CertificateThumbPrint = 'AllowUnencryptedTraffic'
          ModulePath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
          ConfigurationPath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
          State = 'Started'
          DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
}
PullServer -OutputPath 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
```

### <a name="advanced-configuration-for-windows-server-2012-r2"></a>Configuração avançada para Windows Server 2012 R2

```powershell
# This is an advanced Configuration example for Pull Server production deployments on Windows Server 2012 R2.
# Many of the features demonstrated are optional and provided to demonstrate how to adapt the Configuration for multiple scenarios
# Select the needed resources based on the requirements for each environment.
# Optional scenarios include:
#      * Reduce footprint to Server Core
#      * Rename server and join domain
#      * Switch from SSL to TLS for HTTPS
#      * Automatically load certificate from Certificate Authority
#      * Locate Modules and Configuration data on remote SMB share
#      * Manage state of default websites in IIS

param (
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [System.String] $ServerName,
        [System.String] $DomainName,
        [System.String] $CARootName,
        [System.String] $CAServerFQDN,
        [System.String] $CertSubject,
        [System.String] $SMBShare,
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $Credential
    )

Configuration PullServer {
    Import-DscResource -ModuleName xPSDesiredStateConfiguration, xWebAdministration, xCertificate, xComputerManagement
    Node localhost
    {

        # Configure the server to automatically corret configuration drift including reboots if needed.
        LocalConfigurationManager
        {
            ConfigurationMode = 'ApplyAndAutoCorrect'
            RebootNodeifNeeded = $node.RebootNodeifNeeded
            CertificateId = $node.Thumbprint
        }

        # Remove all GUI interfaces so the server has minimum running footprint.
        WindowsFeature ServerCore
        {
            Ensure = 'Absent'
            Name = 'User-Interfaces-Infra'
        }

        # Set the server name and if needed, join a domain. If not joining a domain, remove the DomainName parameter.
        xComputer DomainJoin
        {
            Name = $Node.ServerName
            DomainName = $Node.DomainName
            Credential = $Node.Credential
        }

        # The next series of settings disable SSL and enable TLS, for environments where that is required by policy.
        Registry TLS1_2ServerEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }
        Registry TLS1_2ServerDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }
        Registry TLS1_2ClientEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }
        Registry TLS1_2ClientDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }
        Registry SSL2ServerDisabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server'
            ValueName = 'Enabled'
            ValueData = 0
            ValueType = 'Dword'
        }

        # Install the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
            Ensure = 'Present'
            Name = 'DSC-Service'
        }

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority, complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider modifying the default port, possibly leveraging port 443 in environments where that is enforced as a standard.
        xDSCWebService PSDSCPullServer
        {
            Ensure = 'Present'
            EndpointName = 'PSDSCPullServer'
            Port = 8080
            PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
            CertificateThumbPrint = 'CertificateSubject'
            CertificateSubject = $Node.CertSubject
            ModulePath = "$($Node.SMBShare)\DscService\Modules"
            ConfigurationPath = "$($Node.SMBShare)\DscService\Configuration"
            State = 'Started'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }

        # Validate web config file contains current DB settings
        xWebConfigKeyValue CorrectDBProvider
        {
            ConfigSection = 'AppSettings'
            Key = 'dbprovider'
            Value = 'System.Data.OleDb'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
        xWebConfigKeyValue CorrectDBConnectionStr
        {
            ConfigSection = 'AppSettings'
            Key = 'dbconnectionstr'
            Value = 'Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\WindowsPowerShell\DscService\Devices.mdb;'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }

        # Stop the default website
        xWebsite StopDefaultSite
        {
            Ensure = 'Present'
            Name = 'Default Web Site'
            State = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    }
}
$configData = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            ServerName = $ServerName
            DomainName = $DomainName
            CARootName = $CARootName
            CAServerFQDN = $CAServerFQDN
            CertSubject = $CertSubject
            AutoRenew = $true
            SMBShare = $SMBShare
            Credential = $Credential
            RebootNodeifNeeded = $true
            CertificateFile = 'c:\PullServerConfig\Cert.cer'
            Thumbprint = 'B9A39921918B466EB1ADF2509E00F5DECB2EFDA9'
            }
        )
    }
PullServer -ConfigurationData $configData -OutputPath 'C:\PullServerConfig\'
Set-DscLocalConfigurationManager -ComputerName localhost -Path 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'

# .\Script.ps1 -ServerName web1 -domainname 'test.pha' -carootname 'test-dc01-ca' -caserverfqdn 'dc01.test.pha' -certsubject 'CN=service.test.pha' -smbshare '\\sofs1.test.pha\share'
```


### <a name="verify-pull-server-functionality"></a>Verificar a funcionalidade do servidor de pull

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](invoke-webrequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}
Verify-DSCPullServer 'INSERT SERVER FQDN'

Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a>Configurar clientes

```powershell
Configuration PullClient {
    param(
    $ID,
    $Server
    )
        LocalConfigurationManager
                {
                    ConfigurationID = $ID;
                    RefreshMode = 'PULL';
                    DownloadManagerName = 'WebDownloadManager';
                    RebootNodeIfNeeded = $true;
                    RefreshFrequencyMins = 30;
                    ConfigurationModeFrequencyMins = 15;
                    ConfigurationMode = 'ApplyAndAutoCorrect';
                    DownloadManagerCustomData = @{ServerUrl = "http://"+$Server+":8080/PSDSCPullServer.svc"; AllowUnsecureConnection = $true}
                }
}
PullClient -ID 'INSERTGUID' -Server 'INSERTSERVER' -Output 'C:\DSCConfig\'
Set-DscLocalConfigurationManager -ComputerName 'Localhost' -Path 'C:\DSCConfig\' -Verbose
```


## <a name="additional-references-snippets-and-examples"></a>Exemplos, trechos de código e referências adicionais

Este exemplo mostra como iniciar manualmente uma conexão de cliente (requer WMF5) para teste.

```powershell
Update-DSCConfiguration –Wait -Verbose
```

O cmdlet [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) é usado para adicionar um tipo de registro CNAME em uma zona DNS.

A função do PowerShell para [Criar uma soma de verificação e publicar o MOF da DSC em um servidor de pull de SMB](http://bit.ly/1E46BhI) gera automaticamente a soma de verificação necessária e, em seguida, copia a configuração do MOF e os arquivos de soma de verificação para o servidor de pull de SMB.

## <a name="appendix---understanding-odata-service-data-file-types"></a>Apêndice – Noções básicas sobre tipos de arquivo de dados do serviço ODATA

Um arquivo de dados é armazenado para criar informações durante a implantação de um servidor de pull que inclui o serviço Web OData. O tipo de arquivo depende do sistema operacional, conforme descrito abaixo.

 - **Windows Server 2012** O tipo de arquivo será sempre .mdb
 - **Windows Server 2012 R2** O tipo de arquivo padrão será .edb, a menos que um .mdb seja especificado na configuração

No [Script de exemplo avançado](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) para a instalação de um Servidor de Pull, você também encontrará um exemplo de como controlar automaticamente as configurações do arquivo web.config para evitar qualquer possibilidade de erro causado pelo tipo de arquivo.