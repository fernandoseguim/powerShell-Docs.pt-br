---
ms.date: 11/06/2018
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery,psget
title: Trabalhando com PSRepositories local
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676425"
---
# <a name="working-with-local-powershellget-repositories"></a>Trabalhando com repositórios locais do PowerShellGet

Os repositórios de suporte do módulo PowerShellGet diferente na Galeria do PowerShell.
Esses cmdlets permitem que os cenários a seguir:

- Dar suporte a um conjunto de módulos do PowerShell confiável e validado previamente para uso em seu ambiente
- Teste de um pipeline de CI/CD que compila os módulos do PowerShell ou scripts
- Fornecer módulos e scripts do PowerShell para sistemas que não é possível acessar a internet

Este artigo descreve como configurar um repositório local do PowerShell. O artigo também aborda a [OfflinePowerShellGetDeploy][] módulo disponível a partir da Galeria do PowerShell. Esse módulo contém cmdlets para instalar a versão mais recente do PowerShellGet no seu repositório local.

## <a name="local-repository-types"></a>Tipos de repositório local

Há duas maneiras de criar um PSRepository local: Compartilhamento de arquivo ou servidor do NuGet. Cada tipo tem vantagens e desvantagens:

Servidor do NuGet

| Vantagens| Desvantagens |
| --- | --- |
| Imita a funcionalidade de PowerShellGallery | Aplicativo de várias camadas requer planejamento de operações e suporte |
| O NuGet se integra com o Visual Studio, outras ferramentas | Modelo de autenticação e gerenciamento de contas do NuGet necessários |
| O NuGet dá suporte a metadados em `.Nupkg` pacotes | A publicação requer manutenção e gerenciamento de chave de API |
| Fornece pesquisa, administração de pacote, etc. | |

Comp. de Arquivos

| Vantagens| Desvantagens |
| --- | --- |
| Fácil de configurar, fazer backup e manter | Metadados usados pelo PowerShellGet não estão disponível |
| Modelo de segurança simples - permissões de usuário no compartilhamento | Nenhuma interface do usuário além do compartilhamento de arquivo básico |
| Não há restrições, como substituir itens existentes | Nenhuma gravação de quem atualiza o que e segurança limitada |

PowerShellGet funciona com o tipo e dá suporte à localização de versões e a instalação da dependência.
No entanto, alguns recursos que funcionam para a Galeria do PowerShell não estão disponíveis para servidores de NuGet base ou compartilhamentos de arquivos.

- Tudo o que é um pacote - nenhuma diferenciação de scripts, módulos, recursos de DSC ou recursos de função.
- Servidores de compartilhamento de arquivos não podem ver os metadados do pacote, incluindo as marcas.

## <a name="creating-a-local-repository"></a>Criação de um repositório local

O artigo a seguir lista as etapas para configurar seu próprio servidor do NuGet.

- [NuGet.Server][]

Siga as etapas até o ponto de adição de pacotes. As etapas para [publicando um pacote](#publishing-to-a-local-repository) são abordados neste artigo.

Para um repositório com base no compartilhamento de arquivo, certifique-se de que os usuários tenham permissões para acessar o compartilhamento de arquivos.

## <a name="registering-a-local-repository"></a>Registrando um repositório local

Antes de um repositório pode ser usado, ele deve ser registrado usando o `Register-PSRepository` comando.
Nos exemplos a seguir, o **InstallationPolicy** é definido como *confiáveis*, supondo que você confia que o seu próprio repositório.

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

Tome nota da diferença entre como tratar os dois comandos **ScriptSourceLocation**. Para um repositórios baseados em compartilhamento de arquivo, o **SourceLocation** e **ScriptSourceLocation** devem corresponder. Para um repositório baseado na web, eles devem ser diferentes, portanto, neste exemplo à direita "/" é adicionado para o **SourceLocation**.

Se você quiser PSRepository recentemente criado para ser o repositório padrão, você deve cancelar o registro de todos os outros PSRepositories. Por exemplo:

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> O nome do repositório 'PSGallery' é reservado para uso pela Galeria do PowerShell. Você pode cancelar o registro PSGallery, mas é possível reutilizar o nome PSGallery para qualquer outro repositório.

Se você precisar restaurar a PSGallery, execute o seguinte comando:

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a>Publicação em um repositório local

Depois que você registrou o PSRepository local, você pode publicar em seu local PSRepository. Há dois cenários principais de publicação: publicar seu próprio módulo e publicação de um módulo de PSGallery.

### <a name="publishing-a-module-you-authored"></a>Publicação de um módulo criado por você

Use `Publish-Module` e `Publish-Script` para publicar seu módulo em seu local PSRepository da mesma maneira que faria para a Galeria do PowerShell.

- Especifique o local para seu código
- Forneça uma chave de API
- Especifique o nome do repositório. Por exemplo, `-PSRepository LocalPSRepo`

> [!NOTE]
> Você deve criar uma conta no servidor do NuGet e entrar para gerar e salvar a chave de API.
> Para um compartilhamento de arquivos, use qualquer cadeia de caracteres não vazia para o valor de NuGetApiKey.

Exemplos:

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> Para garantir a segurança, as chaves de API não devem ser codificado em scripts. Use um sistema de gerenciamento de chaves seguro.

### <a name="publishing-a-module-from-the-psgallery"></a>Publicação de um módulo de PSGallery

Para publicar um módulo do PSGallery para seu local PSRepository, você pode usar o cmdlet 'Save-Package'.

- Especifique o nome do pacote
- Especifique 'NuGet' como o provedor
- Especifique o local de PSGallery como o código-fonte (https://www.powershellgallery.com/api/v2)
- Especifique o caminho para seu repositório local

Exemplo:

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

Se o seu local PSRepository é baseado na web, ele requer uma etapa adicional que usa nuget.exe para publicar.

Consulte a documentação para usar [nuget.exe][].

## <a name="installing-powershellget-on-a-disconnected-system"></a>Instalar o PowerShellGet em um sistema desconectado

Implantar o PowerShellGet é difícil em ambientes que exigem sistemas para ser desconectado da internet. O PowerShellGet tem um processo de inicialização que instala a versão mais recente na primeira vez que ele é usado. O módulo OfflinePowerShellGetDeploy na Galeria do PowerShell fornece cmdlets que oferecem suporte a esse processo de inicialização.

Para inicializar uma implantação offline, você precisa:

- Baixe e instale o sistema OfflinePowerShellGetDeploy seu conectados à internet e seus sistemas desconectados
- Baixe o PowerShellGet e suas dependências no sistema conectado à internet usando o `Save-PowerShellGetForOffline` cmdlet
- Copiar PowerShellGet e suas dependências de sistema conectado à internet para o sistema desconectado
- Use o `Install-PowerShellGetOffline` no sistema desconectado para colocar PowerShellGet e suas dependências nas pastas apropriadas

Os seguintes comandos use `Save-PowerShellGetForOffline` colocar todos os componentes em uma pasta `f:\OfflinePowerShellGet`

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

Neste ponto, você deve fazer o conteúdo de `F:\OfflinePowerShellGet` disponíveis para seus sistemas desconectados. Execute o `Install-PowerShellGetOffline` cmdlet para instalar o PowerShellGet no sistema desconectado.

> [!NOTE]
> É importante que você não executar o PowerShellGet na sessão do PowerShell antes de executar esses comandos. Depois que o PowerShellGet está carregado na sessão, os componentes não podem ser atualizados. Se você iniciar o PowerShellGet por engano, saia e reinicie o PowerShell.

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

Depois de executar esses comandos, você está pronto para publicar o PowerShellGet em seu repositório local.

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> Para garantir a segurança, as chaves de API não devem ser codificado em scripts. Use um sistema de gerenciamento de chaves seguro.

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
