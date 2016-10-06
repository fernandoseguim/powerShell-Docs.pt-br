---
title: Recurso do WindowsOptionalFeatureSet DSC
ms.date: 2016-05-24
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 97714d3fa9a1c00fb3d2e79cc873280ca945a840
ms.openlocfilehash: 52eb958e59ecb1d5ae3faf268933bbd544410d47

---

# Recurso do WindowsOptionalFeatureSet DSC

> Aplica-se a: Windows PowerShell 5.0

O recurso **WindowsOptionalFeatureSet** na DSC (Configuração de Estado Desejado) do Windows PowerShell oferece um mecanismo para garantir que os recursos opcionais sejam habilitados em um nó de destino. Esse recurso é um [recurso composto](authoringResourceComposite.md) que chama o [recurso WindowsOptionalFeature](windowsOptionalFeatureResource.md) para cada recurso especificado na propriedade `Name`.

Use esse recurso quando desejar configurar vários recursos opcionais do Windows para o mesmo estado.

## Sintaxe

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ] 
    [ RemoveFilesOnDisable = [bool] ]  
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    
}
```

## Propriedades

|  Propriedade  |  Descrição   | 
|---|---| 
| Nome| Indica o nome dos recursos que você deseja garantir que estejam habilitados ou desabilitados.| 
| Ensure| Especifica se os recursos estão habilitados. Para garantir que os recursos estejam habilitados, defina essa propriedade para "Presente"; para garantir que os recursos estejam desabilitados, defina a propriedade como "Ausente".|
| Origem| Não foi implementado.|
| NoWindowsUpdateCheck| Especifica se o DISM contata o WU (Windows Update) ao procurar os arquivos de origem para habilitar recursos. Se $true, DISM não contatará WU.|
| RemoveFilesOnDisable| Definido como **$true** para remover todos os arquivos associados ao recurso quando eles são desabilitados (ou seja, quando **Garantir** está definido como "Ausente").|
| LogLevel| O nível máximo de saída mostrado nos logs. Os valores aceitos são: "ErrorsOnly" (somente erros são registrados), "ErrorsAndWarning" (erros e avisos são registrados) e "ErrorsAndWarningAndInformation" (erros, avisos e informações de depuração são registrados).|
| LogPath| O caminho até um arquivo de log em que você deseja que o provedor de recursos registre a operação.| 
| DependsOn| Especifica que a configuração de outro recurso deve ser executada antes de ele ser configurado. Por exemplo, se a ID do bloco de script de configuração do recurso que você deseja executar primeiro for __ResourceName__ e seu tipo for __ResourceType__, a sintaxe para usar essa propriedade será `DependsOn = "[ResourceType]ResourceName"`.| 
 






<!--HONumber=Aug16_HO3-->


