---
ms.date: 08/23/2018
keywords: powershell, cmdlet
title: Noções básicas dos pipelines do PowerShell
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: 05ab98b7261f4d41ade1788a924193eccda6318c
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623952"
---
# <a name="understanding-pipelines"></a>Noções básicas dos pipelines

Pipelines atuam como uma série de segmentos conectados do pipe. Itens que se movem pelo pipeline passam por cada segmento. Para criar um pipeline no PowerShell, você conectar comandos com o operador de barra vertical "|". A saída de cada comando é usada como entrada para o próximo comando.

A notação usada para pipelines é semelhante à notação usada em outros shells. À primeira vista, talvez seja aparente como os pipelines são diferentes no PowerShell. Embora você veja o texto na tela, o PowerShell redireciona objetos, e não o texto, entre comandos.

## <a name="the-powershell-pipeline"></a>O pipeline do PowerShell

Pipelines são possivelmente o conceito mais valioso usado nas interfaces de linha de comando. Quando usada corretamente, pipelines reduzem o esforço do uso de comandos complexos facilitam a visualização do fluxo de trabalho dos comandos. Cada comando em um pipeline (chamado de um elemento de pipeline) passa sua saída para o próximo comando do pipeline, item por item. Os comandos não precisam lidar com mais de um item por vez. O resultado é o consumo de recursos reduzido e a capacidade de começar obtendo saída imediatamente.

Por exemplo, se você usar o cmdlet `Out-Host` para forçar uma exibição de página a página da saída de outro comando, a saída parecerá ser apenas o texto normal exibido na tela, dividida em páginas:

```powershell
Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging
```

```Output
    Directory: C:\WINDOWS\system32

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        4/12/2018   2:15 AM                0409
d-----        5/13/2018  11:31 PM                1033
d-----        4/11/2018   4:38 PM                AdvancedInstallers
d-----        5/13/2018  11:13 PM                af-ZA
d-----        5/13/2018  11:13 PM                am-et
d-----        4/11/2018   4:38 PM                AppLocker
d-----        5/13/2018  11:31 PM                appmgmt
d-----        7/11/2018   2:05 AM                appraiser
d---s-        4/12/2018   2:20 AM                AppV
d-----        5/13/2018  11:10 PM                ar-SA
d-----        5/13/2018  11:13 PM                as-IN
d-----        8/14/2018   9:03 PM                az-Latn-AZ
d-----        5/13/2018  11:13 PM                be-BY
d-----        5/13/2018  11:10 PM                BestPractices
d-----        5/13/2018  11:10 PM                bg-BG
d-----        5/13/2018  11:13 PM                bn-BD
d-----        5/13/2018  11:13 PM                bn-IN
d-----        8/14/2018   9:03 PM                Boot
d-----        8/14/2018   9:03 PM                bs-Latn-BA
d-----        4/11/2018   4:38 PM                Bthprops
d-----        4/12/2018   2:19 AM                ca-ES
d-----        8/14/2018   9:03 PM                ca-ES-valencia
d-----        5/13/2018  10:46 PM                CatRoot
d-----        8/23/2018   5:07 PM                catroot2
<SPACE> next page; <CR> next line; Q quit
...
```

A paginação também reduz a utilização da CPU, pois o processamento muda para o cmdlet `Out-Host` quando há uma página completa pronta para exibição. Os cmdlets que a precedem no pipeline pausam a execução até que a próxima página de saída esteja disponível.

Veja a diferença entre o Gerenciador de Tarefas do Windows para monitorar o uso de CPU e da memória e o PowerShell. Execute o seguinte comando: `Get-ChildItem C:\Windows -Recurse`. Compare o uso de CPU e de memória deste comando: `Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`.

> [!NOTE]
> O parâmetro **Paging** não tem suporte de todos os hosts do PowerShell. Por exemplo, ao tentar usar o parâmetro **Paging** no ISE do PowerShell, você verá o seguinte erro:
>
> ```Output
> out-lineoutput : The method or operation is not implemented.
> At line:1 char:1
> + Get-ChildItem C:\Windows -Recurse | Out-Host -Paging
> + ~~~~~~~~~~~~~~~~~~~~~~~~~~~
>     + CategoryInfo          : NotSpecified: (:) [out-lineoutput], NotImplementedException
>     + FullyQualifiedErrorId : System.NotImplementedException,Microsoft.PowerShell.Commands.OutLineOutputCommand
> ```

## <a name="objects-in-the-pipeline"></a>Objetos no pipeline

Quando você executa um cmdlet no PowerShell, vê a saída de texto porque é necessário representar objetos como texto em uma janela de console. A saída de texto não pode exibir todas as propriedades do objeto mostrado.

Por exemplo, considere o cmdlet `Get-Location`. Se você executar `Get-Location` enquanto seu local atual for a raiz da unidade C, você verá a seguinte saída:

```
PS> Get-Location

Path
----
C:\
```

A saída de texto é um resumo das informações, não uma representação completa do objeto retornado por `Get-Location`. O título na saída é adicionado pelo processo que formata os dados para exibição na tela.

Quando você direciona a saída para o cmdlet `Get-Member`, obtém informações sobre o objeto retornado por `Get-Location`.

```powershell
Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

`Get-Location` retorna um objeto **PathInfo** que contém o caminho atual e outras informações.
