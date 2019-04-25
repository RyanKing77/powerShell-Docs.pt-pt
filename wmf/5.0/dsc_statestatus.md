---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: ff2c2bd7369893d72db001ecabf63991ded0bfd5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058986"
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="20888-102">Estado Unificado e Consistente e Representação de Estado</span><span class="sxs-lookup"><span data-stu-id="20888-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="20888-103">Uma série de aprimoramentos foram feitos nesta versão para automatizações de fluxos de criado o estado do LCM e o estado de DSC.</span><span class="sxs-lookup"><span data-stu-id="20888-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="20888-104">Estes incluem unificadas e consistentes Estado representações, propriedade datetime gerenciável de objetos de estado devolvido pelo `Get-DscConfigurationStatus` cmdlet e LCM aprimorado Estado propriedade detalhes devolvida por `Get-DscLocalConfigurationManager` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="20888-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by `Get-DscConfigurationStatus` cmdlet and enhanced LCM state details property returned by `Get-DscLocalConfigurationManager` cmdlet.</span></span>

<span data-ttu-id="20888-105">A representação de estado do LCM e o estado da operação de DSC são revisitada e unificação de acordo com as seguintes regras:</span><span class="sxs-lookup"><span data-stu-id="20888-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>

1. <span data-ttu-id="20888-106">Recursos de Notprocessed não afetam o estado do LCM e o estado de DSC.</span><span class="sxs-lookup"><span data-stu-id="20888-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
2. <span data-ttu-id="20888-107">LCM parar recursos de processamento adicionais depois de encontrar um recurso que pede o reinício.</span><span class="sxs-lookup"><span data-stu-id="20888-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
3. <span data-ttu-id="20888-108">Um recurso que pede o reinício não está no estado pretendido até que realmente acontece reinício.</span><span class="sxs-lookup"><span data-stu-id="20888-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
4. <span data-ttu-id="20888-109">Depois de encontrar um recurso que não consegue, LCM mantém processar ainda mais recursos, desde que não são dependentes de uma falha.</span><span class="sxs-lookup"><span data-stu-id="20888-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
5. <span data-ttu-id="20888-110">O estado geral devolvido pelo `Get-DscConfigurationStatus` cmdlet é o conjunto super de estado de todos os recursos.</span><span class="sxs-lookup"><span data-stu-id="20888-110">The overall status returned by `Get-DscConfigurationStatus` cmdlet is the super set of all resources' status.</span></span>
6. <span data-ttu-id="20888-111">O estado de PendingReboot é um superconjunto do Estado de PendingConfiguration.</span><span class="sxs-lookup"><span data-stu-id="20888-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

<span data-ttu-id="20888-112">A tabela abaixo ilustra o resultante Estado relacionadas com as propriedades em alguns cenários típicos.</span><span class="sxs-lookup"><span data-stu-id="20888-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

| <span data-ttu-id="20888-113">Cenário</span><span class="sxs-lookup"><span data-stu-id="20888-113">Scenario</span></span>                        | <span data-ttu-id="20888-114">LCMState</span><span class="sxs-lookup"><span data-stu-id="20888-114">LCMState</span></span>             | <span data-ttu-id="20888-115">Estado</span><span class="sxs-lookup"><span data-stu-id="20888-115">Status</span></span>     | <span data-ttu-id="20888-116">Pedido de reinício</span><span class="sxs-lookup"><span data-stu-id="20888-116">Reboot Requested</span></span> | <span data-ttu-id="20888-117">ResourcesInDesiredState</span><span class="sxs-lookup"><span data-stu-id="20888-117">ResourcesInDesiredState</span></span>   | <span data-ttu-id="20888-118">ResourcesNotInDesiredState</span><span class="sxs-lookup"><span data-stu-id="20888-118">ResourcesNotInDesiredState</span></span> |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| <span data-ttu-id="20888-119">S<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="20888-119">S<sub>i</sub></span></span>                   | <span data-ttu-id="20888-120">Inativo</span><span class="sxs-lookup"><span data-stu-id="20888-120">Idle</span></span>                 | <span data-ttu-id="20888-121">Sucesso</span><span class="sxs-lookup"><span data-stu-id="20888-121">Success</span></span>    | <span data-ttu-id="20888-122">$false</span><span class="sxs-lookup"><span data-stu-id="20888-122">$false</span></span>        | <span data-ttu-id="20888-123">S</span><span class="sxs-lookup"><span data-stu-id="20888-123">S</span></span>                            | <span data-ttu-id="20888-124">$null</span><span class="sxs-lookup"><span data-stu-id="20888-124">$null</span></span>                          |
| <span data-ttu-id="20888-125">F<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="20888-125">F<sub>i</sub></span></span>                   | <span data-ttu-id="20888-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="20888-126">PendingConfiguration</span></span> | <span data-ttu-id="20888-127">Falha</span><span class="sxs-lookup"><span data-stu-id="20888-127">Failure</span></span>    | <span data-ttu-id="20888-128">$false</span><span class="sxs-lookup"><span data-stu-id="20888-128">$false</span></span>        | <span data-ttu-id="20888-129">$null</span><span class="sxs-lookup"><span data-stu-id="20888-129">$null</span></span>                        | <span data-ttu-id="20888-130">F</span><span class="sxs-lookup"><span data-stu-id="20888-130">F</span></span>                              |
| <span data-ttu-id="20888-131">S,F</span><span class="sxs-lookup"><span data-stu-id="20888-131">S,F</span></span>                             | <span data-ttu-id="20888-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="20888-132">PendingConfiguration</span></span> | <span data-ttu-id="20888-133">Falha</span><span class="sxs-lookup"><span data-stu-id="20888-133">Failure</span></span>    | <span data-ttu-id="20888-134">$false</span><span class="sxs-lookup"><span data-stu-id="20888-134">$false</span></span>        | <span data-ttu-id="20888-135">S</span><span class="sxs-lookup"><span data-stu-id="20888-135">S</span></span>                            | <span data-ttu-id="20888-136">F</span><span class="sxs-lookup"><span data-stu-id="20888-136">F</span></span>                              |
| <span data-ttu-id="20888-137">F,S</span><span class="sxs-lookup"><span data-stu-id="20888-137">F,S</span></span>                             | <span data-ttu-id="20888-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="20888-138">PendingConfiguration</span></span> | <span data-ttu-id="20888-139">Falha</span><span class="sxs-lookup"><span data-stu-id="20888-139">Failure</span></span>    | <span data-ttu-id="20888-140">$false</span><span class="sxs-lookup"><span data-stu-id="20888-140">$false</span></span>        | <span data-ttu-id="20888-141">S</span><span class="sxs-lookup"><span data-stu-id="20888-141">S</span></span>                            | <span data-ttu-id="20888-142">F</span><span class="sxs-lookup"><span data-stu-id="20888-142">F</span></span>                              |
| <span data-ttu-id="20888-143">S<sub>1</sub>, F, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="20888-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="20888-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="20888-144">PendingConfiguration</span></span> | <span data-ttu-id="20888-145">Falha</span><span class="sxs-lookup"><span data-stu-id="20888-145">Failure</span></span>    | <span data-ttu-id="20888-146">$false</span><span class="sxs-lookup"><span data-stu-id="20888-146">$false</span></span>        | <span data-ttu-id="20888-147">S<sub>1</sub>, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="20888-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="20888-148">F</span><span class="sxs-lookup"><span data-stu-id="20888-148">F</span></span>                              |
| <span data-ttu-id="20888-149">F<sub>1</sub>, S, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="20888-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="20888-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="20888-150">PendingConfiguration</span></span> | <span data-ttu-id="20888-151">Falha</span><span class="sxs-lookup"><span data-stu-id="20888-151">Failure</span></span>    | <span data-ttu-id="20888-152">$false</span><span class="sxs-lookup"><span data-stu-id="20888-152">$false</span></span>        | <span data-ttu-id="20888-153">S</span><span class="sxs-lookup"><span data-stu-id="20888-153">S</span></span>                            | <span data-ttu-id="20888-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="20888-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
| <span data-ttu-id="20888-155">S, r</span><span class="sxs-lookup"><span data-stu-id="20888-155">S, r</span></span>                            | <span data-ttu-id="20888-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="20888-156">PendingReboot</span></span>        | <span data-ttu-id="20888-157">Sucesso</span><span class="sxs-lookup"><span data-stu-id="20888-157">Success</span></span>    | <span data-ttu-id="20888-158">$true</span><span class="sxs-lookup"><span data-stu-id="20888-158">$true</span></span>         | <span data-ttu-id="20888-159">S</span><span class="sxs-lookup"><span data-stu-id="20888-159">S</span></span>                            | <span data-ttu-id="20888-160">r</span><span class="sxs-lookup"><span data-stu-id="20888-160">r</span></span>                              |
| <span data-ttu-id="20888-161">F, r</span><span class="sxs-lookup"><span data-stu-id="20888-161">F, r</span></span>                            | <span data-ttu-id="20888-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="20888-162">PendingReboot</span></span>        | <span data-ttu-id="20888-163">Falha</span><span class="sxs-lookup"><span data-stu-id="20888-163">Failure</span></span>    | <span data-ttu-id="20888-164">$true</span><span class="sxs-lookup"><span data-stu-id="20888-164">$true</span></span>         | <span data-ttu-id="20888-165">$null</span><span class="sxs-lookup"><span data-stu-id="20888-165">$null</span></span>                        | <span data-ttu-id="20888-166">F, r</span><span class="sxs-lookup"><span data-stu-id="20888-166">F, r</span></span>                           |
| <span data-ttu-id="20888-167">r, S</span><span class="sxs-lookup"><span data-stu-id="20888-167">r, S</span></span>                            | <span data-ttu-id="20888-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="20888-168">PendingReboot</span></span>        | <span data-ttu-id="20888-169">Sucesso</span><span class="sxs-lookup"><span data-stu-id="20888-169">Success</span></span>    | <span data-ttu-id="20888-170">$true</span><span class="sxs-lookup"><span data-stu-id="20888-170">$true</span></span>         | <span data-ttu-id="20888-171">$null</span><span class="sxs-lookup"><span data-stu-id="20888-171">$null</span></span>                        | <span data-ttu-id="20888-172">r</span><span class="sxs-lookup"><span data-stu-id="20888-172">r</span></span>                              |
| <span data-ttu-id="20888-173">r, F</span><span class="sxs-lookup"><span data-stu-id="20888-173">r, F</span></span>                            | <span data-ttu-id="20888-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="20888-174">PendingReboot</span></span>        | <span data-ttu-id="20888-175">Sucesso</span><span class="sxs-lookup"><span data-stu-id="20888-175">Success</span></span>    | <span data-ttu-id="20888-176">$true</span><span class="sxs-lookup"><span data-stu-id="20888-176">$true</span></span>         | <span data-ttu-id="20888-177">$null</span><span class="sxs-lookup"><span data-stu-id="20888-177">$null</span></span>                        | <span data-ttu-id="20888-178">r</span><span class="sxs-lookup"><span data-stu-id="20888-178">r</span></span>                              |

- <span data-ttu-id="20888-179">S<sub>i</sub>: Uma série de recursos que são aplicadas com êxito</span><span class="sxs-lookup"><span data-stu-id="20888-179">S<sub>i</sub>: A series of resources that applied successfully</span></span>
- <span data-ttu-id="20888-180">F<sub>i</sub>: Uma série de recursos que são aplicadas sem êxito</span><span class="sxs-lookup"><span data-stu-id="20888-180">F<sub>i</sub>: A series of resources that applied unsuccessfully</span></span>
- <span data-ttu-id="20888-181">r: Um recurso que exige reinicialização</span><span class="sxs-lookup"><span data-stu-id="20888-181">r: A resource that requires reboot</span></span>

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="20888-182">Melhoria no cmdlet Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="20888-182">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="20888-183">Foram feitas algumas melhorias para `Get-DscConfigurationStatus` cmdlet nesta versão.</span><span class="sxs-lookup"><span data-stu-id="20888-183">A few enhancements have been made to `Get-DscConfigurationStatus` cmdlet in this release.</span></span> <span data-ttu-id="20888-184">Anteriormente, a propriedade StartDate de objetos devolvido pelo cmdlet é do tipo cadeia.</span><span class="sxs-lookup"><span data-stu-id="20888-184">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="20888-185">Agora, é do tipo Datetime, que permite complexos selecionando e filtragem mais fácil com base nas propriedades de intrínsecas de um objeto de Datetime.</span><span class="sxs-lookup"><span data-stu-id="20888-185">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>

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

<span data-ttu-id="20888-186">O exemplo seguinte devolve todos os registos de operação de DSC que aconteceram no mesmo dia da semana, como o dia atual.</span><span class="sxs-lookup"><span data-stu-id="20888-186">The following example returns all DSC operation records that happened on the same day of week as the current day.</span></span>

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="20888-187">Registos de operações que não faça alterações na configuração do nó (ou seja, apenas operações de leitura) são eliminados.</span><span class="sxs-lookup"><span data-stu-id="20888-187">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="20888-188">Por conseguinte, `Test-DscConfiguration`, `Get-DscConfiguration` operações já não são adulterated em objetos devolvidos de `Get-DscConfigurationStatus` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="20888-188">Therefore, `Test-DscConfiguration`, `Get-DscConfiguration` operations are no longer adulterated in returned objects from `Get-DscConfigurationStatus` cmdlet.</span></span> <span data-ttu-id="20888-189">Registos de operação de definição de configuração de metadados é adicionada para o retorno de `Get-DscConfigurationStatus` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="20888-189">Records of meta configuration setting operation is added to the return of `Get-DscConfigurationStatus` cmdlet.</span></span>

<span data-ttu-id="20888-190">Segue-se um exemplo de resultado da `Get-DscConfigurationStatus –All` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="20888-190">Following is an example of result returned from `Get-DscConfigurationStatus –All` cmdlet.</span></span>

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

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="20888-191">Melhoria no cmdlet Get-dsclocalconfigurationmanager para</span><span class="sxs-lookup"><span data-stu-id="20888-191">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>

<span data-ttu-id="20888-192">Um novo campo de LCMStateDetail é adicionado para o objeto devolvido do `Get-DscLocalConfigurationManager` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="20888-192">A new field of LCMStateDetail is added to the object returned from `Get-DscLocalConfigurationManager` cmdlet.</span></span> <span data-ttu-id="20888-193">Este campo é preenchido quando LCMState é "Ocupado".</span><span class="sxs-lookup"><span data-stu-id="20888-193">This field is populated when LCMState is "Busy".</span></span> <span data-ttu-id="20888-194">Pode ser obtido pelo cmdlet seguinte:</span><span class="sxs-lookup"><span data-stu-id="20888-194">It can be retrieved by following cmdlet:</span></span>

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="20888-195">Segue-se uma saída de exemplo de uma monitorização contínua na configuração que requer dois reinícios num nó remoto.</span><span class="sxs-lookup"><span data-stu-id="20888-195">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>

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
