---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 9a8c261c01a7970f2e7f89172007768b63295673
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="611bc-102">Estado Unificado e Consistente e Representação de Estado</span><span class="sxs-lookup"><span data-stu-id="611bc-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="611bc-103">Uma série de melhorias foram efetuadas nesta versão para automatizações incorporadas estado do MMC e estado de DSC.</span><span class="sxs-lookup"><span data-stu-id="611bc-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="611bc-104">Estes incluem Estado unificado e consistente e a declaração de estado, datetime gerível propriedade dos objetos de estado devolvido pelo cmdlet Get-DscConfigurationStatus e modulação de propriedade de detalhes do Estado do MMC devolvida pelo Get-DscLocalConfigurationManager cmdlet.</span><span class="sxs-lookup"><span data-stu-id="611bc-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by Get-DscConfigurationStatus cmdlet and enhanced LCM state details property returned by Get-DscLocalConfigurationManager cmdlet.</span></span>

<span data-ttu-id="611bc-105">A representação de estado do MMC e o estado da operação de DSC são Revisitado e unificada, de acordo com as seguintes regras:</span><span class="sxs-lookup"><span data-stu-id="611bc-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>
1.  <span data-ttu-id="611bc-106">Recurso Notprocessed não afeta o estado do MMC e o estado de DSC.</span><span class="sxs-lookup"><span data-stu-id="611bc-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
2.  <span data-ttu-id="611bc-107">Parar o MMC recursos de processamento adicional depois de encontrar um recurso de que os pedidos de reinício.</span><span class="sxs-lookup"><span data-stu-id="611bc-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
3.  <span data-ttu-id="611bc-108">Um recurso de que os pedidos de reiniciar o computador não está no estado pretendido até que o reinício, na verdade, acontece.</span><span class="sxs-lookup"><span data-stu-id="611bc-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
4.  <span data-ttu-id="611bc-109">Depois de encontrar um recurso que falha, o MMC mantém os recursos de processamento adicional, desde que não são dependentes de falha de um.</span><span class="sxs-lookup"><span data-stu-id="611bc-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
5.  <span data-ttu-id="611bc-110">O estado geral devolvido pelo cmdlet Get-DscConfigurationStatus é o conjunto super de estado de todos os recursos.</span><span class="sxs-lookup"><span data-stu-id="611bc-110">The overall status returned by Get-DscConfigurationStatus cmdlet is the super set of all resources’ status.</span></span>
6.  <span data-ttu-id="611bc-111">O estado de PendingReboot é um superconjunto do Estado de PendingConfiguration.</span><span class="sxs-lookup"><span data-stu-id="611bc-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

<span data-ttu-id="611bc-112">A tabela abaixo ilustra o resultante Estado relacionadas com propriedades em alguns cenários típicos.</span><span class="sxs-lookup"><span data-stu-id="611bc-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

| <span data-ttu-id="611bc-113">**Cenário**</span><span class="sxs-lookup"><span data-stu-id="611bc-113">**Scenario**</span></span>                    | <span data-ttu-id="611bc-114">**LCMState\***</span><span class="sxs-lookup"><span data-stu-id="611bc-114">**LCMState\***</span></span>       | <span data-ttu-id="611bc-115">**Status**</span><span class="sxs-lookup"><span data-stu-id="611bc-115">**Status**</span></span> | <span data-ttu-id="611bc-116">**Reiniciar o computador solicitado**</span><span class="sxs-lookup"><span data-stu-id="611bc-116">**Reboot Requested**</span></span>  | <span data-ttu-id="611bc-117">**ResourcesInDesiredState**</span><span class="sxs-lookup"><span data-stu-id="611bc-117">**ResourcesInDesiredState**</span></span>  | <span data-ttu-id="611bc-118">**ResourcesNotInDesiredState**</span><span class="sxs-lookup"><span data-stu-id="611bc-118">**ResourcesNotInDesiredState**</span></span> |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| <span data-ttu-id="611bc-119">S**^**</span><span class="sxs-lookup"><span data-stu-id="611bc-119">S**^**</span></span>                          | <span data-ttu-id="611bc-120">Inativo</span><span class="sxs-lookup"><span data-stu-id="611bc-120">Idle</span></span>                 | <span data-ttu-id="611bc-121">Sucesso</span><span class="sxs-lookup"><span data-stu-id="611bc-121">Success</span></span>    | <span data-ttu-id="611bc-122">$false</span><span class="sxs-lookup"><span data-stu-id="611bc-122">$false</span></span>        | <span data-ttu-id="611bc-123">S</span><span class="sxs-lookup"><span data-stu-id="611bc-123">S</span></span>                            | <span data-ttu-id="611bc-124">$null</span><span class="sxs-lookup"><span data-stu-id="611bc-124">$null</span></span>                          |
| <span data-ttu-id="611bc-125">F**^**</span><span class="sxs-lookup"><span data-stu-id="611bc-125">F**^**</span></span>                          | <span data-ttu-id="611bc-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="611bc-126">PendingConfiguration</span></span> | <span data-ttu-id="611bc-127">Falha</span><span class="sxs-lookup"><span data-stu-id="611bc-127">Failure</span></span>    | <span data-ttu-id="611bc-128">$false</span><span class="sxs-lookup"><span data-stu-id="611bc-128">$false</span></span>        | <span data-ttu-id="611bc-129">$null</span><span class="sxs-lookup"><span data-stu-id="611bc-129">$null</span></span>                        | <span data-ttu-id="611bc-130">F</span><span class="sxs-lookup"><span data-stu-id="611bc-130">F</span></span>                              |
| <span data-ttu-id="611bc-131">S, F</span><span class="sxs-lookup"><span data-stu-id="611bc-131">S,F</span></span>                             | <span data-ttu-id="611bc-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="611bc-132">PendingConfiguration</span></span> | <span data-ttu-id="611bc-133">Falha</span><span class="sxs-lookup"><span data-stu-id="611bc-133">Failure</span></span>    | <span data-ttu-id="611bc-134">$false</span><span class="sxs-lookup"><span data-stu-id="611bc-134">$false</span></span>        | <span data-ttu-id="611bc-135">S</span><span class="sxs-lookup"><span data-stu-id="611bc-135">S</span></span>                            | <span data-ttu-id="611bc-136">F</span><span class="sxs-lookup"><span data-stu-id="611bc-136">F</span></span>                              |
| <span data-ttu-id="611bc-137">F, S</span><span class="sxs-lookup"><span data-stu-id="611bc-137">F,S</span></span>                             | <span data-ttu-id="611bc-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="611bc-138">PendingConfiguration</span></span> | <span data-ttu-id="611bc-139">Falha</span><span class="sxs-lookup"><span data-stu-id="611bc-139">Failure</span></span>    | <span data-ttu-id="611bc-140">$false</span><span class="sxs-lookup"><span data-stu-id="611bc-140">$false</span></span>        | <span data-ttu-id="611bc-141">S</span><span class="sxs-lookup"><span data-stu-id="611bc-141">S</span></span>                            | <span data-ttu-id="611bc-142">F</span><span class="sxs-lookup"><span data-stu-id="611bc-142">F</span></span>                              |
| <span data-ttu-id="611bc-143">S<sub>1</sub>, F, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="611bc-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="611bc-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="611bc-144">PendingConfiguration</span></span> | <span data-ttu-id="611bc-145">Falha</span><span class="sxs-lookup"><span data-stu-id="611bc-145">Failure</span></span>    | <span data-ttu-id="611bc-146">$false</span><span class="sxs-lookup"><span data-stu-id="611bc-146">$false</span></span>        | <span data-ttu-id="611bc-147">S<sub>1</sub>, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="611bc-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="611bc-148">F</span><span class="sxs-lookup"><span data-stu-id="611bc-148">F</span></span>                              |
| <span data-ttu-id="611bc-149">F<sub>1</sub>, S, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="611bc-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="611bc-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="611bc-150">PendingConfiguration</span></span> | <span data-ttu-id="611bc-151">Falha</span><span class="sxs-lookup"><span data-stu-id="611bc-151">Failure</span></span>    | <span data-ttu-id="611bc-152">$false</span><span class="sxs-lookup"><span data-stu-id="611bc-152">$false</span></span>        | <span data-ttu-id="611bc-153">S</span><span class="sxs-lookup"><span data-stu-id="611bc-153">S</span></span>                            | <span data-ttu-id="611bc-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="611bc-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
| <span data-ttu-id="611bc-155">S, r</span><span class="sxs-lookup"><span data-stu-id="611bc-155">S, r</span></span>                            | <span data-ttu-id="611bc-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="611bc-156">PendingReboot</span></span>        | <span data-ttu-id="611bc-157">Sucesso</span><span class="sxs-lookup"><span data-stu-id="611bc-157">Success</span></span>    | <span data-ttu-id="611bc-158">$true</span><span class="sxs-lookup"><span data-stu-id="611bc-158">$true</span></span>         | <span data-ttu-id="611bc-159">S</span><span class="sxs-lookup"><span data-stu-id="611bc-159">S</span></span>                            | <span data-ttu-id="611bc-160">r</span><span class="sxs-lookup"><span data-stu-id="611bc-160">r</span></span>                              |
| <span data-ttu-id="611bc-161">F, r</span><span class="sxs-lookup"><span data-stu-id="611bc-161">F, r</span></span>                            | <span data-ttu-id="611bc-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="611bc-162">PendingReboot</span></span>        | <span data-ttu-id="611bc-163">Falha</span><span class="sxs-lookup"><span data-stu-id="611bc-163">Failure</span></span>    | <span data-ttu-id="611bc-164">$true</span><span class="sxs-lookup"><span data-stu-id="611bc-164">$true</span></span>         | <span data-ttu-id="611bc-165">$null</span><span class="sxs-lookup"><span data-stu-id="611bc-165">$null</span></span>                        | <span data-ttu-id="611bc-166">F, r</span><span class="sxs-lookup"><span data-stu-id="611bc-166">F, r</span></span>                           |
| <span data-ttu-id="611bc-167">r, S</span><span class="sxs-lookup"><span data-stu-id="611bc-167">r, S</span></span>                            | <span data-ttu-id="611bc-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="611bc-168">PendingReboot</span></span>        | <span data-ttu-id="611bc-169">Sucesso</span><span class="sxs-lookup"><span data-stu-id="611bc-169">Success</span></span>    | <span data-ttu-id="611bc-170">$true</span><span class="sxs-lookup"><span data-stu-id="611bc-170">$true</span></span>         | <span data-ttu-id="611bc-171">$null</span><span class="sxs-lookup"><span data-stu-id="611bc-171">$null</span></span>                        | <span data-ttu-id="611bc-172">r</span><span class="sxs-lookup"><span data-stu-id="611bc-172">r</span></span>                              |
| <span data-ttu-id="611bc-173">r, F</span><span class="sxs-lookup"><span data-stu-id="611bc-173">r, F</span></span>                            | <span data-ttu-id="611bc-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="611bc-174">PendingReboot</span></span>        | <span data-ttu-id="611bc-175">Sucesso</span><span class="sxs-lookup"><span data-stu-id="611bc-175">Success</span></span>    | <span data-ttu-id="611bc-176">$true</span><span class="sxs-lookup"><span data-stu-id="611bc-176">$true</span></span>         | <span data-ttu-id="611bc-177">$null</span><span class="sxs-lookup"><span data-stu-id="611bc-177">$null</span></span>                        | <span data-ttu-id="611bc-178">r</span><span class="sxs-lookup"><span data-stu-id="611bc-178">r</span></span>                              |

<span data-ttu-id="611bc-179">^ S<sub>posso</sub>: uma série de recursos que aplicada com êxito F<sub>posso</sub>: uma série de recursos que aplicadas sem êxito r: um recurso que requer o reinício \*</span><span class="sxs-lookup"><span data-stu-id="611bc-179">^ S<sub>i</sub>: A series of resources that applied successfully F<sub>i</sub>: A series of resources that applied unsuccessfully r: A resource that requires reboot \*</span></span>

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```
## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="611bc-180">Melhoramento no cmdlet Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="611bc-180">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="611bc-181">Foram efetuados alguns melhoramentos para o cmdlet Get-DscConfigurationStatus nesta versão.</span><span class="sxs-lookup"><span data-stu-id="611bc-181">A few enhancements have been made to Get-DscConfigurationStatus cmdlet in this release.</span></span> <span data-ttu-id="611bc-182">Anteriormente, a propriedade StartDate de objetos devolvido pelo cmdlet é do tipo cadeia.</span><span class="sxs-lookup"><span data-stu-id="611bc-182">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="611bc-183">Agora, é do tipo Datetime, que permite complexas a seleção e filtragem mais fácil com base nas propriedades de intrínsecos de um objeto de Datetime.</span><span class="sxs-lookup"><span data-stu-id="611bc-183">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>
```powershell
(Get-DscConfigurationStatus).StartDate | fl \*
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

<span data-ttu-id="611bc-184">Segue-se um exemplo que devolve que todos os registos de operação de DSC acontecido no mesmo dia da semana como hoje.</span><span class="sxs-lookup"><span data-stu-id="611bc-184">Following is an example that returns all DSC operation records happened on the same day of week as today.</span></span>
```powershell
(Get-DscConfigurationStatus –All) | where { $\_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="611bc-185">Registos de operações que não faça alterações à configuração do nó (ou seja, apenas operações de leitura) são eliminados.</span><span class="sxs-lookup"><span data-stu-id="611bc-185">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="611bc-186">Por conseguinte, teste-DscConfiguration operações Get-DscConfiguration são já não adulterated no devolveu objetos do cmdlet Get-DscConfigurationStatus.</span><span class="sxs-lookup"><span data-stu-id="611bc-186">Therefore, Test-DscConfiguration, Get-DscConfiguration operations are no longer adulterated in returned objects from Get-DscConfigurationStatus cmdlet.</span></span>
<span data-ttu-id="611bc-187">Registos de operação de definição de configuração de metadados é adicionada para o retorno do cmdlet Get-DscConfigurationStatus.</span><span class="sxs-lookup"><span data-stu-id="611bc-187">Records of meta configuration setting operation is added to the return of Get-DscConfigurationStatus cmdlet.</span></span>

<span data-ttu-id="611bc-188">Segue-se um exemplo do resultado devolvido pelo Get-DscConfigurationStatus – todas as cmdlet.</span><span class="sxs-lookup"><span data-stu-id="611bc-188">Following is an example of result returned from Get-DscConfigurationStatus –All cmdlet.</span></span>
```powershell
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="611bc-189">Melhoramento no cmdlet Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="611bc-189">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>
<span data-ttu-id="611bc-190">O objeto devolvido pelo cmdlet Get-DscLocalConfigurationManager é adicionado um novo campo de LCMStateDetail.</span><span class="sxs-lookup"><span data-stu-id="611bc-190">A new field of LCMStateDetail is added to the object returned from Get-DscLocalConfigurationManager cmdlet.</span></span> <span data-ttu-id="611bc-191">Este campo é preenchido quando LCMState é "Ocupado".</span><span class="sxs-lookup"><span data-stu-id="611bc-191">This field is populated when LCMState is “Busy”.</span></span> <span data-ttu-id="611bc-192">Pode ser obtida pelo seguinte cmdlet:</span><span class="sxs-lookup"><span data-stu-id="611bc-192">It can be retrieved by following cmdlet:</span></span>
```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="611bc-193">Segue-se um exemplo de resultado de uma monitorização contínua numa configuração de que necessita de dois reinícios num nó remoto.</span><span class="sxs-lookup"><span data-stu-id="611bc-193">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>
```powershell
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