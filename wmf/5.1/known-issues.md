---
title: Problemas conhecidos no WMF 5.1 (Preview)
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: krishna
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: e2f19ed2fa2d2070860438b128513a463d95adae
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="known-issues-in-wmf-51-preview"></a>Problemas conhecidos no WMF 5.1 (Preview) #

> Observação: essas informações são preliminares e estão sujeitas a alteração.

## <a name="starting-powershell-shortcut-as-administrator"></a>Iniciando o atalho do PowerShell como administrador
Na instalação do Windows Media Format, se você tentar iniciar o PowerShell no atalho como administrador, poderá receber uma mensagem de "Erro não especificado".
Abra novamente o atalho como não administrador. Em seguida, ele funcionará também como administrador.

## <a name="pester"></a>Pester
Nesta versão, há dois problemas dos quais você deve estar ciente ao usar o Pester no Nano Server:

* A execução de testes em relação ao Pester em si pode resultar em algumas falhas devido às diferenças entre FULL CLR e CORE CLR. Particularmente, o método Validate não está disponível no tipo XmlDocument. Seis testes que tentam validar o esquema dos logs de saída do NUnit são conhecidos por falharem. 
* Um teste de cobertura de código falha atualmente porque o Recurso de DSC *WindowsFeature* não existe no Nano Server. No entanto, essas falhas geralmente são benignas e podem ser ignoradas com segurança.

## <a name="operation-validation"></a>Validação da operação 

* Update-Help falhará no módulo Microsoft.PowerShell.Operation.Validation devido a um URI de ajuda que não funciona

## <a name="dsc-after-uninstall-wmf"></a>DSC após desinstalar o WMF 
* A desinstalação do WMF não exclui da pasta de configuração os documentos MOF da DSC. A DSC não funcionará corretamente se os documentos MOF contêm propriedades mais recentes, que não estão disponíveis nos sistemas mais antigos. Nesse caso, execute o seguinte script no console do PowerShell com privilégios elevados para limpar os estados da DSC.
 ```PowerShell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )

    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
 ```  