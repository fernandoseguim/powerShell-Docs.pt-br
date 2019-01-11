---
ms.date: 12/12/2018
keywords: DSC, powershell, recursos, da galeria, instalação
title: Instalar recursos adicionais do DSC
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400293"
---
# <a name="install-additional-dsc-resources"></a>Instalar recursos adicionais do DSC

PowerShell inclui vários recursos de Out-of-the-box para o Desired State Configuration (DSC). O **PSDesiredStateConfiguration** módulo contém todos os recursos de DSC OOB disponíveis em sua instância específica do PowerShell.

Esta é uma lista dos recursos OOB incluídos no PowerShell 4.0 e uma descrição dos recursos do recurso.

> [!NOTE]
> Isso é uma lista incompleta, como o número de recursos OOB cresceu com cada versão do PowerShell.

|Recurso  |Descrição  |
|---------|---------|
|**File**|Controla o estado de arquivos e diretórios. Copia os arquivos de um **fonte** para um **destino** e as atualiza quando o **fonte** alterações comparando as datas, as somas de verificação e hashes.|
|**Archive**|Desempacota os arquivos mortos e um local especificado. Valida os arquivos com o determinado **soma de verificação**.|
|**Environment**|Gerencia as variáveis de ambiente.|
|**Grupo**|Gerencia grupos locais e controla a associação de grupo.|
|**Log**|Grava as mensagens para o `Microsoft-Windows-Desired State Configuration/Analytic` log de eventos.|
|**Pacote**|Instala ou desinstala pacotes usando **argumentos**, **LogPath**, **ReturnCode**, outras configurações.|
|**Registry**|Gerencia os valores e chaves do registro.|
|**Script**|Permite que você crie suas próprias [conjunto de teste get](../resources/get-test-set.md) blocos de script.|
|**Service**|Configura os serviços do Windows.|
|**User** |Gerencia usuários locais e atributos.|
|**WindowsFeature**|Gerencia as funções e recursos.|
|**WindowsProcess**|Configura os processos do Windows.|

Os recursos OOB permitem que um bom ponto de partida para operações comuns. Se os recursos OOB não atender às suas necessidades, você pode escrever seus próprios [recurso personalizado](../resources/authoringResource.md). Antes de escrever um recurso personalizado para resolver seu problema, você deve procurar por meio do grande número de recursos de DSC que já foram criados pela Microsoft e a comunidade do PowerShell.

Você pode encontrar recursos de DSC em ambos os [da Galeria do PowerShell](https://www.powershellgallery.com/) e [GitHub](https://github.com/). Você também pode instalar recursos de DSC diretamente do console do PowerShell usando [PowerShellGet](/powershell/module/powershellget/).

## <a name="installing-powershellget"></a>Instalando o PowerShellGet

Para determinar se você já tiver **PowerShell** obter ou para obter ajuda para instalá-lo, consulte o guia a seguir: [Instalando o PowerShellGet](/powershell/gallery/installing-psget)

## <a name="finding-dsc-resources-using-powershellget"></a>Localizar recursos de DSC usando o PowerShellGet

Uma vez **PowerShellGet** é instalado em seu sistema, você pode localizar e instalar os recursos de DSC hospedados na [Galeria do PowerShell](https://www.powershellgallery.com/).

Primeiro, use o [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet para localizar recursos de DSC. Quando você executa `Find-DSCResource` pela primeira vez, você verá o seguinte prompt para instalar o provedor do NuGet"".

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The
NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider
 by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to
install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

Depois de pressionar 'y', o provedor "NuGet" é instalado, você ver uma lista de recursos de DSC que podem ser instalados da Galeria do PowerShell.

> [!NOTE]
> Lista não é mostrada porque ela é muito grande.

Você também pode especificar o `-Name` parâmetro usando caracteres curinga, ou `-Filter` parâmetro sem caracteres curinga para restringir sua pesquisa. Este exemplo tenta localizar um recurso de "Fuso horário" DSC usando caracteres curinga.

> [!IMPORTANT]
> Atualmente, há um bug na `Find-DSCResource` cmdlet que impeça o uso de curingas em ambos os `-Name` e `-Filter` parâmetros. O segundo exemplo abaixo mostra uma solução alternativa usando `Where-Object`.

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

Você também pode usar `Where-Object` para encontrar recursos DSC com filtragem mais granular. Essa abordagem será mais lenta do que usando incorporado em parâmetros de filtragem.

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

Para obter mais informações sobre filtragem, consulte [Where-Object](/powershell/module/microsoft.powershell.core/where-object).

## <a name="installing-dsc-resources-using-powershellget"></a>Instalar recursos de DSC usando PowerShellGet

Para instalar um recurso de DSC, use o [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, especificando o nome do módulo mostrado sob **módulo** nome nos resultados da pesquisa.

O recurso de "Fuso horário" existe no módulo "ComputerManagementDSC", é assim que o módulo Este exemplo instala.

> [!NOTE]
> Se você não confiar na Galeria do PowerShell, você verá o aviso abaixo que pede confirmação, e instruindo como evitar avisos subsequentes em que você instala.

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Pressione 'y' para continuar a instalação do módulo. Após a instalação, verifique se o novo recurso é instalado usando [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

Você também pode exibir outros recursos em seu módulo recém-instalado, especificando o `-ModuleName` parâmetro.

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a>Consulte também

- [O que são recursos?](../resources/resources.md)
