---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
title: Problemas conhecidos no WMF 5.1
ms.openlocfilehash: 93113962781f1cc84a80f8f97f56ffd7622fec6b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="known-issues-in-wmf-51"></a><span data-ttu-id="b9858-103">Problemas conhecidos no WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="b9858-103">Known Issues in WMF 5.1</span></span> #

> <span data-ttu-id="b9858-104">Observação: essas informações estão sujeitas a alteração.</span><span class="sxs-lookup"><span data-stu-id="b9858-104">Note: This information is subject to change.</span></span>

## <a name="starting-powershell-shortcut-as-administrator"></a><span data-ttu-id="b9858-105">Iniciando o atalho do PowerShell como administrador</span><span class="sxs-lookup"><span data-stu-id="b9858-105">Starting PowerShell shortcut as Administrator</span></span>
<span data-ttu-id="b9858-106">Na instalação do Windows Media Format, se você tentar iniciar o PowerShell no atalho como administrador, poderá receber uma mensagem de "Erro não especificado".</span><span class="sxs-lookup"><span data-stu-id="b9858-106">Upon installing WMF, if you try to start PowerShell as administrator from the shortcut, you may get an "Unspecified error" message.</span></span>
<span data-ttu-id="b9858-107">Abra novamente o atalho como não administrador. Agora ele funciona até mesmo como administrador.</span><span class="sxs-lookup"><span data-stu-id="b9858-107">Reopen the shortcut as non-administrator and the shortcut now works even as administrator.</span></span>

## <a name="pester"></a><span data-ttu-id="b9858-108">Pester</span><span class="sxs-lookup"><span data-stu-id="b9858-108">Pester</span></span>
<span data-ttu-id="b9858-109">Nesta versão, há dois problemas dos quais você deve estar ciente ao usar o Pester no Nano Server:</span><span class="sxs-lookup"><span data-stu-id="b9858-109">In this release, there are two issues you should be aware of when using Pester on Nano Server:</span></span>

* <span data-ttu-id="b9858-110">A execução de testes em relação ao Pester em si pode resultar em algumas falhas devido às diferenças entre FULL CLR e CORE CLR.</span><span class="sxs-lookup"><span data-stu-id="b9858-110">Running tests against Pester itself can result in some failures because of differences between FULL CLR and CORE CLR.</span></span> <span data-ttu-id="b9858-111">Particularmente, o método Validate não está disponível no tipo XmlDocument.</span><span class="sxs-lookup"><span data-stu-id="b9858-111">In particular, the Validate method is not available on the XmlDocument type.</span></span> <span data-ttu-id="b9858-112">Seis testes que tentam validar o esquema dos logs de saída do NUnit são conhecidos por falharem.</span><span class="sxs-lookup"><span data-stu-id="b9858-112">Six tests which attempt to validate the schema of the NUnit output logs are known to fail.</span></span> 
* <span data-ttu-id="b9858-113">Um teste de cobertura de código falha atualmente porque o Recurso de DSC *WindowsFeature* não existe no Nano Server.</span><span class="sxs-lookup"><span data-stu-id="b9858-113">One Code Coverage test fails currently because the *WindowsFeature* DSC Resource does not exist in Nano Server.</span></span> <span data-ttu-id="b9858-114">No entanto, essas falhas geralmente são benignas e podem ser ignoradas com segurança.</span><span class="sxs-lookup"><span data-stu-id="b9858-114">However, these failures are generally benign and can safely be ignored.</span></span>

## <a name="operation-validation"></a><span data-ttu-id="b9858-115">Validação da operação</span><span class="sxs-lookup"><span data-stu-id="b9858-115">Operation Validation</span></span> 

* <span data-ttu-id="b9858-116">O Update-Help falha no módulo Microsoft.PowerShell.Operation.Validation devido a um URI de ajuda que não funciona</span><span class="sxs-lookup"><span data-stu-id="b9858-116">Update-Help fails for Microsoft.PowerShell.Operation.Validation module due to non-working help URI</span></span>

## <a name="dsc-after-uninstall-wmf"></a><span data-ttu-id="b9858-117">DSC após desinstalar o WMF</span><span class="sxs-lookup"><span data-stu-id="b9858-117">DSC after uninstall WMF</span></span> 
* <span data-ttu-id="b9858-118">A desinstalação do WMF não exclui da pasta de configuração os documentos MOF da DSC.</span><span class="sxs-lookup"><span data-stu-id="b9858-118">Uninstalling WMF does not delete DSC MOF documents from the configuration folder.</span></span> <span data-ttu-id="b9858-119">A DSC não funcionará corretamente se os documentos MOF contêm propriedades mais recentes, que não estão disponíveis nos sistemas mais antigos.</span><span class="sxs-lookup"><span data-stu-id="b9858-119">DSC won't work properly if the MOF documents contain newer properties which are not available on the older systems.</span></span> <span data-ttu-id="b9858-120">Nesse caso, execute o seguinte script no console do PowerShell com privilégios elevados para limpar os estados da DSC.</span><span class="sxs-lookup"><span data-stu-id="b9858-120">In this case, run the following script from elevated PowerShell console to to clean up the DSC states.</span></span>
 ```PowerShell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )

    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
 ```  

## <a name="jea-virtual-accounts"></a><span data-ttu-id="b9858-121">Contas Virtuais JEA</span><span class="sxs-lookup"><span data-stu-id="b9858-121">JEA Virtual Accounts</span></span>
<span data-ttu-id="b9858-122">As configurações de sessão e pontos de extremidade JEA configurados para usar contas virtuais no WMF 5.0 não serão configuradas para usar uma conta virtual após a atualização para o WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="b9858-122">JEA endpoints and session configurations configured to use virtual accounts in WMF 5.0 will not be configured to use a virtual account after upgrading to WMF 5.1.</span></span>
<span data-ttu-id="b9858-123">Isso significa que os comandos executados em sessões JEA serão executados sob a identidade do usuário conectado, em vez de uma conta de administrador temporária, impedindo potencialmente que o usuário execute comandos que exijam privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="b9858-123">This means that commands run in JEA sessions will run under the connecting user's identity instead of a temporary administrator account, potentially preventing the user from running commands which require elevated privileges.</span></span>
<span data-ttu-id="b9858-124">Para restaurar as contas virtuais, você precisa cancelar o registro e registrar novamente as configurações de sessão que usam contas virtuais.</span><span class="sxs-lookup"><span data-stu-id="b9858-124">To restore the virtual accounts, you need to unregister and re-register any session configurations that use virtual accounts.</span></span>

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

