---
ms.date: 12/12/2018
keywords: DSC,powershell,configuração,instalação
title: Configurando o Gerenciador de Configurações Local
ms.openlocfilehash: c3ced2376c7d99477c40ae078dcecd775538b350
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400231"
---
# <a name="configuring-the-local-configuration-manager"></a>Configurando o Gerenciador de Configurações Local

> Aplica-se a: Windows PowerShell 5.0

O Gerenciador de Configurações Local (LCM) é o mecanismo de Configuração de Estado Desejado (DSC).
Ele é executado em cada nó de destino e é responsável pela análise e aplicação das configurações que são enviadas para o nó.
Também é responsável por uma série de outros aspectos da DSC, incluindo os itens a seguir.

- Determinar o modo de atualização (push ou pull).
- Especificar com que frequência um nó recebe e aplica as configurações.
- Associar o nó ao serviço de pull.
- Especificar configurações parciais.

Um tipo especial de configuração é utilizado para configurar o LCM para especificar cada um desses comportamentos.
As seções a seguir descrevem como configurar o LCM.

O Windows PowerShell 5.0 introduziu novas configurações para gerenciar o Gerenciador de Configurações Local.
Para obter informações sobre como configurar o LCM no Windows PowerShell 4.0, veja [Configurar o Gerenciador de Configurações Local em versões anteriores do Windows PowerShell](metaconfig4.md).

## <a name="writing-and-enacting-an-lcm-configuration"></a>Escrevendo e aplicando uma configuração do LCM

Para configurar o LCM, você cria e executa um tipo especial de configuração que aplica as configurações de LCM.
Para especificar uma configuração do LCM, é necessário usar o atributo DscLocalConfigurationManager.
Segue uma configuração simples que define o LCM para o modo de push.

```powershell
[DSCLocalConfigurationManager()]
configuration LCMConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
        }
    }
}
```

O processo de aplicação das configurações do LCM é semelhante à aplicação de uma configuração de DSC.
Você criará uma configuração do LCM, a compilará em um arquivo MOF e a aplicará ao nó.
Ao contrário de configurações de DSC, você não aplica uma configuração do LCM chamando o cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).
Em vez disso, chama [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager), fornecendo o caminho até o MOF de configuração do LCM como parâmetro.
Depois de aplicar a configuração do LCM, você pode ver as propriedades do LCM chamando o cmdlet [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).

Uma configuração do LCM pode conter blocos somente para um conjunto limitado de recursos.
No exemplo anterior, o único recurso chamado é **Settings**.
Os outros recursos disponíveis são:

* **ConfigurationRepositoryWeb**: especifica um serviço de pull de HTTP para configurações.
* **ConfigurationRepositoryShare**: especifica um serviço de pull de SMB para configurações.
* **ResourceRepositoryWeb**: especifica um serviço de pull de HTTP para os módulos.
* **ResourceRepositoryShare**: especifica um compartilhamento de SMB para os módulos.
* **ReportServerWeb**: especifica um serviço de pull de HTTP para o qual os relatórios serão enviados.
* **PartialConfiguration**: fornece dados para habilitar as configurações parciais.

## <a name="basic-settings"></a>Configurações básicas

Além de especificar pontos de extremidade/caminhos do serviço de pull e configurações parciais, todas as propriedades do LCM são configuradas em um bloco **Settings**.
As seguintes propriedades estão disponíveis em um bloco **Settings**.

|  Propriedade  |  Tipo  |  Descrição   |
|----------- |------- |--------------- |
| ActionAfterReboot| cadeia de caracteres| Especifica o que acontece após uma reinicialização durante a aplicação de uma configuração. Os valores possíveis são __"ContinueConfiguration"__ e __"StopConfiguration"__. <ul><li> __ContinueConfiguration__: continue a aplicar a configuração atual após a reinicialização do computador. Este é o valor padrão</li><li>__StopConfiguration__ Pare a configuração atual após a reinicialização do computador.</li></ul>|
| AllowModuleOverwrite| bool| __$TRUE__ se as novas configurações baixadas do serviço de pull tiverem permissão para substituir as antigas no nó de destino. Caso contrário, $FALSE.|
| CertificateID| cadeia de caracteres| A impressão digital de um certificado usado para proteger as credenciais passadas em uma configuração. Para obter mais informações, consulte [Quer proteger credenciais na Configuração de Estado Desejado do Windows PowerShell?](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx). <br> __Observação:__ isso será gerenciado automaticamente se estiver usando o serviço de pull de DSC de Automação do Azure.|
| ConfigurationDownloadManagers| CimInstance[]| Obsoleto. Use os blocos __ConfigurationRepositoryWeb__ e __ConfigurationRepositoryShare__ para definir pontos de extremidade de serviço de pull de configuração.|
| ConfigurationID| cadeia de caracteres| Para compatibilidade com versões anteriores do serviço de pull. Um GUID que identifica o arquivo de configuração que deve ser obtido de um serviço de pull. O nó efetuará o pull das configurações serviço de pull se o nome do MOF de configuração for ConfigurationID.mof.<br> __Observação:__ Se você definir essa propriedade, o registro do nó com um serviço de pull usando __RegistrationKey__ não funcionará. Para obter mais informações, consulte [Configurando um cliente de pull com nomes de configuração](../pull-server/pullClientConfigNames.md).|
| ConfigurationMode| cadeia de caracteres | Especifica como o LCM realmente aplica a configuração aos nós de destino. Os valores possíveis são __"ApplyOnly"__, __"ApplyAndMonitor"__ e __"ApplyAndAutoCorrect"__. <ul><li>__ApplyOnly__: a DSC aplica a configuração e não faz nada além disso, a menos que uma nova configuração seja enviada por push para o nó de destino ou quando o pull de uma nova configuração for efetuado de um serviço. Depois da aplicação inicial de uma nova configuração, a DSC não procura um dessincronização em relação a um estado previamente configurado. Observe que a DSC tentará aplicar a configuração até obter êxito antes que __ApplyOnly__ entre em vigor. </li><li> __ApplyAndMonitor__: Este é o valor padrão. O LCM aplica as novas configurações. Após a aplicação inicial de uma nova configuração, se o nó de destino estiver dessincronizado em relação ao estado desejado, a DSC relatará a discrepância nos logs. Observe que a DSC tentará aplicar a configuração até obter êxito antes que __ApplyAndMonitor__ entre em vigor.</li><li>__ApplyAndAutoCorrect__: a DSC aplica as novas configurações. Após a aplicação inicial de uma nova configuração, se o nó de destino estiver dessincronizado em relação ao estado desejado, a DSC relatará a discrepância nos logs e reaplica a configuração atual.</li></ul>|
| ConfigurationModeFrequencyMins| UInt32| A frequência, em minutos, em que a configuração atual é verificada e aplicada. Essa propriedade será ignorada se a propriedade ConfigurationMode estiver definida como ApplyOnly. O valor padrão é 15.|
| DebugMode| cadeia de caracteres| Os valores possíveis são __None__, __ForceModuleImport__ e __All__. <ul><li>Defina como __None__ para usar os recursos armazenados em cache. Este é o padrão e deve ser usada em cenários de produção.</li><li>Definir como __ForceModuleImport__ fará com que o LCM recarregue todos os módulos de recursos DSC, mesmo se tiverem sido carregados e armazenados em cache anteriormente. Isso afeta o desempenho das operações de DSC, já que cada módulo é recarregado no momento do uso. Normalmente, você usaria esse valor durante a depuração de um recurso</li><li>Nesta versão, __All__ é o mesmo que __ForceModuleImport__</li></ul> |
| RebootNodeIfNeeded| bool| Defina como __$true__ para reinicializar automaticamente o nó após uma configuração que requer que a reinicialização seja aplicada. Caso contrário, você precisará reinicializar manualmente o nó para qualquer configuração que exigir. O valor padrão é __$false__. Para usar essa configuração quando uma condição de reinicialização for representada por algo diferente do DSC (como o Windows Installer), combine essa configuração com o módulo [xPendingReboot](https://github.com/powershell/xpendingreboot).|
| RefreshMode| cadeia de caracteres| Especifica como o LCM obtém as configurações. Os valores possíveis são __"Disabled"__, __"Push"__ e __"Pull"__. <ul><li>__Disabled__: as configurações DSC estão desabilitadas para este nó.</li><li> __Push__: as configurações são iniciadas chamando o cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration). A configuração é aplicada imediatamente ao nó. Este é o valor padrão.</li><li>__Pull__: o nó está configurado para verificar regularmente as configurações de um serviço de pull ou caminho SMB. Se essa propriedade estiver definida como __Pull__, você deverá especificar um caminho de (serviço) HTTP ou (compartilhamento) SMB em um bloco __ConfigurationRepositoryWeb__ ou __ConfigurationRepositoryShare__.</li></ul>|
| RefreshFrequencyMins| Uint32| O intervalo de tempo, em minutos, em que o LCM verifica um serviço de pull para obter configurações atualizadas. Esse valor será ignorado se o LCM não estiver configurado no modo de pull. O valor padrão é 30.|
| ReportManagers| CimInstance[]| Obsoleto. Use blocos __ReportServerWeb__ para definir um ponto de extremidade para enviar dados de relatório a um serviço de pull.|
| ResourceModuleManagers| CimInstance[]| Obsoleto. Use os blocos __ResourceRepositoryWeb__ e __ResourceRepositoryShare__ para definir pontos de extremidade HTTP do serviço de pull ou caminhos SMB, respectivamente.|
| PartialConfigurations| CimInstance| Não foi implementado. Não use.|
| StatusRetentionTimeInDays | UInt32| O número de dias que o LCM mantém o status da configuração atual.|

## <a name="pull-service"></a>Serviço de pull

A configuração do LCM dá suporte à definição dos seguintes tipos de ponto de extremidade de serviço de pull:

- **Servidor de configuração**: um repositório de configurações DSC. Defina os servidores de configuração usando blocos **ConfigurationRepositoryWeb** (para servidores baseados na Web) e **ConfigurationRepositoryShare** (para servidores baseados em SMB).
- **Servidor de recursos**: um repositório de recursos de DSC, empacotados como módulos do PowerShell. Defina os servidores de recurso usando blocos **ResourceRepositoryWeb** (para servidores baseados na Web) e **ResourceRepositoryShare** (para servidores baseados em SMB).
- **Servidor de relatório**: um serviço para o qual a DSC envia dados de relatório. Defina os servidores de relatório usando blocos **ReportServerWeb**. Um servidor de relatório deve ser um serviço Web.

Para obter mais detalhes sobre o serviço de pull, veja [Serviço de pull de Desired State Configuration](../pull-server/pullServer.md).

## <a name="configuration-server-blocks"></a>Blocos do servidor de configuração

Para definir um servidor de configuração baseado na Web, crie um bloco **ConfigurationRepositoryWeb**.
Um **ConfigurationRepositoryWeb** define as propriedades a seguir.

|Propriedade|Tipo|Descrição|
|---|---|---|
|AllowUnsecureConnection|bool|Defina como **$TRUE** para permitir conexões entre o nó e o servidor sem autenticação. Defina como **$FALSE** para exigir autenticação.|
|CertificateID|cadeia de caracteres|A impressão digital de um certificado usado para autenticar o servidor.|
|ConfigurationNames|String[]|Uma matriz de nomes de configurações que serão retiradas por pull pelo nó de destino. Serão usadas apenas se o nó for registrado com o serviço de pull usando uma **RegistrationKey**. Para obter mais informações, consulte [Configurando um cliente de pull com nomes de configuração](../pull-server/pullClientConfigNames.md).|
|RegistrationKey|cadeia de caracteres|Um GUID que registra o nó com o serviço de pull. Para obter mais informações, consulte [Configurando um cliente de pull com nomes de configuração](../pull-server/pullClientConfigNames.md).|
|ServerURL|cadeia de caracteres|A URL do serviço de configuração.|

Um exemplo de script para simplificar a configuração do valor ConfigurationRepositoryWeb para nós locais está disponível - confira [Geração de metaconfigurações de DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Para definir um servidor de configuração baseado em SMB, crie um bloco **ConfigurationRepositoryShare**.
Um **ConfigurationRepositoryShare** define as propriedades a seguir.

|Propriedade|Tipo|Descrição|
|---|---|---|
|Credential|MSFT_Credential|A credencial usada para autenticar para o compartilhamento SMB.|
|SourcePath|cadeia de caracteres|O caminho do compartilhamento SMB.|

## <a name="resource-server-blocks"></a>Blocos do servidor de recurso

Para definir um servidor de recurso baseado na Web, crie um bloco **ResourceRepositoryWeb**.
Um **ResourceRepositoryWeb** define as propriedades a seguir.

|Propriedade|Tipo|Descrição|
|---|---|---|
|AllowUnsecureConnection|bool|Defina como **$TRUE** para permitir conexões entre o nó e o servidor sem autenticação. Defina como **$FALSE** para exigir autenticação.|
|CertificateID|cadeia de caracteres|A impressão digital de um certificado usado para autenticar o servidor.|
|RegistrationKey|cadeia de caracteres|Um GUID que identifica o nó para o serviço de pull.|
|ServerURL|cadeia de caracteres|A URL do servidor de configuração.|

Um exemplo de script para simplificar a configuração do valor ResourceRepositoryWeb para nós locais está disponível - confira [Geração de metaconfigurações de DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Para definir um servidor de recurso baseado em SMB, crie um bloco **ResourceRepositoryShare**.
**ResourceRepositoryShare** define as propriedades a seguir.

|Propriedade|Tipo|Descrição|
|---|---|---|
|Credential|MSFT_Credential|A credencial usada para autenticar para o compartilhamento SMB. Para obter um exemplo de passagem de credenciais, consulte [Configurando um servidor de pull de SMB para DSC](../pull-server/pullServerSMB.md)|
|SourcePath|cadeia de caracteres|O caminho do compartilhamento SMB.|

## <a name="report-server-blocks"></a>Blocos do servidor de relatório

Para definir um servidor de relatório, crie um bloco **ReportServerWeb**.
A função de servidor de relatório não é compatível com o serviço de pull baseado em SMB.
**ReportServerWeb** define as propriedades a seguir.

|Propriedade|Tipo|Descrição|
|---|---|---|
|AllowUnsecureConnection|bool|Defina como **$TRUE** para permitir conexões entre o nó e o servidor sem autenticação. Defina como **$FALSE** para exigir autenticação.|
|CertificateID|cadeia de caracteres|A impressão digital de um certificado usado para autenticar o servidor.|
|RegistrationKey|cadeia de caracteres|Um GUID que identifica o nó para o serviço de pull.|
|ServerURL|cadeia de caracteres|A URL do servidor de configuração.|

Um exemplo de script para simplificar a configuração do valor ReportServerWeb para nós locais está disponível - confira [Geração de metaconfigurações de DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

## <a name="partial-configurations"></a>Configurações parciais

Para definir uma configuração parcial, você cria um bloco **PartialConfiguration**.
Para obter mais informações sobre configurações parciais, consulte [Configurações parciais de DSC](../pull-server/partialConfigs.md).
**PartialConfiguration** define as propriedades a seguir.

|Propriedade|Tipo|Descrição|
|---|---|---|
|ConfigurationSource|string[]|Uma matriz de nomes de servidores de configuração, definidos previamente nos blocos **ConfigurationRepositoryWeb** e **ConfigurationRepositoryShare**, dos quais a configuração parcial é retirada.|
|DependsOn|string{}|Uma lista de nomes de outras configurações que devem ser concluídas antes que essa configuração parcial seja aplicada.|
|Descrição|cadeia de caracteres|Texto usado para descrever a configuração parcial.|
|ExclusiveResources|string[]|Uma matriz de recursos exclusivos para essa configuração parcial.|
|RefreshMode|cadeia de caracteres|Especifica como o LCM obtém essa configuração parcial. Os valores possíveis são __"Disabled"__, __"Push"__ e __"Pull"__. <ul><li>__Disabled__: esta configuração parcial está desabilitada.</li><li> __Push__: a configuração parcial é enviada por push para o nó ao chamar o cmdlet [Publish-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration). Depois que todas as configurações parciais para o nó são enviadas por push ou recebidas por pull de um serviço, a configuração pode ser iniciada chamando `Start-DscConfiguration –UseExisting`. Este é o valor padrão.</li><li>__Pull__: o nó é configurado para verificar regularmente a configuração parcial de um serviço de pull. Se essa propriedade for definida como __Pull__, você deverá especificar um serviço de pull em uma propriedade __ConfigurationSource__. Para saber mais sobre o serviço de pull da Automação do Azure, consulte [Visão geral do DSC de Automação do Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview).</li></ul>|
|ResourceModuleSource|string[]|Uma matriz de nomes de servidores de recurso por meio dos quais é possível baixar os recursos necessários para essa configuração parcial. Esses nomes devem se referir a pontos de extremidade de serviço definidos previamente nos blocos **ResourceRepositoryWeb** e **ResourceRepositoryShare**.|

__Observação:__ configurações parciais são compatíveis com o DSC de Automação do Azure, mas somente uma configuração pode ser extraída de cada conta de automação por nó.

## <a name="see-also"></a>Consulte Também

### <a name="concepts"></a>Conceitos
[Visão geral da Configuração do Estado Desejado](../overview/overview.md)

[Introdução à DSC de Automação do Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started)

### <a name="other-resources"></a>Outros recursos

[Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)

[Configurando um cliente de pull com nomes de configuração](../pull-server/pullClientConfigNames.md)
