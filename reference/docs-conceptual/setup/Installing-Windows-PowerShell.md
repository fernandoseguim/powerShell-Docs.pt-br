---
ms.date: 2017-08-09
keywords: powershell, cmdlet, baixar, instalar, configurar, windows 10, windows 8.1, windows 8.0, windows 7
title: Instalar o Windows PowerShell
ms.openlocfilehash: 7a1a4bff461e3012a06a82faf4015a05b8560895
ms.sourcegitcommit: a6ee6e64d369ecf82c730411bed9750278fdb5c1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/18/2017
---
# <a name="installing-windows-powershell"></a>Instalar o Windows PowerShell

O PowerShell vem instalado por padrão em todos os Windows, começando com o Windows 7 SP1 e Windows Server 2008 R2 SP1.

Os usuários do Windows, Linux e macOS que gostariam de instalar **PowerShell 6** (beta), em seus computadores, precisam:

1.  Obter o PowerShell para o sistema operacional e a versão específicos, por meio do [GitHub](https://github.com/powershell/powershell#get-powershell)
1.  Siga as instruções de instalação
  - [Linux](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md)
  - [macOS](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#macos-1012)
  - [Windows](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi)

O PowerShell 6 também está disponível para o Docker; consulte as instruções [Instalação do Docker](https://github.com/PowerShell/PowerShell/tree/master/docker).

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a>Localizando o PowerShell no Windows 7, 8.0, 8.1 e 10

Às vezes, localizar o console do PowerShell ou o ISE (Ambiente de Script Integrado) no Windows pode ser difícil, já que sua localização muda de uma versão do Windows para a outra.

As tabelas a seguir devem ajudar você a localizar PowerShell na sua versão do Windows.
Todas as versões listadas aqui são a versão original, conforme lançada, sem atualizações.

### <a name="for-console"></a>Para o Console

Versão | Local
-- | --
Windows 10 | Clique no ícone do Windows no canto inferior esquerdo e comece digitando PowerShell
Windows 8.1, 8.0 | Na tela inicial, comece a digitar PowerShell.<br/>Se estiver na área de trabalho, clique no ícone do Windows canto inferior esquerdo, comece digitando PowerShell
Windows 7 SP1 | Clique no ícone do Windows no canto inferior esquerdo e, na caixa de pesquisa, comece digitando PowerShell

### <a name="for-ise"></a>Para o ISE

Versão | Local
-- | --
Windows 10 | Clique no ícone do Windows no canto inferior esquerdo e comece digitando ISE
Windows 8.1, 8.0 | Na tela inicial, clique em **ISE do PowerShell**.<br/>Se estiver na área de trabalho, clique no ícone do Windows canto inferior esquerdo, comece digitando **ISE do PowerShell**
Windows 7 SP1 | Clique no ícone do Windows no canto inferior esquerdo e, na caixa de pesquisa, comece digitando PowerShell

## <a name="finding-powershell-in-windows-server-versions"></a>Localizando o PowerShell em versões do Windows Server

Começando com o Windows Server 2008 R2, o sistema operacional Windows pode ser instalado sem a interface gráfica do usuário (GUI).
Edições do Windows Server sem a GUI são nomeadas **Core** e edições com a GUI são nomeadas **Desktop**.

### <a name="windows-server-core-editions"></a>Edições do Windows Server Core

Em todas as edições Core, ao fazer logon no servidor, você obtém uma janela de prompt de comando do Windows.

Digite `powerhell` e pressione **ENTER** para iniciar o PowerShell na sessão de prompt de comando. Digite `exit` para encerrar a sessão do PowerShell e retornar ao prompt de comando.

### <a name="windows-server-desktop-editions"></a>Edições do Windows Server Desktop

Em todas as edições de área de trabalho, clique no ícone do Windows canto inferior esquerdo, comece digitando PowerShell.
Você obtém as opções de ISE e de console.

A única exceção à regra acima é o ISE do Windows Server 2008 R2 SP1; nesse caso, clique no ícone do Windows canto inferior esquerdo, digite ISE do PowerShell.

## <a name="how-to-check-the-version-of-powershell"></a>Como verificar a versão do PowerShell

Para descobrir qual versão do PowerShell você instalou, inicie o console do Windows PowerShell (ou o ISE), digite `$PSVersionTable` e pressione **ENTER**.

## <a name="upgrading-existing-windows-powershell"></a>Atualizando um Windows PowerShell existente

O pacote de instalação para o PowerShell vem dentro de um instalador WMF.
A versão do instalador WMF corresponde à versão do PowerShell; Não há nenhum instalador autônomo para o Windows PowerShell.

Se você precisa atualizar a versão existente do PowerShell, no Windows, use a tabela a seguir para localizar o instalador para a versão do PowerShell para a qual você deseja atualizar.

Windows | PS 3.0 | PS 4.0 | PS 5.0 | PS 5.1 |
--|--|--|--|--|
Windows 10 (consulte a Observação 1)<br/>Windows Server 2016 | - | - | - | instalado
Windows 8.1<br/>Windows Server 2012 R2 | - | instalado | [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 8<br/>Windows Server 2012 | instalado | [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 7 SP1<br/>Windows Server 2008 R2 SP1 | [WMF 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> **Observação 1**:
  >>
  >> Na versão inicial do Windows 10, com as atualizações automáticas ativadas, o PowerShell é atualizado da versão 5.0 para a 5.1.
  >>
  >> Se a versão original do Windows 10 não for atualizada por meio de atualizações do Windows, a versão do PowerShell será a 5.0.

## <a name="need-azure-powershell"></a>O Azure PowerShell é necessário

Se você estiver procurando o **Azure PowerShell**, você poderá começar com a [Visão geral do Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure).

Caso contrário, talvez seja necessário [instalar e configurar o Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps)

## <a name="see-also"></a>Consulte Também

- [Requisitos do Sistema do Windows PowerShell](Windows-PowerShell-System-Requirements.md)
- [Iniciando o Windows PowerShell](Starting-Windows-PowerShell.md)
