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
ms.openlocfilehash: 80b957ed666ca626c6083041cf99c263e2e0dc27
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: pt-BR
---
### <a name="creating-a-domain-controller"></a><span data-ttu-id="efc8e-103">Criar um Controlador de Domínio</span><span class="sxs-lookup"><span data-stu-id="efc8e-103">Creating a Domain Controller</span></span>

<span data-ttu-id="efc8e-104">Este documento presume que seu computador está ingressado no domínio.</span><span class="sxs-lookup"><span data-stu-id="efc8e-104">This document assumes that your machine is domain joined.</span></span>
<span data-ttu-id="efc8e-105">Se atualmente você não tiver um domínio para ingressar, esta seção poderá ajudar a preparar rapidamente um controlador de domínio usando o DSC.</span><span class="sxs-lookup"><span data-stu-id="efc8e-105">If you currently don't have a domain to join, this section can help you quickly stand up a domain controller using DSC.</span></span>

#### <a name="prerequisites"></a><span data-ttu-id="efc8e-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="efc8e-106">Prerequisites</span></span>

1.  <span data-ttu-id="efc8e-107">O computador está em uma rede interna</span><span class="sxs-lookup"><span data-stu-id="efc8e-107">The machine is on an internal network</span></span>
2.  <span data-ttu-id="efc8e-108">O computador não está associado a um domínio existente</span><span class="sxs-lookup"><span data-stu-id="efc8e-108">The machine is not joined to an existing domain</span></span>
3.  <span data-ttu-id="efc8e-109">O computador está executando o Windows Server 2016 ou tem o WMF 5.0 instalado</span><span class="sxs-lookup"><span data-stu-id="efc8e-109">The machine is running Windows Server 2016 or has WMF 5.0 installed</span></span>

#### <a name="install-xactivedirectory"></a><span data-ttu-id="efc8e-110">Instalar xActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="efc8e-110">Install xActiveDirectory</span></span>
<span data-ttu-id="efc8e-111">Se seu computador tiver uma conexão de Internet ativa, execute o seguinte comando em uma janela elevada do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="efc8e-111">If your machine has an active internet connection, run the following command in an elevated PowerShell window:</span></span>
```PowerShell
Install-Module xActiveDirectory -Force
```
<span data-ttu-id="efc8e-112">Se você não tiver uma conexão com a Internet, instale o xActiveDirectory em outro computador e copie a pasta de xActiveDirectory para "C:\Arquivos de Programas\WindowsPowerShell\Modules" em seu computador.</span><span class="sxs-lookup"><span data-stu-id="efc8e-112">If you do not have an internet connection, install xActiveDirectory to another machine and then copy the xActiveDirectory folder to the "C:\Program Files\WindowsPowerShell\Modules" folder on your machine.</span></span>

<span data-ttu-id="efc8e-113">Para confirmar se a instalação foi bem-sucedida, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="efc8e-113">To confirm the installation succeeded, run the following command:</span></span>
```PowerShell
Get-Module xActiveDirectory -ListAvailable
```

#### <a name="set-up-a-domain-with-dsc"></a><span data-ttu-id="efc8e-114">Configurar um nome de domínio com DSC</span><span class="sxs-lookup"><span data-stu-id="efc8e-114">Set up a domain with DSC</span></span>
<span data-ttu-id="efc8e-115">Copie o seguinte script do PowerShell para tornar o seu computador em um Controlador de Domínio em um novo domínio.</span><span class="sxs-lookup"><span data-stu-id="efc8e-115">Copy the following script in PowerShell to make your machine a Domain Controller in a new domain.</span></span>
<span data-ttu-id="efc8e-116">**NOTA DO AUTOR: HÁ UM PROBLEMA CONHECIDO COM AS CREDENCIAIS FORNECIDAS NÃO SENDO USADAS.  POR QUESTÕES DE SEGURANÇA, NÃO ESQUEÇA SUA SENHA DE ADMINISTRADOR LOCAL.**</span><span class="sxs-lookup"><span data-stu-id="efc8e-116">**AUTHOR'S NOTE: THERE IS A KNOWN ISSUE WITH THE CREDENTIALS PROVIDED NOT BEING USED.  TO BE SAFE, DON'T FORGET YOUR LOCAL ADMIN PASSWORD.**</span></span>

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
<span data-ttu-id="efc8e-117">O computador reiniciará algumas vezes.</span><span class="sxs-lookup"><span data-stu-id="efc8e-117">Your machine will restart a few times.</span></span>
<span data-ttu-id="efc8e-118">Você saberá que o processo for concluído quando vir um arquivo chamado "C:\Temp.txt." que contém "O domínio foi criado."</span><span class="sxs-lookup"><span data-stu-id="efc8e-118">You will know the process is complete once you see a file called "C:\temp.txt" containing "Domain has been created."</span></span>

#### <a name="set-up-users-and-groups"></a><span data-ttu-id="efc8e-119">Configurar usuários e grupos</span><span class="sxs-lookup"><span data-stu-id="efc8e-119">Set up Users and Groups</span></span>
<span data-ttu-id="efc8e-120">Os comandos a seguir configurarão um grupo de Operador e de Suporte Técnico no seu domínio e um usuário não administrador correspondente que é membro desse grupo.</span><span class="sxs-lookup"><span data-stu-id="efc8e-120">The following commands will set up an Operator and Helpdesk group in your domain and a corresponding non-administrator user who is a member of that group.</span></span>
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

