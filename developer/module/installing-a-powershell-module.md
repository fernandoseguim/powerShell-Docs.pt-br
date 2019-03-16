---
title: Instalando um módulo do PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: 7c2bfca50de4645676eafc01bbf23d9797e8b758
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059772"
---
# <a name="installing-a-powershell-module"></a>Instalar um módulo do PowerShell

Depois de criar o módulo do PowerShell, você provavelmente desejará instalar o módulo em um sistema, para que você ou outras pessoas podem usá-lo. Em termos gerais, isso simplesmente consiste em copiar os arquivos de módulo (ou seja, a. psm1, ou o assembly binário, o manifesto de módulo e quaisquer outros arquivos associados) em um diretório no computador em questão. Para um projeto muito pequeno, isso pode ser tão simple quanto copiar e colar os arquivos com o Windows Explorer em um único computador remoto. No entanto, para grandes soluções você poderá usar um processo de instalação mais sofisticado. Independentemente de como você pode obter seu módulo no sistema, o PowerShell pode usar várias técnicas que permitirá que os usuários localizar e usar seus módulos. (Para obter mais informações, consulte [importação de um módulo do PowerShell](./importing-a-powershell-module.md).) Portanto, o principal problema para a instalação é garantir que o PowerShell será capaz de encontrar seu módulo.

Este tópico contém as seguintes seções:

- Regras para instalar os módulos

- Onde instalar os módulos

- Instalando várias versões de um módulo

- Tratamento de conflitos de nome de comando

## <a name="rules-for-installing-modules"></a>Regras para instalar os módulos

As informações a seguir se refere a todos os módulos, incluindo os módulos que você cria para seu próprio uso, os módulos que você obteve de outras partes e módulos que você distribuir para outras pessoas.

### <a name="install-modules-in-psmodulepath"></a>Instalar os módulos no PSModulePath

Sempre que possível, instale todos os módulos em um caminho que está listado na **PSModulePath** variável de ambiente ou adicione o caminho do módulo para o **PSModulePath** valor de variável de ambiente.

O **PSModulePath** variável de ambiente ($Env: PSModulePath) contém os locais dos módulos do Windows PowerShell. Cmdlets contam com o valor dessa variável de ambiente para localizar os módulos.

Por padrão, o **PSModulePath** valor de variável de ambiente contém o sistema a seguir e os diretórios de módulo de usuário, mas você pode adicionar a e edite o valor.

- $PSHome\Modules (% Windir%\System32\WindowsPowerShell\v1.0\Modules)

  > [!WARNING]
  > Esse local é reservado para os módulos que acompanham o Windows. Não instale os módulos neste local.

- $Home\Documents\WindowsPowerShell\Modules (%UserProfile%\Documents\WindowsPowerShell\Modules)

- $Env: ProgramFiles\WindowsPowerShell\Modules (% ProgramFiles%\WindowsPowerShell\Modules)

  Para obter o valor da **PSModulePath** variável de ambiente, use um dos comandos a seguir.

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  Para adicionar um caminho de módulo como valor da **PSModulePath** variável de ambiente valor, use o seguinte formato de comando. Esse formato usa o **SetEnvironmentVariable** método o **System. Environment** classe para fazer uma alteração de sessão independente para o **PSModulePath** ambiente variável.

  ```powershell

  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > Depois de adicionar o caminho para **PSModulePath**, você deve transmitir uma mensagem sobre a alteração de ambiente. Transmitindo a alteração permite que outros aplicativos, como o shell acompanhar a alteração. Para transmitir a alteração, que seu código de instalação de produto envie um **WM_SETTINGCHANGE** da mensagem com `lParam` definido como a cadeia de caracteres "Ambiente". Certifique-se de enviar a mensagem depois que seu código de instalação do módulo atualizou **PSModulePath**.

### <a name="use-the-correct-module-directory-name"></a>Use o nome de diretório do módulo correto

Um "bem-formado" é um módulo que é armazenado em um diretório que tem o mesmo nome que o nome base de pelo menos um arquivo no diretório do módulo. Se um módulo não está bem formado, o Windows PowerShell não reconhecê-lo como um módulo.

O "nome base" de um arquivo é o nome sem a extensão de nome de arquivo. Em um módulo bem formado, o nome do diretório que contém os arquivos de módulo deve corresponder ao nome de base pelo menos um arquivo no módulo.

Por exemplo, no módulo exemplo Fabrikam, o diretório que contém os arquivos de módulo é denominado "Fabrikam" e pelo menos um arquivo com o nome de base "Fabrikam". Nesse caso, Fabrikam.psd1 e Fabrikam.dll tem o nome de base "Fabrikam".

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a>Efeito da instalação incorreta

Se o módulo não está bem formado e sua localização não está incluída no valor de **PSModulePath** variável de ambiente, recursos de descoberta básico do Windows PowerShell, como a seguir, não funcionam.

- O recurso de carregamento automático do módulo não é possível importar o módulo automaticamente.

- O `ListAvailable` parâmetro do [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet não é possível localizar o módulo.

- O [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet não é possível localizar o módulo. Para importar o módulo, você deve fornecer o caminho completo para o arquivo de módulo raiz ou o arquivo de manifesto de módulo.

  Recursos adicionais, como a seguir, não funcionam, a menos que o módulo é importado para a sessão. Em módulos bem-formados a **PSModulePath** variável de ambiente, esses recursos funcionam, mesmo quando o módulo não será importado para a sessão.

- O [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet não é possível localizar os comandos no módulo.

- O [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets não podem atualizar ou salvar ajuda para o módulo.

- O [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet não pode localizar e exibir os comandos no módulo.

  Os comandos no módulo estão ausentes do `Show-Command` janela no Windows PowerShell Integrated Scripting ISE (ambiente).

## <a name="where-to-install-modules"></a>Onde instalar os módulos

Esta seção explica onde no sistema de arquivos para instalar os módulos do Windows PowerShell. O local depende de como o módulo é usado.

### <a name="installing-modules-for-a-specific-user"></a>Instalar os módulos para um usuário específico

Se você cria seu próprio módulo ou obter um módulo de terceiros, como um site da comunidade do Windows PowerShell, e você deseja que o módulo estejam disponíveis para sua conta de usuário, instale o módulo em seu diretório de módulos específicos do usuário.

```
$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

O diretório de módulos específicos do usuário é adicionado ao valor de **PSModulePath** variável de ambiente, por padrão.

### <a name="installing-modules-for-all-users-in-program-files"></a>Instalar os módulos para todos os usuários em arquivos de programa

Se você quiser um módulo estejam disponíveis para todas as contas de usuário no computador, instale o módulo no local dos arquivos de programa.

```
$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

> [!NOTE]
> Por padrão no Windows PowerShell 4.0 e posterior, o local dos arquivos de programa é adicionado ao valor da variável de ambiente PSModulePath. Para versões anteriores do Windows PowerShell, você pode manualmente os arquivos de programa local ((%ProgramFiles%\WindowsPowerShell\Modules) de criar e adicionar este caminho à variável de ambiente PSModulePath, conforme descrito acima.

### <a name="installing-modules-in-a-product-directory"></a>Instalar os módulos em um diretório de produto

Se você estiver distribuindo o módulo a outras partes, use o local dos arquivos de programa padrão descrito acima, ou crie seu próprio subdiretório específico da empresa ou produto específico do diretório % ProgramFiles %.

Por exemplo, as tecnologias da Fabrikam, uma empresa fictícia, está enviando um módulo do Windows PowerShell para seu produto Gerenciador da Fabrikam. Seu instalador de módulos cria um subdiretório de módulos no subdiretório de produto Gerenciador da Fabrikam.

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

Para habilitar os recursos de descoberta do módulo Windows PowerShell encontrar o módulo de Fabrikam, o instalador do módulo Fabrikam adiciona o local de módulo para o valor da **PSModulePath** variável de ambiente.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += "C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a>Instalar os módulos no diretório de arquivos comuns

Se um módulo é usado por vários componentes de um produto ou por várias versões de um produto, instale o módulo em um subdiretório específico do módulo do subdiretório Files\Modules %ProgramFiles%\Common.

No exemplo a seguir, o módulo da Fabrikam é instalado em um subdiretório de Fabrikam do subdiretório Files\Modules %ProgramFiles%\Common. Observe que cada módulo reside em seu próprio subdiretório no subdiretório de módulos.

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)

```

Em seguida, o instalador garante que o valor de **PSModulePath** variável de ambiente inclui o caminho do subdiretório comum de módulos de arquivos.

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a>Instalando várias versões de um módulo

Para instalar várias versões do mesmo módulo, use o procedimento a seguir.

1. Crie um diretório para cada versão do módulo. Inclua o número de versão no nome do diretório.

2. Crie um manifesto de módulo para cada versão do módulo. O valor da **ModuleVersion** da chave no manifesto, insira o número de versão do módulo. Salve o arquivo de manifesto (. psd1) no diretório específico da versão do módulo.

3. Adicionar o caminho de pasta do módulo raiz para o valor de **PSModulePath** variável de ambiente, conforme mostrado nos exemplos a seguir.

Para importar uma versão específica do módulo, o usuário final pode usar o `MinimumVersion` ou `RequiredVersion` parâmetros da [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.

Por exemplo, se o módulo de Fabrikam está disponível nas versões 8.0 e 9.0, a estrutura de diretório do módulo Fabrikam pode se parecer com o seguinte.

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

O instalador adiciona ambos os caminhos de módulo para o **PSModulePath** valor de variável de ambiente.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

Quando essas etapas forem concluídas, o **ListAvailable** parâmetro do [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet obtém a ambos os módulos da Fabrikam. Para importar um módulo específico, use o `MinimumVersion` ou `RequiredVersion` parâmetros da [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.

Se ambos os módulos são importados para a mesma sessão, e os módulos contêm cmdlets com os mesmos nomes, os cmdlets que são importados pela última vez são eficazes na sessão.

## <a name="handling-command-name-conflicts"></a>Tratamento de conflitos de nome de comando

Conflitos de nome de comando podem ocorrer quando os comandos que exporta um módulo tem o mesmo nome de comandos na sessão do usuário.

Quando uma sessão contém dois comandos que têm o mesmo nome, o Windows PowerShell executa o tipo de comando que tem precedência. Quando uma sessão contém dois comandos que têm o mesmo nome e o mesmo tipo, o Windows PowerShell executa o comando que foi adicionado à sessão mais recentemente. Para executar um comando que não é executado por padrão, os usuários podem qualificar o nome de comando com o nome do módulo.

Por exemplo, se a sessão contém um `Get-Date` função e o `Get-Date` , Windows PowerShell executa a função por padrão. Para executar o cmdlet, preceda o comando com o nome do módulo, como:

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

Para evitar conflitos de nome, os autores de módulo podem usar o **DefaultCommandPrefix** chave no manifesto do módulo para especificar um prefixo ao substantivo para todos os comandos exportados do módulo.

Os usuários podem usar o **prefixo** parâmetro do `Import-Module` cmdlet para usar um prefixo alternativo. O valor da **prefixar** parâmetro tem precedência sobre o valor da **DefaultCommandPrefix** chave.

## <a name="see-also"></a>Consulte Também

[about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[Escrevendo um módulo do Windows PowerShell](./writing-a-windows-powershell-module.md)
