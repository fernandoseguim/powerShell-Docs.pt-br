---
title: Usando DSC no Nano Server
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 962941ba946a67256baf141bd195361c94a68f90

---

# Usando DSC no Nano Server

> Aplica-se a: Windows PowerShell 5.0

**DSC no Nano Server** é um pacote opcional na pasta `NanoServer\Packages` de mídia do Windows Server 2016. O pacote pode ser instalado quando você cria um VHD para um Nano Server especificando **Microsoft-NanoServer-DSC-Package** como o valor do parâmetro **Packages** da função **New-NanoServerImage**. Por exemplo, se você estivesse criando um VHD para uma máquina virtual, o comando seria semelhante ao seguinte:

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

Para saber mais sobre como instalar e usar o Nano Server, bem como gerenciar o Nano Server com a comunicação remota do PowerShell, confira [Getting Started with Nano Server](https://technet.microsoft.com/en-us/library/mt126167.aspx) (Introdução ao Nano Server).


## Recursos de DSC disponíveis no Nano Server

 Como o Nano Server dá suporte a apenas um conjunto limitado de APIs em comparação com uma versão completa do Windows Server, por enquanto, o DSC no Nano Server não tem paridade funcional completa com DSC em execução em SKUs completas. O DSC no Nano Server está em desenvolvimento ativo e ainda não é um recurso completo.
 
 Os recursos de DSC a seguir estão disponíveis atualmente no Nano Server: 


* Nos modos push e pull

* Todos os cmdlets de DSC que existem em uma versão completa do Windows Server, incluindo o seguinte: 
  * [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx)
  * [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx)   
  * [Enable-DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx)
  * [Disable-DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx)       
  * [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx)
  * [Stop-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143542.aspx)
  * [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx)
  * [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx)      
  * [Publish-DscConfiguraiton](https://technet.microsoft.com/en-us/library/mt517875.aspx) 
  * [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx)
  * [Restore-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407383.aspx)
  * [Remove-DscConfigurationDocument](https://technet.microsoft.com/en-us/library/mt143544.aspx)
  * [Get-DscConfigurationStatus](https://technet.microsoft.com/en-us/library/mt517868.aspx)
  * [Invoke-DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx)
  * [Find-DscResource](https://technet.microsoft.com/en-us/library/mt517874.aspx)
  * [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)
  * [New-DscChecksum](https://technet.microsoft.com/en-us/library/dn521622.aspx)    

* Compilação de configurações (confira [Configurações DSC](configurations.md))

  **Problema:** a criptografia de senha (confira [Protegendo o arquivo MOF](securemof.md)) durante a compilação da configuração não funciona.

* Compilação de metaconfigurações (confira [Configurando o Gerenciador de Configurações Local](metaConfig.md))

* Execução de um recurso no contexto do usuário (confira [Executar DSC com as credenciais do usuário (RunAs)](runAsUser.md))

* Recursos baseados em classe (confira [Escrevendo um recurso personalizado de DSC com classes do PowerShell](authoringResourceClass.md))

* Depuração dos recursos de DSC (confira [Depurando os recursos de DSC](debugresource.md))
  
  **Problema:** não funciona se um recurso estiver usando PsDscRunAsCredential (confira [Executar DSC com as credenciais do usuário](runAsUser.md))

* [Especificando dependências de nó cruzado](crossNodeDependencies.md) 

* [Controle de versão do recurso](sxsResource.md)

* Cliente de pull (configurações e recursos) (confira [Configurando um cliente de pull usando nomes de configuração](pullClientConfigNames.md))

* [Configurações parciais (pull e push)](partialConfigs.md)

* [Relatórios para o servidor de pull](reportServer.md) 

* Criptografia do MOF

* Registro em log de eventos

* Relatórios de DSC de automação do Azure

* Recursos que são totalmente funcionais
  * [Archive](archiveResource.md)
  * [Ambiente](environmentResource.md)
  * [Arquivo](fileResource.md)
  * [Log](logResource.md)
  * ProcessSet
  * [Registro](registryResource.md)
  * [script](scriptResource.md)
  * WindowsPackageCab
  * [WindowsProcess](windowsProcessResource.md)
  * WaitForAll (confira [Especificação de dependências de nó cruzado](crossNodeDependencies.md))
  * WaitForAny (confira [Especificação de dependências de nó cruzado](crossNodeDependencies.md))
  * WaitForSome (confira [Especificação de dependências de nó cruzado](crossNodeDependencies.md))

* Recursos que são parcialmente funcionais
  * [Grupo](groupResource.md)
  * GroupSet
  
  **Problema:** os recursos acima falharão se a instância for chamada duas vezes (executando a mesma configuração duas vezes)
  
  * [Serviço](serviceResource.md)
  * ServiceSet
  
  **Problema:** só funciona para iniciar/interromper o serviço (status). Falha, se alguém tentar alterar outros atributos de serviço como startuptype, credenciais, descrição etc. O erro emitido é semelhante a:
  
  *Não é possível localizar o tipo [management.managementobject]: verifique se o assembly que contém esse tipo é carregado.*
  
* Recursos que não são funcionais
  * [User](userResource.md)
  

## Recursos de DSC não disponíveis no Nano Server

Os recursos de DSC a seguir não estão disponíveis atualmente no Nano Server:

* Descriptografando documento MOF com senhas criptografadas 
* Servidor de pull -- no momento não é possível definir um servidor de pull no Nano Server
* Tudo o que não está na lista de recursos funciona

## Usando recursos personalizados de DSC no Nano Server
 
Devido a conjuntos limitados de APIs do Windows e bibliotecas CLR disponíveis no Nano Server, os recursos de DSC que funcionam com a versão CLR completa do Windows não funcionam necessariamente no Nano Server. Conclua completamente o teste antes de implantar qualquer recurso personalizado de DSC em um ambiente de produção.

## Consulte Também
- [Introdução ao Nano Server](https://technet.microsoft.com/en-us/library/mt126167.aspx)




<!--HONumber=Jun16_HO4-->


