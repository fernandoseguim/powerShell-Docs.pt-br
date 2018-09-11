---
ms.date: 06/12/2017
keywords: wmf,powershell,instalação
ms.openlocfilehash: ff2c2bd7369893d72db001ecabf63991ded0bfd5
ms.sourcegitcommit: ac20e0faaa37142e9c6e4507a21df2f4a3fdbece
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339864"
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="463f9-102">Representação de estado e status consistente e unificada</span><span class="sxs-lookup"><span data-stu-id="463f9-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="463f9-103">Uma série de melhorias foram feitas nessa versão em relação ao estado do LCM e ao status do DSC internos das automações.</span><span class="sxs-lookup"><span data-stu-id="463f9-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="463f9-104">Entre elas estão representações de estado e status consistentes e unificadas, propriedade datetime gerenciável de objetos de status retornados pelo cmdlet `Get-DscConfigurationStatus` e melhoria na propriedade de detalhes do estado do LCM retornada pelo cmdlet `Get-DscLocalConfigurationManager`.</span><span class="sxs-lookup"><span data-stu-id="463f9-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by `Get-DscConfigurationStatus` cmdlet and enhanced LCM state details property returned by `Get-DscLocalConfigurationManager` cmdlet.</span></span>

<span data-ttu-id="463f9-105">A representação do estado do LCM e do status de operação do DSC foi revisitada e unificada de acordo com as seguintes regras:</span><span class="sxs-lookup"><span data-stu-id="463f9-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>

1. <span data-ttu-id="463f9-106">O recurso NotProcessed não afeta o estado do LCM e o status do DSC.</span><span class="sxs-lookup"><span data-stu-id="463f9-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
2. <span data-ttu-id="463f9-107">O LCM interrompe o processamento de mais recursos quando encontra um recurso que solicita a reinicialização.</span><span class="sxs-lookup"><span data-stu-id="463f9-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
3. <span data-ttu-id="463f9-108">Um recurso que solicita a reinicialização não fica no estado desejado até que realmente ocorra uma reinicialização.</span><span class="sxs-lookup"><span data-stu-id="463f9-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
4. <span data-ttu-id="463f9-109">Depois de encontrar um recurso que falha, o LCM mantém o processamento de mais recursos desde que eles não sejam dependentes da primeira falha.</span><span class="sxs-lookup"><span data-stu-id="463f9-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
5. <span data-ttu-id="463f9-110">O status geral retornado pelo cmdlet `Get-DscConfigurationStatus` é o superconjunto de todos os status de recursos.</span><span class="sxs-lookup"><span data-stu-id="463f9-110">The overall status returned by `Get-DscConfigurationStatus` cmdlet is the super set of all resources' status.</span></span>
6. <span data-ttu-id="463f9-111">O estado de PendingReboot é um superconjunto do estado de PendingConfiguration.</span><span class="sxs-lookup"><span data-stu-id="463f9-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

<span data-ttu-id="463f9-112">A tabela abaixo ilustra as propriedades relacionadas a estado e status resultantes em alguns cenários típicos.</span><span class="sxs-lookup"><span data-stu-id="463f9-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

| <span data-ttu-id="463f9-113">Cenário</span><span class="sxs-lookup"><span data-stu-id="463f9-113">Scenario</span></span>                        | <span data-ttu-id="463f9-114">LCMState</span><span class="sxs-lookup"><span data-stu-id="463f9-114">LCMState</span></span>             | <span data-ttu-id="463f9-115">Status</span><span class="sxs-lookup"><span data-stu-id="463f9-115">Status</span></span>     | <span data-ttu-id="463f9-116">Reinicialização solicitada</span><span class="sxs-lookup"><span data-stu-id="463f9-116">Reboot Requested</span></span> | <span data-ttu-id="463f9-117">ResourcesInDesiredState</span><span class="sxs-lookup"><span data-stu-id="463f9-117">ResourcesInDesiredState</span></span>   | <span data-ttu-id="463f9-118">ResourcesNotInDesiredState</span><span class="sxs-lookup"><span data-stu-id="463f9-118">ResourcesNotInDesiredState</span></span> |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| <span data-ttu-id="463f9-119">S<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="463f9-119">S<sub>i</sub></span></span>                   | <span data-ttu-id="463f9-120">Idle</span><span class="sxs-lookup"><span data-stu-id="463f9-120">Idle</span></span>                 | <span data-ttu-id="463f9-121">Sucesso</span><span class="sxs-lookup"><span data-stu-id="463f9-121">Success</span></span>    | <span data-ttu-id="463f9-122">$false</span><span class="sxs-lookup"><span data-stu-id="463f9-122">$false</span></span>        | <span data-ttu-id="463f9-123">S</span><span class="sxs-lookup"><span data-stu-id="463f9-123">S</span></span>                            | <span data-ttu-id="463f9-124">$null</span><span class="sxs-lookup"><span data-stu-id="463f9-124">$null</span></span>                          |
| <span data-ttu-id="463f9-125">F<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="463f9-125">F<sub>i</sub></span></span>                   | <span data-ttu-id="463f9-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="463f9-126">PendingConfiguration</span></span> | <span data-ttu-id="463f9-127">Falha</span><span class="sxs-lookup"><span data-stu-id="463f9-127">Failure</span></span>    | <span data-ttu-id="463f9-128">$false</span><span class="sxs-lookup"><span data-stu-id="463f9-128">$false</span></span>        | <span data-ttu-id="463f9-129">$null</span><span class="sxs-lookup"><span data-stu-id="463f9-129">$null</span></span>                        | <span data-ttu-id="463f9-130">F</span><span class="sxs-lookup"><span data-stu-id="463f9-130">F</span></span>                              |
| <span data-ttu-id="463f9-131">S,F</span><span class="sxs-lookup"><span data-stu-id="463f9-131">S,F</span></span>                             | <span data-ttu-id="463f9-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="463f9-132">PendingConfiguration</span></span> | <span data-ttu-id="463f9-133">Falha</span><span class="sxs-lookup"><span data-stu-id="463f9-133">Failure</span></span>    | <span data-ttu-id="463f9-134">$false</span><span class="sxs-lookup"><span data-stu-id="463f9-134">$false</span></span>        | <span data-ttu-id="463f9-135">S</span><span class="sxs-lookup"><span data-stu-id="463f9-135">S</span></span>                            | <span data-ttu-id="463f9-136">F</span><span class="sxs-lookup"><span data-stu-id="463f9-136">F</span></span>                              |
| <span data-ttu-id="463f9-137">F,S</span><span class="sxs-lookup"><span data-stu-id="463f9-137">F,S</span></span>                             | <span data-ttu-id="463f9-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="463f9-138">PendingConfiguration</span></span> | <span data-ttu-id="463f9-139">Falha</span><span class="sxs-lookup"><span data-stu-id="463f9-139">Failure</span></span>    | <span data-ttu-id="463f9-140">$false</span><span class="sxs-lookup"><span data-stu-id="463f9-140">$false</span></span>        | <span data-ttu-id="463f9-141">S</span><span class="sxs-lookup"><span data-stu-id="463f9-141">S</span></span>                            | <span data-ttu-id="463f9-142">F</span><span class="sxs-lookup"><span data-stu-id="463f9-142">F</span></span>                              |
| <span data-ttu-id="463f9-143">S<sub>1</sub>, F, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="463f9-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="463f9-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="463f9-144">PendingConfiguration</span></span> | <span data-ttu-id="463f9-145">Falha</span><span class="sxs-lookup"><span data-stu-id="463f9-145">Failure</span></span>    | <span data-ttu-id="463f9-146">$false</span><span class="sxs-lookup"><span data-stu-id="463f9-146">$false</span></span>        | <span data-ttu-id="463f9-147">S<sub>1</sub>, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="463f9-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="463f9-148">F</span><span class="sxs-lookup"><span data-stu-id="463f9-148">F</span></span>                              |
| <span data-ttu-id="463f9-149">F<sub>1</sub>, S, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="463f9-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="463f9-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="463f9-150">PendingConfiguration</span></span> | <span data-ttu-id="463f9-151">Falha</span><span class="sxs-lookup"><span data-stu-id="463f9-151">Failure</span></span>    | <span data-ttu-id="463f9-152">$false</span><span class="sxs-lookup"><span data-stu-id="463f9-152">$false</span></span>        | <span data-ttu-id="463f9-153">S</span><span class="sxs-lookup"><span data-stu-id="463f9-153">S</span></span>                            | <span data-ttu-id="463f9-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="463f9-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
| <span data-ttu-id="463f9-155">S, r</span><span class="sxs-lookup"><span data-stu-id="463f9-155">S, r</span></span>                            | <span data-ttu-id="463f9-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="463f9-156">PendingReboot</span></span>        | <span data-ttu-id="463f9-157">Sucesso</span><span class="sxs-lookup"><span data-stu-id="463f9-157">Success</span></span>    | <span data-ttu-id="463f9-158">$true</span><span class="sxs-lookup"><span data-stu-id="463f9-158">$true</span></span>         | <span data-ttu-id="463f9-159">S</span><span class="sxs-lookup"><span data-stu-id="463f9-159">S</span></span>                            | <span data-ttu-id="463f9-160">r</span><span class="sxs-lookup"><span data-stu-id="463f9-160">r</span></span>                              |
| <span data-ttu-id="463f9-161">F, r</span><span class="sxs-lookup"><span data-stu-id="463f9-161">F, r</span></span>                            | <span data-ttu-id="463f9-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="463f9-162">PendingReboot</span></span>        | <span data-ttu-id="463f9-163">Falha</span><span class="sxs-lookup"><span data-stu-id="463f9-163">Failure</span></span>    | <span data-ttu-id="463f9-164">$true</span><span class="sxs-lookup"><span data-stu-id="463f9-164">$true</span></span>         | <span data-ttu-id="463f9-165">$null</span><span class="sxs-lookup"><span data-stu-id="463f9-165">$null</span></span>                        | <span data-ttu-id="463f9-166">F, r</span><span class="sxs-lookup"><span data-stu-id="463f9-166">F, r</span></span>                           |
| <span data-ttu-id="463f9-167">r, S</span><span class="sxs-lookup"><span data-stu-id="463f9-167">r, S</span></span>                            | <span data-ttu-id="463f9-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="463f9-168">PendingReboot</span></span>        | <span data-ttu-id="463f9-169">Sucesso</span><span class="sxs-lookup"><span data-stu-id="463f9-169">Success</span></span>    | <span data-ttu-id="463f9-170">$true</span><span class="sxs-lookup"><span data-stu-id="463f9-170">$true</span></span>         | <span data-ttu-id="463f9-171">$null</span><span class="sxs-lookup"><span data-stu-id="463f9-171">$null</span></span>                        | <span data-ttu-id="463f9-172">r</span><span class="sxs-lookup"><span data-stu-id="463f9-172">r</span></span>                              |
| <span data-ttu-id="463f9-173">r, F</span><span class="sxs-lookup"><span data-stu-id="463f9-173">r, F</span></span>                            | <span data-ttu-id="463f9-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="463f9-174">PendingReboot</span></span>        | <span data-ttu-id="463f9-175">Sucesso</span><span class="sxs-lookup"><span data-stu-id="463f9-175">Success</span></span>    | <span data-ttu-id="463f9-176">$true</span><span class="sxs-lookup"><span data-stu-id="463f9-176">$true</span></span>         | <span data-ttu-id="463f9-177">$null</span><span class="sxs-lookup"><span data-stu-id="463f9-177">$null</span></span>                        | <span data-ttu-id="463f9-178">r</span><span class="sxs-lookup"><span data-stu-id="463f9-178">r</span></span>                              |

- <span data-ttu-id="463f9-179">S<sub>i</sub>: uma série de recursos que são aplicados com êxito</span><span class="sxs-lookup"><span data-stu-id="463f9-179">S<sub>i</sub>: A series of resources that applied successfully</span></span>
- <span data-ttu-id="463f9-180">F<sub>i</sub>: uma série de recursos que são aplicados sem êxito</span><span class="sxs-lookup"><span data-stu-id="463f9-180">F<sub>i</sub>: A series of resources that applied unsuccessfully</span></span>
- <span data-ttu-id="463f9-181">r: um recurso que exige reinicialização</span><span class="sxs-lookup"><span data-stu-id="463f9-181">r: A resource that requires reboot</span></span>

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="463f9-182">Melhorias no cmdlet Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="463f9-182">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="463f9-183">Foram feitas algumas melhorias ao cmdlet `Get-DscConfigurationStatus` nesta versão.</span><span class="sxs-lookup"><span data-stu-id="463f9-183">A few enhancements have been made to `Get-DscConfigurationStatus` cmdlet in this release.</span></span> <span data-ttu-id="463f9-184">Anteriormente, a propriedade StartDate de objetos retornados pelo cmdlet era do tipo String.</span><span class="sxs-lookup"><span data-stu-id="463f9-184">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="463f9-185">Agora, ela é do tipo Datetime, o que permite uma seleção e filtragem complexas, facilitando-as com base nas propriedades intrínsecas de um objeto Datetime.</span><span class="sxs-lookup"><span data-stu-id="463f9-185">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>

```powershell
(Get-DscConfigurationStatus).StartDate | Format-List *

DateTime    : Friday, November 13, 2015 1:39:44 PM
Date        : 11/13/2015 12:00:00 AM
Day         : 13
DayOfWeek   : Friday
DayOfYear   : 317
Hour        : 13
Kind        : Local
Millisecond : 886
Minute      : 39
Month       : 11
Second      : 44
Ticks       : 635830187848860000
TimeOfDay   : 13:39:44.8860000
Year        : 2015
```

<span data-ttu-id="463f9-186">O exemplo a seguir retorna todos os registros de operação de DSC ocorridos no mesmo dia da semana que hoje.</span><span class="sxs-lookup"><span data-stu-id="463f9-186">The following example returns all DSC operation records that happened on the same day of week as the current day.</span></span>

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="463f9-187">Registros de operações que não fazem alterações à configuração do nó (ou seja, operações somente leitura) são eliminados.</span><span class="sxs-lookup"><span data-stu-id="463f9-187">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="463f9-188">Portanto, as operações `Test-DscConfiguration` e `Get-DscConfiguration` não são mais adulteradas em objetos retornados do cmdlet `Get-DscConfigurationStatus`.</span><span class="sxs-lookup"><span data-stu-id="463f9-188">Therefore, `Test-DscConfiguration`, `Get-DscConfiguration` operations are no longer adulterated in returned objects from `Get-DscConfigurationStatus` cmdlet.</span></span> <span data-ttu-id="463f9-189">Registros da operação de definição de metaconfiguração são adicionados ao retorno pelo cmdlet `Get-DscConfigurationStatus`.</span><span class="sxs-lookup"><span data-stu-id="463f9-189">Records of meta configuration setting operation is added to the return of `Get-DscConfigurationStatus` cmdlet.</span></span>

<span data-ttu-id="463f9-190">Veja a seguir um exemplo de resultado retornado pelo cmdlet `Get-DscConfigurationStatus –All`.</span><span class="sxs-lookup"><span data-stu-id="463f9-190">Following is an example of result returned from `Get-DscConfigurationStatus –All` cmdlet.</span></span>

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

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="463f9-191">Melhoria no cmdlet Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="463f9-191">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>

<span data-ttu-id="463f9-192">Um novo campo de LCMStateDetail é adicionado ao objeto retornado pelo cmdlet `Get-DscLocalConfigurationManager`.</span><span class="sxs-lookup"><span data-stu-id="463f9-192">A new field of LCMStateDetail is added to the object returned from `Get-DscLocalConfigurationManager` cmdlet.</span></span> <span data-ttu-id="463f9-193">Este campo é populado quando LCMState é “Ocupado”.</span><span class="sxs-lookup"><span data-stu-id="463f9-193">This field is populated when LCMState is "Busy".</span></span> <span data-ttu-id="463f9-194">Ele pode ser recuperado pelo seguinte cmdlet:</span><span class="sxs-lookup"><span data-stu-id="463f9-194">It can be retrieved by following cmdlet:</span></span>

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="463f9-195">Veja a seguir um exemplo de saída de um monitoramento contínuo em uma configuração que exige duas reinicializações em um nó remoto.</span><span class="sxs-lookup"><span data-stu-id="463f9-195">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>

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
