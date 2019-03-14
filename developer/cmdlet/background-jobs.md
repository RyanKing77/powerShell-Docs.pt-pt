---
title: Tarefas em segundo plano | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: ff4fe159eedc47fc69f4d783cd90d2b0e888c0d5
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794710"
---
# <a name="background-jobs"></a><span data-ttu-id="d899d-102">Background Jobs (Tarefas em Segundo Plano)</span><span class="sxs-lookup"><span data-stu-id="d899d-102">Background Jobs</span></span>

<span data-ttu-id="d899d-103">Cmdlets pode executar sua ação internamente ou como um Windows PowerShell*tarefa em segundo plano*.</span><span class="sxs-lookup"><span data-stu-id="d899d-103">Cmdlets can perform their action internally or as a Windows PowerShell*background job*.</span></span> <span data-ttu-id="d899d-104">Quando um cmdlet é executado como uma tarefa em segundo plano, o trabalho é feito de forma assíncrona no seu próprio thread separado do thread do pipeline, que está a utilizar o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d899d-104">When a cmdlet runs as a background job, the work is done asynchronously in its own thread separate from the pipeline thread that the cmdlet is using.</span></span> <span data-ttu-id="d899d-105">Da perspectiva do usuário, quando um cmdlet é executado como uma tarefa em segundo plano, o prompt de comando retorna imediatamente, mesmo que a tarefa demora um período estendido de tempo para concluir, e o utilizador pode continuar sem interrupção enquanto a tarefa é executada.</span><span class="sxs-lookup"><span data-stu-id="d899d-105">From the user perspective, when a cmdlet runs as a background job, the command prompt returns immediately even if the job takes an extended amount of time to complete, and the user can continue without interruption while the job runs.</span></span>

## <a name="background-jobs-child-jobs-and-the-job-repository"></a><span data-ttu-id="d899d-106">Tarefas em segundo plano, tarefas de subordinado e o repositório de tarefa</span><span class="sxs-lookup"><span data-stu-id="d899d-106">Background Jobs, Child Jobs, and the Job Repository</span></span>

<span data-ttu-id="d899d-107">O objeto de tarefa que é devolvido pelos cmdlets que suportam as tarefas em segundo plano define a tarefa.</span><span class="sxs-lookup"><span data-stu-id="d899d-107">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="d899d-108">(A [tarefa de início](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet também retorna um objeto de tarefa.) O nome da tarefa, um identificador que é utilizado para especificar a tarefa, as informações de estado e das tarefas subordinadas são incluídos nesta definição.</span><span class="sxs-lookup"><span data-stu-id="d899d-108">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="d899d-109">A tarefa não realiza o trabalho.</span><span class="sxs-lookup"><span data-stu-id="d899d-109">The job does not perform any of the work.</span></span> <span data-ttu-id="d899d-110">Cada tarefa em segundo plano tem pelo menos uma tarefa filho uma vez que a tarefa subordinada executa o trabalho real.</span><span class="sxs-lookup"><span data-stu-id="d899d-110">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="d899d-111">Quando executa um cmdlet para que o trabalho é executado como uma tarefa em segundo plano, o cmdlet tem de adicionar o trabalho e das tarefas subordinadas para um repositório comum, conhecido como o *repositório de tarefa*.</span><span class="sxs-lookup"><span data-stu-id="d899d-111">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>

<span data-ttu-id="d899d-112">Para obter mais informações sobre a forma como as tarefas em segundo plano são processadas na linha de comandos, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d899d-112">For more information about how background jobs are handled at the command line, see the following:</span></span>

- [<span data-ttu-id="d899d-113">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="d899d-113">about_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [<span data-ttu-id="d899d-114">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="d899d-114">about_Job_Details</span></span>](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [<span data-ttu-id="d899d-115">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="d899d-115">about_Remote_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a><span data-ttu-id="d899d-116">Escrever um Cmdlet que é executado como uma tarefa em segundo plano</span><span class="sxs-lookup"><span data-stu-id="d899d-116">Writing a Cmdlet That Runs as a Background Job</span></span>

<span data-ttu-id="d899d-117">Para escrever um cmdlet que pode ser executado como uma tarefa em segundo plano, tem de concluir as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="d899d-117">To write a cmdlet that can be run as a background job, you must complete the following tasks:</span></span>

- <span data-ttu-id="d899d-118">Definir um `asJob` mudar o parâmetro para que o usuário pode decidir se pretende executar o cmdlet como uma tarefa em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="d899d-118">Define an `asJob` switch parameter so that the user can decide whether to run the cmdlet as a background job.</span></span>

- <span data-ttu-id="d899d-119">Criar um objeto que deriva de [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) classe.</span><span class="sxs-lookup"><span data-stu-id="d899d-119">Create an object that derives from the [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) class.</span></span> <span data-ttu-id="d899d-120">Este objeto pode ser um objeto de tarefa personalizada ou um objeto de trabalho fornecidos pelo Windows PowerShell, como um [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) objeto.</span><span class="sxs-lookup"><span data-stu-id="d899d-120">This object can be a custom job object or a job object provided by Windows PowerShell, such as a [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.</span></span>

- <span data-ttu-id="d899d-121">Num método de processamento de registo, adicione um `if` instrução que Deteta se o cmdlet deve ser executado como uma tarefa em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="d899d-121">In a record processing method, add an `if` statement that detects whether the cmdlet should run as a background job.</span></span>

- <span data-ttu-id="d899d-122">Para objetos de trabalho personalizados, implemente a classe de tarefa.</span><span class="sxs-lookup"><span data-stu-id="d899d-122">For custom job objects, implement the job class.</span></span>

- <span data-ttu-id="d899d-123">Devolve objetos apropriados, dependendo se o cmdlet é executado como uma tarefa em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="d899d-123">Return the appropriate objects, depending on whether the cmdlet is run as a background job.</span></span>

<span data-ttu-id="d899d-124">Para obter um exemplo de código, consulte [como tarefas de suporte](./how-to-support-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="d899d-124">For a code example, see [How to Support Jobs](./how-to-support-jobs.md).</span></span>

## <a name="background-job-related-apis"></a><span data-ttu-id="d899d-125">APIs de relacionados com tarefas em segundo plano</span><span class="sxs-lookup"><span data-stu-id="d899d-125">Background Job-Related APIs</span></span>

<span data-ttu-id="d899d-126">As seguintes APIs são fornecidas pelo Windows PowerShell para gerir tarefas em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="d899d-126">The following APIs are provided by Windows PowerShell to manage background jobs.</span></span>

<span data-ttu-id="d899d-127">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) deriva de objetos de trabalho personalizado.</span><span class="sxs-lookup"><span data-stu-id="d899d-127">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) Derives custom job objects.</span></span> <span data-ttu-id="d899d-128">Esta é uma classe abstrata.</span><span class="sxs-lookup"><span data-stu-id="d899d-128">This is an abstract class.</span></span>

<span data-ttu-id="d899d-129">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) gere e fornece informações sobre as tarefas em segundo plano ativa atual.</span><span class="sxs-lookup"><span data-stu-id="d899d-129">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) Manages and provides information about the current active background jobs.</span></span>

<span data-ttu-id="d899d-130">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) define o estado da tarefa em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="d899d-130">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) Defines the state of the background job.</span></span> <span data-ttu-id="d899d-131">Estados incluem iniciado e parado em execução.</span><span class="sxs-lookup"><span data-stu-id="d899d-131">States include Started, Running, and Stopped.</span></span>

<span data-ttu-id="d899d-132">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) fornece informações sobre o estado de uma tarefa em segundo plano e, se alterar o último estado foi causada por um erro, o motivo pelo qual a tarefa introduziu o respetivo estado atual.</span><span class="sxs-lookup"><span data-stu-id="d899d-132">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) Provides information about the state of a background job and, if the last state change was caused by an error, the reason the job entered its current state.</span></span>

<span data-ttu-id="d899d-133">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) fornece os argumentos de um evento que é gerado quando uma tarefa em segundo plano muda de estado.</span><span class="sxs-lookup"><span data-stu-id="d899d-133">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) Provides the arguments for an event that is raised when a background job changes state.</span></span>

## <a name="windows-powershell-job-cmdlets"></a><span data-ttu-id="d899d-134">Cmdlets do Windows PowerShell de tarefa</span><span class="sxs-lookup"><span data-stu-id="d899d-134">Windows PowerShell Job Cmdlets</span></span>

<span data-ttu-id="d899d-135">Os cmdlets seguintes são fornecidos pelo Windows PowerShell para gerir tarefas em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="d899d-135">The following cmdlets are provided by Windows PowerShell to manage background jobs.</span></span>

[<span data-ttu-id="d899d-136">Get-Job</span><span class="sxs-lookup"><span data-stu-id="d899d-136">Get-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

<span data-ttu-id="d899d-137">Obtém as tarefas do Windows PowerShell em segundo plano que estão em execução na sessão atual.</span><span class="sxs-lookup"><span data-stu-id="d899d-137">Gets Windows PowerShell background jobs that are running in the current session.</span></span>

[<span data-ttu-id="d899d-138">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="d899d-138">Receive-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

<span data-ttu-id="d899d-139">Obtém os resultados das tarefas de segundo plano do Windows PowerShell na sessão atual.</span><span class="sxs-lookup"><span data-stu-id="d899d-139">Gets the results of the Windows PowerShell background jobs in the current session.</span></span>

[<span data-ttu-id="d899d-140">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="d899d-140">Remove-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

<span data-ttu-id="d899d-141">Elimina uma tarefa em segundo plano do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d899d-141">Deletes a Windows PowerShell background job.</span></span>

[<span data-ttu-id="d899d-142">Start-Job</span><span class="sxs-lookup"><span data-stu-id="d899d-142">Start-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

<span data-ttu-id="d899d-143">Inicia uma tarefa de plano de fundo do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d899d-143">Starts a Windows PowerShell background job.</span></span>

[<span data-ttu-id="d899d-144">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="d899d-144">Stop-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

<span data-ttu-id="d899d-145">Interrompe uma tarefa de plano de fundo do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d899d-145">Stops a Windows PowerShell background job.</span></span>

[<span data-ttu-id="d899d-146">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="d899d-146">Wait-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

<span data-ttu-id="d899d-147">Suprime a linha de comandos até que uma ou todas as tarefas de segundo plano do Windows PowerShell em execução na sessão estejam concluídas.</span><span class="sxs-lookup"><span data-stu-id="d899d-147">Suppresses the command prompt until one or all of the Windows PowerShell background jobs running in the session are complete.</span></span>

## <a name="see-also"></a><span data-ttu-id="d899d-148">Veja Também</span><span class="sxs-lookup"><span data-stu-id="d899d-148">See Also</span></span>

[<span data-ttu-id="d899d-149">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d899d-149">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
