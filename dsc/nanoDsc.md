# Usando DSC no Nano Server

> Aplica-se a: Windows PowerShell 5.0

**DSC no Nano Server** é um pacote opcional na pasta `NanoServer\Packages` de mídia do Windows Server 2016. O pacote pode ser instalado quando você cria um VHD para um Nano Server ao
especificar **Microsoft-NanoServer-DSC-Package** como o valor do parâmetro **Packages** da função **New-NanoServerImage**. Por exemplo, se você estiver criando um VHD para uma máquina virtual,
o comando seria parecido com este:

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

Para obter informações sobre como instalar e usar o Nano Server, bem como gerenciar o Nano Server com a comunicação remota do PowerShell, consulte 
[Introdução ao Nano Server](https://technet.microsoft.com/en-us/library/mt126167.aspx).


## Recursos de DSC disponíveis no Nano Server

 Como o Nano Server dá suporte a apenas um conjunto limitado de APIs em comparação com uma versão completa do Windows Server, o DSC no Nano Server não tem paridade funcional completo com DSC em execução em 
 SKUs completas por enquanto. O DSC no Nano Server está em desenvolvimento ativo e ainda não é um recurso completo.
 
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
    
* Compilando configurações (consulte [Configurações de DSC](configurations.md))
* Compilando metaconfigurações (consulte [Configurando o Gerenciador de Configurações Local](metaConfig.md))
* [Executar DSC com credenciais do usuário (RunAs)](runAsUser.md)
* Recursos baseados em classe (consulte [Escrevendo um recurso DSC personalizado com classes do PowerShell](authoringResourceClass.md))
* [Especificando dependências de nó cruzado](crossNodeDependencies.md) 
* [Controle de versão do recurso](sxsResource.md)
* Eventos
* Cliente de pull (configurações e recursos) (veja [Configurando um cliente de pull usando nomes de configuração](pullClientConfigNames.md))
* [Configurações parciais (pull e push)](partialConfigs.md)
* [Relatórios para o servidor de pull](reportServer.md) 
* Criptografia do MOF
* Registro em log de eventos
* Relatórios de DSC de automação do Azure


* Recursos que funcionam
  * [Archive](archiveResource.md)
  * [Ambiente](environmentResource.md)
  * [Arquivo](fileResource.md)
  * [Grupo](groupResource.md)
  * GroupSet
  * [Log](logResource.md)
  * ProcessSet
  * [Registro](registryResource.md)
  * [Serviço](serviceResource.md)
  * ServiceSet
  * [script](scriptResource.md)
  * [User](userResource.md)
  * WindowsPackageCab
  * [WindowsProcess](windowsProcessResource.md)

  * WaitForAll (veja [Especificando dependências de nó cruzado](crossNodeDependencies.md))
  * WaitForAny (veja [Especificando dependências de nó cruzado](crossNodeDependencies.md))
  * WaitForSome (veja [Especificando dependências de nó cruzado](crossNodeDependencies.md))

## Recursos de DSC não disponíveis no Nano Server

Os recursos de DSC a seguir não estão disponíveis atualmente no Nano Server:

* Servidor de pull -- no momento não é possível definir um servidor de pull no Nano Server
* Tudo o que não está na lista de recursos funciona

## Usando recursos personalizados de DSC no Nano Server
 
Devido a conjuntos limitados de APIs do Windows e bibliotecas CLR disponíveis no Nano Server, os recursos de DSC que funcionam com a versão CLR completa do Windows não funcionam necessariamente no Nano Server. 
Conclua completamente o teste antes de implantar qualquer recurso personalizado de DSC em um ambiente de produção.

## Consulte Também
- [Introdução ao Nano Server](https://technet.microsoft.com/en-us/library/mt126167.aspx)

<!--HONumber=Apr16_HO4-->


