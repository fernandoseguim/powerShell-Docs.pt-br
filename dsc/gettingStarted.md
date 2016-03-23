# Introdução à Configuração de Estado Desejado do PowerShell #

Este guia descreve como começar a criar documentos de Configuração de Estado Desejado do PowerShell e aplicá-los aos computadores. Assume que há uma familiaridade básica com cmdlets, módulos e funções do PowerShell. 


## Criar uma configuração ##

[**Configurações**](https://msdn.microsoft.com/en-us/powershell/dsc/configurations) são documentos que descrevem um ambiente. Os ambientes consistem em "**nós**", que normalmente são máquinas virtuais ou físicas. 

As configurações podem vir de várias formas. A maneira mais fácil de criar uma nova configuração é criar um arquivo .ps1 (script do PowerShell). Para fazer isso, abra o editor escolhido por você. O ISE do PowerShell é uma boa opção, pois entenda a DSC nativamente. Salve o seguinte como um PS1:

```powershell
configuration myFirstConfiguration
{
    import-dscresource -name WindowsFeature

    Node localhost
    {
        WindowsFeature IIS
        {
            Name = "IIS"

        }
        
    }

}
```
## Partes de uma Configuração ##
**Configuration** é uma palavra-chave que foi adicionada ao PowerShell 4.0. Significa um tipo especial de função do PowerShell usado pela Configuração de Estado Desejado. Neste exemplo, a função é chamada de myFirstConfiguration. 

A próxima linha é uma instrução de importação, semelhante à importação de um módulo. Será discutida posteriormente.

"Nó" define o nome do computador em que essa configuração vai agir. Embora ela seja editada localmente, as configurações podem chegar a nós remotos e configurá-los. 

Os nós podem ser nomes ou endereços IP de computador. Você pode ter vários nós em um único documento de configuração. Usando [dados de configuração](https://msdn.microsoft.com/en-us/powershell/dsc/configdata), também é possível aplicar a mesma configuração a vários nós. Nesse caso, o nó é "localhost" - o que significa o computador local. 

O próximo item é um [**recurso**](https://msdn.microsoft.com/en-us/powershell/dsc/resources). Os recursos são blocos de construção de configurações. Cada recurso é um módulo que define a lógica de implementação de um único aspecto de um computador. Você pode exibir todos os recursos no seu computador executando **Get-DscResource** no PowerShell. Os recursos devem estar presentes no computador local e ser importados antes que possam ser usados em uma configuração com **Import-DscResource**, que está na segunda linha dessa configuração. 

**Aplicando uma Configuração**

Se o script acima for salvo e executado, nenhuma saída será produzida. Isso ocorre porque a configuração é apenas uma função e o script acima definiu a função, mas ainda não a executou. Depois de ser definida, a função precisa ser chamada:
```powershell
myFirstConfiguration
```

Quando executadas, as funções de configuração validam a configuração. Ela não deve ter nenhum erro de sintaxe, os recursos devem ter todos os parâmetros obrigatórios definidos e todos os recursos devem ser importados antes da execução.

Depois de ser executada, a configuração cria uma pasta com seu nome contendo um **arquivo .MOF file** para cada nó na configuração. O arquivo MOF é um formato de gerenciamento baseado em padrões que é usado pela DSC do PowerShell para se comunicar pela rede.

Para aplicar a configuração:
```powershell
Start-DscConfiguration -path ./myFirstConfiguration
```
É criado um trabalho do PowerShell que atinge os nós na configuração e os configura. Para ver a saída do trabalho, use -wait. 
```powershell
Start-DscConfiguration -path ./myFirstConfiguration -wait
```

<!--HONumber=Feb16_HO4-->
