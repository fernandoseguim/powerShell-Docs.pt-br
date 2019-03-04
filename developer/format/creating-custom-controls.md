---
title: Criação de controles personalizados | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3baa406-cd33-4420-be5a-07ef09d93480
caps.latest.revision: 8
ms.openlocfilehash: 3504ab1d974c55e9279172d0e851961474ccb926
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853192"
---
# <a name="creating-custom-controls"></a>Criar controles personalizados

Controles personalizados são os componentes mais flexíveis de um arquivo de formatação. Ao contrário de tabela, lista e modos de exibição amplos que definem uma estrutura formal de dados, como uma tabela de dados, controles personalizados permitem que você defina como um item individual de dados é exibido. Você pode definir um conjunto comum de controles personalizados que estão disponíveis para todas as exibições do arquivo de formatação, você pode definir os controles personalizados que estão disponíveis para uma exibição específica, ou você pode definir um conjunto de controles que estão disponíveis para um grupo de objetos.

## <a name="custom-control-example"></a>Exemplo de controle personalizado

O exemplo a seguir mostra um controle personalizado que é definido no arquivo Certificates.Format.ps1xml. Esse controle personalizado é usado para separar os [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objetos exibidos em uma exibição de tabela.

```xml
<Controls>
  <Control>
    <Name>SignatureTypes-GroupingFormat</Name>
    <CustomControl>
      <CustomEntries>
        <CustomEntry>
          <CustomItem>
            <Frame>
              <LeftIndent>4</LeftIndent>
              <CustomItem>
                <Text AssemblyName="System.Management.Automation" BaseName="FileSystemProviderStrings"
                  ResourceId="DirectoryDisplayGrouping"/>
                <ExpressionBinding>
                  <ScriptBlock>split-path $_.Path</ScriptBlock>
                </ExpressionBinding>
                <NewLine/>
              </CustomItem>
            </Frame>
          </CustomItem>
        </CustomEntry>
      </CustomEntries>
    </CustomControl>
  </Control>
</Controls>

```

## <a name="see-also"></a>Consulte Também

[Gravar um arquivo de formatação do PowerShell](./writing-a-powershell-formatting-file.md)
