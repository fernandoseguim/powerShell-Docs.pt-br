---
title: Como adicionar parâmetros dinâmicos para um tópico de Ajuda do provedor | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: cc4877242a16a9caa99564aeaae985f85e38791e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859872"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>Como adicionar parâmetros dinâmicos a um tópico de ajuda do provedor

Esta seção explica como popular o **parâmetros dinâmicos** seção de um tópico de Ajuda do provedor.

*Parâmetros dinâmicos* são parâmetros de um cmdlet ou função que estão disponíveis apenas em condições de especificadas.

Os parâmetros dinâmicos que estão documentados em um tópico de Ajuda do provedor são os parâmetros dinâmicos que adiciona o provedor para o cmdlet ou função quando o cmdlet ou função é usada na unidade de provedor.

Parâmetros dinâmicos também podem ser documentados na Ajuda do cmdlet personalizado para um provedor. Ao escrever a Ajuda do provedor e a Ajuda do cmdlet personalizado para um provedor, inclua a documentação de parâmetro dinâmico em ambos os documentos. Para obter mais informações sobre a Ajuda do cmdlet personalizado, consulte [escrita Windows PowerShell Cmdlet ajuda personalizada para provedores de](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).

Se um provedor não implementa nenhum parâmetro dinâmico, o tópico de Ajuda do provedor contém um vazio `DynamicParameters` elemento.

### <a name="to-add-dynamic-parameters"></a>Para adicionar parâmetros dinâmicos

1. No *AssemblyName*help.xml. dll do arquivo, dentro de `providerHelp` elemento, adicionar um `DynamicParameters` elemento. O `DynamicParameters` elemento deve aparecer após o `Tasks` elemento e antes do `RelatedLinks` elemento.

   Por exemplo:

    ```xml
    <providerHelp>
        <Tasks>
        </Tasks>
        <DynamicParameters>
        </DynamicParameters>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

   Se o provedor não implementa nenhum parâmetro dinâmico, o `DynamicParameters` elemento pode estar vazio.

2. Dentro de `DynamicParameters` elemento para cada parâmetro dinâmico, adicione um `DynamicParameter` elemento.

   Por exemplo:

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. Em cada `DynamicParameter` elemento, adicione uma `Name` e `CmdletSupported` elemento.

   |Nome do elemento|Descrição|
   |------------------|-----------------|
   |Nome|Especifica o nome do parâmetro.|
   |CmdletSupported|Especifica os cmdlets no qual o parâmetro é válido. Digite uma lista separada por vírgulas de nomes de cmdlet.|

   Por exemplo, os documentos XML a seguir a `Encoding` parâmetro dinâmico que adiciona o provedor de sistema de arquivos do Windows PowerShell para o `Add-Content`, `Get-Content`, `Set-Content` cmdlets.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. Em cada `DynamicParameter` elemento, adicionar um `Type` elemento. O `Type` elemento é um contêiner para o `Name` elemento que contém o tipo de .NET do valor do parâmetro dinâmico.

   Por exemplo, o XML a seguir mostra que o tipo de .NET do `Encoding` parâmetro dinâmico é o [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeração.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
    ...
    </DynamicParameters>
    ```

5. Adicionar o `Description` elemento, que contém uma breve descrição do parâmetro dinâmico. Ao redigir a descrição, use as diretrizes prescritas para todos os parâmetros de cmdlet na [como adicionar informações de parâmetro](./how-to-add-parameter-information.md).

   Por exemplo, o XML a seguir inclui a descrição do `Encoding` parâmetro dinâmico.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
            <Description> Specifies the encoding of the output file that contains the content. </Description>
    ...
    </DynamicParameters>
    ```

6. Adicionar o `PossibleValues` elemento e seus elementos filho. Juntos, esses elementos descrevem os valores do parâmetro dinâmico. Esse elemento foi projetado para valores enumerados. Se o parâmetro dinâmico não aceita um valor, tal como acontece com um parâmetro de opção ou os valores não podem ser enumerados, adicione um vazio `PossibleValues` elemento.

   A tabela a seguir lista e descreve o `PossibleValues` elemento e seus elementos filho.

   |Nome do elemento|Descrição|
   |------------------|-----------------|
   |PossibleValues|Esse elemento é um contêiner. Seus elementos filho são descritos abaixo. Adicione um `PossibleValues` elemento para cada tópico de Ajuda do provedor. O elemento pode estar vazio.|
   |PossibleValue|Esse elemento é um contêiner. Seus elementos filho são descritos abaixo. Adicione um `PossibleValue` elemento para cada valor do parâmetro dinâmico.|
   |Valor|Especifica o nome do valor.|
   |Descrição|Esse elemento contém um `Para` elemento. O texto a `Para` elemento descreve o valor que é nomeado no `Value` elemento.|

   Por exemplo, o XML a seguir mostra uma `PossibleValue` elemento o `Encoding` parâmetro dinâmico.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
    ...
            <Description> Specifies the encoding of the output file that contains the content. </Description>
            <PossibleValues>
                <PossibleValue>
                    <Value> ASCII </Value>
                    <Description>
                        <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                    </Description>
                </PossibleValue>
    ...
            </PossibleValues>
    </DynamicParameters>
    ```

## <a name="example"></a>Exemplo

A exemplo a seguir mostra a `DynamicParameters` elemento o `Encoding` parâmetro dinâmico.

```xml
<DynamicParameters/>
    <DynamicParameter>
        <Name> Encoding </Name>
        <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
        <Type>
            <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
        <Type>
        <Description> Specifies the encoding of the output file that contains the content. </Description>
        <PossibleValues>
            <PossibleValue>
                <Value> ASCII </Value>
                <Description>
                    <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                </Description>
            </PossibleValue>
            <PossibleValue>
                <Value> Unicode </Value>
                <Description>
                    <para> Encodes in UTF-16 format using the little-endian byte order. </para>
                </Description>
            </PossibleValue>
        </PossibleValues>
</DynamicParameters>
```