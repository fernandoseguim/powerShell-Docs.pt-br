---
ms.date: 06/12/2017
contributor: manikb
keywords: galeria,powershell,cmdlet,psget
title: Inicializando o NuGet
ms.openlocfilehash: f707e23737361ee7f82a16150402c9e719ee0ae1
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a>Inicializar o provedor do NuGet e o NuGet.exe

O NuGet.exe não está incluído no provedor do NuGet mais recente.
Para operações de publicação de um módulo ou um de script, o PowerShellGet requer o NuGet.exe executável binário.
Somente o provedor do NuGet é necessário para todas as outras operações, incluindo *localizar*, *instalar*, *salvar* e *desinstalar*.
O PowerShellGet inclui a lógica para tratar a inicialização combinada do provedor do NuGet e do NuGet.exe ou a inicialização apenas do provedor do NuGet.
Em ambos os casos, apenas uma única mensagem de aviso deve ocorrer.
Se o computador não estiver conectado à Internet, o usuário ou um administrador deverá copiar uma instância confiável do provedor do NuGet e/ou o arquivo NuGet.exe no computador desconectado.

>**Observação**: a partir da versão 6, o provedor do NuGet é incluído na instalação do PowerShell. [http://github.com/powershell/powershell](http://github.com/powershell/powershell)

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a>Resolvendo erro quando o provedor do NuGet não for instalado em um computador conectado à Internet

```powershell
PS> Find-Module -Repository PSGallery -Verbose -Name Contoso

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n
Find-Module : NuGet provider is required to interact with NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed.
At line:1 char:1
+ Find-Module -Repository PSGallery -Verbose -Name Contoso
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Find-Module], InvalidOperationException
   + FullyQualifiedErrorId : CouldNotInstallNuGetProvider,Find-Module

PS> Find-Module -Repository PSGallery -Verbose -Name Contoso

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Contoso                             Module     PSGallery        Contoso module
```

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Resolvendo erro quando o provedor do NuGet está disponível e o NuGet.exe não está disponível durante a operação de publicação em um computador conectado à Internet

```powershell
PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module

PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Resolução de erro quando o provedor do NuGet e o NuGet.exe não estão disponíveis durante a operação de publicação em um computador conectado à Internet

```powershell
PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed and NuGet.exe is available under
one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetBinaries,Publish-Module

PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a>Inicializando manualmente o provedor do NuGet em um computador que não está conectado à Internet

Os processos demonstrados acima pressupõem que o computador está conectado à Internet e pode baixar arquivos de um local público.
Se isso não for possível, a única opção será inicializar um computador com os processos descritos acima e copiar manualmente o provedor para o nó isolado por meio de um processo confiável offline.
O caso de uso mais comum para esse cenário é quando uma galeria privada está disponível para dar suporte a um ambiente isolado.

Depois de seguir o processo acima para inicializar um computador conectado à Internet, você encontrará os arquivos do provedor no local:

```
C:\Program Files\PackageManagement\ProviderAssemblies\
```

A estrutura de pasta/arquivo do provedor do NuGet será (possivelmente com um número de versão diferente):

NuGet<br>
--2.8.5.208<br>
----Microsoft.PackageManagement.NuGetProvider.dll

Copie essas pastas e arquivos para os computadores offline usando um processo confiável.

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a>Inicializando manualmente o NuGet.exe para dar suporte a operações de publicação em um computador que não está conectado à Internet

Além de processo para inicializar manualmente o provedor do NuGet, se o computador for usado para publicar scripts ou módulos em uma galeria privada usando os cmdlets *Publish-Module* ou *Publish-Script*, o arquivo executável binário NuGet.exe será necessário.
O caso de uso mais comum para esse cenário é quando uma galeria privada está disponível para dar suporte a um ambiente isolado.
Há duas opções para obter o arquivo NuGet.exe.

Uma opção é inicializar um computador que esteja conectado à Internet e copiar os arquivos para os computadores offline usando um processo confiável.
Após inicializar o computador conectado à Internet, o binário NuGet.exe estará localizado em uma das duas pastas:

Se os cmdlets *Publish-Module* ou *Publish-Script* foram executados com permissões elevadas (como um administrador):

```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Se os cmdlets foram executados como um usuário sem permissões elevadas:

```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

Uma segunda opção é baixar o NuGet.exe do site NuGet.Org: [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html)<br>
Ao selecionar uma versão NugGet para computadores de produção, verifique se ela é posterior à 2.8.5.208 e identifique a versão rotulada como "recomendada".
Lembre-se de desbloquear o arquivo se ele tiver sido baixado usando um navegador.
Isso pode ser feito usando o cmdlet *Unblock-File*.

Em ambos os casos, o arquivo NuGet.exe pode ser copiado para qualquer local em *$env:path*, mas os locais padrão são:

Para disponibilizar o executável para que todos os usuários possam usar os cmdlets *Publish-Module* e *Publish-Script*:

```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Para disponibilizar o executável para apenas um usuário específico, copie para o local apenas dentro desse perfil de usuário:

```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```