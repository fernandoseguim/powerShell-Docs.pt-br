---
ms.date: 12/12/2018
keywords: DSC,powershell,configuração,instalação
title: Aplicar, obter e testar configurações em um nó
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400303"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a>Aplicar, obter e testar configurações em um nó

Este guia mostra como trabalhar com configurações em um nó de destino. Este guia é dividido nas seguintes etapas:

## <a name="apply-a-configuration"></a>Aplicar uma configuração

Para aplicar e gerenciar uma configuração, é necessário gerar um arquivo ". MOF". O código a seguir representará uma configuração simples que será usada em todo este guia.

```powershell
Configuration Sample
{
    # This will generate two .mof files, a localhost.mof, and a server02.mof
    Node localhost, server02
    {
        File SampleFile
        {
            DestinationPath = 'C:\Temp\temp.txt'
            Contents = 'This is a simple resource to show Configuration functionality on a Node.'
        }
    }
}

# The -OutputPath parameter is built into every Configuration automatically.
# The value of -OutputPath determines where the .mof file should be stored, once compiled.
Sample -OutputPath "C:\Temp\"
```

Compilar essa configuração resultará em dois arquivos ". MOF".

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

Para aplicar uma configuração, use o [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet. O `-Path` parâmetro especifica um diretório onde residem os arquivos ". MOF". Se nenhum `-Computername` for especificado, `Start-DSCConfiguration` tentará aplicar cada configuração para o nome do computador especificado pelo nome do arquivo '. MOF' (\<computername\>. MOF). Especificar `-Verbose` para `Start-DSCConfiguration` para ver a saída mais detalhada.

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

Se `-Wait` não for especificado, você verá um trabalho criado. O trabalho criado terá uma **ChildJob** para cada arquivo ". MOF" processados pelo `Start-DSCConfiguration`.

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

Se uma configuração está demorando muito tempo e você deseja interrompê-lo, você pode usar [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) para interromper o aplicativo no nó local.

```powershell
Stop-DSCConfiguration -Force
```

Uma vez concluído, você pode exibir o status dos trabalhos por meio do objeto de trabalho retornado pelo [Get-Job](/powershell/module/microsoft.powershell.core/get-job).

```powershell
$job = Get-Job
$job.ChildJobs
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
49     Job49           Configuratio... Completed     True            localhost            Start-DSCConfiguration...
50     Job50           Configuratio... Completed     True            server02             Start-DSCConfiguration...
```

Para ver os **Verbose** de saída, use os comandos a seguir para exibir o **Verbose** fluxo para cada **ChildJob**. Para obter mais informações sobre trabalhos do PowerShell, consulte [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).

```powershell
# View the verbose output of the localhost job using array indexing.
$job.ChildJobs[0].Verbose
```

```output
Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
An LCM method call arrived from computer SERVER01 with user sid S-1-5-21-124525095-708259637-1543119021-1282804.
[SERVER01]: LCM:  [ Start  Set      ]
[SERVER01]: LCM:  [ Start  Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ Start  Test     ]  [[File]SampleFile]
[SERVER01]:                            [[File]SampleFile] The destination object was found and no action is required.
[SERVER01]: LCM:  [ End    Test     ]  [[File]SampleFile]  in 0.0370 seconds.
[SERVER01]: LCM:  [ Skip   Set      ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Set      ]
[SERVER01]: LCM:  [ End    Set      ]    in  0.2400 seconds.
Operation 'Invoke CimMethod' complete.
```

A partir do PowerShell 5.0, o `-UseExisting` parâmetro foi adicionado ao `Start-DSCConfiguration`. Especificando `-UseExisting`, você instruir o cmdlet a usar a configuração aplicada existente em vez de um especificado pelo `-Path` parâmetro.

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a>Uma configuração de teste

Você pode testar uma configuração aplicada atualmente usando [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration). `Test-DSCConfiguration` retornará `True` se o nó está em conformidade, e `False` se não for.

```powershell
Test-DSCConfiguration
```

A partir do PowerShell 5.0, o `-Detailed` parâmetro foi adicionado, que retorna um objeto com coleções para **ResourcesInDesiredState** e **ResourcesNotInDesiredState**

```powershell
Test-DSCConfiguration -Detailed
```

Começando no PowerShell 5.0, você pode testar uma configuração sem aplicá-lo. O `-ReferenceConfiguration` parâmetro aceita o caminho de um arquivo ". MOF" para testar o nó contra. Não **definir** ações são executadas em relação ao nó. No PowerShell 4.0, há soluções alternativas para testar uma configuração sem aplicá-lo, mas eles não são abordados aqui.

## <a name="get-configuration-values"></a>Obter valores de configuração

O [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet retorna os valores atuais de todos os recursos configurados na configuração aplicada no momento.

```powershell
Get-DSCConfiguration
```

Saída da nossa configuração de exemplo teria esta aparência se aplicadas com êxito.

```output
ConfigurationName    : Sample
DependsOn            :
ModuleName           : PSDesiredStateConfiguration
ModuleVersion        :
PsDscRunAsCredential :
ResourceId           : [File]SampleFile
SourceInfo           :
Attributes           : {archive}
Checksum             :
Contents             :
CreatedDate          : 11/27/2018 7:16:06 AM
Credential           :
DestinationPath      : C:\Temp\temp.txt
Ensure               : present
Force                :
MatchSource          :
ModifiedDate         : 11/27/2018 7:16:06 AM
Recurse              :
Size                 : 75
SourcePath           :
SubItems             :
Type                 : file
PSComputerName       :
CimClassName         : MSFT_FileDirectoryConfiguration
```

## <a name="get-configuration-status"></a>Obter o Status de configuração

A partir do PowerShell 5.0 a [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet permite que você veja o histórico de configurações aplicados ao nó. PowerShell DSC mantém o controle das configurações de {{N}} última aplicadas em **enviar por Push** ou **Pull** modo. Isso inclui qualquer *consistência* verificações executadas pelo LCM. Por padrão, `Get-DSCConfigurationStatus` mostra a última entrada histórico.

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

Use o `-All` parâmetro para ver todo o histórico de Status de configuração.

> [!NOTE]
> Saída será truncada para fins de brevidade.

```powershell
Get-DSCConfigurationStatus -All
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
Success    11/27/2018 7:16:06 AM     Initial         PUSH  False                1
Success    11/27/2018 7:04:53 AM     Initial         PUSH  False                1
Success    11/27/2018 7:03:45 AM     Consistency     PUSH  False                2
Success    11/27/2018 7:03:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:48:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:44 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:18:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:03:44 AM     Consistency     PUSH  False                2
```

## <a name="manage-configuration-documents"></a>Gerenciar documentos de configuração

O LCM gerencia a configuração do nó ao trabalhar com **documentos de configuração**. Esses arquivos ". MOF" residem no diretório "C:\Windows\System32\Configuration".

A partir do PowerShell 5.0 a [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) permite que você remova os arquivos ". MOF" para interromper as verificações de consistência futuro ou remover uma configuração de erros quando aplicado. O `-Stage` parâmetro permite que você especifique o arquivo ". MOF" de que deseja remover.

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> No PowerShell 4.0, você ainda pode remover esses arquivos ". MOF" diretamente usando [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).

## <a name="publish-configurations"></a>Configurações de publicação

A partir do PowerShell 5.0, o [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet foi adicionado. Esse cmdlet permite que você publicar um arquivo ". MOF" em computadores remotos, sem aplicá-lo.

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a>Consulte também

- [Obter, testar e definir](../resources/get-test-set.md)
