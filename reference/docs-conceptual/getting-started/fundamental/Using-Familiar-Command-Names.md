---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Usando nomes familiares de comando
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: 37fc6dfad5a2f1363254744141dcab1e13aa5066
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952674"
---
# <a name="using-familiar-command-names"></a>Usando nomes familiares de comando
Usando um mecanismo chamado *aliasing*, o Windows PowerShell permite que os usuários consultem comandos por nomes alternativos. Usar alias permite que usuários com experiência em outros shells reutilizem nomes de comando comuns que já conhecem para executar operações semelhantes no Windows PowerShell. Embora não abordemos aliases do Windows PowerShell em detalhes, você ainda pode usá-los ao começar a usar o Windows PowerShell.

Usar alias associa um nome de comando digitado a outro comando. Por exemplo, o Windows PowerShell tem uma função interna denominada **Clear-Host** que limpa a janela de saída. Se você digitar o comando **cls** ou **clear** em um prompt de comando, o Windows PowerShell interpretará que se trata de um alias para a função **Clear-Host** e executará a função **Clear-Host**.

Esse recurso ajuda os usuários a aprender a usar o Windows PowerShell. Primeiro, a maioria dos usuários do Cmd.exe e do UNIX têm um grande repertório de comandos que os usuários já conhecer por nome e, embora os equivalentes do Windows PowerShell possam não produzir resultados idênticos, eles são parecidos o suficiente para que os usuários possam usá-los para trabalhar sem precisar primeiro memorizar os nomes do Windows PowerShell. Em segundo lugar, a principal fonte de frustração em aprender um novo shell quando o usuário já está familiarizado com outro são os erros causados pela "memória finger". Se tiver usado Cmd.exe por anos, quando tiver uma tela cheia de saída e desejar limpá-la, você digitará reflexivamente o comando **cls** e pressionaria a tecla Enter. Sem o alias para a função **Clear-Host** no Windows PowerShell, você simplesmente receberia a mensagem de erro "**'cls' não é reconhecido como um cmdlet, função, programa operável ou arquivo de script.**" e ficar sem ideia de como limpar a saída.

Veja a seguir uma lista resumida dos comandos Cmd.exe e UNIX comuns que podem ser usados no Windows PowerShell:

|||||
|-|-|-|-|
|cat|dir|montagem|rm|
|cd|echo|move|rmdir|
|chdir|erase|popd|sleep|
|clear|h|ps|sort|
|cls|history|pushd|tee|
|copy|kill|pwd|tipo|
|del|lp|r|write|
|diff|ls|ren||

Se estiver usando um desses comandos reflexivamente e quiser saber o nome real do comando nativo do Windows PowerShell, você poderá usar o comando **Get-Alias**:

```
PS> Get-Alias cls

CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

Para tornar os exemplos mais legível, o Guia do Usuário do Windows PowerShell normalmente evita o uso de aliases. No entanto, saber mais sobre aliases logo no início ainda poderá ser útil se você estiver trabalhando com trechos de código arbitrários do Windows PowerShell de outra fonte ou se desejar definir seus próprios aliases. No restante desta seção, discutiremos os aliases padrão e como definir seus próprios aliases.

### <a name="interpreting-standard-aliases"></a>Interpretando aliases padrão
Ao contrário dos aliases descritos acima, que foram criados para compatibilidade de nome com outras interfaces, os aliases criados no Windows PowerShell geralmente são criados para fins de concisão. Esses nomes mais curtos podem ser digitados rapidamente, mas serão impossíveis de ler se você não souber ao que eles se referem.

O Windows PowerShell tenta chegar a um equilíbrio entre a clareza e a concisão, fornecendo um conjunto de aliases padrão que se baseiam nos nomes de forma abreviada de substantivos e verbos comuns. Isso proporciona que um conjunto principal de aliases para cmdlets comuns que podem ser lidos quando você souber os nomes de forma abreviada. Por exemplo, em aliases padrão o verbo **Get (Obter)** é abreviado para **g**, o verbo **Set (Definir)** é abreviado para **s**, o substantivo **Item** é abreviado como **i**, o substantivo **Location (Local)** é abreviado para **l** e o substantivo Command (Comando) é abreviado como **cm**.

Veja aqui um breve exemplo para ilustrar como isso funciona. O alias padrão para Get-Item vem da combinação de **g** para Get e **i** para Item: **gi**. O alias padrão para Set-Item vem da combinação de **s** para Set e **i** para Item: **si**. O alias padrão para Get-Location vem da combinação de **g** para Get e **l** para Location: **gl**. O alias padrão para Set-Location vem da combinação de **s** para Set e **l** para Location: **sl**. O alias padrão para Get-Command vem da combinação de **g** para Get e **cm** para Command: **gcm**. Não há cmdlet Set-Command, porém, se houvesse, poderíamos deduzir que o alias padrão viria de **s** para Set e **cm** para Command: **scm**. Além disso, pessoas familiarizadas com o alias do Windows PowerShell que encontrassem **scm** seriam capazes de deduzir que o alias se refere a Set-Command.

### <a name="creating-new-aliases"></a>Criando um novo alias
Você pode criar seus próprios aliases usando o cmdlet Set-Alias. Por exemplo, as seguintes instruções criam os aliases de cmdlet padrão discutidos em Interpretando aliases padrão:

```
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

Internamente, o Windows PowerShell usa comandos como estes durante a inicialização, mas esses aliases não são mutáveis. Se você tentar executar um desses comandos, receberá um erro explicando que o alias não pode ser modificado. Por exemplo:

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```