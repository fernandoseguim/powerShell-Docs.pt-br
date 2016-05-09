
# Método ApplyConfiguration da classe MSFT_DSCLocalConfigurationManager

Usa o Agente de Configuração para aplicar a configuração pendente. 

Se não houver nenhuma configuração pendente, esse método reaplicará a configuração atual.


## Sintaxe
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## Parâmetros
----------

*force* \[in\]  
Se isso for **true**, a configuração atual é reaplicada, mesmo que haja uma configuração pendente.

## Retornar valor
------------

Retorna zero em caso de êxito; caso contrário, retorna um código de erro.

## Comentários

Esse é um método estático.

## Requisitos
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration


## Consulte também


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)

 

 





<!--HONumber=Apr16_HO2-->


