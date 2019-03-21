---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Usando DSC no Nano Server
ms.openlocfilehash: ac5eaf3885788f40e12e4f0a0f19025668280f7e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58054655"
---
# <a name="using-dsc-on-nano-server"></a>Usando DSC no Nano Server

> Aplica-se a: Windows PowerShell 5.0

**DSC no Nano Server** é um pacote opcional na pasta `NanoServer\Packages` de mídia do Windows Server 2016. O pacote pode ser instalado quando você cria um VHD para um Nano Server especificando **Microsoft-NanoServer-DSC-Package** como o valor do parâmetro **Packages** da função **New-NanoServerImage**. Por exemplo, se você estivesse criando um VHD para uma máquina virtual, o comando seria semelhante ao seguinte:

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

Para saber mais sobre como instalar e usar o Nano Server, bem como gerenciar o Nano Server com a comunicação remota do PowerShell, confira [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server) (Introdução ao Nano Server).

## <a name="dsc-features-available-on-nano-server"></a>Recursos de DSC disponíveis no Nano Server

Como o Nano Server dá suporte a apenas um conjunto limitado de APIs em comparação com uma versão completa do Windows Server, por enquanto, o DSC no Nano Server não tem paridade funcional completa com DSC em execução em SKUs completas. O DSC no Nano Server está em desenvolvimento ativo e ainda não é um recurso completo.

Os recursos de DSC a seguir estão disponíveis atualmente no Nano Server:

Nos modos push e pull

- Todos os cmdlets de DSC que existem em uma versão completa do Windows Server, incluindo o seguinte:
- [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [Stop-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [Publish-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [Restore-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [Remove-DscConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [Find-DscResource](https://technet.microsoft.com/en-us/library/mt517874.aspx)
- [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- Compilação de configurações (confira [Configurações DSC](../configurations/configurations.md))

  **Problema:** a criptografia de senha (confira [Protegendo o arquivo MOF](../pull-server/secureMOF.md)) durante a compilação da configuração não funciona.

- Compilação de metaconfigurações (confira [Configurando o Gerenciador de Configurações Local](../managing-nodes/metaConfig.md))

- Execução de um recurso no contexto do usuário (confira [Executar DSC com as credenciais do usuário (RunAs)](../configurations/runAsUser.md))

- Recursos baseados em classe (confira [Escrevendo um recurso personalizado de DSC com classes do PowerShell](../resources/authoringResourceClass.md))

- Depuração dos recursos de DSC (confira [Depurando os recursos de DSC](../troubleshooting/debugResource.md))

  **Problema:** não funciona se um recurso estiver usando PsDscRunAsCredential (confira [Executar DSC com credenciais de usuário](../configurations/runAsUser.md))

- [Especificando dependências de nó cruzado](../configurations/crossNodeDependencies.md)

- [Controle de versão do recurso](../configurations/sxsResource.md)

- Cliente de pull (configurações e recursos) (confira [Configurando um cliente de pull usando nomes de configuração](../pull-server/pullClientConfigNames.md))

- [Configurações parciais (pull e push)](../pull-server/partialConfigs.md)

- [Relatórios para o servidor de pull](../pull-server/reportServer.md)

- Criptografia do MOF

- Registro em log de eventos

- Relatórios de DSC de automação do Azure

- Recursos que são totalmente funcionais

- **Archive**
- **Environment**
- **File**
- **Log**
- **ProcessSet**
- **Registry**
- **Script**
- **WindowsPackageCab**
- **WindowsProcess**
- **WaitForAll** (confira [Especificação de dependências de nó cruzado](../configurations/crossNodeDependencies.md))
- **WaitForAny** (confira [Especificação de dependências de nó cruzado](../configurations/crossNodeDependencies.md))
- **WaitForSome** (confira [Especificação de dependências de nó cruzado](../configurations/crossNodeDependencies.md))

- Recursos que são parcialmente funcionais
- **Grupo**
- **GroupSet**

  **Problema:** os recursos acima falharão se a instância específica for chamada duas vezes (executando a mesma configuração duas vezes)

- **Service**
- **ServiceSet**

  **Problema:** funciona apenas para iniciar/interromper o serviço (status). Falha, se alguém tentar alterar outros atributos de serviço como startuptype, credenciais, descrição etc. O erro emitido é semelhante a:

  *Não é possível localizar o tipo [management.managementobject]: verifique se o assembly que contém esse tipo é carregado.*

- Recursos que não são funcionais
- **User**

## <a name="dsc-features-not-available-on-nano-server"></a>Recursos de DSC não disponíveis no Nano Server

Os recursos de DSC a seguir não estão disponíveis atualmente no Nano Server:

- Descriptografando documento MOF com senhas criptografadas
- Servidor de pull -- no momento não é possível definir um servidor de pull no Nano Server
- Tudo o que não está na lista de recursos funciona

## <a name="using-custom-dsc-resources-on-nano-server"></a>Usando recursos personalizados de DSC no Nano Server

Devido a conjuntos limitados de APIs do Windows e bibliotecas CLR disponíveis no Nano Server, os recursos de DSC que funcionam com a versão CLR completa do Windows não funcionam necessariamente no Nano Server.
Conclua completamente o teste antes de implantar qualquer recurso personalizado de DSC em um ambiente de produção.

## <a name="see-also"></a>Consulte Também

- [Introdução ao Nano Server](/windows-server/get-started/getting-started-with-nano-server)
