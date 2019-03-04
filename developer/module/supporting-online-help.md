---
title: Suporte à Ajuda Online | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: b76f45299d11dc10c8b16ed80f87c7f1fcc5ed65
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857912"
---
# <a name="supporting-online-help"></a>Suporte à ajuda online

Começando no Windows PowerShell 3.0, há duas maneiras para dar suporte a `Get-Help` recurso Online para comandos do Windows PowerShell. Este tópico explica como implementar esse recurso para tipos diferentes de comando.

## <a name="about-online-help"></a>Sobre a Ajuda Online

A Ajuda online sempre foi uma parte essencial do Windows PowerShell. Embora o `Get-Help` cmdlet exibirá tópicos da Ajuda no prompt de comando, muitos usuários preferem a experiência de leitura online, incluindo codificação por cores, hiperlinks e compartilhamento de ideias no conteúdo da comunidade e documentos com base em wiki. Mais importante é que, antes do advento do ajuda atualizável, a Ajuda online fornecida a versão mais atualizada dos arquivos de Ajuda.

Com o advento da Ajuda atualizável no Windows PowerShell 3.0, a Ajuda online ainda desempenha um papel vital. Além da experiência de usuário flexível, a Ajuda online fornece ajuda para os usuários que não têm ou não é possível usar a Ajuda atualizável para baixar os tópicos da Ajuda.

## <a name="how-get-help--online-works"></a>Como Get-Help-Online funciona

Para ajudar os usuários a localizar os tópicos da Ajuda online para comandos, o `Get-Help` command tem um parâmetro Online que abre a versão online do tópico da Ajuda para um comando no navegador de Internet padrão do usuário.

Por exemplo, o comando a seguir abre o tópico de Ajuda online para o `Invoke-Command` cmdlet.

```powershell
Get-Help Invoke-Command -Online
```

Para implementar `Get-Help` -on-line, o `Get-Help` cmdlet procura para um identificador de URI (Uniform Resource) para o tópico da Ajuda on-line de versão nos seguintes locais.

- O primeiro link na seção Links relacionados do tópico da Ajuda para o comando. O tópico da Ajuda deve ser instalado no computador do usuário. Esse recurso foi introduzido no Windows PowerShell 2.0.

- A propriedade HelpUri de qualquer comando. A propriedade HelpUri é acessível, mesmo quando o tópico da Ajuda para o comando não está instalado no computador do usuário. Esse recurso foi introduzido no Windows PowerShell 3.0.

  `Get-Help` procura por um URI na primeira entrada na seção Links relacionados antes de obter o valor da propriedade HelpUri. Se o valor da propriedade estiver incorreto ou foi alterada, você pode substituí-la, inserindo um valor diferente no primeiro Link relacionado. No entanto, o primeiro Link relacionado funciona apenas quando os tópicos de ajuda são instalados no computador do usuário.

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>Adicionando um URI para o primeiro link relacionado de um tópico de ajuda de comando

Você pode dar suporte a `Get-Help` -on-line para qualquer comando, adicionando um URI válido para a primeira entrada na seção Links relacionados do tópico da Ajuda baseada em XML para o comando. Essa opção só é válida em tópicos de ajuda baseados em XML e funciona somente quando o tópico da Ajuda está instalado no computador do usuário. Quando o tópico da Ajuda está instalado e o URI é preenchido, esse valor tem precedência sobre o **HelpUri** propriedade do comando. Para obter informações sobre tópicos de ajuda baseados em XML para os comandos, consulte [Writing XML-Based tópicos da Ajuda para comandos](../help/writing-xml-based-help-topics-for-commands.md).

Para dar suporte a esse recurso, o URI deve aparecer na `maml:uri` elemento sob o primeiro `maml:relatedLinks/maml:navigationLink` elemento o `maml:relatedLinks` elemento.

O XML a seguir mostra a colocação correta do URI. A "versão Online:" texto no `maml:linkText` elemento é uma prática recomendada, mas não é necessária.

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>http://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a>Adição da propriedade HelpUri para um comando

Esta seção mostra como adicionar a propriedade HelpUri para comandos de tipos diferentes.

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a>Adicionando uma propriedade HelpUri para um Cmdlet

Para cmdlets escritos em C#, adicione uma **HelpUri** atributo à classe do Cmdlet. O valor do atributo deve ser um URI que começa com "http" ou "https".

O código a seguir mostra o atributo HelpUri o `Get-History` classe cmdlet.

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>Adicionando uma propriedade HelpUri para uma função avançada

Para funções avançadas, adicione uma **HelpUri** propriedade para o **CmdletBinding** atributo. O valor da propriedade deve ser um URI que começa com "http" ou "https".

O código a seguir mostra o atributo HelpUri da função New-calendário

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>Adicionando um atributo HelpUri para um comando CIM

Para comandos CIM, adicione uma **HelpUri** atributo para o **CmdletMetadata** elemento no arquivo CDXML. O valor do atributo deve ser um URI que começa com "http" ou "https".

O código a seguir mostra o atributo HelpUri do comando Start-Debug CIM

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>Adicionando um atributo HelpUri para um fluxo de trabalho

Para fluxos de trabalho que são escritos na linguagem do Windows PowerShell, adicione um **. ExternalHelp** diretiva de comentário para o código de fluxo de trabalho. O valor da diretiva deve ser um URI que começa com "http" ou "https".

> [!NOTE]
> Não há suporte para a propriedade HelpUri para fluxos de trabalho baseados em XAML no Windows PowerShell.

O seguinte código mostra o. Diretiva ExternalHelp em um arquivo de fluxo de trabalho.

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```