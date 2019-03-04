---
title: 'Criação de ajuda atualizável: Passo a passo | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860312"
---
# <a name="updatable-help-authoring-step-by-step"></a>Criação de ajuda atualizável: passo a passo

Este documenta lista as etapas no processo de criação de ajuda atualizável.

## <a name="authoring-updatable-help-step-by-step"></a>Criação de ajuda atualizável: passo a passo

Ajuda atualizável foi projetada para usuários finais, mas ele também oferece benefícios significativos para os autores de módulo e gravadores de Ajuda, incluindo a capacidade de adicionar conteúdo, corrigem os erros, entregar em várias culturas de interface do usuário e respondem aos comentários do usuário e solicitações, muito tempo após o módulo foi enviado. Este tópico explica como você empacota e ajuda de carregamento de arquivos para que os usuários podem baixar e instalá-las usando o [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.

As etapas a seguir fornecem uma visão geral do processo de suporte à Ajuda atualizável.

### <a name="step-1-find-an-internet-site-for-your-help-files"></a>Etapa 1: Encontrar um site da Internet para seus arquivos de ajuda

A primeira etapa na criação de ajuda atualizável é encontrar um local da Internet para os arquivos de Ajuda do seu módulo. Na verdade, você pode usar dois locais diferentes. Você pode manter o arquivo de informações do seu módulo ajuda (HelpInfo XML - descritos abaixo) em um local de Internet e os arquivos CAB conteúdos de Ajuda em outro local de Internet. Todas as ajuda CAB arquivos de conteúdo para um módulo devem estar no mesmo local. Você pode colocar os arquivos CAB de conteúdo da Ajuda para módulos diferentes no mesmo local.

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a>Etapa 2: Adicionar uma chave de HelpInfoURI ao manifesto do módulo

Adicionar um **HelpInfoURI** chave ao manifesto do módulo. O valor da chave é o URI Uniform Resource Identifier () do local do arquivo XML HelpInfo informações para o seu módulo. Para segurança, o endereço deve começar com "http" ou "https". O URI deve especificar um local da Internet, mas não deve incluir o nome do arquivo XML HelpInfo.

Por exemplo:

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a>Etapa 3: Crie um arquivo XML HelpInfo

O arquivo de informações XML HelpInfo contém o URI do local da Internet dos seus arquivos de Ajuda e os números de versão dos arquivos de ajuda mais recentes para o seu módulo em cada cultura de interface do usuário com suporte. Cada módulo do Windows PowerShell tem um arquivo XML HelpInfo. Quando você atualiza seus arquivos de Ajuda, editar ou substituir o arquivo XML HelpInfo; Você não adicionar outro. Para obter mais informações, consulte [como criar um arquivo de XML HelpInfo](./how-to-create-a-helpinfo-xml-file.md).

### <a name="step-4-sign-your-help-files"></a>Etapa 4: Assinar seus arquivos de ajuda

Assinaturas digitais não são necessárias, mas eles são uma recomendação de melhores práticas, sempre que o compartilhamento de arquivos.

### <a name="step-5-create-cab-files"></a>Etapa 5: Criar arquivos CAB

Usar uma ferramenta que cria arquivos de gabinete (. cab), como MakeCab.exe, para criar um. Arquivo CAB que contém os arquivos de ajuda para o seu módulo. Crie um arquivo CAB separado para os arquivos de Ajuda em cada cultura de interface do usuário com suporte. Para obter mais informações, consulte [como preparar atualizável ajuda arquivos CAB](./how-to-prepare-updatable-help-cab-files.md).

### <a name="step-6-upload-your-files"></a>Etapa 6: Carregar seus arquivos

Para publicar arquivos de ajuda novos ou atualizados, carregar os arquivos CAB para o local de Internet que é especificado pela **HelpContentUri** elemento no arquivo XML HelpInfo. Em seguida, carregue o arquivo XML HelpInfo para o local de Internet que é especificado pelo valor da **HelpInfoUri** chave no manifesto de módulo.
