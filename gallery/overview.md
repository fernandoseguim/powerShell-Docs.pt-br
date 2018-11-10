---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galeria,powershell,cmdlet,psgallery,psget
title: A Galeria do PowerShell
ms.openlocfilehash: d3e3b9d8bb3d6cefd3a3bfe79b012bb1dc1d8a2d
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225611"
---
# <a name="the-powershell-gallery"></a>A Galeria do PowerShell

A Galeria do PowerShell é o repositório central de conteúdo do PowerShell. Nela, você pode encontrar módulos úteis do PowerShell que contêm comandos do PowerShell e recursos de DSC (Configuração de Estado Desejado).
Você também pode encontrar scripts do PowerShell, alguns dos quais podem conter fluxos de trabalho do PowerShell e que descrevem um conjunto de tarefas e fornecem o sequenciamento para essas tarefas. Alguns desses pacotes são criados pela Microsoft e outros são criados pela comunidade do PowerShell.

## <a name="powershellget-overview"></a>Visão geral do PowerShellGet

O módulo do PowerShellGet contém cmdlets para descoberta, instalação, atualização e publicação de pacotes PowerShell que contêm artefatos como Módulos, Recursos de DSC, Funcionalidades de Função e Scripts da [Galeria do PowerShell](https://www.PowerShellGallery.com) e outros repositórios privados.

## <a name="getting-started-with-the-gallery"></a>Introdução à Galeria

A instalação de pacotes da Galeria requer a versão mais recente do módulo PowerShellGet.
Confira [Instalando o PowerShellGet](installing-psget.md) para obter instruções completas.

Confira a página [Introdução](getting-started.md) para obter mais informações sobre como usar os comandos PowerShellGet com a Galeria. Também é possível executar *Update-Help -Module PowerShellGet* para instalar a ajuda local para esses comandos.

## <a name="supported-operating-systems"></a>Sistemas operacionais com suporte

O módulo **PowerShellGet** exige o **Windows PowerShell 3.0 ou mais recente** ou o **PowerShell Core 6.0 ou mais recente**.

Uma versão adequada do **Windows PowerShell** está disponível para esses sistemas operacionais:

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

O **PowerShellGet** requer o .NET Framework 4.5 ou posterior. Você pode instalar o .NET Framework 4.5 ou acima acessando [aqui](https://msdn.microsoft.com/library/5a4x27ek.aspx).

Como **PowerShell Core** é uma plataforma cruzada, o que significa que funciona no Windows, Linux e MacOS, ele também deixa **PowerShellGet** disponível nesses sistemas. Para obter uma lista completa de sistemas compatíveis com **PowerShell Core**, consulte [Instalação do PowerShell](/powershell/scripting/setup/installing-powershell).

Muitos módulos hospedados na galeria darão suporte a sistemas operacionais diferentes e têm outros requisitos. Consulte a documentação dos módulos para saber mais.

## <a name="got-a-question-have-feedback"></a>Tem alguma pergunta? Deseja fazer comentários?

Encontre mais informações sobre a Galeria do PowerShell e o PowerShellGet na página [Introdução](getting-started.md). Forneça comentários e relate problemas usando o [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).
