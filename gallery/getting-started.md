---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery
title: Introdução à Galeria do PowerShell
ms.openlocfilehash: 85b0a754aba25d850dc918024419318554f92b33
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225668"
---
# <a name="getting-started-with-the-powershell-gallery"></a>Introdução à Galeria do PowerShell

O modo adequado de instalar pacote da Galeria do PowerShell é usar os cmdlets do módulo [PowerShellGet](/powershell/module/powershellget). Não é necessário entrar para baixar itens da Galeria do PowerShell.

> [!NOTE]
> É possível baixar o pacote diretamente da Galeria do PowerShell, mas essa não é uma abordagem recomendada.
> Para saber mais detalhes, confira [Download manual do pacote](/powershell/gallery/how-to/working-with-packages/manual-download).

## <a name="discovering-packages-from-the-powershell-gallery"></a>Descobrir pacotes da Galeria do PowerShell

Você pode encontrar pacotes na Galeria do PowerShell, usando o controle **Pesquisar** no site ou navegando pelas páginas de Módulos e Scripts. Você pode também encontrar pacotes da Galeria do PowerShell executando os cmdlets [Find-Module][] e [Find-Script][], dependendo do tipo de item, com `-Repository PSGallery`.

A filtragem dos resultados da Galeria pode ser feita usando os seguintes parâmetros:

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

Caso tenha interesse apenas em descobrir recursos de DSC específicos na Galeria, execute o cmdlet [Find-DscResource]. Find-DscResource retorna dados em recursos de DSC contidos na Galeria.
Como os recursos de DSC sempre são fornecidos como parte de um módulo, você ainda precisa executar [Install-Module][] para instalar esses recursos.

## <a name="learning-about-packages-in-the-powershell-gallery"></a>Aprender sobre itens na Galeria do PowerShell

Depois de identificar um pacote no qual tem interesse, talvez você queira aprender mais sobre ele. Você pode fazer isso examinando a página específica do pacote na Galeria. Nessa página, você poderá ver todos os metadados carregados com o pacote. Esses metadados do pacote são fornecidos pelo autor dele e não são verificados pela Microsoft. O Proprietário do pacote está intimamente ligado à conta da Galeria usada para publicar o pacote e é mais confiável do que o campo Autor.

Se você descobrir que um pacote que acredita que não tenha sido publicado de boa fé, clique em **Relatar Abuso** na página do pacote.

Se estiver executando [Find-Module][] ou [Find-Script][], você poderá exibir esses dados no objeto PSGetModuleInfo retornado. Por exemplo, executar `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`
retorna dados sobre o módulo PSReadLine na Galeria.

## <a name="downloading-packages-from-the-powershell-gallery"></a>Baixar pacotes da Galeria do PowerShell

Recomendamos o processo a seguir para baixar pacotes da Galeria do PowerShell:

### <a name="inspect"></a>Inspecionar

Para baixar um pacote da Galeria para inspeção, execute o cmdlet [Save-Module][] ou [Save-Script][], dependendo do tipo de pacote. Isso permite que você salve o pacote localmente sem instalá-lo e inspecione o conteúdo do pacote. Lembre-se de excluir o pacote salvo manualmente.

Alguns desses pacotes são criados pela Microsoft e outros são criados pela comunidade do PowerShell.
A Microsoft recomenda que você examine o conteúdo e o código dos pacotes nesta galeria antes da instalação.

Se você descobrir que um pacote que acredita que não tenha sido publicado de boa fé, clique em **Relatar Abuso** na página do pacote.

### <a name="install"></a>Instalar

Para instalar um pacote da Galeria para uso, execute o cmdlet [Install-Module][] ou [Install-Script][], dependendo do tipo de pacote.

[Install-Module][] instala o módulo em `$env:ProgramFiles\WindowsPowerShell\Modules` por padrão.
Isso requer uma conta de administrador. Se você adicionar o parâmetro `-Scope CurrentUser`, o módulo será instalado em `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`.

[Install-Script][] instala o script em `$env:ProgramFiles\WindowsPowerShell\Scripts` por padrão.
Isso requer uma conta de administrador. Se você adicionar o parâmetro `-Scope CurrentUser`, o script será instalado em `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`.

Por padrão, [Install-Module][] e [Install-Script][] instalam a versão mais recente de um pacote.
Para instalar uma versão mais antiga do pacote, adicione o parâmetro `-RequiredVersion`.

### <a name="deploy"></a>Implantar

Para implantar um pacote da Galeria do PowerShell na Automação do Azure, clique em **Implantar na Automação do Azure** na página de detalhes do pacote. Você será redirecionado ao Portal de Gerenciamento do Azure, em que você entra usando as credenciais de sua conta do Azure. Implantar pacotes com dependências implantará todas as dependências na Automação do Azure. O botão "Implantar na Automação do Azure" pode ser desabilitado adicionando a marca **AzureAutomationNotSupported** aos metadados do pacote.

Para saber mais sobre a Automação do Azure, confira a documentação da [Automação do Azure](/azure/automation).

## <a name="updating-packages-from-the-powershell-gallery"></a>Atualizar pacotes da Galeria do PowerShell

Para atualizar pacotes instalados usando a Galeria do PowerShell, execute o cmdlet [Update-Module][] ou [Update-Script][]. Quando executado sem parâmetros adicionais, [Update-Module][] tenta atualizar cada módulo instalado executando [Install-Module][]. Para atualizar os módulos seletivamente, adicione o parâmetro `-Name`.

Da mesma forma, quando executado sem parâmetros adicionais, [Update-Script][] também tenta atualizar cada script instalado executando [Install-Script][]. Para atualizar os scripts seletivamente, adicione o parâmetro `-Name`.

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a>Listar pacotes que você instalou da Galeria do PowerShell

Para descobrir quais módulos você instalou da Galeria do PowerShell, execute o cmdlet [Get-InstalledModule][]. Esse comando lista todos os módulos no seu sistema que foram instalados diretamente da Galeria do PowerShell.

De forma semelhante, para descobrir quais scripts você instalou da Galeria do PowerShell, execute o cmdlet [Get-InstalledScript][]. Esse comando lista todos os scripts no seu sistema que foram instalados diretamente da Galeria do PowerShell.

[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script
