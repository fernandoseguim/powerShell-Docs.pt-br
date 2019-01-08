---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Configurar uma máquina virtual na inicialização inicial usando DSC
ms.openlocfilehash: 7b9ebc6c818aa39365759945667426c8976997e5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400312"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a>Configurar uma máquina virtual na inicialização inicial usando DSC

> [!IMPORTANT]
> Aplica-se a: Windows PowerShell 5.0

## <a name="requirements"></a>Requisitos

> [!NOTE]
> A chave do Registro **DSCAutomationHostEnabled** descrita neste tópico não está disponível no PowerShell 4.0.
> Para obter informações sobre como configurar novas máquinas virtuais na inicialização inicial no PowerShell 4.0, confira [Deseja configurar seus computadores automaticamente usando DSC na inicialização inicial?] (https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)

Para executar esses exemplos, você precisará de:

- Um VHD inicializável com o qual trabalhar. Você pode baixar um arquivo ISO com uma cópia de avaliação do Windows Server 2016 no [Centro de Avaliação TechNet](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016). Você pode encontrar instruções sobre como criar um VHD de uma imagem ISO em [Criando discos rígidos virtuais inicializáveis](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).
- Um computador host com Hyper-V habilitado. Para obter informações, consulte [Visão geral do Hyper-V](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).

  Usando o DSC, você pode automatizar a instalação e a configuração de software em um computador na inicialização inicial.
  Você faz isso inserindo um documento MOF de configuração ou então uma metaconfiguração em uma mídia inicializável (como um VHD), de modo que eles sejam executados durante o processo inicial de inicialização.
  Esse comportamento é especificado pela chave do Registro [DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) em `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies`.
  Por padrão, o valor dessa chave é 2, o que permite que o DSC seja executado no momento da inicialização.

  Se você não quiser que o DSC seja executado no momento da inicialização, defina o valor da chave do Registro [DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) como 0.

- Inserir um documento MOF de configuração em um VHD
- Inserir uma metaconfiguração DSC em um VHD
- Desabilite a DSC no momento da inicialização

> [!NOTE]
> Você pode inserir tanto `Pending.mof` quanto `MetaConfig.mof` em um computador simultaneamente.
> Se ambos os arquivos estiverem presentes, as configurações especificadas em `MetaConfig.mof` têm precedência.

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a>Inserir um documento MOF de configuração em um VHD

Para aplicar uma configuração na inicialização inicial, você pode inserir um documento MOF configuração compilado no VHD como seu arquivo `Pending.mof`.
Se a chave do Registro **DSCAutomationHostEnabled** estiver definida como 2 (o valor padrão), o DSC aplicará a configuração definida por `Pending.mof` quando o computador for inicializado pela primeira vez.

Neste exemplo, usaremos a configuração a seguir, que instalará o IIS no novo computador:

```powershell
Configuration SampleIISInstall
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    node ('localhost')
    {
        WindowsFeature IIS
        {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
    }
}
```

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a>Para inserir o documento de configuração de MOF no VHD

1. Chamando o cmdlet [Mount-VHD](/powershell/module/hyper-v/mount-vhd), monte o VHD no qual você deseja inserir a configuração. Por exemplo:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. Em um computador executando o PowerShell 5.0 ou posterior, salve a configuração acima (**SampleIISInstall**) como um arquivo de script (.ps1) do PowerShell.

3. No console do PowerShell, navegue até a pasta na qual você salvou o arquivo .ps1.

4. Execute os seguintes comandos do PowerShell para compilar o documento MOF (para obter informações sobre compilação de configurações DSC, consulte [Configurações DSC](../configurations/configurations.md)):

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

5. Isso criará um arquivo `localhost.mof` em uma nova pasta chamada `SampleIISInstall`.
   Renomear e mover esse arquivo para o local apropriado no VHD como `Pending.mof`, usando o cmdlet [Move-Item](/powershell/module/microsoft.powershell.management/move-item). Por exemplo:

   ```powershell
       Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

6. Chamando o cmdlet [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd), desmonte o VHD. Por exemplo:

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

7. Crie uma VM usando o VHD no qual você instalou o documento MOF do DSC.

Após a inicialização inicial e instalação do sistema operacional, o IIS será instalado.
Você pode verificar isso chamando o cmdlet [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature).

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a>Inserir uma metaconfiguração DSC em um VHD

Você também pode configurar um computador para receber uma configuração na inicialização inicial, inserindo uma metaconfiguração (veja [Configuring the Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md) (Configurando o LCM (Gerenciador de Configurações Local)) no VHD como seu arquivo `MetaConfig.mof`.
Se a chave do Registro **DSCAutomationHostEnabled** estiver definida como 2 (o valor padrão), o DSC aplicará a metaconfiguração definida por `MetaConfig.mof` ao LCM quando o computador for inicializado pela primeira vez.
Se a metaconfiguração especificar que o LCM deve obter configurações de um servidor de recepção, o computador tentará efetuar pull de uma configuração do servidor de pull na inicialização inicial.
Para obter informações sobre a configuração de um servidor de pull de DSC, consulte [Configurando um servidor de pull da Web de DSC](../pull-server/pullServer.md).

Neste exemplo, usaremos a configuração descrita na seção anterior (**SampleIISInstall**) e a metaconfiguração a seguir:

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientBootstrap
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('SampleIISInstall')
        }
    }
}
```

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a>Para inserir o documento MOF de metaconfiguração no VHD

1. Chamando o cmdlet [Mount-VHD](/powershell/module/hyper-v/mount-vhd), monte o VHD no qual você deseja inserir a metaconfiguração. Por exemplo:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. [Configure um servidor de pull da Web](../pull-server/pullServer.md) e salve a configuração **SampleIISInistall** na pasta apropriada.

3. Em um computador executando o PowerShell 5.0 ou posterior, salve a metaconfiguração acima (**PullClientBootstrap**) como um arquivo de script do PowerShell (.ps1).

4. No console do PowerShell, navegue até a pasta na qual você salvou o arquivo .ps1.

5. Execute os seguintes comandos do PowerShell para compilar o documento MOF de metaconfiguração (para obter informações sobre compilação de configurações DSC, consulte [Configurações DSC](../configurations/configurations.md)):

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

6. Isso criará um arquivo `localhost.meta.mof` em uma nova pasta chamada `PullClientBootstrap`.
   Renomear e mover esse arquivo para o local apropriado no VHD como `MetaConfig.mof`, usando o cmdlet [Move-Item](/powershell/module/microsoft.powershell.management/move-item).

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

7. Chamando o cmdlet [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd), desmonte o VHD. Por exemplo:

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

8. Crie uma VM usando o VHD no qual você instalou o documento MOF do DSC.

Após a inicialização inicial e a instalação do sistema operacional, a DSC efetuará pull da configuração do servidor de pull e o IIS será instalado.
Você pode verificar isso chamando o cmdlet [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature).

## <a name="disable-dsc-at-boot-time"></a>Desabilite a DSC no momento da inicialização

Por padrão, o valor da chave `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled` é definido como 2, o que permite que uma configuração DSC seja executada se o computador estiver no estado pendente ou atual. Se não desejar que uma configuração seja executada na inicialização inicial, você precisará definir o valor desta chave como 0:

1. Chamando o cmdlet [Mount-VHD](/powershell/module/hyper-v/mount-vhd), monte o VHD. Por exemplo:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. Carregue a subchave `HKLM\Software` do Registro do VHD chamando `reg load`.

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

3. Navegue até `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\*` usando o provedor do Registro do PowerShell.

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies`
   ```

4. Altere o valor de `DSCAutomationHostEnabled` para 0.

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. Descarregue o Registro executando os comandos a seguir:

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a>Consulte Também

[Configurações DSC](../configurations/configurations.md)

[Chave do Registro de DSCAutomationHostEnabled](DSCAutomationHostEnabled.md)

[Configurando o LCM (Gerenciador de Configurações Local)](../managing-nodes/metaConfig.md)

[Configurando um servidor de pull da Web de DSC](../pull-server/pullServer.md)
