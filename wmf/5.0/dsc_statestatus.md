---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: b279d388754c5ee42215f21317f7b3d8089b7608
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093874"
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="bfcd7-102">Representação de estado e status consistente e unificada</span><span class="sxs-lookup"><span data-stu-id="bfcd7-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="bfcd7-103">Uma série de melhorias foram feitas nessa versão em relação ao estado do LCM e ao status do DSC internos das automações.</span><span class="sxs-lookup"><span data-stu-id="bfcd7-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="bfcd7-104">Entre elas estão representações de estado e status consistentes e unificadas, propriedade datetime gerenciável de objetos de status retornados pelo cmdlet `Get-DscConfigurationStatus` e melhoria na propriedade de detalhes do estado do LCM retornada pelo cmdlet `Get-DscLocalConfigurationManager`.</span><span class="sxs-lookup"><span data-stu-id="bfcd7-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by `Get-DscConfigurationStatus` cmdlet and enhanced LCM state details property returned by `Get-DscLocalConfigurationManager` cmdlet.</span></span>

<span data-ttu-id="bfcd7-105">A representação do estado do LCM e do status de operação do DSC foi revisitada e unificada de acordo com as seguintes regras:</span><span class="sxs-lookup"><span data-stu-id="bfcd7-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>

1. <span data-ttu-id="bfcd7-106">O recurso NotProcessed não afeta o estado do LCM e o status do DSC.</span><span class="sxs-lookup"><span data-stu-id="bfcd7-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
1. <span data-ttu-id="bfcd7-107">O LCM interrompe o processamento de mais recursos quando encontra um recurso que solicita a reinicialização.</span><span class="sxs-lookup"><span data-stu-id="bfcd7-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
1. <span data-ttu-id="bfcd7-108">Um recurso que solicita a reinicialização não fica no estado desejado até que realmente ocorra uma reinicialização.</span><span class="sxs-lookup"><span data-stu-id="bfcd7-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
1. <span data-ttu-id="bfcd7-109">Depois de encontrar um recurso que falha, o LCM mantém o processamento de mais recursos desde que eles não sejam dependentes da primeira falha.</span><span class="sxs-lookup"><span data-stu-id="bfcd7-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
1. <span data-ttu-id="bfcd7-110">O status geral retornado pelo cmdlet `Get-DscConfigurationStatus` é o superconjunto de todos os status de recursos.</span><span class="sxs-lookup"><span data-stu-id="bfcd7-110">The overall status returned by `Get-DscConfigurationStatus` cmdlet is the super set of all resources' status.</span></span>
1. <span data-ttu-id="bfcd7-111">O estado de PendingReboot é um superconjunto do estado de PendingConfiguration.</span><span class="sxs-lookup"><span data-stu-id="bfcd7-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

   <span data-ttu-id="bfcd7-112">A tabela abaixo ilustra as propriedades relacionadas a estado e status resultantes em alguns cenários típicos.</span><span class="sxs-lookup"><span data-stu-id="bfcd7-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

   | <span data-ttu-id="bfcd7-113">Cenário</span><span class="sxs-lookup"><span data-stu-id="bfcd7-113">Scenario</span></span>                    | <span data-ttu-id="bfcd7-114">LCMState</span><span class="sxs-lookup"><span data-stu-id="bfcd7-114">LCMState</span></span>       | <span data-ttu-id="bfcd7-115">Status</span><span class="sxs-lookup"><span data-stu-id="bfcd7-115">Status</span></span> | <span data-ttu-id="bfcd7-116">Reinicialização solicitada</span><span class="sxs-lookup"><span data-stu-id="bfcd7-116">Reboot Requested</span></span>  | <span data-ttu-id="bfcd7-117">ResourcesInDesiredState</span><span class="sxs-lookup"><span data-stu-id="bfcd7-117">ResourcesInDesiredState</span></span>  | <span data-ttu-id="bfcd7-118">ResourcesNotInDesiredState</span><span class="sxs-lookup"><span data-stu-id="bfcd7-118">ResourcesNotInDesiredState</span></span> |
   |---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
   | <span data-ttu-id="bfcd7-119">S**^**</span><span class="sxs-lookup"><span data-stu-id="bfcd7-119">S**^**</span></span>                          | <span data-ttu-id="bfcd7-120">Idle</span><span class="sxs-lookup"><span data-stu-id="bfcd7-120">Idle</span></span>                 | <span data-ttu-id="bfcd7-121">Sucesso</span><span class="sxs-lookup"><span data-stu-id="bfcd7-121">Success</span></span>    | <span data-ttu-id="bfcd7-122">$false</span><span class="sxs-lookup"><span data-stu-id="bfcd7-122">$false</span></span>        | <span data-ttu-id="bfcd7-123">S</span><span class="sxs-lookup"><span data-stu-id="bfcd7-123">S</span></span>                            | <span data-ttu-id="bfcd7-124">$null</span><span class="sxs-lookup"><span data-stu-id="bfcd7-124">$null</span></span>                          |
   | <span data-ttu-id="bfcd7-125">F**^**</span><span class="sxs-lookup"><span data-stu-id="bfcd7-125">F**^**</span></span>                          | <span data-ttu-id="bfcd7-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="bfcd7-126">PendingConfiguration</span></span> | <span data-ttu-id="bfcd7-127">Falha</span><span class="sxs-lookup"><span data-stu-id="bfcd7-127">Failure</span></span>    | <span data-ttu-id="bfcd7-128">$false</span><span class="sxs-lookup"><span data-stu-id="bfcd7-128">$false</span></span>        | <span data-ttu-id="bfcd7-129">$null</span><span class="sxs-lookup"><span data-stu-id="bfcd7-129">$null</span></span>                        | <span data-ttu-id="bfcd7-130">F</span><span class="sxs-lookup"><span data-stu-id="bfcd7-130">F</span></span>                              |
   | <span data-ttu-id="bfcd7-131">S,F</span><span class="sxs-lookup"><span data-stu-id="bfcd7-131">S,F</span></span>                             | <span data-ttu-id="bfcd7-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="bfcd7-132">PendingConfiguration</span></span> | <span data-ttu-id="bfcd7-133">Falha</span><span class="sxs-lookup"><span data-stu-id="bfcd7-133">Failure</span></span>    | <span data-ttu-id="bfcd7-134">$false</span><span class="sxs-lookup"><span data-stu-id="bfcd7-134">$false</span></span>        | <span data-ttu-id="bfcd7-135">S</span><span class="sxs-lookup"><span data-stu-id="bfcd7-135">S</span></span>                            | <span data-ttu-id="bfcd7-136">F</span><span class="sxs-lookup"><span data-stu-id="bfcd7-136">F</span></span>                              |
   | <span data-ttu-id="bfcd7-137">F,S</span><span class="sxs-lookup"><span data-stu-id="bfcd7-137">F,S</span></span>                             | <span data-ttu-id="bfcd7-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="bfcd7-138">PendingConfiguration</span></span> | <span data-ttu-id="bfcd7-139">Falha</span><span class="sxs-lookup"><span data-stu-id="bfcd7-139">Failure</span></span>    | <span data-ttu-id="bfcd7-140">$false</span><span class="sxs-lookup"><span data-stu-id="bfcd7-140">$false</span></span>        | <span data-ttu-id="bfcd7-141">S</span><span class="sxs-lookup"><span data-stu-id="bfcd7-141">S</span></span>                            | <span data-ttu-id="bfcd7-142">F</span><span class="sxs-lookup"><span data-stu-id="bfcd7-142">F</span></span>                              |
   | <span data-ttu-id="bfcd7-143">S<sub>1</sub>, F, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="bfcd7-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="bfcd7-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="bfcd7-144">PendingConfiguration</span></span> | <span data-ttu-id="bfcd7-145">Falha</span><span class="sxs-lookup"><span data-stu-id="bfcd7-145">Failure</span></span>    | <span data-ttu-id="bfcd7-146">$false</span><span class="sxs-lookup"><span data-stu-id="bfcd7-146">$false</span></span>        | <span data-ttu-id="bfcd7-147">S<sub>1</sub>, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="bfcd7-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="bfcd7-148">F</span><span class="sxs-lookup"><span data-stu-id="bfcd7-148">F</span></span>                              |
   | <span data-ttu-id="bfcd7-149">F<sub>1</sub>, S, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="bfcd7-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="bfcd7-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="bfcd7-150">PendingConfiguration</span></span> | <span data-ttu-id="bfcd7-151">Falha</span><span class="sxs-lookup"><span data-stu-id="bfcd7-151">Failure</span></span>    | <span data-ttu-id="bfcd7-152">$false</span><span class="sxs-lookup"><span data-stu-id="bfcd7-152">$false</span></span>        | <span data-ttu-id="bfcd7-153">S</span><span class="sxs-lookup"><span data-stu-id="bfcd7-153">S</span></span>                            | <span data-ttu-id="bfcd7-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="bfcd7-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
   | <span data-ttu-id="bfcd7-155">S, r</span><span class="sxs-lookup"><span data-stu-id="bfcd7-155">S, r</span></span>                            | <span data-ttu-id="bfcd7-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="bfcd7-156">PendingReboot</span></span>        | <span data-ttu-id="bfcd7-157">Sucesso</span><span class="sxs-lookup"><span data-stu-id="bfcd7-157">Success</span></span>    | <span data-ttu-id="bfcd7-158">$true</span><span class="sxs-lookup"><span data-stu-id="bfcd7-158">$true</span></span>         | <span data-ttu-id="bfcd7-159">S</span><span class="sxs-lookup"><span data-stu-id="bfcd7-159">S</span></span>                            | <span data-ttu-id="bfcd7-160">r</span><span class="sxs-lookup"><span data-stu-id="bfcd7-160">r</span></span>                              |
   | <span data-ttu-id="bfcd7-161">F, r</span><span class="sxs-lookup"><span data-stu-id="bfcd7-161">F, r</span></span>                            | <span data-ttu-id="bfcd7-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="bfcd7-162">PendingReboot</span></span>        | <span data-ttu-id="bfcd7-163">Falha</span><span class="sxs-lookup"><span data-stu-id="bfcd7-163">Failure</span></span>    | <span data-ttu-id="bfcd7-164">$true</span><span class="sxs-lookup"><span data-stu-id="bfcd7-164">$true</span></span>         | <span data-ttu-id="bfcd7-165">$null</span><span class="sxs-lookup"><span data-stu-id="bfcd7-165">$null</span></span>                        | <span data-ttu-id="bfcd7-166">F, r</span><span class="sxs-lookup"><span data-stu-id="bfcd7-166">F, r</span></span>                           |
   | <span data-ttu-id="bfcd7-167">r, S</span><span class="sxs-lookup"><span data-stu-id="bfcd7-167">r, S</span></span>                            | <span data-ttu-id="bfcd7-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="bfcd7-168">PendingReboot</span></span>        | <span data-ttu-id="bfcd7-169">Sucesso</span><span class="sxs-lookup"><span data-stu-id="bfcd7-169">Success</span></span>    | <span data-ttu-id="bfcd7-170">$true</span><span class="sxs-lookup"><span data-stu-id="bfcd7-170">$true</span></span>         | <span data-ttu-id="bfcd7-171">$null</span><span class="sxs-lookup"><span data-stu-id="bfcd7-171">$null</span></span>                        | <span data-ttu-id="bfcd7-172">r</span><span class="sxs-lookup"><span data-stu-id="bfcd7-172">r</span></span>                              |
   | <span data-ttu-id="bfcd7-173">r, F</span><span class="sxs-lookup"><span data-stu-id="bfcd7-173">r, F</span></span>                            | <span data-ttu-id="bfcd7-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="bfcd7-174">PendingReboot</span></span>        | <span data-ttu-id="bfcd7-175">Sucesso</span><span class="sxs-lookup"><span data-stu-id="bfcd7-175">Success</span></span>    | <span data-ttu-id="bfcd7-176">$true</span><span class="sxs-lookup"><span data-stu-id="bfcd7-176">$true</span></span>         | <span data-ttu-id="bfcd7-177">$null</span><span class="sxs-lookup"><span data-stu-id="bfcd7-177">$null</span></span>                        | <span data-ttu-id="bfcd7-178">r</span><span class="sxs-lookup"><span data-stu-id="bfcd7-178">r</span></span>                              |

   <span data-ttu-id="bfcd7-179">^
   S<sub>i</sub>: uma série de recursos que são aplicadas com êxito<sub>i</sub>: uma série de recursos que não são aplicados com êxito r: um recurso que exige reinicialização \*</span><span class="sxs-lookup"><span data-stu-id="bfcd7-179">^
   S<sub>i</sub>: A series of resources that applied successfully F<sub>i</sub>: A series of resources that applied unsuccessfully r: A resource that requires reboot \*</span></span>

   ```powershell
   $LCMState = (Get-DscLocalConfigurationManager).LCMState
   $Status = (Get-DscConfigurationStatus).Status

   $RebootRequested = (Get-DscConfigurationStatus).RebootRequested

   $ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

   $ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
   ```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="bfcd7-180">Melhorias no cmdlet Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="bfcd7-180">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="bfcd7-181">Foram feitas algumas melhorias ao cmdlet `Get-DscConfigurationStatus` nesta versão.</span><span class="sxs-lookup"><span data-stu-id="bfcd7-181">A few enhancements have been made to `Get-DscConfigurationStatus` cmdlet in this release.</span></span> <span data-ttu-id="bfcd7-182">Anteriormente, a propriedade StartDate de objetos retornados pelo cmdlet era do tipo String.</span><span class="sxs-lookup"><span data-stu-id="bfcd7-182">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="bfcd7-183">Agora, ela é do tipo Datetime, o que permite uma seleção e filtragem complexas, facilitando-as com base nas propriedades intrínsecas de um objeto Datetime.</span><span class="sxs-lookup"><span data-stu-id="bfcd7-183">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>

```powershell
(Get-DscConfigurationStatus).StartDate | Format-List *
DateTime : Friday, November 13, 2015 1:39:44 PM
Date : 11/13/2015 12:00:00 AM
Day : 13
DayOfWeek : Friday
DayOfYear : 317
Hour : 13
Kind : Local
Millisecond : 886
Minute : 39
Month : 11
Second : 44
Ticks : 635830187848860000
TimeOfDay : 13:39:44.8860000
Year : 2015
```

<span data-ttu-id="bfcd7-184">Veja a seguir um exemplo que retorna todos os registros de operação do DSC ocorridos no mesmo dia da semana que hoje.</span><span class="sxs-lookup"><span data-stu-id="bfcd7-184">Following is an example that returns all DSC operation records happened on the same day of week as today.</span></span>

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="bfcd7-185">Registros de operações que não fazem alterações à configuração do nó (ou seja, operações somente leitura) são eliminados.</span><span class="sxs-lookup"><span data-stu-id="bfcd7-185">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="bfcd7-186">Portanto, as operações `Test-DscConfiguration` e `Get-DscConfiguration` não são mais adulteradas em objetos retornados do cmdlet `Get-DscConfigurationStatus`.</span><span class="sxs-lookup"><span data-stu-id="bfcd7-186">Therefore, `Test-DscConfiguration`, `Get-DscConfiguration` operations are no longer adulterated in returned objects from `Get-DscConfigurationStatus` cmdlet.</span></span>
<span data-ttu-id="bfcd7-187">Registros da operação de definição de metaconfiguração são adicionados ao retorno pelo cmdlet `Get-DscConfigurationStatus`.</span><span class="sxs-lookup"><span data-stu-id="bfcd7-187">Records of meta configuration setting operation is added to the return of `Get-DscConfigurationStatus` cmdlet.</span></span>

<span data-ttu-id="bfcd7-188">Apresentamos a seguir um exemplo de resultado retornado pelo cmdlet `Get-DscConfigurationStatus` –All.</span><span class="sxs-lookup"><span data-stu-id="bfcd7-188">Following is an example of result returned from `Get-DscConfigurationStatus` –All cmdlet.</span></span>

```output
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="bfcd7-189">Melhoria no cmdlet Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="bfcd7-189">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>

<span data-ttu-id="bfcd7-190">Um novo campo de LCMStateDetail é adicionado ao objeto retornado pelo cmdlet `Get-DscLocalConfigurationManager`.</span><span class="sxs-lookup"><span data-stu-id="bfcd7-190">A new field of LCMStateDetail is added to the object returned from `Get-DscLocalConfigurationManager` cmdlet.</span></span> <span data-ttu-id="bfcd7-191">Este campo é populado quando LCMState é “Ocupado”.</span><span class="sxs-lookup"><span data-stu-id="bfcd7-191">This field is populated when LCMState is "Busy".</span></span> <span data-ttu-id="bfcd7-192">Ele pode ser recuperado pelo seguinte cmdlet:</span><span class="sxs-lookup"><span data-stu-id="bfcd7-192">It can be retrieved by following cmdlet:</span></span>

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="bfcd7-193">Veja a seguir um exemplo de saída de um monitoramento contínuo em uma configuração que exige duas reinicializações em um nó remoto.</span><span class="sxs-lookup"><span data-stu-id="bfcd7-193">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>

```output
Start a configuration that requires two reboots

Monitor LCM State:
LCM State: Busy, LCM is applying a new configuration.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: Idle,
LCM State: Busy, LCM is performing a consistency check.
LCM State: Idle,
```