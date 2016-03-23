# Separação de IDs de nó e de configuração

## Visão geral

Para proporcionar uma experiência mais flexível e simplificada ao usar o DSC no modo Pull, adicionamos uma série de recursos nesta versão. Esses recursos destinam-se a permitir que você tenha a flexibilidade de configurar e implantar configurações em vários nós com facilidade, ao mesmo tempo que acompanha as informações de status e relatório de cada nó individualmente. Esses recursos são os seguintes:

* Um nome de configuração que identifica a configuração de um computador. Esse nome pode ser compartilhado por vários nós de destino 
* Uma ID de agente que identifica exclusivamente um único nó
* Uma etapa de registro que ocorre apenas na primeira vez em que um nó de destino se conecta a um servidor de recepção

**Observação:** esses recursos e funcionalidades foram adicionados e não substituem os conceitos e recursos existentes de pull. É possível usar esses novos recursos ou os antigos com o novo servidor de recepção fornecido nesta versão.

## ID de agente

Esse recurso destina-se aos usuários que não desejam instalar e gerenciar identificadores exclusivos para cada nó de destino. Agora, não há mais a necessidade de realizar a escrituração contábil de GUIDs. O DSC gera automaticamente uma ID de agente que ele usa ao se comunicar com o servidor de recepção. Essa ID é usada pelo servidor de recepção para identificar de forma exclusiva todas as informações com determinado nó. Isso também significa que você não precisa configurar cada nó de destino com uma metaconfiguração exclusiva contendo uma ID exclusiva, para que uma única metaconfiguração possa ser usada por vários nós de destino, ao mesmo tempo que ainda retém a identidade exclusiva de cada nó. 

## Nome da configuração

O nome da configuração é um nome amigável que define esse nome da configuração que será aplicado por um nó de destino. As alterações associadas a ele são as seguintes:  

### Nomenclatura amigável

Pode ser qualquer cadeia de caracteres. Ele não precisa estar no formato de um GUID; portanto, uma configuração que configura o SQL Server pode simplesmente ser nomeada “SQL_Server”. Isso torna muito mais fácil a identificação do efeito de determinada configuração.

### Atribuição

A configuração atribuída a um nó de destino é gerenciada centralmente no servidor de recepção. Isso pode ser inicializado definindo a propriedade ConfigrationName na metaconfiguração, mas isso é usado somente durante o registro. Após o registro, o servidor informa ao nó de destino qual configuração será obtida. Para o servidor de recepção local, esse mapeamento entre as configurações e os nós de destino só pode ser feito durante o registro; contudo, na Automação do Azure, essas alterações podem ser feitas facilmente na interface do usuário ou por meio de cmdlets. Para alterar a configuração atribuída a um nó de destino para o servidor de recepção local, é possível executar novamente o registro.

### Configurações múltiplas/parciais

Caso nomes de configuração múltipla sejam atribuídos a um nó de destino, eles serão tratados como configurações parciais. Para que isso funcione, a metaconfiguração no nó de destino deve ser configurada para aceitar as configurações parciais. **Observação:** há suporte para isso apenas no servidor de recepção local. A Automação do Azure não dá suporte a configurações parciais.

## Registro

Como os nomes de configuração não são mais GUIDs (agora são nomes amigáveis), qualquer pessoa pode adivinhá-los. Para atenuar o problema de segurança inerente a isso, adicionamos uma etapa de registro antes que um nó possa iniciar a solicitação de configurações de um servidor. Um nó se registra no servidor de recepção com um segredo compartilhado (que o nó e o servidor já conhecem) e, opcionalmente, com o nome da configuração que será solicitado. Esse segredo compartilhado não precisa ser exclusivo para cada computador. Suposição: o segredo compartilhado é um identificador difícil de detectar, como um GUID. Esse segredo compartilhado é definido pela propriedade **RegistrationKey** na metaconfiguração do nó de destino.

### Metaconfiguração de exemplo

```powershell
[DscLocalConfigurationManager()]
Configuration SampleMetaConfig
{
    Settings
    {
        RefreshMode = "PULL";
        AllowModuleOverwrite = $true;
        RebootNodeIfNeeded = $true;
        ConfigurationModeFrequencyMins = 60;
    }

    ConfigurationRepositoryWeb ConfigurationManager
    {
        ServerURL = “https://PullServerMachine:8080/psdscpullserver.svc”
        RegistrationKey = "140a952b-b9d6-406b-b416-e0f759c9c0e4"
        ConfigurationNames = @(“WebRole”)
    }
}

SampleMetaConfig
```

O valor de RegistrationKey deve ser definido no servidor de recepção. Para fazer isso enquanto configura o servidor de recepção, crie um arquivo de texto com o nome **RegistrationKeys.txt** em um local específico e defina esse local no web.config do servidor de recepção, conforme mostrado abaixo.  

```XML
<add key="ConfigurationPath" value="C:\Program Files\WindowsPowerShell\DscService\Configuration">

<add key="ModulePath" value="C:\Program Files\WindowsPowerShell\DscService\Modules">

<add key="RegistrationKeyPath" value="C:\Program Files\WindowsPowerShell\DscService">
```

Use a versão mais recente do recurso DSC xDSCWebService para implantar por completo um servidor de recepção local para usar com isso. Veja [Configuração de exemplo](https://github.com/grayzu/PSSummitEU2015/blob/master/PullServer/02%20-%20PullServer%20Config.ps1) para concluir a configuração.

**Observação:** não há suporte para esse recurso quando o servidor de recepção é configurado para ser um compartilhamento de arquivos. Somente há suporte para isso no servidor de recepção baseado na Web.<!--HONumber=Mar16_HO2-->
