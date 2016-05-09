# Configurações DSC

>Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

As configurações DSC são scripts do PowerShell que definem um tipo especial de função. 
Para definir uma configuração utilize a palavra-chave do PowerShell __Configuration__.

```powershell
Configuration MyDscConfiguration {

    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
```

Salve o script como um arquivo .ps1.

## Sintaxe da configuração

Um script de configuração é composto por estas partes:

- O bloco **Configuration**. É o bloco de script externo. Para defini-lo, use a palavra-chave **Configuration** e forneça um nome. Nesse caso, o nome da configuração é "MyDscConfiguration".
- Um ou mais blocos de **Nó**. Definem os nós (computadores ou máquinas virtuais) que você está configurando. Na configuração acima, há um bloco de **Nó** que tem como destino um computador denominado "TEST-PC1".
- Um ou mais blocos de recurso. É onde a configuração define as propriedades para os recursos que estão sendo configurados. Nesse caso, há dois blocos de recurso; cada um deles chama o recurso "WindowsFeature".

Dentro de um bloco de **configuração**, é possível fazer qualquer coisa que normalmente poderia ser feita em uma função do PoweShell. No exemplo anterior, se você não quisesse embutir em código o nome do computador de destino na configuração, poderia adicionar um parâmetro para o nome do nó:

```powershell
Configuration MyDscConfiguration {

    param(
        [string[]]$computerName="localhost"
    )
    Node $computerName {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
```

Neste exemplo, o nome do nó é especificado ao ser passado como o parâmetro $computerName quando você [compila a configuração](# Compiling the configuration). O nome padrão é "localhost".

## Compilando a configuração
Para poder aplicar uma configuração, você precisa compilá-la em um documento MOF. Chame a configuração como chamaria uma função do PowerShell.
>__Observação:__ para chamar uma configuração, a função precisa estar no escopo global (como acontece com qualquer outra função do PowerShell). Isso pode ser feito por meio de "dot-sourcing" do script ou ao executar o script de configuração usando F5 ou clicando no botão __Executar Script__ no ISE. Para fazer o dot-source do script, execute o comando `. .\myConfig.ps1`, em que `myConfig.ps1` é o nome do arquivo de script que contém sua configuração.

Quando você chama a configuração, ela cria:

- Uma pasta no diretório atual com o mesmo nome que a configuração.
- Um arquivo chamado _NodeName_.mof no novo diretório, em que _NodeName_ é o nome do nó de destino da configuração. Se houver mais de um nó, será criado um arquivo MOF para cada nó.

>__Observação__: o arquivo MOF contém todas as informações de configuração para o nó de destino. Por isso, é importante mantê-lo seguro. Para obter mais informações, consulte [Protegendo o arquivo MOF](secureMOF.md).

A compilação da primeira configuração acima resulta na seguinte estrutura de pastas:

```powershell
PS C:\users\default\Documents\DSC Configurations> . .\MyDscConfiguration.ps1
PS C:\users\default\Documents\DSC Configurations> MyDscConfiguration
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name                                                                                              
----                -------------         ------ ----                                                                                         
-a----       10/23/2015   4:32 PM           2842 TEST-PC1.mof
```  

Se a configuração utilizar um parâmetro, como no segundo exemplo, ele precisará ser fornecido no tempo de compilação. A aparência deveria ser esta:

```powershell
PS C:\users\default\Documents\DSC Configurations> . .\MyDscConfiguration.ps1
PS C:\users\default\Documents\DSC Configurations> MyDscConfiguration -computerName 'MyTestNode'
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name                                                                                              
----                -------------         ------ ----                                                                                         
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```      

## Usando o DependsOn
Uma palavra-chave útil da DSC é __DependsOn__. Normalmente (mas nem sempre), a DSC aplica os recursos na ordem em que aparecem dentro da configuração. Contudo, o __DependsOn__ especifica quais recursos dependem de outros recursos, enquanto o LCM garante que sejam aplicados na ordem correta, independentemente da ordem na qual as instâncias de recurso são definidas. Por exemplo, uma configuração pode especificar que uma instância do recurso __User__ depende da existência de uma instância __Group__:

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = "Present"
            GroupName = "TestGroup"
        }

        User UserExample {
            Ensure = "Present"
            UserName = "TestUser"
            FullName = "TestUser"
            DependsOn = "[Group]GroupExample"
        }
    }
}
```

## Usando Novos Recursos na sua Configuração
Se você executou os exemplos anteriores, talvez tenha notado que foi informado que estava usando um recurso sem importá-lo explicitamente.
Atualmente, a DSC vem com 12 recursos como parte do módulo PSDesiredStateConfiguration. Outros recursos em módulos externos devem ser colocados em `$env:PSModulePath` para serem reconhecidos pelo LCM. Um novo cmdlet, [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), pode ser usado para determinar quais recursos estão instalados no sistema e disponíveis para uso pelo LCM. 
Depois que esses módulos forem colocados em `$env:PSModulePath` e reconhecidos adequadamente pelo [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), ainda precisam ser carregados na sua configuração. __Import-DscResource__ é uma palavra-chave dinâmica que pode ser reconhecida apenas dentro de um bloco de __configuração__ (ou seja, não é um cmdlet). O __Import-DscResource__ dá suporte a dois parâmetros:
* __ModuleName__ é a forma recomendada de usar o __Import-DscResource__. Aceita o nome do módulo que contém os recursos que serão importados (assim como uma matriz de cadeia de caracteres de nomes de módulos). 
* __Name__ é o nome do recurso que será importado. Não é o nome amigável gerado como "Name" pelo [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), mas o nome de classe usado na hora de definir o esquema de recurso (gerado como __ResourceType__ pelo [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)). 

## Consulte Também
* [Visão Geral da Configuração de Estado Desejado do Windows PowerShell](overview.md)
* [Recursos de DSC](resources.md)
* [Configurando o Gerenciador de Configurações Local](metaConfig.md)


<!--HONumber=Apr16_HO2-->


