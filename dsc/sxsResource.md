# Usando recursos com várias versões

> Aplica-se a: Windows PowerShell 5.0

No PowerShell 5.0, recursos de DSC podem ter várias versões e as versões podem ser instaladas em um computador lado a lado. Isso é implementado por ter várias versões de um módulo de recursos
que estão contidas na mesma pasta do módulo.

## Instalando várias versões de recurso lado a lado

Você pode usar os parâmetros **MinimumVersion**, **MaximumVersion** e **RequiredVersion** do cmdlet [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) para especificar
qual versão de um módulo instalar. Se você chamar **Install-Module** sem especificar uma versão, a versão mais recente será instalada.

Por exemplo, há várias versões do módulo **xFailOverCluster**, cada um com um recurso **xCluster**. O resultado da chamada **Install-Module** sem especificar o
número de versão é o seguinte:

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

Agora, se você chamar **Install-Module** novamente, mas especificar uma **RequiredVersion** de 1.1.0.0, resultará no seguinte:

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster -RequiredVersion 1.1
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## Especificando uma versão do recurso em uma configuração

Se você tiver vários recursos instalados em um computador, deve especificar a versão do recurso ao usá-lo em uma configuração. Você pode fazer isso especificando o parâmetro **ModuleVersion** 
da palavra-chave **Import-DscResource**. Se você não especificar a versão de um módulo de recursos de um recurso com mais de uma versão instalada, a configuração
gerará um erro.

A configuração a seguir mostra como especificar a versão do recurso a ser chamado:

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}     
```

>Observação: o parâmetro ModuleVersion de Import-DscResource não está disponível no PowerShell 4.0. No PowerShell 4.0, você pode especificar uma versão do módulo, passando um objeto de especificação do módulo 
>para o parâmetro ModuleName de Import-DscResource. Um objeto de especificação de módulo é uma tabela de hash que contém as chaves ModuleName e RequiredVersion. Por exemplo:

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}     
```

Isso também funcionará no PowerShell 5.0, mas é recomendável que você use o parâmetro **ModuleVersion**.

## Consulte também
* [Configurações DSC](configurations.md)
* [Recursos de DSC](resources.md)

<!--HONumber=Apr16_HO4-->


