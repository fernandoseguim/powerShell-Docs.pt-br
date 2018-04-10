---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,instalação
title: Problemas conhecidos no WMF 5.1
ms.openlocfilehash: 467a191f40d85bfca7c794915d6274a9a1b201e7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="known-issues-in-wmf-51"></a>Problemas conhecidos no WMF 5.1 #

> Observação: essas informações estão sujeitas a alteração.

## <a name="starting-powershell-shortcut-as-administrator"></a>Iniciando o atalho do PowerShell como administrador
Na instalação do Windows Media Format, se você tentar iniciar o PowerShell no atalho como administrador, poderá receber uma mensagem de "Erro não especificado".
Abra novamente o atalho como não administrador. Agora ele funciona até mesmo como administrador.

## <a name="pester"></a>Pester
Nesta versão, há dois problemas dos quais você deve estar ciente ao usar o Pester no Nano Server:

* A execução de testes em relação ao Pester em si pode resultar em algumas falhas devido às diferenças entre FULL CLR e CORE CLR. Particularmente, o método Validate não está disponível no tipo XmlDocument. Seis testes que tentam validar o esquema dos logs de saída do NUnit são conhecidos por falharem.
* Um teste de cobertura de código falha atualmente porque o Recurso de DSC *WindowsFeature* não existe no Nano Server. No entanto, essas falhas geralmente são benignas e podem ser ignoradas com segurança.

## <a name="operation-validation"></a>Validação da operação

* O Update-Help falha no módulo Microsoft.PowerShell.Operation.Validation devido a um URI de ajuda que não funciona

## <a name="dsc-after-uninstall-wmf"></a>DSC após desinstalar o WMF
* A desinstalação do WMF não exclui da pasta de configuração os documentos MOF da DSC. A DSC não funcionará corretamente se os documentos MOF contêm propriedades mais recentes, que não estão disponíveis nos sistemas mais antigos. Nesse caso, execute o seguinte script no console do PowerShell com privilégios elevados para limpar os estados da DSC.
 ```powershell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )

    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
 ```

## <a name="jea-virtual-accounts"></a>Contas Virtuais JEA
As configurações de sessão e pontos de extremidade JEA configurados para usar contas virtuais no WMF 5.0 não serão configuradas para usar uma conta virtual após a atualização para o WMF 5.1.
Isso significa que os comandos executados em sessões JEA serão executados sob a identidade do usuário conectado, em vez de uma conta de administrador temporária, impedindo potencialmente que o usuário execute comandos que exijam privilégios elevados.
Para restaurar as contas virtuais, você precisa cancelar o registro e registrar novamente as configurações de sessão que usam contas virtuais.

```powershell
# Find the JEA endpoint by its name
$jea = Get-PSSessionConfiguration -Name MyJeaEndpoint

# Copy the cached PSSC file so it can be re-registered
$pssc = Copy-Item $jea.ConfigFilePath $env:temp -PassThru

# Unregister the current PSSC
Unregister-PSSessionConfiguration -Name $jea.Name

# Re-register the PSSC
Register-PSSessionConfiguration -Name $jea.Name -Path $pssc.FullName -Force

# Ensure the access policies remain the same
Set-PSSessionConfiguration -Name $newjea.Name -SecurityDescriptorSddl $jea.SecurityDescriptorSddl
```