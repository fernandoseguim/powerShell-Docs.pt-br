---
title: Obtendo informações de ajuda detalhadas
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
---
# Obtendo informações de ajuda detalhadas
O Windows PowerShell inclui tópicos detalhados que explicam os conceitos do Windows PowerShell e a linguagem do Windows PowerShell. Também há tópicos da Ajuda para cada cmdlet e tópicos de provedor e de Ajuda para muitas funções e scripts.

Você pode exibir esses tópicos da Ajuda no prompt de comando ou exibir as versões mais atualizadas dos seguintes tópicos na Biblioteca do Microsoft TechNet. Muitos programas que hospedam o Windows PowerShell, como o Ambiente de Script Integrado do Windows PowerShell, fornecem recursos adicionais de Ajuda, como a Ajuda contextual e o arquivo de Ajuda compilado (.chm).

## Obtendo Ajuda para os cmdlets
Para obter Ajuda para cmdlets do Windows PowerShell, use o cmdlet [Get-Help [m2]](assetId:///2d7fe1b4-0025-4580-a911-d81922dd6cd2). Por exemplo, para obter Ajuda para o cmdlet [Get-ChildItem [m2]](assetId:///4b270d63-c995-45b8-b5b4-3f8887efbfcc), digite:

```
get-help get-childitem
```

ou

```
get-childitem -?
```

Você pode até mesmo obter ajuda para o cmdlet Get-Help. Por exemplo:

```
get-help get-help
```

Para obter uma lista de todos os tópicos de Ajuda de cmdlet na sua sessão, digite:

```
get-help -category cmdlet
```

Para exibir uma página de cada tópico da Ajuda por vez, use a função **help** ou seu alias **man**. Por exemplo, para exibir a Ajuda para o cmdlet Get-ChildItem, digite

```
man get-childitem
```

ou

```
help get-childitem
```

Para exibir informações detalhadas sobre um cmdlet, função ou script, incluindo descrições de seus parâmetros e exemplos de uso, use o parâmetro *Detailed* do cmdlet Get-Help. Por exemplo, para obter informações detalhadas sobre o cmdlet Get-ChildItem, digite:

```
get-help get-childitem -detailed
```

Para exibir todo o conteúdo do tópico da Ajuda, use o parâmetro *Full* do cmdlet Get-Help. Por exemplo, para exibir todo o conteúdo do tópico de Ajuda para o cmdlet Get-ChildItem, digite:

```
get-help get-childitem -full
```

Para obter Ajuda detalhada sobre os parâmetros de um cmdlet, use o parâmetro *Parameter* do cmdlet Get-Help. Por exemplo, para obter Ajuda detalhada para todos os parâmetros do cmdlet Get-ChildItem, digite:

```
get-help get-childitem -parameter *
```

Para exibir apenas os exemplos em um tópico da Ajuda, use o parâmetro *Example* da Ajuda do Get-Help. Por exemplo, para exibir apenas os exemplos do tópico de Ajuda para o cmdlet Get-ChildItem, digite:

```
get-help get-childitem -examples
```

Para obter informações sobre como escrever tópicos da Ajuda para os cmdlets que você criar, consulte o tópico "Como criar Ajuda para cmdlets" no MSDN.

## Obtendo Ajuda conceitual
O cmdlet Get-Help exibe também informações sobre tópicos conceituais no Windows PowerShell, incluindo tópicos sobre a linguagem do Windows PowerShell. Tópicos de Ajuda conceituais começam com o prefixo "about_", como about_line_editing. (O nome do tópico conceitual deve ser inserido em inglês, mesmo em versões do Windows PowerShell em idiomas diferentes do inglês.)

Para exibir uma lista de tópicos conceituais, digite:

```
get-help about_*
```

Para exibir um tópico de Ajuda específico, digite o nome do tópico, como por exemplo:

```
get-help about_command_syntax
```

Os parâmetros de Get-Help, como *Detailed*, *Parameter* e *Examples* não têm efeito sobre a exibição dos tópicos de Ajuda conceitual.

## Obtendo Ajuda para provedores
O cmdlet Get-Help exibe informações sobre provedores do Windows PowerShell. Para obter Ajuda sobre um provedor, digite "Get-Help" seguido do nome do provedor. Por exemplo, para obter Ajuda para o provedor de Registro, digite:

```
get-help registry
```

Para obter uma lista de todos os tópicos de Ajuda de provedor na sua sessão, digite

```
get-help -category provider
```

Os parâmetros de Get-Help, como *Detailed*, *Parameter* e *Examples* não têm efeito sobre a exibição dos tópicos de Ajuda de provedor.

## Obtendo Ajuda para scripts e funções
Muitos scripts e funções no Windows PowerShell têm tópicos da Ajuda. Use o cmdlet Get-Help para exibir tópicos da Ajuda para scripts e funções.

Para exibir a Ajuda para uma função, digite "get-help" seguido pelo nome da função. Por exemplo, para obter Ajuda para a função Disable-PSRemoting, digite:

```
get-help disable-psremoting
```

Para exibir a Ajuda para um script, digite o caminho totalmente qualificado para o arquivo de script. Se o script estiver em um caminho listado na variável de ambiente Path, você poderá omitir o caminho do comando.

Por exemplo, se você tiver um script chamado "TestScript.ps1" no diretório C:\\PS\-Test, para exibir o tópico da Ajuda para o script, digite:

```
get-help c:\ps-test\TestScript.ps1
```

Os parâmetros que foram projetados para exibir o cmdlet Help, como *Detailed*, *Full*, *Examples* e *Parameter* funcionam tanto para o script quanto para a função Help. No entanto, ao exibir toda a Ajuda digitando “get-help *”, a Ajuda para funções e scripts não é exibida.

Para obter informações sobre como criar Ajuda para suas funções e scripts, consulte [about_Functions [m2]](assetId:///61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](assetId:///7dc08334-dcfe-450b-b949-0554855623af) e [about_Comment_Based_Help](assetId:///99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).

## Obtendo Ajuda online
Se você estiver conectado à Internet, uma das melhores maneiras de obter Ajuda será exibir os tópicos da Ajuda online. Como tópicos online são fáceis de atualizar, eles provavelmente fornecerão o conteúdo mais atual.

Para obter Ajuda online, experimente o parâmetro *Online* do cmdlet Get-Help. O parâmetro *Online* do cmdlet Get-Help funciona somente para o cmdlet, função e script Help. Não é possível usar o parâmetro *Online* com tópicos de Ajuda conceitual (About) ou de provedor. Além disso, como esse recurso é opcional, ele não funciona para o tópico de Ajuda de todos os cmdlets, funções ou scripts.

No entanto, todos os tópicos de Ajuda que acompanham o Windows PowerShell, incluindo tópicos de Ajuda de provedor e conceitual (About), estão disponíveis online na seção [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) da Biblioteca do Microsoft TechNet.

Para usar o parâmetro *Online* do cmdlet Get-Help, use o seguinte formato de comando.

```
get-help <command-name> -online
```

Por exemplo, para obter a versão online do tópico da Ajuda para o cmdlet Get-ChildItem, digite:

```
get-help get-childitem -online
```

Se uma versão online do tópico da Ajuda estiver disponível, ela será aberta no navegador padrão.

Se a Ajuda online tiver suporte em um tópico da Ajuda, você também poderá exibir a URL (o endereço de Internet) do tópico da Ajuda. O endereço de Internet é exibido na seção Links Relacionados de um tópico da Ajuda.

Por exemplo, para ver a URL para a versão online do cmdlet Add-Computer, digite:

```
get-help add-computer
```

A primeira linha na seção Links Relacionados do tópico é mostrada abaixo.

```
Online version: http://go.microsoft.com/fwlink/?LinkID=135194
```

Para obter informações sobre como dar suporte online aos seus tópicos de Ajuda, consulte [about_Comment_Based_Help](assetId:///99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf) e consulte "Como criar Ajuda para cmdlets" ([http://go.microsoft.com/fwlink/?LinkID=123415](http://go.microsoft.com/fwlink/?LinkID=123415)) na Biblioteca do MSDN (Microsoft Developer Network).

## Consulte Também
[about_Functions [m2]](assetId:///61d40692-5300-4de9-a9b5-bae31815e105)
[about_Scripts](assetId:///7dc08334-dcfe-450b-b949-0554855623af)
[about_Comment_Based_Help](assetId:///99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)
[Get-Help [m2]](assetId:///2d7fe1b4-0025-4580-a911-d81922dd6cd2)



<!--HONumber=Apr16_HO1-->


