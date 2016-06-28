---
title: "Configurando o Gerenciador de Configurações Local"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 901cf8190252ac344182bf49d550a8adade559a0
ms.openlocfilehash: c66b8d6abf4886143f71c0de823cbfde86d875ba

---

# Configurando o Gerenciador de Configurações Local

> Aplica-se a: Windows PowerShell 5.0

O Gerenciador de Configurações Local (LCM) é o mecanismo da Configuração de Estado Desejado (DSC) do Windows PowerShell. Ele é executado em cada nó de destino e é responsável pela análise e aplicação das configurações que são enviadas para o nó. Também é responsável por uma série de outros aspectos da DSC, incluindo os itens a seguir.

* Determinar o modo de atualização (push ou pull).
* Especificar com que frequência um nó recebe e aplica as configurações.
* Associar o nó com servidores de pull.
* Especificar configurações parciais.

Um tipo especial de configuração é utilizado para configurar o LCM para especificar cada um desses comportamentos. As seções a seguir descrevem como configurar o LCM.

> **Observação**: este tópico se aplica ao LCM introduzido no Windows PowerShell 5.0. Para obter informações sobre como configurar o LCM no Windows PowerShell 4.0, consulte o [Gerenciador de Configurações Local (LCM) de Configuração de Estado Desejado do Windows PowerShell 4.0](metaconfig4.md).

## Escrevendo e aplicando uma configuração do LCM

Para configurar o LCM, você cria e executa um tipo especial de configuração. Para especificar uma configuração do LCM, é necessário usar o atributo DscLocalConfigurationManager. Segue uma configuração simples que define o LCM para o modo de push.

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

Você chama e executa a configuração para criar o MOF de configuração, como faria com uma configuração normal (para obter informações sobre como criar o MOF de configuração, consulte [Compilando a configuração](configurations.md#compiling-the-configuration)). Ao contrário de configurações normais, você não aplica uma configuração do LCM chamando o cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx). Em vez disso, você chama o cmdlet [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx), fornecendo o caminho até o MOF de configuração como parâmetro. Depois de aplicar a configuração, você pode ver as propriedades do LCM chamando o cmdlet [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx).

Uma configuração do LCM pode conter blocos somente para um conjunto limitado de recursos. No exemplo anterior, o único recurso chamado é **Settings**. Os outros recursos disponíveis são:

* **ConfigurationRepositoryWeb**: especifica um servidor de pull de HTTP para configurações. 
* **ConfigurationRepositoryShare**: especifica um servidor de pull de SMB para configurações.
* **ResourceRepositoryWeb**: especifica um servidor de pull de HTTP para os módulos.
* **ResourceRepositoryShare**: especifica um servidor de pull de SMB para os módulos.
* **ReportServerWeb**: especifica um servidor de pull de HTTP para o qual os relatórios serão enviados.
* **PartialConfiguration**: especifica configurações parciais.

## Configurações básicas

Além de especificar servidores de pull e configurações parciais, todas as propriedades do LCM são configuradas em um bloco **Settings**. As seguintes propriedades estão disponíveis em um bloco **Settings**.

|  Propriedade  |  Tipo  |  Descrição   | 
|----------- |------- |--------------- | 
| ConfigurationModeFrequencyMins| UInt32| A frequência, em minutos, em que a configuração atual é verificada e aplicada. Essa propriedade será ignorada se a propriedade ConfigurationMode estiver definida como ApplyOnly. O valor padrão é 15. <br> __Observação__: o valor dessa propriedade deve ser um múltiplo do valor da propriedade __RefreshFrequencyMins__ ou o valor da propriedade __RefreshFrequencyMins__ deve ser um múltiplo do valor dessa propriedade.| 
| RebootNodeIfNeeded| bool| Defina como __$true__ para reinicializar automaticamente o nó após uma configuração que requer que a reinicialização seja aplicada. Caso contrário, você precisará reinicializar manualmente o nó para qualquer configuração que exigir. O valor padrão é __$false__.| 
| ConfigurationMode| cadeia de caracteres | Especifica como o LCM realmente aplica a configuração aos nós de destino. Os valores possíveis são __"ApplyOnly"__,__"ApplyandMonitior"(default)__ e __"ApplyandAutoCorrect"__. <ul><li>__ApplyOnly__: a DSC aplica a configuração e não faz nada além disso, a menos que uma nova configuração seja enviada por push para o nó de destino ou quando o pull de uma nova configuração for efetuado de um servidor. Depois da aplicação inicial de uma nova configuração, a DSC não procura um dessincronização em relação a um estado previamente configurado.</li><li> __ApplyAndMonitor__: este é o valor padrão. O LCM aplica as novas configurações. Após a aplicação inicial de uma nova configuração, se o nó de destino estiver dessincronizado em relação ao estado desejado, a DSC relatará a discrepância nos logs.</li><li>__ApplyAndAutoCorrect__: a DSC aplica as novas configurações. Após a aplicação inicial de uma nova configuração, se o nó de destino estiver dessincronizado em relação ao estado desejado, a DSC relatará a discrepância nos logs e reaplica a configuração atual.</li></ul>| 
| ActionAfterReboot| cadeia de caracteres| Especifica o que acontece após uma reinicialização durante a aplicação de uma configuração. Os valores possíveis são __"ContinueConfiguration(default)"__ e __"StopConfiguration"__. <ul><li> __ContinueConfiguration__: continue a aplicar a configuração atual após a reinicialização do computador.</li><li>__StopConfiguration__: interrompa a configuração atual após a reinicialização do computador.</li></ul>| 
| RefreshMode| cadeia de caracteres| Especifica como o LCM obtém as configurações. Os valores possíveis são __"Disabled"__, __"Push(default)"__ e __"Pull"__. <ul><li>__Disabled__: as configurações DSC estão desabilitadas para este nó.</li><li> __Push__: as configurações são iniciadas chamando o cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx). A configuração é aplicada imediatamente ao nó. Este é o valor padrão.</li><li>__Pull__: o nó está configurado para verificar regularmente as configurações de um servidor de pull. Se essa propriedade estiver definida como __Pull__, você deverá especificar um servidor de pull em um bloco __ConfigurationRepositoryWeb__ ou __ConfigurationRepositoryShare__. Para obter mais informações sobre servidores de pull, consulte [Configurando um servidor de pull de DSC](pullServer.md).</li></ul>| 
| CertificateID| cadeia de caracteres| Um GUID que especifica um certificado usado para proteger credenciais para acessar a configuração. Para obter mais informações, consulte [Quer proteger credenciais na Configuração de Estado Desejado do Windows PowerShell?](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx).| 
| ConfigurationID| cadeia de caracteres| Um GUID que identifica o arquivo de configuração que deve ser obtido de um servidor de pull no modo de pull. O nó efetuará o pull das configurações no servidor de pull se o nome do MOF de configuração for ConfigurationID.mof.<br> __Observação:__ se você definir essa propriedade, registrar o nó com um servidor de pull usando __RegistrationKey__ não funcionará. Para obter mais informações, consulte [Configurando um cliente de pull com nomes de configuração](pullClientConfigNames.md).| 
| RefreshFrequencyMins| Uint32| O intervalo de tempo, em minutos, em que o LCM verifica um servidor de pull para obter configurações atualizadas. Esse valor será ignorado se o LCM não estiver configurado no modo de pull. O valor padrão é 30.<br> __Observação:__ o valor dessa propriedade deve ser um múltiplo do valor da propriedade __ConfigurationModeFrequencyMins__ ou o valor da propriedade __ConfigurationModeFrequencyMins__ deve ser um múltiplo do valor dessa propriedade.| 
| AllowModuleOverwrite| bool| __$TRUE__ se as novas configurações baixadas do servidor de configuração tiverem permissão para substituir as antigas no nó de destino. Caso contrário, $FALSE.| 
| DebugMode| cadeia de caracteres| Os valores possíveis são __None(Default)__, __ForceModuleImport__ e __All__. <ul><li>Defina como __None__ para usar os recursos armazenados em cache. Este é o padrão e deve ser usada em cenários de produção.</li><li>Definir como __ForceModuleImport__ fará com que o LCM recarregue todos os módulos de recursos DSC, mesmo se tiverem sido carregados e armazenados em cache anteriormente. Isso afeta o desempenho das operações de DSC, já que cada módulo é recarregado no momento do uso. Normalmente, você usaria esse valor durante a depuração de um recurso</li><li>Nesta versão, __All__ é o mesmo que __ForceModuleImport__</li></ul> |
| ConfigurationDownloadManagers| CimInstance[]| Obsoleto. Use os blocos __ConfigurationRepositoryWeb__ e __ConfigurationRepositoryShare__ para definir servidores de pull de configuração.| 
| ResourceModuleManagers| CimInstance[]| Obsoleto. Use os blocos __ResourceRepositoryWeb__ e __ResourceRepositoryShare__ para definir servidores de pull de recurso.| 
| ReportManagers| CimInstance[]| Obsoleto. Use os blocos __ReportServerWeb__ para definir servidores de relatório.| 
| PartialConfigurations| CimInstance| Não foi implementado. Não use.| 
| StatusRetentionTimeInDays | UInt32| O número de dias que o LCM mantém o status da configuração atual.| 

## Servidores de pull

Um servidor de pull é um serviço Web OData ou um compartilhamento SMB que é usado como local central para arquivos de DSC. A configuração do LCM dá suporte para definir os seguintes tipos de servidores de pull:

* **Servidor de configuração**: um repositório de configurações DSC. Defina os servidores de configuração usando blocos **ConfigurationRepositoryWeb** (para servidores baseados na Web) e **ConfigurationRepositoryShare** (para servidores baseados em SMB).
* Servidor de recursos — um repositório de recursos de DSC, empacotados como módulos do PowerShell. Defina os servidores de recurso usando blocos **ResourceRepositoryWeb** (para servidores baseados na Web) e **ResourceRepositoryShare** (para servidores baseados em SMB).
* Servidor de relatório — um serviço para o qual a DSC envia dados de relatório. Defina os servidores de relatório usando blocos **ReportServerWeb**. Um servidor de relatório deve ser um serviço Web.

Para obter informações sobre a configuração e o uso de servidores de pull, consulte [Configurando um servidor de pull de DSC](pullServer.md).

## Blocos do servidor de configuração

Para definir um servidor de configuração baseado na Web, crie um bloco **ConfigurationRepositoryWeb**. Um **ConfigurationRepositoryWeb** define as propriedades a seguir.

|Propriedade|Tipo|Descrição|
|---|---|---| 
|AllowUnsecureConnection|bool|Defina como **$TRUE** para permitir conexões entre o nó e o servidor sem autenticação. Defina como **$FALSE** para exigir autenticação.|
|CertificateID|cadeia de caracteres|Um GUID que representa o certificado usado para autenticar o servidor.|
|ConfigurationNames|String[]|Uma matriz de nomes de configurações que serão retiradas por pull pelo nó de destino. Serão usadas apenas se o nó for registrado com o servidor de pull usando uma **RegistrationKey**. Para obter mais informações, consulte [Configurando um cliente de pull com nomes de configuração](pullClientConfigNames.md).|
|RegistrationKey|cadeia de caracteres|Um GUID que registra o nó com o servidor de pull. Para obter mais informações, consulte [Configurando um cliente de pull com nomes de configuração](pullClientConfigNames.md).|
|ServerURL|cadeia de caracteres|A URL do servidor de configuração.|

Para definir um servidor de configuração baseado em SMB, crie um bloco **ConfigurationRepositoryShare**. Um **ConfigurationRepositoryShare** define as propriedades a seguir.

|Propriedade|Tipo|Descrição|
|---|---|---|
|Credential|MSFT_Credential|A credencial usada para autenticar para o compartilhamento SMB.|
|SourcePath|cadeia de caracteres|O caminho do compartilhamento SMB.|

## Blocos do servidor de recurso

Para definir um servidor de recurso baseado na Web, crie um bloco **ResourceRepositoryWeb**. Um **ResourceRepositoryWeb** define as propriedades a seguir.

|Propriedade|Tipo|Descrição|
|---|---|---|
|AllowUnsecureConnection|bool|Defina como **$TRUE** para permitir conexões entre o nó e o servidor sem autenticação. Defina como **$FALSE** para exigir autenticação.|
|CertificateID|cadeia de caracteres|Um GUID que representa o certificado usado para autenticar o servidor.|
|RegistrationKey|cadeia de caracteres|Um GUID que identifica o nó para o servidor de pull. Para obter mais informações, consulte Como registrar um nó com um servidor de pull de DSC.|
|ServerURL|cadeia de caracteres|A URL do servidor de configuração.|
 
Para definir um servidor de recurso baseado em SMB, crie um bloco **ResourceRepositoryShare**. **ResourceRepositoryShare** define as propriedades a seguir.

|Propriedade|Tipo|Descrição|
|---|---|---|
|Credential|MSFT_Credential|A credencial usada para autenticar para o compartilhamento SMB.|
|SourcePath|cadeia de caracteres|O caminho do compartilhamento SMB.|

## Blocos do servidor de relatório

Um servidor de relatório deve ser um serviço Web OData. Para definir um servidor de relatório, crie um bloco **ReportServerWeb**. **ReportServerWeb** define as propriedades a seguir.

|Propriedade|Tipo|Descrição|
|---|---|---| 
|AllowUnsecureConnection|bool|Defina como **$TRUE** para permitir conexões entre o nó e o servidor sem autenticação. Defina como **$FALSE** para exigir autenticação.|
|CertificateID|cadeia de caracteres|Um GUID que representa o certificado usado para autenticar o servidor.|
|RegistrationKey|cadeia de caracteres|Um GUID que identifica o nó para o servidor de pull. Para obter mais informações, consulte Como registrar um nó com um servidor de pull de DSC.|
|ServerURL|cadeia de caracteres|A URL do servidor de configuração.|

## Configurações parciais

Para definir uma configuração parcial, você cria um bloco **PartialConfiguration**. Para obter mais informações sobre configurações parciais, consulte [Configurações parciais de DSC](partialConfigs.md). **PartialConfiguration** define as propriedades a seguir.

|Propriedade|Tipo|Descrição|
|---|---|---| 
|ConfigurationSource|string[]|Uma matriz de nomes de servidores de configuração, definidos previamente nos blocos **ConfiguratoinRepositoryWeb** e **ConfigurationRepositoryShare**, dos quais a configuração parcial é retirada por pull.|
|DependsOn|string{}|Uma lista de nomes de outras configurações que devem ser concluídas antes que essa configuração parcial seja aplicada.|
|Descrição|cadeia de caracteres|Texto usado para descrever a configuração parcial.|
|ExclusiveResources|string[]|Uma matriz de recursos exclusivos para essa configuração parcial.|
|RefreshMode|cadeia de caracteres|Especifica como o LCM obtém essa configuração parcial. Os valores possíveis são __"Disabled"__, __"Push(default)"__ e __"Pull"__. <ul><li>__Disabled__: esta configuração parcial está desabilitada.</li><li> __Push__: a configuração parcial é enviada por push para o nó ao chamar o cmdlet [Publish-DscConfiguration](https://technet.microsoft.com/en-us/library/mt517875.aspx). Depois que todas as configurações parciais para o nó são enviadas por push ou recebidas por pull de um servidor, a configuração pode ser iniciada chamando `Start-DscConfiguration –UseExisting`. Este é o valor padrão.</li><li>__Pull__: o nó é configurado para verificar regularmente a configuração parcial de um servidor de pull. Se essa propriedade for definida como __Pull__, você deverá especificar um servidor de pull em uma propriedade __ConfigurationSource__. Para obter mais informações sobre servidores de pull, consulte [Configurando um servidor de pull de DSC](pullServer.md).</li></ul>|
|ResourceModuleSource|string[]|Uma matriz de nomes de servidores de recurso por meio dos quais é possível baixar os recursos necessários para essa configuração parcial. Esses nomes devem se referir a servidores de recurso definidos previamente nos blocos **ResourceRepositoryWeb** e **ResourceRepositoryShare**.|

## Consulte Também 

### Conceitos
[Visão Geral da Configuração de Estado Desejado do Windows PowerShell](overview.md)
 
[Configurando um servidor de pull de DSC](pullServer.md) 

[Gerenciador de Configurações Local de Configuração de Estado Desejado do Windows PowerShell 4.0](metaConfig4.md) 

### Outros recursos
[Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) 

[Configurando um cliente de pull com nomes de configuração](pullClientConfigNames.md) 




<!--HONumber=Jun16_HO4-->


