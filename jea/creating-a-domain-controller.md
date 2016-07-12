---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "criando um controlador de domínio"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: d4a72a7c5883b1d3ba8de3dbc9cfe016a6fb3498
ms.openlocfilehash: 8473eb668e4da5bab01c2f2b7647cbced413bd22

---

### Criar um Controlador de Domínio

Este documento presume que seu computador está ingressado no domínio.
Se atualmente você não tiver um domínio para ingressar, esta seção poderá ajudar a preparar rapidamente um controlador de domínio usando o DSC.

#### Pré-requisitos

1.  O computador está em uma rede interna
2.  O computador não está associado a um domínio existente
3.  O computador está executando o Windows Server 2016 ou tem o WMF 5.0 instalado

#### Instalar xActiveDirectory
Se seu computador tiver uma conexão de Internet ativa, execute o seguinte comando em uma janela elevada do PowerShell:
```PowerShell
Install-Module xActiveDirectory -Force
```
Se você não tiver uma conexão com a Internet, instale o xActiveDirectory em outro computador e copie a pasta de xActiveDirectory para "C:\Arquivos de Programas\WindowsPowerShell\Modules" em seu computador.

Para confirmar se a instalação foi bem-sucedida, execute o seguinte comando:
```PowerShell
Get-Module xActiveDirectory -ListAvailable
```

#### Configurar um nome de domínio com DSC
Copie o seguinte script do PowerShell para tornar o seu computador em um Controlador de Domínio em um novo domínio.
**NOTA DO AUTOR: HÁ UM PROBLEMA CONHECIDO COM AS CREDENCIAIS FORNECIDAS NÃO SENDO USADAS.  POR QUESTÕES DE SEGURANÇA, NÃO ESQUEÇA SUA SENHA DE ADMINISTRADOR LOCAL.**

```PowerShell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value $env:COMPUTERNAME -Force

# This "MetaConfiguration" sets the DSC Engine to automatically reboot if required
[DscLocalConfigurationManager()]
Configuration MetaConfiguration
{
    Node $env:Computername
    {
        Settings
        {
            RebootNodeIfNeeded = $true
        }
    }

}

MetaConfiguration
# Apply the MetaConfiguration
Set-DscLocalConfigurationManager .\MetaConfiguration

# Configure a domain controller of a new "Contoso" domain
configuration DomainController
{
    param
    (
        $node,
        $cred
    )
    Import-DscResource -ModuleName xActiveDirectory

    Node $node
    {
        WindowsFeature ADDS
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain Contoso
        {
            DomainName = 'contoso.com'
            DomainAdministratorCredential = $cred
            SafemodeAdministratorPassword = $cred
            DependsOn = '[WindowsFeature]ADDS'
        }

        file temp
        {
            DestinationPath = 'C:\temp.txt'
            Contents = 'Domain has been created'
            DependsOn = '[xADDomain]Contoso'
        }
    }
}

$ConfigData = @{
    AllNodes = @(
        @{
            NodeName = $env:Computername
            PSDscAllowPlainTextPassword = $true
        }
    )
}

# Enter your desired password for the domain administrator (note, this will be stored as plain text)
DomainController -cred (Get-Credential -Message "Enter desired credential for domain administrator") -node $env:Computername -configurationData $ConfigData

# Apply the configuration to create the domain controller
Start-DSCConfiguration -path .\DomainController -ComputerName $env:Computername -Wait -Force -Verbose
```
O computador reiniciará algumas vezes.
Você saberá que o processo for concluído quando vir um arquivo chamado "C:\Temp.txt." que contém "O domínio foi criado."

#### Configurar usuários e grupos
Os comandos a seguir configurarão um grupo de Operador e de Suporte Técnico no seu domínio e um usuário não administrador correspondente que é membro desse grupo.
```PowerShell
# Make Groups
$NonAdminOperatorGroup = New-ADGroup -Name "JEA_NonAdmin_Operator" -GroupScope DomainLocal -PassThru
$NonAdminHelpDeskGroup = New-ADGroup -Name "JEA_NonAdmin_HelpDesk" -GroupScope DomainLocal -PassThru
$TestGroup = New-ADGroup -Name "Test_Group" -GroupScope DomainLocal -PassThru

# Make Users
$OperatorUser = New-ADUser -Name "OperatorUser" -AccountPassword (ConvertTo-SecureString 'pa$$w0rd' -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $OperatorUser

$HelpDeskUser = New-ADUser -name "HelpDeskUser" -AccountPassword (ConvertTo-SecureString 'pa$$w0rd' -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $HelpDeskUser

# Add Users to Groups
Add-ADGroupMember -Identity $NonAdminOperatorGroup -Members $OperatorUser
Add-ADGroupMember -Identity $NonAdminHelpDeskGroup -Members $HelpDeskUser
```




<!--HONumber=Jul16_HO1-->


