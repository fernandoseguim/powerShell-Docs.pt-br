---
title:   Lista de verificação da criação de recursos
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Lista de verificação da criação de recursos
Esta lista de verificação é uma lista de melhores práticas ao criar um novo Recurso DSC
## O módulo de recurso contém os arquivos .psd1 e schema.mof de cada um dos recursos 
A primeira coisa que você deve fazer é verificar se o recurso tem a estrutura correta e se ele contém todos os arquivos necessários. Cada módulo de recurso deve conter um arquivo .psd1 e cada recurso de não composição deve ter o arquivo schema.mof. Recursos que não contêm o esquema não serão listados por **Get-DscResource** e os usuários não poderão usar o IntelliSense ao escrever código nesses módulos no ISE. 
A estrutura de diretórios de exemplo para o recurso xRemoteFile, que faz parte do módulo de recurso xPSDesiredStateConfiguration, poderia ter a seguinte aparência:


```
xPSDesiredStateConfiguration
    DSCResources
        MSFT_xRemoteFile
            MSFT_xRemoteFile.psm1
            MSFT_xRemoteFile.schema.mof
    Examples
        xRemoteFile_DownloadFile.ps1
    ResourceDesignerScripts
        GenerateXRemoteFileSchema.ps1
    Tests
        ResourceDesignerTests.ps1
    xPSDesiredStateConfiguration.psd1
```

## O recurso e o esquema estão corretos e foram verificados usando cmdlets DscResourceDesigner ##
Outro aspecto importante é verificar o arquivo de esquema do recurso (*.schema.mof). 
Certifique-se de que:
-   Os tipos de propriedade estão corretos (por exemplo, não use Cadeia de caracteres para propriedades que aceitam valores numéricos; em vez disso, use UInt32 ou outros tipos numéricos)
-   Os atributos de propriedade foram especificados corretamente ([key], [required], [write] e [read])


- Pelo menos, um parâmetro no esquema deve estar marcado como [key]


- A propriedade [read] não pode coexistir com um desses: [required], [key] e [write]


- Se vários qualificadores forem especificados, exceto [read], [key] terá precedência, se [write] e [required] forem especificados, [required] terá precedência
-   ValueMap foi especificado, quando apropriado

Exemplo:
```
[Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
```

-   O nome amigável é especificado e está em conformidade com as convenções de nomenclatura do DSC

Exemplo:
```[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]```

-   Cada campo contém uma descrição significativa

Abaixo você encontrará um bom exemplo do arquivo de esquema do recurso (este é o esquema real do recurso xRemoteFile do DSC Resource Kit)
```
[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]
class MSFT_xRemoteFile : OMI_BaseResource
{
    [Key, Description("Path under which downloaded or copied file should be accessible after operation.")] String DestinationPath;
    [Required, Description("Uri of a file which should be copied or downloaded. This parameter supports HTTP and HTTPS values.")] String Uri;
    [Write, Description("User agent for the web request.")] String UserAgent;
    [Write, EmbeddedInstance("MSFT_KeyValuePair"), Description("Headers of the web request.")] String Headers[];
    [Write, EmbeddedInstance("MSFT_Credential"), Description("Specifies a user account that has permission to send the request.")] String Credential;
    [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
}; 
```
Além disso, é necessário usar os cmdlets **Test-xDscResource** e **Test-xDscSchema** do Designer de Recursos DSC para verificar automaticamente o recurso e o esquema:
```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```
Por exemplo:
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## O recurso é carregado sem erros ##
Depois de verificar se o recurso contém todos os arquivos necessários e verificá-los usando o Designer de Recursos DSC, é hora de verificar se o módulo de recurso pode ser carregado com êxito.
É possível fazê-lo manualmente ou executando `Import-Module <resource_module> -force ` e confirmando se não ocorreu nenhum erro, ou ainda escrevendo uma automação de teste. No caso do último, é possível seguir esta estrutura em seu caso de teste:
```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```
4   O recurso é idempotente no caso positivo. Uma das características fundamentais de cada um dos recursos DSC deve ser a idempotência. Isso significa que podemos aplicar uma configuração DSC contendo esse recurso várias vezes sem alterar o resultado além da aplicação inicial. Por exemplo, se criarmos uma configuração que contém o seguinte recurso File:
```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
} 
```
Depois de aplicá-la pela primeira vez, o arquivo test.txt deve aparecer na pasta C:\test. No entanto, execuções posteriores da mesma configuração não devem alterar o estado do computador (por exemplo, nenhuma cópia do arquivo test.txt deve ser criada).
Para garantir que nosso recurso é idempotente, podemos chamar repetidamente **Set-TargetResource** ao testar o recurso diretamente ou chamar **Start-DscConfiguration** várias vezes ao realizar testes de ponta a ponta. O resultado deve ser o mesmo após cada execução. 


## O cenário de modificação de usuário foi testado ##
A modificação de usuário é outro cenário comum que vale a pena testar. Ela ajuda a verificar se **Set-TargetResource** e **Test-TargetResource** funcionam corretamente. Aqui estão as etapas que devem ser seguidas para testá-la:
1.  Inicie com o recurso fora do estado desejado.
2.  Executar a configuração com o recurso
3.  Verificar se **Test-DscConfiguration** retorna True
4.  Modificar o recurso fora do estado desejado
5.  Verifique se **Test-DscConfiguration** retorna false. Veja um exemplo mais concreto usando o recurso de Registro:
1.  Inicie com a chave do Registro fora do estado desejado
2.  Executar **Start-DscConfiguration** com uma configuração para colocá-la no estado desejado e verificar se ela é passada.
3.  Executar **Test-DscConfiguration** e verificar se ela retorna True
4.  Modificar o valor da chave para que ela não esteja no estado desejado
5.  Executar **Test-DscConfiguration** e verificar se ela retorna False
6.  A funcionalidade de Get-TargetResource foi verificada usando Get-DscConfiguration

Get-TargetResource deve retornar detalhes do estado atual do recurso. Certifique-se de testá-lo chamando Get-DscConfiguration depois de aplicar a configuração e verificar se a saída reflete corretamente o estado atual do computador. É importante testá-lo separadamente, pois quaisquer problemas nesta área não aparecerão ao chamar Start-DscConfiguration.

## O recurso foi verificado com a chamada às funções **Get/Set/Test-TargetResource** diretamente ##

Certifique-se de testar as funções **Get/Set/Test-TargetResource** implementadas em seu recurso chamando-as diretamente e verificando se funcionam como esperado.

## O recurso foi verificado de ponta a ponta usando **Start-DscConfiguration** ##

É importante testar as funções **Get/Set/Test-TargetResource** chamando-as diretamente; no entanto, nem todos os problemas serão descobertos dessa maneira. Você deve concentrar uma parte significativa do teste no uso de **Start-DscConfiguration** ou no servidor de pull. Na verdade, essa é a forma como os usuários usarão o recurso; portanto, não subestime a importância desse tipo de testes. 
Possíveis tipos de problemas:
-   A Credencial/Sessão podem se comportar de maneira diferente, porque o agente do DSC é executado como um serviço.  Certifique-se de testar quaisquer recursos aqui de ponta a ponta.
-   Faz sentido verificar as mensagens de erro exibidas pelo recurso. Por exemplo, os erros gerados por **Start-DscConfiguration** podem ser diferentes daqueles exibidos ao chamar diretamente a função **Set-TargetResource**.

## O recurso se comporta corretamente em todas as plataformas do DSC com suporte (caso contrário, retorna um erro específico) ##
O recurso deve funcionar em todas as plataformas do DSC com suporte (Windows Server 2008 R2 e mais recente). Certifique-se de instalar o Windows Management Framework (WMF) mais recente em seu sistema operacional para obter a versão mais recente do DSC. Se, por design, o recurso não funcionar em algumas dessas plataformas, uma mensagem de erro específica deverá ser retornada. Além disso, certifique-se de que o recurso verifica se os cmdlets que estão sendo chamados estão presentes em um computador específico. O Windows Server 2012 adicionou um grande número de novos cmdlets que não estão disponíveis no Windows Server 2008R2, mesmo com o WMF instalado. 

## A funcionalidade do recurso foi verificada no Windows Client (se aplicável) ##
Um intervalo de teste muito comum é verificar o recurso somente nas versões do servidor do Windows. Muitos recursos também foram projetados para funcionar em SKUs do Cliente; portanto, se esse for o seu caso, não se esqueça de testá-lo nessas plataformas também. 
## Get-DSCResource lista os recursos ##
Depois de implantar o módulo no computador, uma chamada a Get-DscResource deverá listar seu recurso, entre outros, como resultado. Se não encontrar seu recurso na lista, verifique se o arquivo schema.mof para esse recurso existe. 
## O módulo de recurso contém exemplos ##
Se pretende compartilhar o recurso (esperamos que sim), crie exemplos de qualidade que ajudarão outras pessoas a entender como usá-lo. Isso é crucial, especialmente porque muitos usuários tratam o código de exemplo como documentação. 
-   Primeiro, é necessário determinar os exemplos que serão incluídos com o módulo – no mínimo, deve-se abranger os casos de uso mais importantes para o recurso:
-   Se o módulo contiver vários recursos que precisam funcionar juntos para um cenário de ponta a ponta, o exemplo de ponta a ponta básico seria, teoricamente, o primeiro.
-   Os exemplos inicias devem ser bem simples – como começar a usar seus recursos em partes gerenciáveis pequenas (por exemplo, criar um novo VHD)
-   Os exemplos posteriores devem se basear nesses exemplos (por exemplo, criar uma VM desde um VHD, remover a VM e modificá-la) e mostrar a funcionalidade avançada (por exemplo, criar uma VM com memória dinâmica)
-   Os exemplos de configurações devem ser parametrizados (todos os valores devem ser passados para a configuração como parâmetros e não deve haver nenhum valor fixo):
```powershell
configuration Sample_xRemoteFile_DownloadFile
{
    param
    (
        [string[]] $nodeName = 'localhost',

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $destinationPath,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $uri,

        [String] $userAgent,

        [Hashtable] $headers
    )

    Import-DscResource -Name MSFT_xRemoteFile -ModuleName xPSDesiredStateConfiguration

    Node $nodeName
    {
        xRemoteFile DownloadFile
        {
            DestinationPath = $destinationPath
            Uri = $uri
            UserAgent = $userAgent
            Headers = $headers
        }
    }
} 
```
-   É uma prática recomendada incluir um exemplo (comentado) de como chamar a configuração com os valores reais no final do script de exemplo. 
Por exemplo, na configuração acima, não será óbvio para todas as pessoas que é a melhor maneira de especificar UserAgent é:

`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer`  
É por isso que devemos incluir um comentário com a execução de exemplo da configuração:
```
<# 
Sample use (parameter values need to be changed according to your scenario):

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
-userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
#>  
```
-   Para cada exemplo, escreva uma breve descrição que explica o que ele faz e o significado dos parâmetros. 
-   Certifique-se de que os exemplos abrangem a maioria dos cenários importantes para o recurso e que nada está faltando, verifique se todos eles são executados e coloque o computador no estado desejado.  

## Mensagens de erro são fáceis de entender e ajudam os usuários a resolver problemas ##
Mensagens de erro úteis devem ser:
-   Existentes: o maior problema com mensagens de erro é que elas, geralmente, não existem; portanto, certifique-se de que elas existem. 
-   Fáceis de entender: legíveis por humanos e sem códigos de erro obscuros
-   Precisas: descrevem qual é exatamente o problema
-   Construtivas: fazem recomendações sobre como corrigir o problema
-   Cortês: não culpe o usuário nem o faça se sentir um tolo.Verifique os erros nos cenários de ponta a ponta (usando **Start-DscConfiguration**), pois eles podem ser diferentes daqueles retornados ao executar as funções de recurso diretamente. 

## Mensagens de log são informativas e fáceis de entender (incluindo –verbose, –debug e logs do ETW) ##
Certifique-se de que logs gerados pelo recurso são fáceis de entender e fornecem valor ao usuário. Os recursos devem gerar todas as informações que podem ser úteis para o usuário; contudo, mais logs nem sempre são o melhor. É necessário evitar a redundância e gerar dados que não fornecem valor adicional – não faça alguém percorrer centenas de entradas de log para encontrar o que está procurando. Obviamente, não fornecer nenhum log também não é uma solução aceitável para esse problema. 

Durante o teste, também é necessário analisar logs detalhados e de depuração (executando **Start-DscConfiguration** com as opções –verbose e –debug de maneira adequada), bem como os logs do ETW. Para ver os logs do ETW no DSC, vá para o Visualizador de Eventos e abra a seguinte pasta: Aplicativos e Serviços – Microsoft – Windows – Configuração de Estado Desejado.  Por padrão, haverá o canal Operacional, mas lembre-se de habilitar os canais Analítico e de Depuração (é necessário fazer isso antes de executar a configuração). 
Para habilitar os canais Analítico/de Depuração, é possível executar o script abaixo:
```powershell
$statusEnabled = $true
# Use "Analytic" to enable Analytic channel
$eventLogFullName = "Microsoft-Windows-Dsc/Debug" 
$commandToExecute = "wevtutil set-log $eventLogFullName /e:$statusEnabled /q:$statusEnabled   "
$log = New-Object System.Diagnostics.Eventing.Reader.EventLogConfiguration $eventLogFullName
if($statusEnabled -eq $log.IsEnabled)
{
    Write-Host -Verbose "The channel event log is already enabled"
    return
}     
Invoke-Expression $commandToExecute 
```
## A implementação de recurso não contêm caminhos fixos ##
Assegure-se de que não há nenhum caminho fixo na implementação de recurso, especialmente, se ele assume um idioma (en-us) ou quando houver variáveis do sistema que podem ser usadas.
Se o recurso precisar acessar caminhos específicos, use variáveis de ambiente em vez de fixar o caminho no código, pois ele pode ser diferente em outros computadores.

Exemplo:

Em vez de:
```
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
 ```
É possível escrever:
```
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)} 
```
## A implementação de recurso não contêm informações do usuário ##
Assegure-se de que não há nenhum nome de email, informações de conta ou nome de pessoas no código.
## O recurso foi testado com credenciais válidas/inválidas ##
Caso o recurso use uma credencial como parâmetro:
-   Verifique se o recurso funciona quando o Sistema Local (ou a conta de computador de recursos remotos) não tem acesso.
-   Verifique se o recurso funciona com uma credencial especificada para Get, Set e Test 
-   Caso o recurso acesse compartilhamentos, teste todas as variantes para as quais é necessário dar suporte.  
Por exemplo:
- Compartilhamentos de janelas padrão.
- Compartilhamentos DFS.
- Compartilhamentos SAMBA (se desejar dar suporte ao Linux).

## O recurso não usa cmdlets que exigem a entrada interativa ##
As funções **Get/Set/Test-TargetResource** devem ser executadas automaticamente e não devem aguardar pela entrada do usuário em nenhum estágio de execução (por exemplo, não se deve usar **Get-Credential** dentro dessas funções). Se precisar fornecer a entrada do usuário, será necessário passá-la para a configuração como parâmetro durante a fase de compilação. 
## A funcionalidade do recurso foi totalmente testada ##
Você é responsável por se certificar de que o recurso está se comportando corretamente; portanto, teste sua funcionalidade manualmente ou, melhor ainda, escreva a automação. Esta lista de verificação contém itens cujo teste é importante e/ou que, frequentemente, estão ausentes. Haverá vários testes, principalmente, aqueles funcionais que serão específicos ao recurso que está sendo testado e que não são mencionados aqui. Não se esqueça dos casos de teste negativos. Provavelmente, essa será a parte mais demorada dos testes de recurso. 
## Prática recomendada: o módulo de recurso contém a pasta Tests com o script ResourceDesignerTests.ps1 ##
É uma prática recomendada criar a pasta “Tests” dentro do módulo de recurso, criar o arquivo ResourceDesignerTests.ps1 e adicionar testes usando **Test-xDscResource** e **Test-xDscSchema** para todos os recursos em determinado módulo. 
Dessa forma, podemos validar rapidamente os esquemas de todos os recursos de determinado módulo e fazer a verificação de integridade antes da publicação.
Para xRemoteFile, ResourceTests.ps1 poderá ser bem simples, da seguinte forma:
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof 
```
**Prática recomendada: as pasta de recursos contém script de designer de recursos para gerar esquema** Cada recurso deve conter um script de designer de recursos que gera um esquema mof do recurso. Este arquivo deve ser colocado em <ResourceName>\ResourceDesignerScripts e nomeado Generate<ResourceName>Schema.ps1 Para o recurso xRemoteFile, esse arquivo será chamado GenerateXRemoteFileSchema.ps1 e conterá:
```powershell 
$DestinationPath = New-xDscResourceProperty -Name DestinationPath -Type String -Attribute Key -Description 'Path under which downloaded or copied file should be accessible after operation.'
$Uri = New-xDscResourceProperty -Name Uri -Type String -Attribute Required -Description 'Uri of a file which should be copied or downloaded. This parameter supports HTTP and HTTPS values.'
$Headers = New-xDscResourceProperty -Name Headers -Type Hashtable[] -Attribute Write -Description 'Headers of the web request.'
$UserAgent = New-xDscResourceProperty -Name UserAgent -Type String -Attribute Write -Description 'User agent for the web request.' 
$Ensure = New-xDscResourceProperty -Name Ensure -Type String -Attribute Read -ValidateSet "Present", "Absent" -Description 'Says whether DestinationPath exists on the machine'
$Credential = New-xDscResourceProperty -Name Credential -Type PSCredential -Attribute Write -Description 'Specifies a user account that has permission to send the request.'
$CertificateThumbprint = New-xDscResourceProperty -Name CertificateThumbprint -Type String -Attribute Write -Description 'Digital public key certificate that is used to send the request.'

New-xDscResource -Name MSFT_xRemoteFile -Property @($DestinationPath, $Uri, $Headers, $UserAgent, $Ensure, $Credential, $CertificateThumbprint) -ModuleName xPSDesiredStateConfiguration2 -FriendlyName xRemoteFile 
```
22  Prática recomendada: o recurso será compatível com -whatif se o recurso estiver executando operações "perigosas", é uma prática recomendada para implementar a funcionalidade -whatif. Após a conclusão, certifique-se de que a saída –whatif descreve corretamente as operações que ocorreriam se o comando fosse executado sem a opção –whatif.
Além disso, verifique se as operações não são executadas (não é feita nenhuma alteração ao estado do nó) quando a opção –whatif está presente. 
Por exemplo, vamos supor que estamos testando o recurso File. Veja abaixo uma configuração simples que cria o arquivo “test.txt” com o conteúdo “test”:
```powershell
configuration config
{
    node localhost 
    {
        File file
        {
            Contents="test"
            DestinationPath="C:\test\test.txt"
        }
    }
}
config 
```
Se compilarmos e, em seguida, executarmos a configuração com a opção –whatif, a saída nos informará exatamente o que aconteceria quando a configuração fosse executada. Todavia, a configuração propriamente dita não foi executada (o arquivo test.txt não foi criado).
```powershell 
Start-DscConfiguration -path .\config -ComputerName localhost -wait -verbose -whatif
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer CHARLESX1 with user sid
S-1-5-21-397955417-626881126-188441444-5179871.
What if: [X]: LCM:  [ Start  Set      ]
What if: [X]: LCM:  [ Start  Resource ]  [[File]file]
What if: [X]: LCM:  [ Start  Test     ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]: LCM:  [ End    Test     ]  [[File]file]  in 0.0270 seconds.
What if: [X]: LCM:  [ Start  Set      ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]:                            [C:\test\test.txt] Creating and writing contents and setting attributes.
What if: [X]: LCM:  [ End    Set      ]  [[File]file]  in 0.0180 seconds.
What if: [X]: LCM:  [ End    Resource ]  [[File]file]
What if: [X]: LCM:  [ End    Set      ]
VERBOSE: [X]: LCM:  [ End    Set      ]    in  0.1050 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

Isso conclui nossa lista de verificação. Tenha em mente de que esta lista não é completa, mas abrange muitos problemas importantes enfrentados durante a criação, o desenvolvimento e teste dos recursos DSC. Ter uma lista de verificação ajuda a garantir que não esquecemos nenhum desses aspectos. De fato, nós mesmos usamos uma na Microsoft ao desenvolver recursos DSC. 
Se você desenvolveu diretrizes e práticas recomendadas que você usa para escrever e testar recursos DSC, compartilhe-as!



<!--HONumber=May16_HO3-->


