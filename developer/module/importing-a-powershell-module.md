---
title: Importando um módulo do PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 697791b3-2135-4a39-b9d7-8566ed67acf2
caps.latest.revision: 13
ms.openlocfilehash: bb5d036e5658c365a4fafa2cac05c0bba9f87019
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854052"
---
# <a name="importing-a-powershell-module"></a>Importar um módulo do PowerShell

Uma vez o tiver instalado um módulo em um sistema, você provavelmente desejará importar o módulo. Importação é o processo que carrega o módulo na memória ativa, para que um usuário pode acessar esse módulo em sua sessão do PowerShell. No PowerShell 2.0, você pode importar um módulo do PowerShell instalados recentemente com uma chamada para [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet. No PowerShell 3.0, o PowerShell é capaz de importar implicitamente um módulo quando uma das funções ou cmdlets no módulo é chamada por um usuário. Observe que ambas as versões pressupõem que você instale o módulo em um local onde o PowerShell é capaz de localizá-lo; Para obter mais informações, consulte [instalando um módulo do PowerShell](./installing-a-powershell-module.md). Você pode usar um manifesto de módulo para restringir quais partes do seu módulo são exportados, e você pode usar parâmetros da `Import-Module` chamada para restringir quais partes são importados.

## <a name="importing-a-snap-in-powershell-10"></a>Importando um Snap-In (PowerShell 1.0)

Módulos não existia no PowerShell 1.0: em vez disso, você precisava registrar e usar o snap-ins. No entanto, não se recomenda que você use essa tecnologia neste ponto, como módulos são geralmente mais fáceis de instalar e importar. Para obter mais informações, consulte [como criar um Snap-in do PowerShell do Windows](../cmdlet/how-to-create-a-windows-powershell-snap-in.md).

## <a name="importing-a-module-with-import-module-powershell-20"></a>Importando um módulo com Import-Module (PowerShell 2.0)

PowerShell 2.0 usa o adequadamente nomeadas [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) para importar módulos. Quando esse cmdlet é executado, Windows PowerShell procura o módulo especificado nos diretórios especificados no `PSModulePath` variável. Quando o diretório especificado for encontrado, o Windows PowerShell procura por arquivos na seguinte ordem: arquivos de manifesto de módulo (. psd1), arquivos de módulo (. psm1), arquivos de módulo binário (. dll) de script. Para obter mais informações sobre como adicionar diretórios à pesquisa, consulte [modificando o caminho de instalação do PSModulePath](./modifying-the-psmodulepath-installation-path.md). O código a seguir descreve como importar um módulo:

```powershell
Import-Module myModule
```

Supondo que myModule estava localizado no `PSModulePath`, PowerShell carregaria myModule na memória ativa. Se myModule não foi localizado em um `PSModulePath` caminho, você pode ainda informar explicitamente ao PowerShell onde encontrá-lo:

```powershell
Import-Module -Name C:\myRandomDirectory\myModule -Verbose
```

Você também pode usar o parâmetro - verbose para identificar o que está sendo exportado fora do módulo e o que está sendo importado na memória ativa. Importações e exportações restringem o que é exposto ao usuário: a diferença é que está controlando a visibilidade. Essencialmente, exportações são controladas pelo código dentro do módulo. Em contraste, as importações são controladas pelo `Import-Module` chamar. Para obter mais informações, consulte **restringindo os membros que são importados**, abaixo.

## <a name="implicitly-importing-a-module-powershell-30"></a>Implicitamente, importando um módulo (PowerShell 3.0)

Módulos a partir do Windows PowerShell 3.0, são importados automaticamente quando qualquer cmdlet ou função no módulo é usada em um comando. Esse recurso funciona em qualquer módulo em um diretório incluído no valor da **PSModulePath** variável de ambiente. Se você não salvar seu módulo em um caminho válido no entanto, você ainda pode carregá-los usando o explícito [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) opção, descrita acima.

As seguintes ações disparam a importação automática de um módulo, também conhecido como "módulo de carregamento automático."

- Usando um cmdlet em um comando. Por exemplo, digitar `Get-ExecutionPolicy` importa o módulo Microsoft.PowerShell.Security que contém o `Get-ExecutionPolicy` cmdlet.

- Usando o [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) para obter o comando.  Por exemplo, digitar `Get-Command Get-JobTrigger` importa os **PSScheduledJob** módulo que contém o `Get-JobTrigger` cmdlet. Um `Get-Command` é considerado como descoberta de comando que inclui caracteres curinga e não aciona a importação de um módulo.

- Usando o [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet para obter ajuda para um cmdlet. Por exemplo, digitar `Get-Help Get-WinEvent` importa o módulo Microsoft.PowerShell.Diagnostics que contém o `Get-WinEvent` cmdlet.

Para dar suporte a importação automática de módulos, o `Get-Command` cmdlet obtém todos os cmdlets e funções em todos os módulos instalados, mesmo se o módulo não será importado para a sessão. Para obter mais informações, consulte o tópico de ajuda para o [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet.

## <a name="the-importing-process"></a>O processo de importação

Quando um módulo é importado, um estado de sessão nova é criado para o módulo e um [psmoduleinfo](/dotnet/api/System.Management.Automation.PSModuleInfo) objeto é criado na memória. Um estado de sessão é criado para cada módulo que é importado (Isso inclui o módulo raiz e todos os módulos aninhados). Os membros que são exportados do módulo raiz, incluindo todos os membros que foram exportados para o módulo raiz por todos os módulos aninhados, em seguida, são importados para o estado de sessão do chamador.

Os metadados dos membros que são exportados a partir de um módulo tem uma propriedade de ModuleName. Essa propriedade é preenchida com o nome do módulo que exportou-los.

> [!WARNING]
> Se o nome de um membro exportado utiliza um verbo não aprovado ou se o nome do membro usa caracteres restritos, um aviso é exibido quando o [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet é executado.

Por padrão, o [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet não retorna nenhum objeto no pipeline. No entanto, o cmdlet oferece suporte a um `PassThru` parâmetro que pode ser usado para retornar um [psmoduleinfo](/dotnet/api/System.Management.Automation.PSModuleInfo) objeto para cada módulo que é importado. Para enviar a saída para o host, os usuários devem executar o [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet.

## <a name="restricting--the-members-that-are-imported"></a>Restringindo os membros que são importados

Quando um módulo é importado usando o [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet, por padrão, todos os módulos exportados, os membros são importados para a sessão, incluindo todos os comandos exportados para o módulo por um módulo aninhado. Por padrão, variáveis e aliases não são exportadas. Para restringir os membros que são exportados, use uma [manifesto de módulo](./how-to-write-a-powershell-module-manifest.md). Para restringir os membros que são importados, use os seguintes parâmetros da `Import-Module` cmdlet.

- `Function`: Esse parâmetro restringe as funções que são exportadas. (Se você estiver usando um manifesto de módulo, consulte a chave FunctionsToExport.)

- `Cmdlet`: Esse parâmetro restringe os cmdlets que são exportados (se você estiver usando uma consulte de manifesto, módulo a chave CmdletsToExport.)

- `Variable`: Esse parâmetro restringe as variáveis que são exportadas (se você estiver usando uma consulte de manifesto, módulo a chave VariablesToExport.)

- `Alias`: Esse parâmetro restringe os aliases exportados (se você estiver usando uma consulte de manifesto, módulo a chave AliasesToExport.)

## <a name="see-also"></a>Consulte Também

[Escrevendo um módulo do Windows PowerShell](./writing-a-windows-powershell-module.md)
