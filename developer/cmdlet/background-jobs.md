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
# <a name="background-jobs"></a>Background Jobs (Tarefas em Segundo Plano)

Cmdlets pode executar sua ação internamente ou como um Windows PowerShell*tarefa em segundo plano*. Quando um cmdlet é executado como uma tarefa em segundo plano, o trabalho é feito de forma assíncrona no seu próprio thread separado do thread do pipeline, que está a utilizar o cmdlet. Da perspectiva do usuário, quando um cmdlet é executado como uma tarefa em segundo plano, o prompt de comando retorna imediatamente, mesmo que a tarefa demora um período estendido de tempo para concluir, e o utilizador pode continuar sem interrupção enquanto a tarefa é executada.

## <a name="background-jobs-child-jobs-and-the-job-repository"></a>Tarefas em segundo plano, tarefas de subordinado e o repositório de tarefa

O objeto de tarefa que é devolvido pelos cmdlets que suportam as tarefas em segundo plano define a tarefa. (A [tarefa de início](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet também retorna um objeto de tarefa.) O nome da tarefa, um identificador que é utilizado para especificar a tarefa, as informações de estado e das tarefas subordinadas são incluídos nesta definição. A tarefa não realiza o trabalho. Cada tarefa em segundo plano tem pelo menos uma tarefa filho uma vez que a tarefa subordinada executa o trabalho real. Quando executa um cmdlet para que o trabalho é executado como uma tarefa em segundo plano, o cmdlet tem de adicionar o trabalho e das tarefas subordinadas para um repositório comum, conhecido como o *repositório de tarefa*.

Para obter mais informações sobre a forma como as tarefas em segundo plano são processadas na linha de comandos, consulte o seguinte:

- [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [about_Job_Details](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [about_Remote_Jobs](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a>Escrever um Cmdlet que é executado como uma tarefa em segundo plano

Para escrever um cmdlet que pode ser executado como uma tarefa em segundo plano, tem de concluir as seguintes tarefas:

- Definir um `asJob` mudar o parâmetro para que o usuário pode decidir se pretende executar o cmdlet como uma tarefa em segundo plano.

- Criar um objeto que deriva de [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) classe. Este objeto pode ser um objeto de tarefa personalizada ou um objeto de trabalho fornecidos pelo Windows PowerShell, como um [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) objeto.

- Num método de processamento de registo, adicione um `if` instrução que Deteta se o cmdlet deve ser executado como uma tarefa em segundo plano.

- Para objetos de trabalho personalizados, implemente a classe de tarefa.

- Devolve objetos apropriados, dependendo se o cmdlet é executado como uma tarefa em segundo plano.

Para obter um exemplo de código, consulte [como tarefas de suporte](./how-to-support-jobs.md).

## <a name="background-job-related-apis"></a>APIs de relacionados com tarefas em segundo plano

As seguintes APIs são fornecidas pelo Windows PowerShell para gerir tarefas em segundo plano.

[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) deriva de objetos de trabalho personalizado. Esta é uma classe abstrata.

[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) gere e fornece informações sobre as tarefas em segundo plano ativa atual.

[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) define o estado da tarefa em segundo plano. Estados incluem iniciado e parado em execução.

[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) fornece informações sobre o estado de uma tarefa em segundo plano e, se alterar o último estado foi causada por um erro, o motivo pelo qual a tarefa introduziu o respetivo estado atual.

[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) fornece os argumentos de um evento que é gerado quando uma tarefa em segundo plano muda de estado.

## <a name="windows-powershell-job-cmdlets"></a>Cmdlets do Windows PowerShell de tarefa

Os cmdlets seguintes são fornecidos pelo Windows PowerShell para gerir tarefas em segundo plano.

[Get-Job](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

Obtém as tarefas do Windows PowerShell em segundo plano que estão em execução na sessão atual.

[Receive-Job](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

Obtém os resultados das tarefas de segundo plano do Windows PowerShell na sessão atual.

[Remove-Job](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

Elimina uma tarefa em segundo plano do Windows PowerShell.

[Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

Inicia uma tarefa de plano de fundo do Windows PowerShell.

[Stop-Job](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

Interrompe uma tarefa de plano de fundo do Windows PowerShell.

[Wait-Job](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

Suprime a linha de comandos até que uma ou todas as tarefas de segundo plano do Windows PowerShell em execução na sessão estejam concluídas.

## <a name="see-also"></a>Veja Também

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
