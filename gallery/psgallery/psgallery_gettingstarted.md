---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: galeria,powershell,cmdlet,psgallery
title: psgallery_gettingstarted
ms.openlocfilehash: 6b2119a736cc428598c245526e5af970d86af998
ms.sourcegitcommit: 79e8f03afb8d0b0bb0a167e56464929b27f51990
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2017
---
<a id="get-started-with-the-powershell-gallery" class="xliff"></a>
# Introdução à Galeria do PowerShell

<a id="what-is-the-powershell-gallery" class="xliff"></a>
## O que é a Galeria do PowerShell?

A Galeria do PowerShell é o repositório central de conteúdo do PowerShell.
Nela, você pode encontrar módulos úteis do PowerShell que contêm comandos do PowerShell e recursos de DSC (Configuração de Estado Desejado). Você também pode encontrar scripts do PowerShell, alguns dos quais podem conter fluxos de trabalho do PowerShell e que descrevem um conjunto de tarefas e fornecem o sequenciamento para essas tarefas.
Alguns desses itens são criados pela Microsoft e outros são criados pela comunidade do PowerShell.

<a id="requirements" class="xliff"></a>
## Requisitos

Baixar itens da Galeria do PowerShell para o seu sistema requer o módulo [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409). Você pode encontrar o módulo PowerShellGet em qualquer um dos recursos indicados a seguir. Não é necessário entrar para baixar itens da Galeria do PowerShell.

-   [Windows 10](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)
-   [Windows Management Framework 5.0](http://go.microsoft.com/fwlink/?LinkId=398175)
-   [Instalador MSI (para PowerShell 3 e 4)](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

O PowerShellGet também requer o [provedor NuGet](http://go.microsoft.com/fwlink/?LinkId=722208) para funcionar com a Galeria do PowerShell. Você será solicitado a instalar o provedor NuGet automaticamente na primeira utilização do PowerShellGet se o provedor NuGet não estiver em um dos seguintes locais:

- `$env:ProgramFiles\PackageManagement\ProviderAssemblies`
- `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies`

Ou, você pode executar `Install-PackageProvider -Name NuGet -Force` para automatizar o download e a instalação do provedor do NuGet.

  
Se você uma versão mais antiga que a 2.8.5.201 do NuGet, você precisará chamar os seguintes cmdlets do PowerShell para instalar e passar para a versão mais recente do NuGet.

1.  `Install-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
2.  `Import-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
3.  Exclua a versão mais antiga do NuGet do local instalado acima.

Para obter mais informações, consulte <http://oneget.org/>.

  
Observação: devido a alterações nos formatos de empacotamento, é recomendável atualizar para a versão mais recente do PowerShellGet e do PackageManagement para instalar itens que foram atualizados recentemente. O PowerShellGet está incluído no Windows 10; você pode aprender mais sobre ele [aqui](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409).
O PowerShellGet também faz parte do WMF (Windows Management Framework) 5.0, que você pode baixar [aqui](http://go.microsoft.com/fwlink/?LinkId=398175).

<a id="discovering-items-from-the-powershell-gallery" class="xliff"></a>
## Descobrindo itens da Galeria do PowerShell

Você pode encontrar itens na Galeria do PowerShell usando o controle **Pesquisar** no site ou navegando pelas páginas de Módulos e Scripts. Você também pode encontrar itens da Galeria do PowerShell, executando os cmdlets [**Find-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) e [**Find-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), dependendo do tipo de item, com `-Repository PSGallery`.

A filtragem dos resultados da Galeria pode ser feita usando os seguintes parâmetros de [**Find-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) e [**Find-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)

- Nome
- AllVersions
- MinimumVersion
- RequiredVersion
- Tag
- Includes
- DscResource
- RoleCapability
- Comando
- Filtro

Se estiver interessado apenas em descobrir recursos de DSC específicos na galeria, você poderá executar o cmdlet [**Find-DscResource**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).
[**Find-DscResource**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) retorna dados de recursos de DSC contidos na Galeria. Como os recursos de DSC sempre são enviados como parte de um módulo, você ainda precisará executar [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) para instalar esses recursos de DSC.

<a id="learning-about-items-in-the-powershell-gallery" class="xliff"></a>
## Aprendendo sobre itens na Galeria do PowerShell

Depois de identificar um item no qual tem interesse, talvez você queira aprender mais sobre ele. Você pode fazer isso examinando a página específica do item na Galeria. Nessa página, você poderá ver todos os metadados carregados com o item. Esses metadados do item são fornecidos pelo autor do item e não são verificados pela Microsoft. O Proprietário do item está intimamente ligado à conta da Galeria usada para publicar o item e é mais confiável do que o campo Autor.

Se você descobrir que um item que acredita que não tenha sido publicado de boa fé, clique em **Relatar Abuso** na página do item.

Se estiver executando [**Find-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) ou [**Find-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), você poderá exibir esses dados no objeto PSGetModuleInfo retornado. Por exemplo, executar [**Find-Module -Name PSReadLine -Repository PSGallery | Get-Member**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) retorna dados do módulo PSReadLine na Galeria.

<a id="downloading-items-from-the-powershell-gallery" class="xliff"></a>
## Baixando itens da Galeria do PowerShell

Recomendamos o processo a seguir para baixar itens da Galeria do PowerShell:

<a id="inspect" class="xliff"></a>
### Inspecionar

Para baixar um item da Galeria para inspeção, execute o cmdlet [**Save-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) ou [**Save-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), dependendo do tipo de item. Isso permite que você salve o item localmente sem instalá-lo e inspecione o conteúdo do item. Lembre-se de excluir o item salvo manualmente.

Alguns desses itens são criados pela Microsoft e outros são criados pela comunidade do PowerShell. A Microsoft recomenda que você examine o conteúdo e o código dos itens nesta galeria antes da instalação.

Se você descobrir que um item que acredita que não tenha sido publicado de boa fé, clique em **Relatar Abuso** na página do item.

<a id="install" class="xliff"></a>
### Instalar

Para instalar um item da Galeria para uso, execute o cmdlet [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) ou [**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), dependendo do tipo de item.

[**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) instala o módulo em `$env:ProgramFiles\WindowsPowerShell\Modules`, por padrão. Isso requer uma conta de administrador. Se você adicionar o parâmetro `-Scope
CurrentUser`, o módulo será instalado em `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`.

[**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) instala o script em `$env:ProgramFiles\WindowsPowerShell\Scripts`, por padrão. Isso requer uma conta de administrador. Se você adicionar o parâmetro `-Scope
CurrentUser`, o script será instalado em `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`.

Por padrão, [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) e [**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) instalam a versão mais recente de um item. Para instalar uma versão mais antiga do item, adicione o parâmetro `-RequiredVersion`.

<a id="deploy" class="xliff"></a>
### Implantar

Para implantar um item da Galeria do PowerShell na Automação do Azure, clique em **Implantar na Automação do Azure** na página de detalhes do item. Você será redirecionado ao Portal de Gerenciamento do Azure, em que você entra usando as credenciais de sua conta do Azure. Observe que implantar itens com dependências implantará todas as dependências na Automação do Azure. O botão Implantar na Automação do Azure pode ser desabilitado adicionando a marca **AzureAutomationNotSupported** aos metadados do item.

Para saber mais sobre a Automação do Azure, consulte o [Site da Automação do Azure](http://azure.microsoft.com/en-us/services/automation/).

<a id="updating-items-from-the-powershell-gallery" class="xliff"></a>
## Atualizando itens da Galeria do PowerShell

Para atualizar os itens instalados da Galeria do PowerShell, execute o cmdlet [**Update-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) ou [**Update-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409). Quando executado sem parâmetros adicionais, [**Update-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) também tenta atualizar cada módulo instalado executando [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).
Para atualizar os módulos seletivamente, adicione o parâmetro `-Name`.

Da mesma forma, quando executado sem parâmetros adicionais, [**Update-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) também tenta atualizar cada script instalado executando [**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).
Para atualizar os scripts seletivamente, adicione o parâmetro `-Name`.

<a id="list-items-that-you-have-installed-from-the-powershell-gallery" class="xliff"></a>
## Listar itens que você instalou da Galeria do PowerShell

Para descobrir quais módulos você instalou da Galeria do PowerShell, execute o cmdlet [**Get-InstalledModule**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409). Esse comando lista todos os módulos no seu sistema que foram instalados diretamente da Galeria do PowerShell.

De forma semelhante, para descobrir quais scripts você instalou da Galeria do PowerShell, execute o cmdlet [**Get-InstalledScript**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409). Esse comando lista todos os scripts no seu sistema que foram instalados diretamente da Galeria do PowerShell.

