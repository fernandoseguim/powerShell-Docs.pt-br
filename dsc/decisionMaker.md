# Visão Geral da Configuração de Estado Desejado para Tomadores de Decisão #

Este documento descreve os benefícios comerciais do uso da Configuração de Estado Desejado (DSC) do PowerShell. Não é um guia técnico.

## Qual é a Configuração de Estado Desejado? ##

A DSC (Configuração de Estado Desejado) do Windows PowerShell fornece uma plataforma de gerenciamento de configuração integrada no Windows que se baseia em padrões abertos. A DSC é flexível o suficiente para funcionar de maneira confiável e consistente em cada estágio do ciclo de vida de implantação (desenvolvimento, teste, pré-produção, produção), bem como durante a expansão. 

A DSC gira em torno da ideia de "[configurações](https://msdn.microsoft.com/en-us/powershell/dsc/configurations)", que são documentos fáceis de ler que descrevem um ambiente composto por computadores ("nós") com características específicas. Essas características podem ser tão simples quanto assegurar que um recurso específico do Windows esteja habilitado ou tão complexas quanto a implantação do SharePoint. 

A DSC também tem monitoramento e emissão de relatórios internos. Se um sistema não for mais compatível, a DSC poderá gerar um alerta e agir para corrigir o sistema. 

## Benefícios do Uso da Configuração de Estado Desejado ##

As configurações são concebidas para serem fáceis de ler, armazenar e atualizar. As configurações simplesmente declaram o estado em que os dispositivos de destino devem estar, em vez de escrever instruções de como usá-los nesse estado. Assim, fica mais barato aprender, adotar, implementar e manter a configuração por meio da DSC. 

A criação de configurações significa que etapas complexas de implantação são capturadas como uma "única fonte da verdade" em um único local. Isso diminui a probabilidade de erros em implantações repetidas de um conjunto específico de máquinas. Por sua vez, as implantações se tornam mais rápidas e confiáveis. Isso permite um retorno rápido em implantações complexas.

As configurações também podem ser compartilhadas por meio da [Galeria do PowerShell](https://powershellgallery.com). Isso significa que cenários comuns e práticas recomendadas talvez já existam para o trabalho que é necessário.


## Configuração de Estado Desejado e DevOps ##

[DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) é uma combinação de pessoas, tecnologias e culturas que permite uma implantação e uma iteração rápidas. A DSC foi concebida pensando em DevOps. Ter uma única configuração definindo um ambiente significa que os desenvolvedores podem codificar seus requisitos em uma configuração, verificar essa configuração no controle do código-fonte e as equipes de operações podem implantar facilmente o código sem precisar passar por processos manuais propensos a erro. 

As configurações também são [orientadas a dados](https://msdn.microsoft.com/en-us/powershell/dsc/configdata), o que ajuda as equipes de operações a identificar e alterar os ambientes sem a intervenção do desenvolvedor. 

## Configuração de Estado Desejado no Local e Externamente ##

A DSC pode ser usada para gerenciar implantações locais e externas. Para soluções locais, a Configuração de Estado Desejado tem um [servidor pull](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver) que pode ser utilizado para centralizar o gerenciamento de máquinas e relatar seu status. Para soluções de nuvem, a Configuração de Estado Desejado é útil onde quer que o Windows seja utilizável. Também há ofertas específicas do Azure integradas na Configuração de Estado Desejado, como a [Automação do Azure](https://azure.microsoft.com/en-us/documentation/services/automation/), que centraliza os relatórios de Configuração de Estado Desejado. 

## DSC e Compatibilidade ##

Embora a DSC tenha sido introduzida no Windows Server 2012 R2, está disponível para sistemas operacionais de nível inferior por meio do pacote do Windows Management Framework (WMF). Mais informações sobre o WMF podem ser encontradas na [home page do PowerShell](https://msdn.microsoft.com/en-us/powershell/). 

A DSC também pode ser usada para gerenciar o Linux. Para obter mais informações, consulte [Introdução à DSC para Linux](https://msdn.microsoft.com/en-us/powershell/dsc/lnxgettingstarted)

<!--HONumber=Mar16_HO1-->


