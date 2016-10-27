
O DSC usa a chave do Registro <b>DSCAutomationHostEnabled </b>em <b>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System</b> para configurar automaticamente o computador na inicialização inicial.
O DSCAutomationHostEnabled dá suporte a três modos:

|  O valor de DSCAutomationHostEnabled  |  Descrição   | 
|---|---| 
0 | Desabilite a configuração do computador na inicialização. |
1 | Habilite a configuração do computador na inicialização. |
2 | Habilite a configuração do computador somente se o DSC estiver no estado atual ou pendente. Este é o valor padrão. |




<!--HONumber=Oct16_HO2-->


