---
title: "Gerenciador de Configurações Local (LCM) de Configuração de Estado Desejado do Windows PowerShell 4.0"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 25195166f4d9dd668427d6bb5d748ef61273cdee

---

# Gerenciador de Configurações Local (LCM) de Configuração de Estado Desejado do Windows PowerShell 4.0

>Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O Gerenciador de Configurações Local (LCM) é o mecanismo de Configuração de Estado Desejado (DSC) do Windows PowerShell. É executado em todos os nós de destino e é responsável por chamar os recursos de configuração que estão incluídos em um script de configuração DSC. Este tópico lista as propriedades do Gerenciador de Configurações Local e descreve como você pode modificar as configurações do Gerenciador de Configurações Local em um nó de destino.

## Propriedades do Gerenciador de Configurações Local
O exemplo a seguir lista as propriedades do Gerenciador de Configurações Local que podem ser definidas ou recuperadas.
 
* **AllowModuleOverwrite**: controla se as novas configurações baixadas do servidor de configuração têm permissão para substituir as antigas no nó de destino. Os valores possíveis são True e False.
* **CertificateID**: um GUID é o certificado usado para proteger credenciais para acessar a configuração. Para obter mais informações, consulte [Quer proteger credenciais na Configuração de Estado Desejado do Windows PowerShell?](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx)
* **ConfigurationID**: indica um GUID que é usado para obter um arquivo de configuração específico de um servidor configurado como um servidor de “pull”. O GUID garante que o arquivo de configuração correto seja acessado.
* **ConfigurationMode**: especifica como o Gerenciador de Configurações Local realmente aplica a configuração aos nós de destino. Pode usar os seguintes valores:
    - **ApplyOnly**: com essa opção, a DSC aplicará a configuração e não fará nada além disso, a menos que uma nova configuração seja detectada quando você enviar uma nova configuração diretamente para o destino de nó (“push”) ou se tiver configurado um servidor de “pull” e a DSC descobrir uma nova configuração quando verificar com o servidor de “pull”. Nenhuma ação será executada se a configuração de destino estiver dessincronizada.
    - **ApplyAndMonitor**: com essa opção (que é o padrão), a DSC aplica a todas as novas configurações, independentemente de terem sido enviadas por você diretamente para o nó de destino ou descobertas em um servidor de “pull”. Por conseguinte, se a configuração do nó de destino estiver dessincronizada em relação ao arquivo de configuração, a DSC relatará a discrepância em logs. Para obter mais informações sobre o registro em log de DSC, consulte [Usando Logs de Evento para Diagnosticar Erros na Configuração de Estado Desejado](http://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx).
    - **ApplyAndAutoCorrect**: com essa opção, a DSC aplica todas as novas configurações, independentemente de terem sido enviadas por você diretamente para o nó de destino ou descobertas em um servidor de “pull”. Depois disso, se a configuração do nó de destino estiver dessincronizada em relação ao arquivo de configuração, a DSC relatará a discrepância em logs e tentará ajustar a configuração do nó de destino para colocar em conformidade com o arquivo de configuração.
* **ConfigurationModeFrequencyMins**: representa a frequência (em minutos) em que o aplicativo em segundo plano de DSC tenta implementar a configuração atual no nó de destino. O valor padrão é 15. Esse valor pode ser definido em conjunto com RefreshMode. Quando RefreshMode é definido como PULL, o nó de destino entra em contato com o servidor de configuração em um intervalo definido por RefreshFrequencyMins e baixa a configuração atual. Independentemente do valor RefreshMode, no intervalo definido por ConfigurationModeFrequencyMins, o mecanismo de consistência aplica a configuração que foi baixada por último ao nó de destino. RefreshFrequencyMins deve ser definido como um número inteiro, múltiplo de ConfigurationModeFrequencyMins.
* **Credential**: indica credenciais (como é o caso de Get-Credential) necessárias para acessar recursos remotos, como entrar em contato com o servidor de configuração.
* **DownloadManagerCustomData**: representa uma matriz que contém dados personalizados específicos para o gerenciador de downloads.
* **DownloadManagerName**: indica o nome da configuração e o gerenciador de downloads do módulo.
* **RebootNodeIfNeeded**: determinadas alterações na configuração de um nó de destino podem exigir que ele seja reiniciado para as alterações serem aplicadas. Com o valor **True**, essa propriedade reiniciará o nó assim que a configuração for completamente aplicada, sem aviso adicional. Se **False** (o valor padrão), a configuração será concluída, mas o nó deverá ser reiniciado manualmente para que as alterações entrem em vigor.
* **RefreshFrequencyMins**: usado ao configurar um servidor de “pull”. Representa a frequência (em minutos) em que o Gerenciador de Configurações Local contata um servidor de “pull” para baixar a configuração atual. Esse valor pode ser definido em conjunto com ConfigurationModeFrequencyMins. Quando RefreshMode é definido como PULL, o nó de destino entra em contato com o servidor de “pull” em um intervalo definido por RefreshFrequencyMins e baixa a configuração atual. No intervalo definido por ConfigurationModeFrequencyMins, o mecanismo de consistência aplica a configuração que foi baixada por último ao nó de destino. Se RefreshFrequencyMins não for definido como um número inteiro, múltiplo de ConfigurationModeFrequencyMins, será arredondado pelo sistema. O valor padrão é 30.
* **RefreshMode**: os valores possíveis são **Push** (o padrão) e **Pull**. Na configuração de “push”, é necessário colocar um arquivo de configuração em cada nó de destino, usando qualquer computador cliente. No modo de “pull”, você deve configurar um servidor de “pull” para o Gerenciador de Configurações Local contatar e acessar os arquivos de configuração.

### Exemplo de atualização das configurações do Gerenciador de Configurações Local

Você pode atualizar as configurações do Gerenciador de Configurações Local de um nó de destino incluindo um bloco **LocalConfigurationManager** dentro do bloco de nó em um script de configuração, conforme mostrado no exemplo a seguir.

```powershell
Configuration ExampleConfig
{
    Node “Server001”
    {
        LocalConfigurationManager
        {
            ConfigurationID = "646e48cb-3082-4a12-9fd9-f71b9a562d4e"
            ConfigurationModeFrequencyMins = 45
            ConfigurationMode = "ApplyAndAutocorrect"
            RefreshMode = "Pull"
            RefreshFrequencyMins = 90
            DownloadManagerName = "WebDownloadManager"
            DownloadManagerCustomData = (@{ServerUrl="https://$PullServer/psdscpullserver.svc"})
            CertificateID = "71AA68562316FE3F73536F1096B85D66289ED60E"
            Credential = $cred
            RebootNodeIfNeeded = $true
            AllowModuleOverwrite = $false
        }
# One or more resource blocks can be added here
    }
}

# The following line invokes the configuration and creates a file called Server001.meta.mof at the specified path
ExampleConfig -OutputPath "c:\users\public\dsc"  
```

A execução do script no exemplo anterior gera um arquivo MOF que especifica e armazena as configurações desejadas. Para aplicar as configurações, pode-se usar o cmdlet **Set-DscLocalConfigurationManager**, conforme mostrado no exemplo a seguir.

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> **Observação**: para o parâmetro **Path**, você deve especificar o mesmo caminho que especificou para o parâmetro **OutputPath** quando chamou a configuração no exemplo anterior.

Para ver as configurações do Gerenciador de Configurações Local atual, você pode usar o cmdlet **Get-DscLocalConfigurationManager**. Se você invocar esse cmdlet sem parâmetros, ele receberá, por padrão, as configurações do Gerenciador de Configurações Local para o nó no qual será executado. Para especificar outro nó, use o parâmetro **CimSession** com esse cmdlet.




<!--HONumber=Jun16_HO4-->


