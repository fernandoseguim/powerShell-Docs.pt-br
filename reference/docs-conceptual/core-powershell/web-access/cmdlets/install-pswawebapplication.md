---
ms.topic: reference
keywords: powershell, cmdlet
ms.date: 12/12/2016
title: Install-PswaWebApplication
ms.openlocfilehash: 29e074b75eeb387640831229c63142e6dd5e991a
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268292"
---
# <a name="install-pswawebapplication"></a><span data-ttu-id="08418-103">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="08418-103">Install-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="08418-104">SINOPSE</span><span class="sxs-lookup"><span data-stu-id="08418-104">SYNOPSIS</span></span>

<span data-ttu-id="08418-105">Configura o aplicativo Web Windows PowerShell Web Access no IIS.</span><span class="sxs-lookup"><span data-stu-id="08418-105">Configures the Windows PowerShell Web Access web application in IIS.</span></span>

## <a name="syntax"></a><span data-ttu-id="08418-106">SINTAXE</span><span class="sxs-lookup"><span data-stu-id="08418-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="08418-107">Padrão</span><span class="sxs-lookup"><span data-stu-id="08418-107">Default</span></span>
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="08418-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="08418-108">DESCRIPTION</span></span>

<span data-ttu-id="08418-109">O cmdlet **Install-PswaWebApplication** configura o aplicativo Web Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="08418-109">The **Install-PswaWebApplication** cmdlet configures Windows PowerShell Web Access web application.</span></span>
<span data-ttu-id="08418-110">Este cmdlet instala o aplicativo Web, associa-o a um site e, opcionalmente, cria um certificado SSL de teste usando o parâmetro **useTestCertificate**.</span><span class="sxs-lookup"><span data-stu-id="08418-110">This cmdlet installs the web application, associates it with a web site, and optionally creates a test SSL certificate using the **useTestCertificate** parameter.</span></span> <span data-ttu-id="08418-111">Por motivo de segurança, os administradores da Web não devem usar um certificado de teste para ambientes de produção.</span><span class="sxs-lookup"><span data-stu-id="08418-111">For security reasons web administrators should not use a test certificate for production environments.</span></span>

## <a name="parameters"></a><span data-ttu-id="08418-112">PARÂMETROS</span><span class="sxs-lookup"><span data-stu-id="08418-112">PARAMETERS</span></span>

### <a name="-usetestcertificate"></a><span data-ttu-id="08418-113">-UseTestCertificate</span><span class="sxs-lookup"><span data-stu-id="08418-113">-UseTestCertificate</span></span>

<span data-ttu-id="08418-114">Especifica que um certificado de teste é criado.</span><span class="sxs-lookup"><span data-stu-id="08418-114">Specifies that a test certificate is created.</span></span> <span data-ttu-id="08418-115">Se esse parâmetro for definido como true, esse cmdlet criará um certificado de teste e configurará o aplicativo Web Windows PowerShell Web Access para usar o certificado para solicitações HTTPS.</span><span class="sxs-lookup"><span data-stu-id="08418-115">If this parameter is set to true, then this cmdlet creates a test certificate and configures the Windows PowerShell Web Access web application to use the certificate for HTTPS requests.</span></span> <span data-ttu-id="08418-116">Se esse parâmetro for definido como false, não serão criados certificados nem associações.</span><span class="sxs-lookup"><span data-stu-id="08418-116">If this parameter is set to false, then no certificate or binding is created.</span></span> <span data-ttu-id="08418-117">Defina esse valor como false se outro certificado for usado para o Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="08418-117">Set this value to false if another certificate is used for Windows PowerShell Web Access.</span></span>

|||
|-|-|
| <span data-ttu-id="08418-118">Aliases</span><span class="sxs-lookup"><span data-stu-id="08418-118">Aliases</span></span>                              | <span data-ttu-id="08418-119">none</span><span class="sxs-lookup"><span data-stu-id="08418-119">none</span></span>                                 |
| <span data-ttu-id="08418-120">Necessário?</span><span class="sxs-lookup"><span data-stu-id="08418-120">Required?</span></span>                            | <span data-ttu-id="08418-121">false</span><span class="sxs-lookup"><span data-stu-id="08418-121">false</span></span>                                |
| <span data-ttu-id="08418-122">Posição?</span><span class="sxs-lookup"><span data-stu-id="08418-122">Position?</span></span>                            | <span data-ttu-id="08418-123">chamada</span><span class="sxs-lookup"><span data-stu-id="08418-123">named</span></span>                                |
| <span data-ttu-id="08418-124">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="08418-124">Default Value</span></span>                        | <span data-ttu-id="08418-125">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="08418-125">true</span></span>                                 |
| <span data-ttu-id="08418-126">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="08418-126">Accept Pipeline Input?</span></span>               | <span data-ttu-id="08418-127">false</span><span class="sxs-lookup"><span data-stu-id="08418-127">false</span></span>                                |
| <span data-ttu-id="08418-128">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="08418-128">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="08418-129">false</span><span class="sxs-lookup"><span data-stu-id="08418-129">false</span></span>                                |

### <a name="-webapplicationname"></a><span data-ttu-id="08418-130">-WebApplicationName</span><span class="sxs-lookup"><span data-stu-id="08418-130">-WebApplicationName</span></span>

<span data-ttu-id="08418-131">Especifica o nome do seu aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="08418-131">Specifies the name for your web application.</span></span> <span data-ttu-id="08418-132">Essa opção é exibida como a última parte da URL do Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="08418-132">This is displayed as the last part of the Windows PowerShell Web Access URL.</span></span>

|||
|-|-|
| <span data-ttu-id="08418-133">Aliases</span><span class="sxs-lookup"><span data-stu-id="08418-133">Aliases</span></span>                              | <span data-ttu-id="08418-134">none</span><span class="sxs-lookup"><span data-stu-id="08418-134">none</span></span>                                 |
| <span data-ttu-id="08418-135">Necessário?</span><span class="sxs-lookup"><span data-stu-id="08418-135">Required?</span></span>                            | <span data-ttu-id="08418-136">false</span><span class="sxs-lookup"><span data-stu-id="08418-136">false</span></span>                                |
| <span data-ttu-id="08418-137">Posição?</span><span class="sxs-lookup"><span data-stu-id="08418-137">Position?</span></span>                            | <span data-ttu-id="08418-138">1</span><span class="sxs-lookup"><span data-stu-id="08418-138">1</span></span>                                    |
| <span data-ttu-id="08418-139">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="08418-139">Default Value</span></span>                        | <span data-ttu-id="08418-140">pswa</span><span class="sxs-lookup"><span data-stu-id="08418-140">pswa</span></span>                                 |
| <span data-ttu-id="08418-141">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="08418-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="08418-142">false</span><span class="sxs-lookup"><span data-stu-id="08418-142">false</span></span>                                |
| <span data-ttu-id="08418-143">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="08418-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="08418-144">false</span><span class="sxs-lookup"><span data-stu-id="08418-144">false</span></span>                                |

### <a name="-websitename"></a><span data-ttu-id="08418-145">-WebSiteName</span><span class="sxs-lookup"><span data-stu-id="08418-145">-WebSiteName</span></span>

<span data-ttu-id="08418-146">Especifica o nome do site do Servidor Web (IIS) no qual este aplicativo Web Windows PowerShell Web Access será instalado.</span><span class="sxs-lookup"><span data-stu-id="08418-146">Specifies the name of the Web Server (IIS) website on which to install this Windows PowerShell Web Access web application.</span></span>

|||
|-|-|
| <span data-ttu-id="08418-147">Aliases</span><span class="sxs-lookup"><span data-stu-id="08418-147">Aliases</span></span>                              | <span data-ttu-id="08418-148">none</span><span class="sxs-lookup"><span data-stu-id="08418-148">none</span></span>                                 |
| <span data-ttu-id="08418-149">Necessário?</span><span class="sxs-lookup"><span data-stu-id="08418-149">Required?</span></span>                            | <span data-ttu-id="08418-150">false</span><span class="sxs-lookup"><span data-stu-id="08418-150">false</span></span>                                |
| <span data-ttu-id="08418-151">Posição?</span><span class="sxs-lookup"><span data-stu-id="08418-151">Position?</span></span>                            | <span data-ttu-id="08418-152">chamada</span><span class="sxs-lookup"><span data-stu-id="08418-152">named</span></span>                                |
| <span data-ttu-id="08418-153">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="08418-153">Default Value</span></span>                        | <span data-ttu-id="08418-154">Site padrão</span><span class="sxs-lookup"><span data-stu-id="08418-154">Default Web Site</span></span>                     |
| <span data-ttu-id="08418-155">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="08418-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="08418-156">false</span><span class="sxs-lookup"><span data-stu-id="08418-156">false</span></span>                                |
| <span data-ttu-id="08418-157">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="08418-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="08418-158">false</span><span class="sxs-lookup"><span data-stu-id="08418-158">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="08418-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="08418-159">-Confirm</span></span>

<span data-ttu-id="08418-160">Solicita que você confirme antes de executar o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="08418-160">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="08418-161">Necessário?</span><span class="sxs-lookup"><span data-stu-id="08418-161">Required?</span></span>                            | <span data-ttu-id="08418-162">false</span><span class="sxs-lookup"><span data-stu-id="08418-162">false</span></span>                                |
| <span data-ttu-id="08418-163">Posição?</span><span class="sxs-lookup"><span data-stu-id="08418-163">Position?</span></span>                            | <span data-ttu-id="08418-164">chamada</span><span class="sxs-lookup"><span data-stu-id="08418-164">named</span></span>                                |
| <span data-ttu-id="08418-165">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="08418-165">Default Value</span></span>                        | <span data-ttu-id="08418-166">false</span><span class="sxs-lookup"><span data-stu-id="08418-166">false</span></span>                                |
| <span data-ttu-id="08418-167">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="08418-167">Accept Pipeline Input?</span></span>               | <span data-ttu-id="08418-168">false</span><span class="sxs-lookup"><span data-stu-id="08418-168">false</span></span>                                |
| <span data-ttu-id="08418-169">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="08418-169">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="08418-170">false</span><span class="sxs-lookup"><span data-stu-id="08418-170">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="08418-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="08418-171">-WhatIf</span></span>

<span data-ttu-id="08418-172">Mostra o que aconteceria se o cmdlet fosse executado.</span><span class="sxs-lookup"><span data-stu-id="08418-172">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="08418-173">O cmdlet não é executado.</span><span class="sxs-lookup"><span data-stu-id="08418-173">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="08418-174">Necessário?</span><span class="sxs-lookup"><span data-stu-id="08418-174">Required?</span></span>                            | <span data-ttu-id="08418-175">false</span><span class="sxs-lookup"><span data-stu-id="08418-175">false</span></span>                                |
| <span data-ttu-id="08418-176">Posição?</span><span class="sxs-lookup"><span data-stu-id="08418-176">Position?</span></span>                            | <span data-ttu-id="08418-177">chamada</span><span class="sxs-lookup"><span data-stu-id="08418-177">named</span></span>                                |
| <span data-ttu-id="08418-178">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="08418-178">Default Value</span></span>                        | <span data-ttu-id="08418-179">false</span><span class="sxs-lookup"><span data-stu-id="08418-179">false</span></span>                                |
| <span data-ttu-id="08418-180">Aceitar entrada do pipeline?</span><span class="sxs-lookup"><span data-stu-id="08418-180">Accept Pipeline Input?</span></span>               | <span data-ttu-id="08418-181">false</span><span class="sxs-lookup"><span data-stu-id="08418-181">false</span></span>                                |
| <span data-ttu-id="08418-182">Aceitar caracteres curinga?</span><span class="sxs-lookup"><span data-stu-id="08418-182">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="08418-183">false</span><span class="sxs-lookup"><span data-stu-id="08418-183">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="08418-184">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="08418-184">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="08418-185">Esse cmdlet oferece suporte aos parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="08418-185">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span> <span data-ttu-id="08418-186">Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="08418-186">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="08418-187">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="08418-187">INPUTS</span></span>

<span data-ttu-id="08418-188">Este cmdlet não aceita nenhuma entrada.</span><span class="sxs-lookup"><span data-stu-id="08418-188">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="08418-189">SAÍDAS</span><span class="sxs-lookup"><span data-stu-id="08418-189">OUTPUTS</span></span>

<span data-ttu-id="08418-190">Este cmdlet não produz nenhuma saída.</span><span class="sxs-lookup"><span data-stu-id="08418-190">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="08418-191">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="08418-191">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="08418-192">EXEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="08418-192">EXAMPLE 1</span></span>

<span data-ttu-id="08418-193">Este exemplo instala o aplicativo Web PSWA usando os valores padrão para os parâmetros **WebApplicationName** (*pswa*) e **WebSiteName** (*Site Padrão*).</span><span class="sxs-lookup"><span data-stu-id="08418-193">This example installs the PSWA web application using the default values for the **WebApplicationName** (*pswa*) and **WebSiteName** (*Default Web Site*) parameters .</span></span>

```
Install-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="08418-194">EXEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="08418-194">EXAMPLE 2</span></span>

<span data-ttu-id="08418-195">Este exemplo instala o aplicativo Web PSWA com um certificado de teste e usando os valores padrão para os parâmetros **WebApplicationName** e **WebSiteName**.</span><span class="sxs-lookup"><span data-stu-id="08418-195">This example installs the PSWA web application with a test certificate, and using the default values for the **WebApplicationName** and **WebSiteName** parameters.</span></span>

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="08418-196">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="08418-196">Related topics</span></span>

- [<span data-ttu-id="08418-197">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="08418-197">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="08418-198">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="08418-198">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="08418-199">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="08418-199">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="08418-200">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="08418-200">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)