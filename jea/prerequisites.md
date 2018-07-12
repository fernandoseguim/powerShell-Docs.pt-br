---
ms.date: 06/12/2017
keywords: jea,powershell,segurança
title: Pré-requisitos do JEA
ms.openlocfilehash: acc16c0c7eec357b621c0706a66b8752ae5578cd
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893028"
---
# <a name="prerequisites"></a>Pré-requisitos

> Aplica-se a: Windows PowerShell 5.0

O Just Enough Administration é um recurso incluído com o Windows PowerShell 5.0 e posteriores.
Este tópico descreve os pré-requisitos que devem ser atendidos para começar a usar o JEA.

## <a name="install-jea"></a>Instalar o JEA

O JEA está disponível com o Windows PowerShell 5.0 e posteriores, mas para a funcionalidade completa é recomendado que você instale a versão mais recente do PowerShell disponível para o seu sistema.
A tabela a seguir descreve a disponibilidade do JEA no Windows Server:

Sistema operacional de servidor   | Disponibilidade do JEA
--------------------------|--------------------------------
Windows Server 2016       | Pré-instalado
Windows Server 2012 R2    | Funcionalidade completa com o WMF 5.1
Windows Server 2012       | Funcionalidade completa com o WMF 5.1
Windows Server 2008 R2    | Funcionalidade reduzida<sup>1</sup> com WMF 5.1

Você também pode usar o JEA no seu computador residencial ou do trabalho:

Sistema Operacional do Cliente   | Disponibilidade do JEA
--------------------------|-----------------------------------------------------
Windows 10 1607+          | Pré-instalado
Windows 10 1603, 1511     | Pré-instalado, com funcionalidade reduzida<sup>2</sup>
Windows 10 1507           | Não disponível
Windows 8, 8.1            | Funcionalidade completa com o WMF 5.1
Windows 7                 | Funcionalidade reduzida<sup>1</sup> com WMF 5.1

<sup>1</sup> O JEA não pode ser configurado para usar contas de serviço gerenciado por grupo no Windows Server 2008 R2 ou Windows 7.
*Há suporte* para contas virtuais e outros recursos de JEA.

<sup>2</sup> As versões 1511 e 1603 do Windows 10 não oferecem suporte aos seguintes recursos do JEA: execução como uma conta de serviço gerenciado de grupo, regras de acesso condicional nas configurações de sessão, a unidade do usuário e a concessão de acesso a contas de usuário local.
Para obter suporte para esses recursos, atualize o Windows para a versão 1607 (Atualização de Aniversário) ou superior.

### <a name="check-which-version-of-powershell-is-installed"></a>Verificar qual versão do PowerShell que está instalada

Para verificar qual a versão do PowerShell que está instalada em seu sistema, verifique a variável `$PSVersionTable` em um prompt do Windows PowerShell.

```powershell
$PSVersionTable.PSVersion
```

```output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

Você está pronto para usar o JEA se a versão *Principal* for maior ou igual a **5**.
Para obter a melhor experiência e ter acesso a todos os recursos mais recentes, é recomendável que você atualize para a versão **5.1** do PowerShell assim que possível.

### <a name="install-windows-management-framework"></a>Instalar o Windows Management Framework

Se estiver executando uma versão mais antiga do PowerShell, você precisará atualizar o sistema com a atualização mais recente do WMF (Windows Management Framework).
Os pacotes de atualização e um link para as notas de versão mais recentes do WMF estão disponíveis no [Centro de Download](https://blogs.msdn.microsoft.com/powershell/2016/02/24/windows-management-framework-wmf-5-0-rtm-packages-has-been-republished/).

É altamente recomendável que você teste a compatibilidade da sua carga de trabalho com WMF antes de atualizar todos os seus servidores.

Os usuários do Windows 10 devem instalar as atualizações mais recentes do recurso para obter a versão atual do Windows PowerShell.

## <a name="enable-powershell-remoting"></a>Habilitar a Comunicação Remota do PowerShell

A Comunicação Remota do PowerShell fornece a base na qual o JEA é criado.
Portanto, é necessário garantir que a comunicação remota do PowerShell esteja habilitada e [devidamente protegida](/powershell/scripting/setup/winrmsecurity) em seu sistema antes de usar o JEA.

A Comunicação Remota do PowerShell é habilitada por padrão no Windows Server 2012, 2012 R2 e 2016.
Você pode habilitar a Comunicação Remota do PowerShell executando o seguinte comando em uma janela elevada do PowerShell.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>Habilitar o módulo do PowerShell e o registro em log de bloco de script (opcional)

As etapas a seguir habilitam o log para todas as ações do PowerShell em seu sistema.
O registro em log do Módulo do PowerShell não é necessário para o JEA, no entanto é altamente recomendável que você o ative para garantir que os comandos que os usuários executam sejam registrados em um local central.

Você pode configurar a política de Registro em Log do Módulo do PowerShell usando a Política de Grupo.

1. Abra o Editor de Política de Grupo Local em uma estação de trabalho ou um Objeto de Política de Grupo no Console de Gerenciamento de Política de Grupo em um Controlador de Domínio do Active Directory
2. Navegue até **Configuração do Computador\\Modelos Administrativos\\Componentes do Windows\\Windows PowerShell**
3. Clique duas vezes em **Habilitar o Log de Módulo**
4. Clique em **Habilitado**
5. Na seção Opções, clique em **Mostrar** ao lado dos Nomes de Módulo
6. Digite `\*` na janela pop-up. Isso instrui o PowerShell a registrar comandos de todos os módulos.
7. Clique em **OK** para definir a política
8. Clique duas vezes em **Ativar Registro de Bloco de Script do PowerShell**
9. Clique em **Habilitado**
10. Clique em **OK** para definir a política
11. (Somente em computadores ingressados no domínio) Execute `gpupdate` ou aguarde a Política de Grupo processar a política atualizada e aplicar as configurações

Você também pode habilitar transcrição do PowerShell de todo o sistema por meio da Política de Grupo.

## <a name="next-steps"></a>Próximas etapas

[Criar um arquivo de capacidade de função](role-capabilities.md)

[Criar um arquivo de configuração de sessão](session-configurations.md)

## <a name="see-also"></a>Consulte também

[Informações adicionais sobre a Comunicação Remota do PowerShell e segurança do WinRM](/powershell/scripting/setup/winrmsecurity)

[*Postagem no blog sobre segurança* PowerShell ♥ the Blue Team](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)