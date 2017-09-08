---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet
ms.date: 2016-12-12
title: uninstall pswawebapplication
ms.technology: powershell
ms.openlocfilehash: 64d546427e44d7bd284da8f682a7218afbadd0ad
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2017
---
#  <a name="uninstall-pswawebapplication"></a><span data-ttu-id="9e2a2-103">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="9e2a2-103">Uninstall-PswaWebApplication</span></span>

##  <a name="synopsis"></a><span data-ttu-id="9e2a2-104">SINOPSE</span><span class="sxs-lookup"><span data-stu-id="9e2a2-104">SYNOPSIS</span></span>

<span data-ttu-id="9e2a2-105">Desinstala o aplicativo Web Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="9e2a2-105">Uninstalls the Windows PowerShell® web application.</span></span>

## <a name="syntax"></a><span data-ttu-id="9e2a2-106">SINTAXE</span><span class="sxs-lookup"><span data-stu-id="9e2a2-106">SYNTAX</span></span>

###  <a name="default"></a><span data-ttu-id="9e2a2-107">Padrão</span><span class="sxs-lookup"><span data-stu-id="9e2a2-107">Default</span></span>
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="9e2a2-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="9e2a2-108">DESCRIPTION</span></span>

<span data-ttu-id="9e2a2-109">O cmdlet **Uninstall-PswaWebApplication** desinstala o aplicativo Web Windows PowerShell e remove o site do IIS.</span><span class="sxs-lookup"><span data-stu-id="9e2a2-109">The **Uninstall-PswaWebApplication** cmdlet uninstalls the Windows PowerShell web application and removes the website from IIS.</span></span> <span data-ttu-id="9e2a2-110">O cmdlet não desinstala o IIS nem nenhum outro recurso que foi instalado porque era necessário para a execução do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9e2a2-110">The cmdlet does not uninstall IIS, or any other features installed because they were required for Windows PowerShell to run.</span></span>

## <a name="parameters"></a><span data-ttu-id="9e2a2-111">PARÂMETROS</span><span class="sxs-lookup"><span data-stu-id="9e2a2-111">PARAMETERS</span></span>

### <a name="-deletetestcertificate"></a><span data-ttu-id="9e2a2-112">-DeleteTestCertificate</span><span class="sxs-lookup"><span data-stu-id="9e2a2-112">-DeleteTestCertificate</span></span>

<span data-ttu-id="9e2a2-113">Indica que os certificados de teste criados pelo cmdlet **Install\_PswaWebApplication** (com o parâmetro **UseTestCertificate**) são excluídos.</span><span class="sxs-lookup"><span data-stu-id="9e2a2-113">Indicates that the test certificates created by the **Install\_PswaWebApplication** cmdlet (with the **UseTestCertificate** parameter) is deleted.</span></span>
<span data-ttu-id="9e2a2-114">Somente é removido o certificado de teste com o mesmo nome que aquele criado pelo cmdlet **Install-PswaWebApplication**.</span><span class="sxs-lookup"><span data-stu-id="9e2a2-114">Only the test certificate with the same name as the one created by the **Install-PswaWebApplication** cmdlet is removed.</span></span>

|||  
|-|-|
| <span data-ttu-id="9e2a2-115">Aliases</span><span class="sxs-lookup"><span data-stu-id="9e2a2-115">Aliases</span></span>                              | <span data-ttu-id="9e2a2-116">none</span><span class="sxs-lookup"><span data-stu-id="9e2a2-116">none</span></span>                                 |
| <span data-ttu-id="9e2a2-117">Necessário?</span><span class="sxs-lookup"><span data-stu-id="9e2a2-117">Required?</span></span>                            | <span data-ttu-id="9e2a2-118">false</span><span class="sxs-lookup"><span data-stu-id="9e2a2-118">false</span></span>                                |
| <span data-ttu-id="9e2a2-119">Posição?</span><span class="sxs-lookup"><span data-stu-id="9e2a2-119">Position?</span></span>                            | <span data-ttu-id="9e2a2-120">chamada</span><span class="sxs-lookup"><span data-stu-id="9e2a2-120">named</span></span>                                |
| <span data-ttu-id="9e2a2-121">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="9e2a2-121">Default Value</span></span>                        | <span data-ttu-id="9e2a2-122">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="9e2a2-122">true</span></span>                                 |
| <span data-ttu-id="9e2a2-123">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="9e2a2-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9e2a2-124">false</span><span class="sxs-lookup"><span data-stu-id="9e2a2-124">false</span></span>                                |
| <span data-ttu-id="9e2a2-125">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="9e2a2-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9e2a2-126">false</span><span class="sxs-lookup"><span data-stu-id="9e2a2-126">false</span></span>                                |

### <a name="-webapplicationname-ltstringgt"></a><span data-ttu-id="9e2a2-127">-WebApplicationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="9e2a2-127">-WebApplicationName &lt;String&gt;</span></span>

<span data-ttu-id="9e2a2-128">Especifica o nome do aplicativo Web a ser desinstalado.</span><span class="sxs-lookup"><span data-stu-id="9e2a2-128">Specifies the name of the web application to uninstall.</span></span>

|||  
|-|-|
| <span data-ttu-id="9e2a2-129">Aliases</span><span class="sxs-lookup"><span data-stu-id="9e2a2-129">Aliases</span></span>                              | <span data-ttu-id="9e2a2-130">none</span><span class="sxs-lookup"><span data-stu-id="9e2a2-130">none</span></span>                                 |
| <span data-ttu-id="9e2a2-131">Necessário?</span><span class="sxs-lookup"><span data-stu-id="9e2a2-131">Required?</span></span>                            | <span data-ttu-id="9e2a2-132">false</span><span class="sxs-lookup"><span data-stu-id="9e2a2-132">false</span></span>                                |
| <span data-ttu-id="9e2a2-133">Posição?</span><span class="sxs-lookup"><span data-stu-id="9e2a2-133">Position?</span></span>                            | <span data-ttu-id="9e2a2-134">1</span><span class="sxs-lookup"><span data-stu-id="9e2a2-134">1</span></span>                                    |
| <span data-ttu-id="9e2a2-135">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="9e2a2-135">Default Value</span></span>                        | <span data-ttu-id="9e2a2-136">pswa</span><span class="sxs-lookup"><span data-stu-id="9e2a2-136">pswa</span></span>                                 |
| <span data-ttu-id="9e2a2-137">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="9e2a2-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9e2a2-138">false</span><span class="sxs-lookup"><span data-stu-id="9e2a2-138">false</span></span>                                |
| <span data-ttu-id="9e2a2-139">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="9e2a2-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9e2a2-140">false</span><span class="sxs-lookup"><span data-stu-id="9e2a2-140">false</span></span>                                |

### <a name="-websitename-ltstringgt"></a><span data-ttu-id="9e2a2-141">-WebSiteName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="9e2a2-141">-WebSiteName &lt;String&gt;</span></span>

<span data-ttu-id="9e2a2-142">Especifica o nome do site em que o aplicativo Web está instalado.</span><span class="sxs-lookup"><span data-stu-id="9e2a2-142">Specifies the name of the web site where the web application is installed.</span></span>

|||  
|-|-|
| <span data-ttu-id="9e2a2-143">Aliases</span><span class="sxs-lookup"><span data-stu-id="9e2a2-143">Aliases</span></span>                              | <span data-ttu-id="9e2a2-144">none</span><span class="sxs-lookup"><span data-stu-id="9e2a2-144">none</span></span>                                 |
| <span data-ttu-id="9e2a2-145">Necessário?</span><span class="sxs-lookup"><span data-stu-id="9e2a2-145">Required?</span></span>                            | <span data-ttu-id="9e2a2-146">false</span><span class="sxs-lookup"><span data-stu-id="9e2a2-146">false</span></span>                                |
| <span data-ttu-id="9e2a2-147">Posição?</span><span class="sxs-lookup"><span data-stu-id="9e2a2-147">Position?</span></span>                            | <span data-ttu-id="9e2a2-148">chamada</span><span class="sxs-lookup"><span data-stu-id="9e2a2-148">named</span></span>                                |
| <span data-ttu-id="9e2a2-149">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="9e2a2-149">Default Value</span></span>                        | <span data-ttu-id="9e2a2-150">Site padrão</span><span class="sxs-lookup"><span data-stu-id="9e2a2-150">Default Web Site</span></span>                     |
| <span data-ttu-id="9e2a2-151">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="9e2a2-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9e2a2-152">false</span><span class="sxs-lookup"><span data-stu-id="9e2a2-152">false</span></span>                                |
| <span data-ttu-id="9e2a2-153">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="9e2a2-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9e2a2-154">false</span><span class="sxs-lookup"><span data-stu-id="9e2a2-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="9e2a2-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9e2a2-155">-Confirm</span></span>

<span data-ttu-id="9e2a2-156">Solicita que você confirme antes de executar o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9e2a2-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="9e2a2-157">Necessário?</span><span class="sxs-lookup"><span data-stu-id="9e2a2-157">Required?</span></span>                            | <span data-ttu-id="9e2a2-158">false</span><span class="sxs-lookup"><span data-stu-id="9e2a2-158">false</span></span>                                |
| <span data-ttu-id="9e2a2-159">Posição?</span><span class="sxs-lookup"><span data-stu-id="9e2a2-159">Position?</span></span>                            | <span data-ttu-id="9e2a2-160">chamada</span><span class="sxs-lookup"><span data-stu-id="9e2a2-160">named</span></span>                                |
| <span data-ttu-id="9e2a2-161">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="9e2a2-161">Default Value</span></span>                        | <span data-ttu-id="9e2a2-162">false</span><span class="sxs-lookup"><span data-stu-id="9e2a2-162">false</span></span>                                |
| <span data-ttu-id="9e2a2-163">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="9e2a2-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9e2a2-164">false</span><span class="sxs-lookup"><span data-stu-id="9e2a2-164">false</span></span>                                |
| <span data-ttu-id="9e2a2-165">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="9e2a2-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9e2a2-166">false</span><span class="sxs-lookup"><span data-stu-id="9e2a2-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="9e2a2-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9e2a2-167">-WhatIf</span></span>

<span data-ttu-id="9e2a2-168">Mostra o que aconteceria se o cmdlet fosse executado.</span><span class="sxs-lookup"><span data-stu-id="9e2a2-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="9e2a2-169">O cmdlet não é executado.</span><span class="sxs-lookup"><span data-stu-id="9e2a2-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="9e2a2-170">Necessário?</span><span class="sxs-lookup"><span data-stu-id="9e2a2-170">Required?</span></span>                            | <span data-ttu-id="9e2a2-171">false</span><span class="sxs-lookup"><span data-stu-id="9e2a2-171">false</span></span>                                |
| <span data-ttu-id="9e2a2-172">Posição?</span><span class="sxs-lookup"><span data-stu-id="9e2a2-172">Position?</span></span>                            | <span data-ttu-id="9e2a2-173">chamada</span><span class="sxs-lookup"><span data-stu-id="9e2a2-173">named</span></span>                                |
| <span data-ttu-id="9e2a2-174">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="9e2a2-174">Default Value</span></span>                        | <span data-ttu-id="9e2a2-175">false</span><span class="sxs-lookup"><span data-stu-id="9e2a2-175">false</span></span>                                |
| <span data-ttu-id="9e2a2-176">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="9e2a2-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9e2a2-177">false</span><span class="sxs-lookup"><span data-stu-id="9e2a2-177">false</span></span>                                |
| <span data-ttu-id="9e2a2-178">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="9e2a2-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9e2a2-179">false</span><span class="sxs-lookup"><span data-stu-id="9e2a2-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="9e2a2-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="9e2a2-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="9e2a2-181">Esse cmdlet oferece suporte aos parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="9e2a2-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="9e2a2-182">Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9e2a2-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="9e2a2-183">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="9e2a2-183">INPUTS</span></span>

<span data-ttu-id="9e2a2-184">Este cmdlet não aceita nenhuma entrada.</span><span class="sxs-lookup"><span data-stu-id="9e2a2-184">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="9e2a2-185">SAÍDAS</span><span class="sxs-lookup"><span data-stu-id="9e2a2-185">OUTPUTS</span></span>

<span data-ttu-id="9e2a2-186">Esse cmdlet não retorna nenhuma saída.</span><span class="sxs-lookup"><span data-stu-id="9e2a2-186">This cmdlet returns no output.</span></span>

## <a name="examples"></a><span data-ttu-id="9e2a2-187">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="9e2a2-187">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="9e2a2-188">EXEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="9e2a2-188">EXAMPLE 1</span></span>

<span data-ttu-id="9e2a2-189">Este comando desinstala o aplicativo Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9e2a2-189">This command uninstalls the Windows PowerShell Web Application.</span></span>
<span data-ttu-id="9e2a2-190">Você poderá usar este cmdlet para desinstalar o aplicativo Web Windows PowerShell se ele tiver sido instalado usando os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="9e2a2-190">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values.</span></span>

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="9e2a2-191">EXEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="9e2a2-191">EXAMPLE 2</span></span>

<span data-ttu-id="9e2a2-192">Esse comando desinstala o aplicativo Web Windows PowerShell e exclui o certificado de teste associado ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9e2a2-192">This command uninstalls the Windows PowerShell Web Application, and deletes the test certificate associated with the application.</span></span>
<span data-ttu-id="9e2a2-193">Você poderá usar este cmdlet para desinstalar o aplicativo Web Windows PowerShell se o tiver instalado usando os valores padrão e tiver criado um certificado de teste.</span><span class="sxs-lookup"><span data-stu-id="9e2a2-193">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values and created a test certificate.</span></span>

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="9e2a2-194">EXAMPLE 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="9e2a2-194">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="9e2a2-195">Este comando desinstala o aplicativo Web Windows PowerShell quando um aplicativo e um site personalizados foram especificados durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="9e2a2-195">This command uninstalls the Windows PowerShell Web Application when a custom website and application were specified during the install.</span></span>
<span data-ttu-id="9e2a2-196">O comando remove o site chamado *MySite* e o aplicativo chamado *TestApplication* e especifica que os certificados de teste associados ao aplicativo também são excluídos.</span><span class="sxs-lookup"><span data-stu-id="9e2a2-196">The command removes the website named *MySite* and the application named *TestApplication* and specifies that the test certificates associated with the application are also deleted.</span></span>

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

##  <a name="related-topics"></a><span data-ttu-id="9e2a2-197">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="9e2a2-197">Related topics</span></span>

-  [<span data-ttu-id="9e2a2-198">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9e2a2-198">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
-  [<span data-ttu-id="9e2a2-199">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9e2a2-199">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
-  [<span data-ttu-id="9e2a2-200">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="9e2a2-200">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
-  [<span data-ttu-id="9e2a2-201">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9e2a2-201">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
-  [<span data-ttu-id="9e2a2-202">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9e2a2-202">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
