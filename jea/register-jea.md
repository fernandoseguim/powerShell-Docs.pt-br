---
ms.date: 06/12/2017
keywords: jea,powershell,segurança
title: Registrando Configurações de JEA
ms.openlocfilehash: 2c4a8f64c966903a6eb8fcabe4cd25ae7f98b2c4
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522825"
---
# <a name="registering-jea-configurations"></a>Registrando Configurações de JEA

> Aplica-se a: Windows PowerShell 5.0

A última etapa antes de usar o JEA, depois que você tiver criado os [recursos de função](role-capabilities.md) e os [arquivo de configuração de sessão](session-configurations.md), é registrar o ponto de extremidade JEA.
Esse processo aplica as informações de configuração de sessão no sistema e torna o ponto de extremidade disponível para uso pelos usuários e pelos mecanismos de automação.

## <a name="single-machine-configuration"></a>Configuração de computador único

Em ambientes pequenos, você pode implantar o JEA ao registrar o arquivo de configuração de sessão usando o cmdlet [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration).

Antes de começar, verifique se os pré-requisitos a seguir foram atendidos:
- Uma ou mais funções foram criadas e colocadas na pasta 'RoleCapabilities' de um módulo de PowerShell válido.
- Um arquivo de configuração de sessão foi criado e testado.
- O usuário que está registrando a configuração JEA tem direitos de administrador nos sistemas.

Também é necessário selecionar um nome para o ponto de extremidade JEA.
O nome do ponto de extremidade JEA será necessário quando os usuários desejarem se conectar ao sistema usando o JEA.
Você pode usar o cmdlet [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) para verificar os nomes dos pontos de extremidade existentes no sistema.
Pontos de extremidade que começam com 'microsoft' geralmente são fornecidos com o Windows.
O ponto de extremidade 'microsoft.powershell' é o ponto de extremidade padrão usado ao se conectar a um ponto de extremidade remoto do PowerShell.

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

Depois de determinar um nome apropriado para seu ponto de extremidade JEA, execute o seguinte comando para registrar o ponto de extremidade.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> O comando acima reiniciará o serviço WinRM no sistema.
> Isso encerrará todas as sessões de comunicação remota do PowerShell, bem como quaisquer configurações de DSC em andamento.
> É recomendável que você coloque em offline todos computadores de produção antes de executar o comando para evitar interromper as operações de negócios.

Se o registro foi bem-sucedido, você estará pronto para [usar o JEA](using-jea.md).
Você pode excluir o arquivo de configuração de sessão a qualquer momento; ele não é mais usado depois do registro.

## <a name="multi-machine-configuration-with-dsc"></a>Configuração de vários computadores com o DSC

Se você estiver implantando o JEA em vários computadores, o modelo de implantação mais simples é usar o recurso [Configuração de Estado Desejado](https://msdn.microsoft.com/powershell/dsc/overview) do JEA para implantar o JEA de forma rápida e consistente em cada computador.

Para implantar o JEA com o DSC, você precisará garantir que os seguintes pré-requisitos sejam atendidos:
- Um ou mais recursos de função foram criados e adicionados a um módulo de PowerShell válido.
- O módulo do PowerShell que contém as funções é armazenado em um compartilhamento de arquivo (somente leitura) acessível por cada computador.
- As configurações para a configuração de sessão foram determinadas. Não é necessário criar um arquivo de configuração de sessão ao usar o recurso DSC do JEA.
- Você tem credenciais que permitem a execução de ações administrativas em cada computador ou tem acesso a um servidor de pull de DSC usado para gerenciar os computadores.
- O [recurso DSC do JEA](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource) foi baixado

Em um computador de destino (ou servidor de pull, se você estiver usando um), crie uma configuração DSC para seu ponto de extremidade JEA.
Nessa configuração, será utilizado o recurso DSC de JustEnoughAdministration para configurar o arquivo de configuração de sessão e o Recurso de arquivo para copiar sobre os recursos de função do compartilhamento de arquivos.

As seguintes propriedades são configuráveis usando o recurso de DSC:
- Definições de Função
- Grupos de Conta Virtual
- Nome de Conta de Serviço Gerenciado de Grupo
- Diretório de transcrição
- Unidade de usuário
- Regras de acesso condicional
- Scripts de inicialização para a sessão JEA

A sintaxe para cada uma dessas propriedades em uma configuração DSC é consistente com o arquivo de configuração de sessão do PowerShell.

Abaixo está um exemplo de configuração de DSC para um módulo de manutenção geral do servidor.

Ele assume que um módulo válido do PowerShell contendo recursos de função em uma subpasta 'RoleCapabilities' está localizado no compartilhamento de arquivos '\\\\myfileshare\\JEA'.


```powershell
Configuration JEAMaintenance
{
    Import-DscResource -Module JustEnoughAdministration, PSDesiredStateConfiguration

    File MaintenanceModule
    {
        SourcePath = "\\myfileshare\JEA\ContosoMaintenance"
        DestinationPath = "C:\Program Files\WindowsPowerShell\Modules\ContosoMaintenance"
        Checksum = "SHA-256"
        Ensure = "Present"
        Type = "Directory"
        Recurse = $true
    }

    JeaEndpoint JEAMaintenanceEndpoint
    {
        EndpointName = "JEAMaintenance"
        RoleDefinitions = "@{ 'CONTOSO\JEAMaintenanceAuditors' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit' }; 'CONTOSO\JEAMaintenanceAdmins' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit', 'GeneralServerMaintenance-Admin' } }"
        TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
        DependsOn = '[File]MaintenanceModule'
    }
}
```

Essa configuração pode ser aplicada em um sistema [invocando diretamente o Gerenciador de Configurações Local](https://msdn.microsoft.com/powershell/dsc/metaconfig) ou atualizando a [configuração do servidor de pull](https://msdn.microsoft.com/powershell/dsc/pullserver).

O recurso DSC também permite que você substitua o ponto de extremidade de comunicação remota padrão Microsoft.PowerShell.
Se você fizer isso, o recurso registrará automaticamente um ponto de extremidade irrestrito de backup chamado "Microsoft.PowerShell.Restricted", que tem a ACL do WinRM padrão (permitindo que Usuários de Gerenciamento Remoto e membros do grupo local de Administradores o acessem).

## <a name="unregistering-jea-configurations"></a>Cancelando o registro de configurações de JEA

Para remover um ponto de extremidade JEA em um sistema, use o cmdlet [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration).
O cancelamento do registro de um ponto de extremidade JEA impedirá que novos usuários criem novas sessões de JEA no sistema.
Ele também permite que você atualize uma configuração de JEA, registrando novamente um arquivo de configuração de sessão atualizado usando o mesmo nome de ponto de extremidade.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> O cancelamento do registro de um ponto de extremidade JEA fará com que o serviço WinRM seja reiniciado.
> Isso interromperá a maioria das operações de gerenciamento remotas em andamento, incluindo outras sessões do PowerShell, invocações de WMI e algumas ferramentas de gerenciamento.
> Cancele o registro de pontos de extremidade do PowerShell somente durante janelas de manutenção planejadas.

## <a name="next-steps"></a>Próximas etapas

- [Testar o ponto de extremidade JEA](using-jea.md)