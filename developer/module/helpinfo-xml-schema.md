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
# <a name="helpinfo-xml-schema"></a><span data-ttu-id="90a4b-102">Esquema XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="90a4b-102">HelpInfo XML Schema</span></span>

<span data-ttu-id="90a4b-103">Este tópico contém o esquema XML para arquivos de informações de ajuda atualizável, comumente conhecido como "Arquivos XML HelpInfo".</span><span class="sxs-lookup"><span data-stu-id="90a4b-103">This topic contains the XML schema for Updatable Help Information files, commonly known as "HelpInfo XML files."</span></span>

## <a name="helpinfo-xml-schema"></a><span data-ttu-id="90a4b-104">Esquema XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="90a4b-104">HelpInfo XML Schema</span></span>

<span data-ttu-id="90a4b-105">Arquivos XML HelpInfo baseiam-se no esquema XML a seguir.</span><span class="sxs-lookup"><span data-stu-id="90a4b-105">HelpInfo XML files are based on the following XML schema.</span></span>

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

## <a name="helpinfo-xml-elements"></a><span data-ttu-id="90a4b-106">Elementos XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="90a4b-106">HelpInfo XML Elements</span></span>

<span data-ttu-id="90a4b-107">O arquivo XML HelpInfo inclui os seguintes elementos.</span><span class="sxs-lookup"><span data-stu-id="90a4b-107">The HelpInfo XML file includes the following elements.</span></span>

<span data-ttu-id="90a4b-108">HelpContentURI contém o URI do local da Ajuda arquivos CAB para o módulo.</span><span class="sxs-lookup"><span data-stu-id="90a4b-108">HelpContentURI Contains the URI of the location of the help CAB files for the module.</span></span> <span data-ttu-id="90a4b-109">O URI deve começar com "http" ou "https".</span><span class="sxs-lookup"><span data-stu-id="90a4b-109">The URI must begin with "http" or "https".</span></span> <span data-ttu-id="90a4b-110">O URI deve especificar um local da Internet, mas não deve incluir o nome do arquivo CAB.</span><span class="sxs-lookup"><span data-stu-id="90a4b-110">The URI should specify an Internet location, but must not include the CAB file name.</span></span> <span data-ttu-id="90a4b-111">O **HelpContentURI** valor pode ser igual ou diferente do **HelpInfoURI** valor.</span><span class="sxs-lookup"><span data-stu-id="90a4b-111">The **HelpContentURI** value can be the  same or different from the **HelpInfoURI** value.</span></span>

<span data-ttu-id="90a4b-112">SupportedUICultures representa os arquivos de Ajuda do módulo em todas as culturas de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="90a4b-112">SupportedUICultures Represents the module help files in all UI cultures.</span></span> <span data-ttu-id="90a4b-113">Contém **UICulture** elementos, cada um deles representa um conjunto de arquivos de ajuda para o módulo em uma cultura de interface do usuário especificado.</span><span class="sxs-lookup"><span data-stu-id="90a4b-113">Contains **UICulture** elements, each of which represents a set of help files for the module in a specified UI culture.</span></span>

<span data-ttu-id="90a4b-114">UICulture representa um conjunto de arquivos de ajuda para o módulo em uma cultura de interface do usuário especificado.</span><span class="sxs-lookup"><span data-stu-id="90a4b-114">UICulture Represents a set of help files for the module in a specified UI culture.</span></span> <span data-ttu-id="90a4b-115">Adicionar um **UICulture** elemento para cada cultura de interface do usuário na qual os arquivos de ajuda são gravados.</span><span class="sxs-lookup"><span data-stu-id="90a4b-115">Add a **UICulture** element for each UI culture in which the help files are written.</span></span>

<span data-ttu-id="90a4b-116">UICultureName contém o código de idioma para a cultura de interface do usuário na qual os arquivos de ajuda são gravados.</span><span class="sxs-lookup"><span data-stu-id="90a4b-116">UICultureName Contains the language code for the UI culture in which the help files are written.</span></span>

<span data-ttu-id="90a4b-117">UICultureVersion contém um número de versão de 4 partes em "N1. N2. N3. N4 "formato que representa a versão do arquivo CAB de ajuda na cultura da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="90a4b-117">UICultureVersion Contains a 4-part version number in "N1.N2.N3.N4" format that represents the version of the help CAB file in the UI culture.</span></span> <span data-ttu-id="90a4b-118">Aumente esse número de versão sempre que você carregar a Ajuda de novos arquivos CAB na cultura da interface do usuário que é especificado pelo **UICultureName**.</span><span class="sxs-lookup"><span data-stu-id="90a4b-118">Increment this version number whenever you upload new help CAB files in the UI culture that is specified by **UICultureName**.</span></span> <span data-ttu-id="90a4b-119">Para obter mais informações sobre esse valor, consulte "Versão classe (sistema)" no MSDN.</span><span class="sxs-lookup"><span data-stu-id="90a4b-119">For more information about this value, see "Version Class (System)" in MSDN.</span></span>