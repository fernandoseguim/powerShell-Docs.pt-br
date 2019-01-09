---
ms.date: 06/12/2017
keywords: DSC,powershell,configuração,instalação
title: Recurso ProcessSet da DSC
ms.openlocfilehash: 91a2d5b562864addcb8e11062916d291448bbf57
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046994"
---
# <a name="dsc-windowsprocess-resource"></a>Recurso WindowsProcess de DSC

_Aplica-se a: Windows PowerShell 5.0_

O recurso **ProcessSet** na DSC (Configuração de Estado Desejado) do Windows PowerShell fornece um mecanismo para configurar processos em um nó de destino. Esse recurso é um [recurso composto](../../../resources/authoringResourceComposite.md) que chama o [Recurso do WindowsProcess](windowsProcessResource.md) para cada grupo especificado no parâmetro `GroupName`.

## <a name="syntax"></a>Sintaxe

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Propriedades

| Propriedade | Descrição |
| --- | --- |
| Argumentos| Uma cadeia de caracteres que contém os argumentos a serem passados ao processo no estado em que se encontram. Se você precisar passar vários argumentos, coloque todos nessa cadeia de caracteres.|
| Caminho| Os caminhos para os executáveis do processo. Se esses forem os nomes dos arquivos executáveis (caminhos não totalmente qualificados), o recurso DSC pesquisará a variável de ambiente **Path** (`$env:Path`) para localizar os arquivos. Se os valores dessa propriedade forem caminhos totalmente qualificados, a DSC não usará a variável de ambiente **Path** para localizar os arquivos e gerará um erro se qualquer um dos caminhos não existir. Caminhos relativos não são permitidos.|
| Credential| Indica as credenciais para iniciar o processo.|
| Ensure| Especifica se os processos existem. Defina essa propriedade como "Present" para garantir que o processo exista. Caso contrário, defina-a como "Absent". O padrão é "Present".|
| StandardErrorPath| O caminho para o qual os processos gravam o erro padrão. Qualquer arquivo existente será substituído.|
| StandardInputPath| O fluxo do qual o processo recebe entrada padrão.|
| StandardOutputPath| O caminho do arquivo para o qual os processos gravam a saída padrão. Qualquer arquivo existente será substituído.|
| WorkingDirectory| O local usado como diretório de trabalho atual para os processos.|
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for **ResourceName** e seu tipo for **_ResourceType**, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.|
