# SIL (Log de Inventário de Software)

**IMPORTANTE: ** *ao instalar o WMF 5.0 em um Windows Server 2012 R2 Server que já esteja executando o SIL, será necessário executar o cmdlet Start-SilLogging uma vez após a instalação do WMF, pois o processo de instalação interromperá incorretamente o recurso Log de Inventário de Software.*

O Log de Inventário de Software ajuda a reduzir os custos operacionais da obtenção de informações precisas sobre o software Microsoft instalado localmente em um servidor, mas especialmente em vários servidores em um ambiente de TI (presumindo-se que ele foi instalado e está em execução em todo o ambiente de TI). Desde que um esteja configurado, é possível encaminhar esses dados para um servidor de agregação e coletar os dados de log em um único local usando um processo uniforme e automático.

Embora também seja possível registrar em log os dados de inventário de software consultando cada computador diretamente, o Log de Inventário de Software, ao utilizar uma arquitetura de encaminhamento (pela rede) iniciada por cada servidor, pode superar os desafios comuns da descoberta de servidor para muitos cenários de gerenciamento de ativos e de inventário de software. O Log de Inventário de Software usa o SSL para proteger os dados que são encaminhados por HTTPS para um servidor de agregação. Armazenar os dados em um único local torna os dados mais fáceis de analisar, manipular e compartilhar, quando necessário.

Nenhum desses dados são enviados à Microsoft como parte da funcionalidade do recurso. Os dados e a funcionalidade do Log de Inventário de Software destinam-se para utilização exclusiva do proprietário e administradores autorizados do software do servidor.

Para obter mais informações e documentação sobre os cmdlets do Log de Inventário de Software, veja os recursos online do Windows Server 2012 R2 em <http://technet.microsoft.com/library/dn383584.aspx>.


<!--HONumber=Jun16_HO4-->


