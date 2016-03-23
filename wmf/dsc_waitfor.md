# Especificando dependências de nó cruzado

Com os recursos internos WaitFor\* (WaitForAll, WaitForAny e WaitForSome), agora é possível especificar dependências entre computadores durante execuções de configuração, sem a orquestração externa. Cada comportamento ou cada recurso WaitFor\* é descrito abaixo:

* **WaitForAll** Aguarda até que o recurso especificado esteja no estado desejado em *Todos* os nós de destino definidos na propriedade NodeName.
* **WaitForAny** Aguarda até que o recurso especificado esteja no estado desejado em *Qualquer* nó de destino definido na propriedade NodeName.
* **WaitForSome** Aguarda até que o recurso especificado esteja no estado desejado no número específico, definido pela propriedade NodeCount, de nós de destino definidos na propriedade NodeName.

Estes recursos fornecem sincronização de nó para nó usando conexões CIM por meio do protocolo WS-Man. Ao usar esses recursos, uma configuração pode aguardar até que o estado de recurso específico de outro computador seja alterado antes de continuar com sua própria configuração. 

Por exemplo, na configuração a seguir, o nó de destino aguarda até que o recurso **xADDomain** seja concluído no nó **MyDC** com algumas repetições, antes que o nó de destino possa ingressar no domínio.

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
**Dica:** por padrão, os recursos WaitFor\* fazem uma tentativa e falham; portanto, embora isso não seja necessário, em geral, será conveniente especificar um intervalo de repetição e uma contagem.
<!--HONumber=Mar16_HO2-->
