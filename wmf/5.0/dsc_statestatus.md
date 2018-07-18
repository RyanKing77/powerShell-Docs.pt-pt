---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: b279d388754c5ee42215f21317f7b3d8089b7608
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093886"
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="1dee1-102">Estado Unificado e Consistente e Representação de Estado</span><span class="sxs-lookup"><span data-stu-id="1dee1-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="1dee1-103">Uma série de aprimoramentos foram feitos nesta versão para automatizações de fluxos de criado o estado do LCM e o estado de DSC.</span><span class="sxs-lookup"><span data-stu-id="1dee1-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="1dee1-104">Estes incluem unificadas e consistentes Estado representações, propriedade datetime gerenciável de objetos de estado devolvido pelo `Get-DscConfigurationStatus` cmdlet e LCM aprimorado Estado propriedade detalhes devolvida por `Get-DscLocalConfigurationManager` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1dee1-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by `Get-DscConfigurationStatus` cmdlet and enhanced LCM state details property returned by `Get-DscLocalConfigurationManager` cmdlet.</span></span>

<span data-ttu-id="1dee1-105">A representação de estado do LCM e o estado da operação de DSC são revisitada e unificação de acordo com as seguintes regras:</span><span class="sxs-lookup"><span data-stu-id="1dee1-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>

1. <span data-ttu-id="1dee1-106">Recursos de Notprocessed não afetam o estado do LCM e o estado de DSC.</span><span class="sxs-lookup"><span data-stu-id="1dee1-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
1. <span data-ttu-id="1dee1-107">LCM parar recursos de processamento adicionais depois de encontrar um recurso que pede o reinício.</span><span class="sxs-lookup"><span data-stu-id="1dee1-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
1. <span data-ttu-id="1dee1-108">Um recurso que pede o reinício não está no estado pretendido até que realmente acontece reinício.</span><span class="sxs-lookup"><span data-stu-id="1dee1-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
1. <span data-ttu-id="1dee1-109">Depois de encontrar um recurso que não consegue, LCM mantém processar ainda mais recursos, desde que não são dependentes de uma falha.</span><span class="sxs-lookup"><span data-stu-id="1dee1-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
1. <span data-ttu-id="1dee1-110">O estado geral devolvido pelo `Get-DscConfigurationStatus` cmdlet é o conjunto super de estado de todos os recursos.</span><span class="sxs-lookup"><span data-stu-id="1dee1-110">The overall status returned by `Get-DscConfigurationStatus` cmdlet is the super set of all resources' status.</span></span>
1. <span data-ttu-id="1dee1-111">O estado de PendingReboot é um superconjunto do Estado de PendingConfiguration.</span><span class="sxs-lookup"><span data-stu-id="1dee1-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

   <span data-ttu-id="1dee1-112">A tabela abaixo ilustra o resultante Estado relacionadas com as propriedades em alguns cenários típicos.</span><span class="sxs-lookup"><span data-stu-id="1dee1-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

   | <span data-ttu-id="1dee1-113">Cenário</span><span class="sxs-lookup"><span data-stu-id="1dee1-113">Scenario</span></span>                    | <span data-ttu-id="1dee1-114">LCMState</span><span class="sxs-lookup"><span data-stu-id="1dee1-114">LCMState</span></span>       | <span data-ttu-id="1dee1-115">Estado</span><span class="sxs-lookup"><span data-stu-id="1dee1-115">Status</span></span> | <span data-ttu-id="1dee1-116">Pedido de reinício</span><span class="sxs-lookup"><span data-stu-id="1dee1-116">Reboot Requested</span></span>  | <span data-ttu-id="1dee1-117">ResourcesInDesiredState</span><span class="sxs-lookup"><span data-stu-id="1dee1-117">ResourcesInDesiredState</span></span>  | <span data-ttu-id="1dee1-118">ResourcesNotInDesiredState</span><span class="sxs-lookup"><span data-stu-id="1dee1-118">ResourcesNotInDesiredState</span></span> |
   |---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
   | <span data-ttu-id="1dee1-119">S**^**</span><span class="sxs-lookup"><span data-stu-id="1dee1-119">S**^**</span></span>                          | <span data-ttu-id="1dee1-120">Inativo</span><span class="sxs-lookup"><span data-stu-id="1dee1-120">Idle</span></span>                 | <span data-ttu-id="1dee1-121">Sucesso</span><span class="sxs-lookup"><span data-stu-id="1dee1-121">Success</span></span>    | <span data-ttu-id="1dee1-122">$false</span><span class="sxs-lookup"><span data-stu-id="1dee1-122">$false</span></span>        | <span data-ttu-id="1dee1-123">S</span><span class="sxs-lookup"><span data-stu-id="1dee1-123">S</span></span>                            | <span data-ttu-id="1dee1-124">$null</span><span class="sxs-lookup"><span data-stu-id="1dee1-124">$null</span></span>                          |
   | <span data-ttu-id="1dee1-125">F**^**</span><span class="sxs-lookup"><span data-stu-id="1dee1-125">F**^**</span></span>                          | <span data-ttu-id="1dee1-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="1dee1-126">PendingConfiguration</span></span> | <span data-ttu-id="1dee1-127">Falha</span><span class="sxs-lookup"><span data-stu-id="1dee1-127">Failure</span></span>    | <span data-ttu-id="1dee1-128">$false</span><span class="sxs-lookup"><span data-stu-id="1dee1-128">$false</span></span>        | <span data-ttu-id="1dee1-129">$null</span><span class="sxs-lookup"><span data-stu-id="1dee1-129">$null</span></span>                        | <span data-ttu-id="1dee1-130">F</span><span class="sxs-lookup"><span data-stu-id="1dee1-130">F</span></span>                              |
   | <span data-ttu-id="1dee1-131">S, F</span><span class="sxs-lookup"><span data-stu-id="1dee1-131">S,F</span></span>                             | <span data-ttu-id="1dee1-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="1dee1-132">PendingConfiguration</span></span> | <span data-ttu-id="1dee1-133">Falha</span><span class="sxs-lookup"><span data-stu-id="1dee1-133">Failure</span></span>    | <span data-ttu-id="1dee1-134">$false</span><span class="sxs-lookup"><span data-stu-id="1dee1-134">$false</span></span>        | <span data-ttu-id="1dee1-135">S</span><span class="sxs-lookup"><span data-stu-id="1dee1-135">S</span></span>                            | <span data-ttu-id="1dee1-136">F</span><span class="sxs-lookup"><span data-stu-id="1dee1-136">F</span></span>                              |
   | <span data-ttu-id="1dee1-137">F, S</span><span class="sxs-lookup"><span data-stu-id="1dee1-137">F,S</span></span>                             | <span data-ttu-id="1dee1-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="1dee1-138">PendingConfiguration</span></span> | <span data-ttu-id="1dee1-139">Falha</span><span class="sxs-lookup"><span data-stu-id="1dee1-139">Failure</span></span>    | <span data-ttu-id="1dee1-140">$false</span><span class="sxs-lookup"><span data-stu-id="1dee1-140">$false</span></span>        | <span data-ttu-id="1dee1-141">S</span><span class="sxs-lookup"><span data-stu-id="1dee1-141">S</span></span>                            | <span data-ttu-id="1dee1-142">F</span><span class="sxs-lookup"><span data-stu-id="1dee1-142">F</span></span>                              |
   | <span data-ttu-id="1dee1-143">S<sub>1</sub>, F, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="1dee1-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="1dee1-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="1dee1-144">PendingConfiguration</span></span> | <span data-ttu-id="1dee1-145">Falha</span><span class="sxs-lookup"><span data-stu-id="1dee1-145">Failure</span></span>    | <span data-ttu-id="1dee1-146">$false</span><span class="sxs-lookup"><span data-stu-id="1dee1-146">$false</span></span>        | <span data-ttu-id="1dee1-147">S<sub>1</sub>, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="1dee1-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="1dee1-148">F</span><span class="sxs-lookup"><span data-stu-id="1dee1-148">F</span></span>                              |
   | <span data-ttu-id="1dee1-149">F<sub>1</sub>, S, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="1dee1-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="1dee1-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="1dee1-150">PendingConfiguration</span></span> | <span data-ttu-id="1dee1-151">Falha</span><span class="sxs-lookup"><span data-stu-id="1dee1-151">Failure</span></span>    | <span data-ttu-id="1dee1-152">$false</span><span class="sxs-lookup"><span data-stu-id="1dee1-152">$false</span></span>        | <span data-ttu-id="1dee1-153">S</span><span class="sxs-lookup"><span data-stu-id="1dee1-153">S</span></span>                            | <span data-ttu-id="1dee1-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="1dee1-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
   | <span data-ttu-id="1dee1-155">S, o r</span><span class="sxs-lookup"><span data-stu-id="1dee1-155">S, r</span></span>                            | <span data-ttu-id="1dee1-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="1dee1-156">PendingReboot</span></span>        | <span data-ttu-id="1dee1-157">Sucesso</span><span class="sxs-lookup"><span data-stu-id="1dee1-157">Success</span></span>    | <span data-ttu-id="1dee1-158">$true</span><span class="sxs-lookup"><span data-stu-id="1dee1-158">$true</span></span>         | <span data-ttu-id="1dee1-159">S</span><span class="sxs-lookup"><span data-stu-id="1dee1-159">S</span></span>                            | <span data-ttu-id="1dee1-160">r</span><span class="sxs-lookup"><span data-stu-id="1dee1-160">r</span></span>                              |
   | <span data-ttu-id="1dee1-161">F, r</span><span class="sxs-lookup"><span data-stu-id="1dee1-161">F, r</span></span>                            | <span data-ttu-id="1dee1-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="1dee1-162">PendingReboot</span></span>        | <span data-ttu-id="1dee1-163">Falha</span><span class="sxs-lookup"><span data-stu-id="1dee1-163">Failure</span></span>    | <span data-ttu-id="1dee1-164">$true</span><span class="sxs-lookup"><span data-stu-id="1dee1-164">$true</span></span>         | <span data-ttu-id="1dee1-165">$null</span><span class="sxs-lookup"><span data-stu-id="1dee1-165">$null</span></span>                        | <span data-ttu-id="1dee1-166">F, r</span><span class="sxs-lookup"><span data-stu-id="1dee1-166">F, r</span></span>                           |
   | <span data-ttu-id="1dee1-167">r, S</span><span class="sxs-lookup"><span data-stu-id="1dee1-167">r, S</span></span>                            | <span data-ttu-id="1dee1-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="1dee1-168">PendingReboot</span></span>        | <span data-ttu-id="1dee1-169">Sucesso</span><span class="sxs-lookup"><span data-stu-id="1dee1-169">Success</span></span>    | <span data-ttu-id="1dee1-170">$true</span><span class="sxs-lookup"><span data-stu-id="1dee1-170">$true</span></span>         | <span data-ttu-id="1dee1-171">$null</span><span class="sxs-lookup"><span data-stu-id="1dee1-171">$null</span></span>                        | <span data-ttu-id="1dee1-172">r</span><span class="sxs-lookup"><span data-stu-id="1dee1-172">r</span></span>                              |
   | <span data-ttu-id="1dee1-173">r, F</span><span class="sxs-lookup"><span data-stu-id="1dee1-173">r, F</span></span>                            | <span data-ttu-id="1dee1-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="1dee1-174">PendingReboot</span></span>        | <span data-ttu-id="1dee1-175">Sucesso</span><span class="sxs-lookup"><span data-stu-id="1dee1-175">Success</span></span>    | <span data-ttu-id="1dee1-176">$true</span><span class="sxs-lookup"><span data-stu-id="1dee1-176">$true</span></span>         | <span data-ttu-id="1dee1-177">$null</span><span class="sxs-lookup"><span data-stu-id="1dee1-177">$null</span></span>                        | <span data-ttu-id="1dee1-178">r</span><span class="sxs-lookup"><span data-stu-id="1dee1-178">r</span></span>                              |

   <span data-ttu-id="1dee1-179">^
   S<sub>eu</sub>: uma série de recursos que são aplicadas com êxito F<sub>eu</sub>: uma série de recursos que são aplicadas sem êxito r: um recurso que exige reinicialização \*</span><span class="sxs-lookup"><span data-stu-id="1dee1-179">^
   S<sub>i</sub>: A series of resources that applied successfully F<sub>i</sub>: A series of resources that applied unsuccessfully r: A resource that requires reboot \*</span></span>

   ```powershell
   $LCMState = (Get-DscLocalConfigurationManager).LCMState
   $Status = (Get-DscConfigurationStatus).Status

   $RebootRequested = (Get-DscConfigurationStatus).RebootRequested

   $ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

   $ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
   ```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="1dee1-180">Melhoria no cmdlet Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="1dee1-180">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="1dee1-181">Foram feitas algumas melhorias para `Get-DscConfigurationStatus` cmdlet nesta versão.</span><span class="sxs-lookup"><span data-stu-id="1dee1-181">A few enhancements have been made to `Get-DscConfigurationStatus` cmdlet in this release.</span></span> <span data-ttu-id="1dee1-182">Anteriormente, a propriedade StartDate de objetos devolvido pelo cmdlet é do tipo cadeia.</span><span class="sxs-lookup"><span data-stu-id="1dee1-182">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="1dee1-183">Agora, é do tipo Datetime, que permite complexos selecionando e filtragem mais fácil com base nas propriedades de intrínsecas de um objeto de Datetime.</span><span class="sxs-lookup"><span data-stu-id="1dee1-183">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>

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

<span data-ttu-id="1dee1-184">Segue-se um exemplo que devolve que todos os registos de operação de DSC aconteceram no mesmo dia da semana como hoje mesmo.</span><span class="sxs-lookup"><span data-stu-id="1dee1-184">Following is an example that returns all DSC operation records happened on the same day of week as today.</span></span>

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="1dee1-185">Registos de operações que não faça alterações na configuração do nó (ou seja, apenas operações de leitura) são eliminados.</span><span class="sxs-lookup"><span data-stu-id="1dee1-185">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="1dee1-186">Por conseguinte, `Test-DscConfiguration`, `Get-DscConfiguration` operações já não são adulterated em objetos devolvidos de `Get-DscConfigurationStatus` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1dee1-186">Therefore, `Test-DscConfiguration`, `Get-DscConfiguration` operations are no longer adulterated in returned objects from `Get-DscConfigurationStatus` cmdlet.</span></span>
<span data-ttu-id="1dee1-187">Registos de operação de definição de configuração de metadados é adicionada para o retorno de `Get-DscConfigurationStatus` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1dee1-187">Records of meta configuration setting operation is added to the return of `Get-DscConfigurationStatus` cmdlet.</span></span>

<span data-ttu-id="1dee1-188">Segue-se um exemplo de resultado da `Get-DscConfigurationStatus` – todos os cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1dee1-188">Following is an example of result returned from `Get-DscConfigurationStatus` –All cmdlet.</span></span>

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

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="1dee1-189">Melhoria no cmdlet Get-dsclocalconfigurationmanager para</span><span class="sxs-lookup"><span data-stu-id="1dee1-189">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>

<span data-ttu-id="1dee1-190">Um novo campo de LCMStateDetail é adicionado para o objeto devolvido do `Get-DscLocalConfigurationManager` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1dee1-190">A new field of LCMStateDetail is added to the object returned from `Get-DscLocalConfigurationManager` cmdlet.</span></span> <span data-ttu-id="1dee1-191">Este campo é preenchido quando LCMState é "Ocupado".</span><span class="sxs-lookup"><span data-stu-id="1dee1-191">This field is populated when LCMState is "Busy".</span></span> <span data-ttu-id="1dee1-192">Pode ser obtido pelo cmdlet seguinte:</span><span class="sxs-lookup"><span data-stu-id="1dee1-192">It can be retrieved by following cmdlet:</span></span>

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="1dee1-193">Segue-se uma saída de exemplo de uma monitorização contínua na configuração que requer dois reinícios num nó remoto.</span><span class="sxs-lookup"><span data-stu-id="1dee1-193">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>

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