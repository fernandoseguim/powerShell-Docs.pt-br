# Visão Geral da Configuração de Estado Desejado do Windows PowerShell 

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

Este tópico descreve o recurso de Configuração de Estado Desejado (DSC) do Windows PowerShell no Windows PowerShell. Ele pode ser usado para obter uma visão geral da DSC e localizar os recursos de documentação de que você precisa para compreender e usar a DSC.

## Descrição do recurso
A DSC é uma nova plataforma de gerenciamento do Windows PowerShell que permite implantar e gerenciar dados de configuração para serviços de software e gerenciar o ambiente no qual esses serviços são executados.

Ela fornece um conjunto de extensões de linguagem do Windows PowerShell, novos cmdlets do Windows PowerShell e recursos que podem ser utilizados para especificar declarativamente como você deseja que o ambiente de software seja configurado. Também fornece um meio para manter e gerenciar as configurações existentes.

## Aplicações práticas
Seguem alguns exemplos de cenários em que você pode usar recursos internos de DSC para configurar e gerenciar um conjunto de computadores (também conhecidos como nós de destino) de uma maneira automatizada:

* Habilitar ou desabilitar funções e recursos de servidor
* Gerenciar configurações de Registro
* Gerenciar arquivos e diretórios
* Iniciar, interromper e gerenciar processos e serviços
* Gerenciar grupos e contas de usuário
* Implantar software novo
* Gerenciar variáveis de ambiente
* Executar scripts do Windows PowerShell
* Corrigir uma configuração que esteja dessincronizada em relação ao estado desejado
* Descobrir o estado de configuração real em um nó específico

## Conceitos Principais
A DSC é uma plataforma declarativa usada para configuração, implantação e gerenciamento de sistemas. Consiste em três componentes principais:

* [Configurações](configurations.md) são scripts declarativos do PowerShell que definem e configuram instâncias de recursos. Após executar a configuração, a DSC (e os recursos que estão sendo chamados pela configuração) vai simplesmente “realizar”, garantindo que o sistema exista no estado disposto pela configuração. As configurações da DSC também são idempotentes: o Gerenciador de Configurações Local (LCM) continuará garantindo que os computadores sejam configurados no estado declarado pela configuração.
* Recursos são os blocos de construção fundamentais da DSC, escritos para modelar os vários componentes de um subsistema e implementar o fluxo de controle de seus estados mutáveis. Residem dentro de módulos do PowerShell e podem ser escritos para modelar algo tão genérico quanto um arquivo ou um processo do Windows ou tão específico quanto um servidor IIS ou em uma VM em execução no Azure.
* O Gerenciador de Configurações Local (LCM) é o mecanismo pelo qual a DSC facilita a interação entre recursos e configurações. Regularmente, o LCM sonda o sistema usando o fluxo de controle implementado pelos recursos para garantir que o estado disposto por uma Configuração seja mantido. Se o sistema estiver sem estado, o LCM usará mais lógica dentro dos recursos para “realizar”, de acordo com a declaração de Configuração. 

A DSC também inclui uma série de novas palavras-chave, cmdlets e ferramentas de linguagem que permitem a criação de configurações, ajudam a criar recursos de DSC, invocar as configurações e gerenciar o LCM. Muitos desses cmdlets podem ser encontrados no Windows 8.1 como parte do módulo PsDesiredStateConfig (incluindo `Start-DscConfiguration`, `Set-DscLocalConfigurationManager` e `Get-DscResource`). O xDscResourceDesigner (encontrado na [Galeria do PowerShell](https://www.powershellgallery.com/packages/xDSCResourceDesigner/)) é uma coleção de cmdlets que simplificam o desenvolvimento de recursos de DSC.

## Consulte Também
* [Configurações DSC](configurations.md)
* [Recursos de DSC](resources.md)
* [Configurando o Gerenciador de Configurações Local](metaconfig.md)

<!--HONumber=Feb16_HO4-->
