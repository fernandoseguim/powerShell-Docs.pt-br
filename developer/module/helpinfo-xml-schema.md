---
title: Esquema XML HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74dcb396-c295-4457-b84c-4432bdaa8df3
caps.latest.revision: 7
ms.openlocfilehash: 0f965f4ee1ef92a6a538b52b4348c04366cabf66
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862312"
---
# <a name="helpinfo-xml-schema"></a>Esquema XML HelpInfo

Este tópico contém o esquema XML para arquivos de informações de ajuda atualizável, comumente conhecido como "Arquivos XML HelpInfo".

## <a name="helpinfo-xml-schema"></a>Esquema XML HelpInfo

Arquivos XML HelpInfo baseiam-se no esquema XML a seguir.

```xml
<?xml version="1.0" encoding="utf-8"?>
<schema targetNamespace="http://schemas.microsoft.com/powershell/help/2010/05" xmlns="http://www.w3.org/2001/XMLSchema">
  <element name="HelpInfo">
    <complexType>
      <sequence>
        <element name="HelpContentURI" type="anyURI" minOccurs="1" maxOccurs="1" />
        <element name="SupportedUICultures" minOccurs="1" maxOccurs="1">
          <complexType>
            <sequence>
              <element name="UICulture" minOccurs="1" maxOccurs="unbounded">
                <complexType>
                  <sequence>
                    <element name="UICultureName" type="language" minOccurs="1" maxOccurs="1" />
                    <element name="UICultureVersion" type="string" minOccurs="1" maxOccurs="1" />
                  </sequence>
                </complexType>
              </element>
            </sequence>
          </complexType>
        </element>
      </sequence>
    </complexType>
  </element>
</schema>
```

## <a name="helpinfo-xml-elements"></a>Elementos XML HelpInfo

O arquivo XML HelpInfo inclui os seguintes elementos.

HelpContentURI contém o URI do local da Ajuda arquivos CAB para o módulo. O URI deve começar com "http" ou "https". O URI deve especificar um local da Internet, mas não deve incluir o nome do arquivo CAB. O **HelpContentURI** valor pode ser igual ou diferente do **HelpInfoURI** valor.

SupportedUICultures representa os arquivos de Ajuda do módulo em todas as culturas de interface do usuário. Contém **UICulture** elementos, cada um deles representa um conjunto de arquivos de ajuda para o módulo em uma cultura de interface do usuário especificado.

UICulture representa um conjunto de arquivos de ajuda para o módulo em uma cultura de interface do usuário especificado. Adicionar um **UICulture** elemento para cada cultura de interface do usuário na qual os arquivos de ajuda são gravados.

UICultureName contém o código de idioma para a cultura de interface do usuário na qual os arquivos de ajuda são gravados.

UICultureVersion contém um número de versão de 4 partes em "N1. N2. N3. N4 "formato que representa a versão do arquivo CAB de ajuda na cultura da interface do usuário. Aumente esse número de versão sempre que você carregar a Ajuda de novos arquivos CAB na cultura da interface do usuário que é especificado pelo **UICultureName**. Para obter mais informações sobre esse valor, consulte "Versão classe (sistema)" no MSDN.