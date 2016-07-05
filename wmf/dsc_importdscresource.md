# Palavra-chave de Import-DscResource dá suporte ao parâmetro -ModuleVersion

Adicionamos um novo parâmetro à palavra-chave dinâmica `Import-DscResource`, disponível ao criar configurações DSC. Os autores da configuração agora podem especificar exatamente de qual versão do módulo os recursos DSC deverão ser carregados. A nova sintaxe da palavra-chave é:

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* **Nome**: nomes de um ou mais recursos a ser importados.
* **ModuleName**: nomes de módulo ou objetos ModuleSpecification de um ou mais módulos a ser importados.
* **ModuleVersion**: versão de módulo a ser importada. Se for usado, ModuleName deverá representar apenas um módulo por nome. 

No ISE do Windows PowerShell, ele é exibido com o IntelliSense:

![](images/Import-DscResource-Modversion.jpg)

**Observação**: o parâmetro `–ModuleVersion` só pode ser usado em combinação com o parâmetro `–ModuleName`. Ele não pode ser usado com nomes de recurso que usam apenas o parâmetro `–Name`.

Antes disso, a única maneira de especificar a versão do módulo ao carregar recursos DSC era usar o objeto de especificação do Módulo, por exemplo: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`



<!--HONumber=Jun16_HO4-->


