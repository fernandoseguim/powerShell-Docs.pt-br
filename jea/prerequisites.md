---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "pré-requisitos"
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: ac9231a475ba84e9051bbd06a65f3f20c9e49846

---

# Pré-requisitos

## Estado Inicial
Antes de iniciar esta seção, verifique o seguinte:

1. O JEA está disponível no seu sistema. Confira o [LEIAME](./README.md) para ver os sistemas operacionais com suporte e os downloads necessários.
2. Você tem direitos administrativos no computador no qual está experimentando o JEA.
3. O computador está ingressado no domínio.
Consulte a seção [Criando um Controlador de Domínio](#creating-a-domain-controller) para configurar rapidamente um novo domínio em um servidor se você ainda não tiver um.

## Habilitar a Comunicação Remota do PowerShell
O gerenciamento com o JEA ocorre por meio da comunicação remota do PowerShell.
Execute o seguinte em uma janela de Administrador do PowerShell para verificar se está habilitado e configurado corretamente:

```PowerShell
Enable-PSRemoting
```

Se você não estiver familiarizado com a comunicação remota do PowerShell, seria uma boa ideia executar `Get-Help about_Remote` para saber mais sobre esse importante conceito básico.

## Identificar os Usuários ou Grupos
Para demonstrar o JEA em ação, você precisa identificar os outros usuários e grupos não administradores que serão usados em todo este guia.

Se você estiver usando um domínio existente, identifique ou crie alguns grupos e usuários não privilegiados.
Você concederá acesso para esses usuários não administradores ao JEA.
Sempre que você consultar a variável `$NonAdministrator` na parte superior de um script, atribua-a aos usuários ou grupos de não administradores selecionados.

Se você criou um novo domínio do zero, será muito mais fácil.
Use a seção [Configurar usuários e grupos](creating-a-domain-controller.md#set-up-users-and-groups) no apêndice para criar usuários e grupos não administradores.
Os valores padrão de `$NonAdministrator` serão os grupos criados nessa seção.

## Configurar o arquivo de Capacidade de Função de manutenção
Execute os seguintes comandos do PowerShell para criar o arquivo de Capacidade de Função de demonstração que usaremos para a próxima seção.
Posteriormente neste guia, você aprenderá sobre o que esse arquivo faz.

```PowerShell
# Fields in the role capability
$MaintenanceRoleCapabilityCreationParams = @{
    Author = 'Contoso Admin'
    CompanyName = 'Contoso'
    VisibleCmdlets = 'Restart-Service'
    FunctionDefinitions =
            @{ Name = 'Get-UserInfo'; ScriptBlock = { $PSSenderInfo } }
}

# Create the demo module, which will contain the maintenance Role Capability File
New-Item -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module" -ItemType Directory
New-ModuleManifest -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\Demo_Module.psd1"
New-Item -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities" -ItemType Directory

# Create the Role Capability file
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities\Maintenance.psrc" @MaintenanceRoleCapabilityCreationParams
```

## Criar e registrar um arquivo de configuração de sessão de demonstração
Execute os seguintes comandos para criar e registrar o arquivo de Configuração de Sessão de demonstração que usaremos na próxima seção.
Posteriormente neste guia, você aprenderá sobre o que esse arquivo faz.

```PowerShell
# Determine domain
$domain = (Get-CimInstance -ClassName Win32_ComputerSystem).Domain

# Replace with your non-admin group name
$NonAdministrator = "$domain\JEA_NonAdmin_Operator"

# Specify the settings for this JEA endpoint
# Note: You will not be able to use a virtual account if you are using WMF 5.0 on Windows 7 or Windows Server 2008 R2
$JEAConfigParams = @{
    SessionType = 'RestrictedRemoteServer'
    RunAsVirtualAccount = $true
    RoleDefinitions = @{
        $NonAdministrator = @{ RoleCapabilities = 'Maintenance' }
    }
    TranscriptDirectory = "$env:ProgramData\JEAConfiguration\Transcripts"
}

# Set up a folder for the Session Configuration files
if (-not (Test-Path "$env:ProgramData\JEAConfiguration"))
{
    New-Item -Path "$env:ProgramData\JEAConfiguration" -ItemType Directory
}

# Specify the name of the JEA endpoint
$sessionName = 'JEA_Demo'

if (Get-PSSessionConfiguration -Name $sessionName -ErrorAction SilentlyContinue)
{
    Unregister-PSSessionConfiguration -Name $sessionName -ErrorAction Stop
}

New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo.pssc" @JEAConfigParams

# Register the session configuration
Register-PSSessionConfiguration -Name $sessionName -Path "$env:ProgramData\JEAConfiguration\JEADemo.pssc"
```

## Habilitar o registro em log do Módulo do PowerShell (opcional)
As etapas a seguir habilitam o log para todas as ações do PowerShell em seu sistema.
Você não precisa habilitar isso para que o JEA funcione, mas será útil na seção [Relatando no JEA](reporting-on-jea.md).

1. Abra o Editor de diretiva de Grupo Local
2. Navegue para “Configuração do Computador\Modelos Administrativos\Componentes do Windows\Windows PowerShell”
3. Clique duas vezes em "Ativar o Registro de Log de Módulo"
4. Clique em “Habilitado”
5. Na seção Opções, clique em "Mostrar" ao lado dos Nomes de Módulo
6. Digite “\*” na janela pop-up. Isso significa que o PowerShell registrará comandos de todos os módulos.
7. Clique em OK e aplique a política

Observação: você também pode habilitar transcrição do PowerShell de todo o sistema por meio da Política de Grupo.

**Parabéns, você configurou seu computador com o ponto de extremidade de demonstração e está pronto para começar a usar JEA!**




<!--HONumber=Jun16_HO4-->


