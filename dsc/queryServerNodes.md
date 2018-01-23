---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC,powershell,configuração,instalação"
title: "Função de DSC para consultar informações do nó do servidor de pull."
ms.openlocfilehash: f97e1d62873fb9e23147ff137468a767455cd82c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-function-to-query-node-information-from-pull-server"></a><span data-ttu-id="2ff14-103">Função de DSC para consultar informações do nó do servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="2ff14-103">DSC function to query node information from pull server.</span></span>

```powershell
function QueryNodeInformation
{
Param (      
       [string] $Uri =
"http://localhost:7070/PSDSCComplianceServer.svc/Status",                         
       [string] $ContentType = "application/json"           
     )

  Write-Host "Querying node information from pull server URI  = $Uri" -ForegroundColor Green

  Write-Host "Querying node status in content type  = $ContentType " -ForegroundColor Green

   $response = Invoke-WebRequest -Uri $Uri -Method Get -ContentType $ContentType -UseDefaultCredentials -Headers 
    @{Accept = $ContentType}

   if($response.StatusCode -ne 200)
 {
     Write-Host "node information was not retrieved." -ForegroundColor Red
 }

 $jsonResponse = ConvertFrom-Json $response.Content

  return $jsonResponse
}
```

<span data-ttu-id="2ff14-104">Substitua o parâmetro `Uri` pelo URI para o servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="2ff14-104">Replace the `Uri` parameter with the URI for your pull server.</span></span> <span data-ttu-id="2ff14-105">Se quiser as informações do nó em formato XML, defina `ContentType` como `application/xml`.</span><span class="sxs-lookup"><span data-stu-id="2ff14-105">If you want the node information in XML format, set `ContentType` to `application/xml`.</span></span>

<span data-ttu-id="2ff14-106">Para recuperar as informações do nó do parâmetro `$json`, use o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2ff14-106">To retrieve the node information from the `$json` parameter, use the following:</span></span>

```powershell
$json = QueryNodeInformation –Uri http://localhost:7070/PSDSCComplianceServer.svc/Status 

$json.value | Format-Table TargetName, ConfigurationId, ServerChecksum, NodeCompliant, LastComplianceTime, StatusCode
```

