---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galeria,powershell,cmdlet,psgallery,psget
title: A Galeria do PowerShell
ms.openlocfilehash: 9519b8bcca9f43419a33db380c3b852e9bb354ac
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="the-powershell-gallery"></a>A Galeria do PowerShell

A Galeria do PowerShell é o repositório central de conteúdo do PowerShell. Você pode encontrar novos comandos do PowerShell ou recursos DSC (Configuração de Estado Desejado) na Galeria.

## <a name="powershellget-overview"></a>Visão geral do PowerShellGet

O módulo do PowerShellGet contém cmdlets para descoberta, instalação, atualização e publicação dos artefatos do PowerShell como Módulos, Recursos de DSC, Funcionalidades de Função e Scripts da [Galeria do PowerShell](https://www.PowerShellGallery.com) e outros repositórios privados.

## <a name="getting-started-with-the-gallery"></a>Introdução à Galeria

A instalação de itens da Galeria exige a versão mais recente do módulo PowerShellGet, disponível no Windows 10, no WMF (Windows Management Framework) 5.0 ou no instalador baseado em MSI (para PowerShell 3 e 4).

- [**Obter o Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),
- [**Obter o WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175) ou
- [**Obter o instalador MSI**](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

Com o módulo [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) mais recente, você pode:

-   Pesquisar itens na Galeria com [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) e [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)
-   Salvar itens da Galeria no sistema com [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) e [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334)
-   Instalar itens da Galeria com [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) e [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)
-   Carregar itens na Galeria com [Publish-Module](https://go.microsoft.com/fwlink/?LinkId=821666) e [Publish-Script](https://go.microsoft.com/fwlink/?LinkId=822331)
-   Adicionar um repositório personalizado com [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)

Confira a página [Introdução](psgallery/psgallery_gettingstarted.md) para obter mais informações sobre como usar os comandos PowerShellGet com a Galeria. Também é possível executar *Update-Help -Module PowerShellGet* para instalar a ajuda local para esses comandos.

## <a name="supported-operating-systems"></a>Sistemas operacionais com suporte

O módulo **PowerShellGet** exige o **PowerShell 3.0 ou mais recente**.

Portanto, **PowerShellGet** exige um dos seguintes sistemas operacionais:

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** também exige o .NET Framework 4.5 ou posterior. Você pode instalar o .NET Framework 4.5 ou acima acessando [aqui](https://msdn.microsoft.com/library/5a4x27ek.aspx).


## <a name="got-a-question-have-feedback"></a>Tem alguma pergunta? Deseja fazer comentários?

Encontre mais informações sobre a Galeria do PowerShell e o PowerShellGet na página [Introdução](psgallery/psgallery_gettingstarted.md). Forneça comentários e relate problemas usando o [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).