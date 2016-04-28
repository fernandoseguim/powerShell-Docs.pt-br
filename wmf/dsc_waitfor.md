# Especificando dependências de nó cruzado

Com os recursos internos WaitFor\* (WaitForAll, WaitForAny e WaitForSome), agora é possível especificar dependências entre computadores durante execuções de configuração, sem a orquestração externa. Cada comportamento ou cada recurso WaitFor\* é descrito abaixo:

* <ctype="x-NOTFOUND" mdpre="**" mdpost="**">WaitForAll</ctype="x-NOTFOUND"> aguarda até que o recurso especificado esteja no estado desejado em <ctype="x-NOTFOUND" mdpre="*" mdpost="*">Todos</ctype="x-NOTFOUND"> os nós de destino definidos na propriedade NodeName.
* <ctype="x-NOTFOUND" mdpre="**" mdpost="**">WaitForAny</ctype="x-NOTFOUND"> aguarda até que o recurso especificado esteja no estado desejado em <ctype="x-NOTFOUND" mdpre="*" mdpost="*">Qualquer</ctype="x-NOTFOUND"> nó de destino definido na propriedade NodeName.
* <ctype="x-NOTFOUND" mdpre="**" mdpost="**">WaitForSome</ctype="x-NOTFOUND"> aguarda até que o recurso especificado esteja no estado desejado no número específico, definido pela propriedade NodeCount, de nós de destino definidos na propriedade NodeName.

Estes recursos fornecem sincronização de nó para nó usando conexões CIM por meio do protocolo WS-Man. Ao usar esses recursos, uma configuração pode aguardar até que o estado de recurso específico de outro computador seja alterado antes de continuar com sua própria configuração. 

Por exemplo, na configuração a seguir, o nó de destino aguarda até que o recurso <ctype="x-NOTFOUND" mdpre="**" mdpost="**">xADDomain</ctype="x-NOTFOUND"> seja concluído no nó <ctype="x-NOTFOUND" mdpre="**" mdpost="**">MyDC</ctype="x-NOTFOUND"> com algumas repetições, antes que o nó de destino possa ingressar no domínio.

```PowerShell
Configuration JoinDomain

{
    Import-DscResource -Module xComputerManagement

    WaitForAll DC
    {
        ResourceName      = '[xADDomain]NewDomain'
        NodeName          = 'MyDC'
        RetryIntervalSec  = 15
        RetryCount        = 30
    }

    xComputer JoinDomain
    {
        Name             = 'MyPC'
        DomainName       = 'Contoso.com'
        Credential       = (get-credential)
        DependsOn        ='[WaitForAll]DC'
    }
}
```
<ctype="x-NOTFOUND" mdpre="**" mdpost="**">Dica:</ctype="x-NOTFOUND"> por padrão, os recursos WaitFor\* fazem uma tentativa e falham; portanto, embora isso não seja necessário, em geral, será conveniente especificar um intervalo de repetição e uma contagem.


<!--HONumber=Mar16_HO3-->


