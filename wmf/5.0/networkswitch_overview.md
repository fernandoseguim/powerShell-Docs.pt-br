# Gerenciamento de comutador de rede com o PowerShell

O cmdlet **Get-NetworkSwitchEthernetPort** agora retorna as seguintes informações adicionais com instâncias:
-   IPAddress – o endereço IP associado à porta
-   PortMode – o modo da porta: acesso, roteiro ou tronco
-   AccessVLAN – a ID da VLAN associada a essa porta no modo de acesso
-   TrunkedVLANList – uma lista de IDs de VLANs associadas a essa porta no modo de tronco

## Gerenciamento fundamental de comutador de rede com o Windows PowerShell
Os cmdlets Network Switch, introduzidos na primeira Preview do WMF 5.0, permitem aplicar a configuração do comutador, da VLAN (LAN virtual) e a configuração básica de porta do comutador de rede da Camada 2 a comutadores de rede certificados com o logotipo do Windows Server 2012 R2. A Microsoft mantém seu compromisso em dar suporte à visão da DAL (Camada de [Abstração de Datacenter](http://technet.microsoft.com/en-us/cloud/dal.aspx)) e em mostrar o valor para nossos clientes e parceiros neste espaço. Com esses cmdlets, é possível executar:

-   Configuração do comutador global, como:
    -   Definir nome do host
    -   Definir faixa do comutador
    -   Persistir a configuração
    -   Habilitar ou desabilitar um recurso

-   Configuração de VLAN:
    -   Criar ou remover uma VLAN
    -   Habilitar ou desabilitar uma VLAN
    -   Enumerar uma VLAN
    -   Definir o nome amigável de uma VLAN

-   Configuração de porta da Camada 2:
    -   Enumerar portas
    -   Habilitar ou desabilitar portas
    -   Definir modos e propriedades de porta
    -   Adicionar ou associar a VLAN ao Tronco ou Acesso na porta

Comece a explorar procurando todos os cmdlets NetworkSwitch!

```powershell
PS> Get-Command *-NetworkSwitch*

| CommandType | Name                                      | Source        |
|-------------|-------------------------------------------|---------------|
|             |                                           |               |
| Function    | Disable-NetworkSwitchEthernetPort         | NetworkSwitch |
| Function    | Disable-NetworkSwitchFeature              | NetworkSwitch |
| Function    | Disable-NetworkSwitchVlan                 | NetworkSwitch |
| Function    | Enable-NetworkSwitchEthernetPort          | NetworkSwitch |
| Function    | Enable-NetworkSwitchFeature               | NetworkSwitch |
| Function    | Enable-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Get-NetworkSwitchEthernetPort             | NetworkSwitch |
| Function    | Get-NetworkSwitchFeature                  | NetworkSwitch |
| Function    | Get-NetworkSwitchGlobalData               | NetworkSwitch |
| Function    | Get-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | New-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | Remove-NetworkSwitchEthernetPortIPAddress | NetworkSwitch |
| Function    | Remove-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Restore-NetworkSwitchConfiguration        | NetworkSwitch |
| Function    | Save-NetworkSwitchConfiguration           | NetworkSwitch |
| Function    | Set-NetworkSwitchEthernetPortIPAddress    | NetworkSwitch |
| Function    | Set-NetworkSwitchPortMode                 | NetworkSwitch |
| Function    | Set-NetworkSwitchPortProperty             | NetworkSwitch |
| Function    | Set-NetworkSwitchVlanProperty             | NetworkSwitch |
```

Mais informações estão disponíveis na postagem no blog de Jeffrey Snover sobre o comunicado da Preview do WMF 5.0: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx>


<!--HONumber=Jun16_HO4-->


