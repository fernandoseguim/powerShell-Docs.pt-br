---
ms.topic: reference
keywords: powershell, cmdlet
ms.date: 12/12/2016
title: Uninstall-PswaWebApplication
ms.openlocfilehash: b2a3e4d584fd04ee49e1e6408dba39fd8bc555dc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="uninstall-pswawebapplication"></a><span data-ttu-id="6fb78-103">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="6fb78-103">Uninstall-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="6fb78-104">SINOPSE</span><span class="sxs-lookup"><span data-stu-id="6fb78-104">SYNOPSIS</span></span>

<span data-ttu-id="6fb78-105">Desinstala o aplicativo Web Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="6fb78-105">Uninstalls the Windows PowerShell® web application.</span></span>

## <a name="syntax"></a><span data-ttu-id="6fb78-106">SINTAXE</span><span class="sxs-lookup"><span data-stu-id="6fb78-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="6fb78-107">Padrão</span><span class="sxs-lookup"><span data-stu-id="6fb78-107">Default</span></span>
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="6fb78-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="6fb78-108">DESCRIPTION</span></span>

<span data-ttu-id="6fb78-109">O cmdlet **Uninstall-PswaWebApplication** desinstala o aplicativo Web Windows PowerShell e remove o site do IIS.</span><span class="sxs-lookup"><span data-stu-id="6fb78-109">The **Uninstall-PswaWebApplication** cmdlet uninstalls the Windows PowerShell web application and removes the website from IIS.</span></span> <span data-ttu-id="6fb78-110">O cmdlet não desinstala o IIS nem nenhum outro recurso que foi instalado porque era necessário para a execução do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6fb78-110">The cmdlet does not uninstall IIS, or any other features installed because they were required for Windows PowerShell to run.</span></span>

## <a name="parameters"></a><span data-ttu-id="6fb78-111">PARÂMETROS</span><span class="sxs-lookup"><span data-stu-id="6fb78-111">PARAMETERS</span></span>

### <a name="-deletetestcertificate"></a><span data-ttu-id="6fb78-112">-DeleteTestCertificate</span><span class="sxs-lookup"><span data-stu-id="6fb78-112">-DeleteTestCertificate</span></span>

<span data-ttu-id="6fb78-113">Indica que os certificados de teste criados pelo cmdlet **Install\_PswaWebApplication** (com o parâmetro **UseTestCertificate**) são excluídos.</span><span class="sxs-lookup"><span data-stu-id="6fb78-113">Indicates that the test certificates created by the **Install\_PswaWebApplication** cmdlet (with the **UseTestCertificate** parameter) is deleted.</span></span>
<span data-ttu-id="6fb78-114">Somente é removido o certificado de teste com o mesmo nome que aquele criado pelo cmdlet **Install-PswaWebApplication**.</span><span class="sxs-lookup"><span data-stu-id="6fb78-114">Only the test certificate with the same name as the one created by the **Install-PswaWebApplication** cmdlet is removed.</span></span>

|||
|-|-|
| <span data-ttu-id="6fb78-115">Aliases</span><span class="sxs-lookup"><span data-stu-id="6fb78-115">Aliases</span></span>                              | <span data-ttu-id="6fb78-116">none</span><span class="sxs-lookup"><span data-stu-id="6fb78-116">none</span></span>                                 |
| <span data-ttu-id="6fb78-117">Necessário?</span><span class="sxs-lookup"><span data-stu-id="6fb78-117">Required?</span></span>                            | <span data-ttu-id="6fb78-118">false</span><span class="sxs-lookup"><span data-stu-id="6fb78-118">false</span></span>                                |
| <span data-ttu-id="6fb78-119">Posição?</span><span class="sxs-lookup"><span data-stu-id="6fb78-119">Position?</span></span>                            | <span data-ttu-id="6fb78-120">chamada</span><span class="sxs-lookup"><span data-stu-id="6fb78-120">named</span></span>                                |
| <span data-ttu-id="6fb78-121">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="6fb78-121">Default Value</span></span>                        | <span data-ttu-id="6fb78-122">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="6fb78-122">true</span></span>                                 |
| <span data-ttu-id="6fb78-123">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="6fb78-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="6fb78-124">false</span><span class="sxs-lookup"><span data-stu-id="6fb78-124">false</span></span>                                |
| <span data-ttu-id="6fb78-125">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="6fb78-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="6fb78-126">false</span><span class="sxs-lookup"><span data-stu-id="6fb78-126">false</span></span>                                |

### <a name="-webapplicationname-ltstringgt"></a><span data-ttu-id="6fb78-127">-WebApplicationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="6fb78-127">-WebApplicationName &lt;String&gt;</span></span>

<span data-ttu-id="6fb78-128">Especifica o nome do aplicativo Web a ser desinstalado.</span><span class="sxs-lookup"><span data-stu-id="6fb78-128">Specifies the name of the web application to uninstall.</span></span>

|||
|-|-|
| <span data-ttu-id="6fb78-129">Aliases</span><span class="sxs-lookup"><span data-stu-id="6fb78-129">Aliases</span></span>                              | <span data-ttu-id="6fb78-130">none</span><span class="sxs-lookup"><span data-stu-id="6fb78-130">none</span></span>                                 |
| <span data-ttu-id="6fb78-131">Necessário?</span><span class="sxs-lookup"><span data-stu-id="6fb78-131">Required?</span></span>                            | <span data-ttu-id="6fb78-132">false</span><span class="sxs-lookup"><span data-stu-id="6fb78-132">false</span></span>                                |
| <span data-ttu-id="6fb78-133">Posição?</span><span class="sxs-lookup"><span data-stu-id="6fb78-133">Position?</span></span>                            | <span data-ttu-id="6fb78-134">1</span><span class="sxs-lookup"><span data-stu-id="6fb78-134">1</span></span>                                    |
| <span data-ttu-id="6fb78-135">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="6fb78-135">Default Value</span></span>                        | <span data-ttu-id="6fb78-136">pswa</span><span class="sxs-lookup"><span data-stu-id="6fb78-136">pswa</span></span>                                 |
| <span data-ttu-id="6fb78-137">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="6fb78-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="6fb78-138">false</span><span class="sxs-lookup"><span data-stu-id="6fb78-138">false</span></span>                                |
| <span data-ttu-id="6fb78-139">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="6fb78-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="6fb78-140">false</span><span class="sxs-lookup"><span data-stu-id="6fb78-140">false</span></span>                                |

### <a name="-websitename-ltstringgt"></a><span data-ttu-id="6fb78-141">-WebSiteName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="6fb78-141">-WebSiteName &lt;String&gt;</span></span>

<span data-ttu-id="6fb78-142">Especifica o nome do site em que o aplicativo Web está instalado.</span><span class="sxs-lookup"><span data-stu-id="6fb78-142">Specifies the name of the web site where the web application is installed.</span></span>

|||
|-|-|
| <span data-ttu-id="6fb78-143">Aliases</span><span class="sxs-lookup"><span data-stu-id="6fb78-143">Aliases</span></span>                              | <span data-ttu-id="6fb78-144">none</span><span class="sxs-lookup"><span data-stu-id="6fb78-144">none</span></span>                                 |
| <span data-ttu-id="6fb78-145">Necessário?</span><span class="sxs-lookup"><span data-stu-id="6fb78-145">Required?</span></span>                            | <span data-ttu-id="6fb78-146">false</span><span class="sxs-lookup"><span data-stu-id="6fb78-146">false</span></span>                                |
| <span data-ttu-id="6fb78-147">Posição?</span><span class="sxs-lookup"><span data-stu-id="6fb78-147">Position?</span></span>                            | <span data-ttu-id="6fb78-148">chamada</span><span class="sxs-lookup"><span data-stu-id="6fb78-148">named</span></span>                                |
| <span data-ttu-id="6fb78-149">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="6fb78-149">Default Value</span></span>                        | <span data-ttu-id="6fb78-150">Site padrão</span><span class="sxs-lookup"><span data-stu-id="6fb78-150">Default Web Site</span></span>                     |
| <span data-ttu-id="6fb78-151">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="6fb78-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="6fb78-152">false</span><span class="sxs-lookup"><span data-stu-id="6fb78-152">false</span></span>                                |
| <span data-ttu-id="6fb78-153">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="6fb78-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="6fb78-154">false</span><span class="sxs-lookup"><span data-stu-id="6fb78-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="6fb78-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6fb78-155">-Confirm</span></span>

<span data-ttu-id="6fb78-156">Solicita que você confirme antes de executar o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6fb78-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="6fb78-157">Necessário?</span><span class="sxs-lookup"><span data-stu-id="6fb78-157">Required?</span></span>                            | <span data-ttu-id="6fb78-158">false</span><span class="sxs-lookup"><span data-stu-id="6fb78-158">false</span></span>                                |
| <span data-ttu-id="6fb78-159">Posição?</span><span class="sxs-lookup"><span data-stu-id="6fb78-159">Position?</span></span>                            | <span data-ttu-id="6fb78-160">chamada</span><span class="sxs-lookup"><span data-stu-id="6fb78-160">named</span></span>                                |
| <span data-ttu-id="6fb78-161">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="6fb78-161">Default Value</span></span>                        | <span data-ttu-id="6fb78-162">false</span><span class="sxs-lookup"><span data-stu-id="6fb78-162">false</span></span>                                |
| <span data-ttu-id="6fb78-163">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="6fb78-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="6fb78-164">false</span><span class="sxs-lookup"><span data-stu-id="6fb78-164">false</span></span>                                |
| <span data-ttu-id="6fb78-165">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="6fb78-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="6fb78-166">false</span><span class="sxs-lookup"><span data-stu-id="6fb78-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="6fb78-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6fb78-167">-WhatIf</span></span>

<span data-ttu-id="6fb78-168">Mostra o que aconteceria se o cmdlet fosse executado.</span><span class="sxs-lookup"><span data-stu-id="6fb78-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="6fb78-169">O cmdlet não é executado.</span><span class="sxs-lookup"><span data-stu-id="6fb78-169">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="6fb78-170">Necessário?</span><span class="sxs-lookup"><span data-stu-id="6fb78-170">Required?</span></span>                            | <span data-ttu-id="6fb78-171">false</span><span class="sxs-lookup"><span data-stu-id="6fb78-171">false</span></span>                                |
| <span data-ttu-id="6fb78-172">Posição?</span><span class="sxs-lookup"><span data-stu-id="6fb78-172">Position?</span></span>                            | <span data-ttu-id="6fb78-173">chamada</span><span class="sxs-lookup"><span data-stu-id="6fb78-173">named</span></span>                                |
| <span data-ttu-id="6fb78-174">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="6fb78-174">Default Value</span></span>                        | <span data-ttu-id="6fb78-175">false</span><span class="sxs-lookup"><span data-stu-id="6fb78-175">false</span></span>                                |
| <span data-ttu-id="6fb78-176">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="6fb78-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="6fb78-177">false</span><span class="sxs-lookup"><span data-stu-id="6fb78-177">false</span></span>                                |
| <span data-ttu-id="6fb78-178">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="6fb78-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="6fb78-179">false</span><span class="sxs-lookup"><span data-stu-id="6fb78-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="6fb78-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="6fb78-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="6fb78-181">Esse cmdlet oferece suporte aos parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="6fb78-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="6fb78-182">Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6fb78-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="6fb78-183">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="6fb78-183">INPUTS</span></span>

<span data-ttu-id="6fb78-184">Este cmdlet não aceita nenhuma entrada.</span><span class="sxs-lookup"><span data-stu-id="6fb78-184">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="6fb78-185">SAÍDAS</span><span class="sxs-lookup"><span data-stu-id="6fb78-185">OUTPUTS</span></span>

<span data-ttu-id="6fb78-186">Esse cmdlet não retorna nenhuma saída.</span><span class="sxs-lookup"><span data-stu-id="6fb78-186">This cmdlet returns no output.</span></span>

## <a name="examples"></a><span data-ttu-id="6fb78-187">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="6fb78-187">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="6fb78-188">EXEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="6fb78-188">EXAMPLE 1</span></span>

<span data-ttu-id="6fb78-189">Este comando desinstala o aplicativo Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6fb78-189">This command uninstalls the Windows PowerShell Web Application.</span></span>
<span data-ttu-id="6fb78-190">Você poderá usar este cmdlet para desinstalar o aplicativo Web Windows PowerShell se ele tiver sido instalado usando os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="6fb78-190">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values.</span></span>

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="6fb78-191">EXEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="6fb78-191">EXAMPLE 2</span></span>

<span data-ttu-id="6fb78-192">Esse comando desinstala o aplicativo Web Windows PowerShell e exclui o certificado de teste associado ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6fb78-192">This command uninstalls the Windows PowerShell Web Application, and deletes the test certificate associated with the application.</span></span>
<span data-ttu-id="6fb78-193">Você poderá usar este cmdlet para desinstalar o aplicativo Web Windows PowerShell se o tiver instalado usando os valores padrão e tiver criado um certificado de teste.</span><span class="sxs-lookup"><span data-stu-id="6fb78-193">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values and created a test certificate.</span></span>

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="6fb78-194">EXAMPLE 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="6fb78-194">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="6fb78-195">Este comando desinstala o aplicativo Web Windows PowerShell quando um aplicativo e um site personalizados foram especificados durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="6fb78-195">This command uninstalls the Windows PowerShell Web Application when a custom website and application were specified during the install.</span></span>
<span data-ttu-id="6fb78-196">O comando remove o site chamado *MySite* e o aplicativo chamado *TestApplication* e especifica que os certificados de teste associados ao aplicativo também são excluídos.</span><span class="sxs-lookup"><span data-stu-id="6fb78-196">The command removes the website named *MySite* and the application named *TestApplication* and specifies that the test certificates associated with the application are also deleted.</span></span>

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="6fb78-197">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="6fb78-197">Related topics</span></span>

- [<span data-ttu-id="6fb78-198">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="6fb78-198">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="6fb78-199">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="6fb78-199">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="6fb78-200">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="6fb78-200">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="6fb78-201">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="6fb78-201">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="6fb78-202">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="6fb78-202">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)