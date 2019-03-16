---
title: Erros de terminação | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b804e738-aefa-41bb-9649-f9ed897fd96c
caps.latest.revision: 8
ms.openlocfilehash: d1967fe7996f75ec5229920f7ec49aa5ff6bdbfd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059240"
---
# <a name="terminating-errors"></a>Terminating Errors (Erros de Terminação)

Este tópico aborda o método usado para relatar erros de terminação. Ele também aborda como chamar o método a partir do cmdlet, e ele discute as exceções que podem ser devolvidas pelo tempo de execução do Windows PowerShell, quando o método é chamado.

Quando acabar erro ocorre, o cmdlet deve reportar o erro ao chamar o [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) método. Este método permite que o cmdlet enviar um registo de erro que descreve a condição que causou o erro de terminação. Para obter mais informações sobre os registos de erro, consulte [registos de erros do Windows PowerShell](./windows-powershell-error-records.md).

Quando o [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) método é chamado, o tempo de execução do Windows PowerShell permanentemente interrompe a execução do pipeline e lança um [ System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) exceção. Qualquer tentativa subseqüente de chamar [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError), ou várias outras APIs faz com que essas chamadas lançar um [ System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) exceção.

O [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) exceção também pode ocorrer se o outro cmdlet no pipeline relatar um erro de terminação, se o utilizador recebe o pedido para parar o pipeline, ou se o pipeline foi parado antes da conclusão por qualquer motivo. O cmdlet não tem de capturar a [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) exceção a menos que ele tem de limpar abrir recursos ou o seu estado interno.

Cmdlets de escrever qualquer número de objetos de saída ou erros de não terminação antes de comunicar um erro de terminação. No entanto, o erro de terminação permanentemente deixa o pipeline e nenhuma saída ainda mais, erros, a terminar ou podem ser reportados erros de não terminação.

Pode chamar cmdlets [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) apenas a partir do thread que chamou a [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), ou [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método de processamento de entrada. Não tente chamar [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) ou [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) de outro thread. Em vez disso, devem ser comunicados erros de volta para o thread principal.

É possível que um cmdlet para lançar uma exceção na sua implementação do [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), ou [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método. Qualquer exceção gerada entre esses métodos (exceto para algumas condições de erro grave que parar o anfitrião do Windows PowerShell) é interpretada como um erro de terminação que para o pipeline, mas não de Windows PowerShell como um todo. (Isto aplica-se apenas ao thread principal do cmdlet. Exceções não identificadas em threads gerados pelo cmdlet, em geral, pare o anfitrião do Windows PowerShell.) Recomendamos que utilize [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) em vez de gerar uma exceção porque o registo de erros fornece informações adicionais sobre a condição de erro, que é útil para o utilizador final. Cmdlets devem honrar a diretriz de código gerenciado contra capturando e lidar com todas as exceções (`catch (Exception e)`). Converta somente as exceções de tipos conhecidos e esperados em registos de erro.

## <a name="see-also"></a>Veja Também

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Registos de erro do PowerShell do Windows](./windows-powershell-error-records.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
