---
title: Tutorial de GetProc | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851332"
---
# <a name="getproc-tutorial"></a>GetProc Tutorial (Tutorial: GetProc)

Esta secção fornece um tutorial para criar um cmdlet de Get-Proc que é muito parecido com o [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet fornecido pelo Windows PowerShell. Este tutorial disponibiliza os fragmentos de código que ilustram a forma como os cmdlets são implementados e uma explicação do código.

## <a name="topics-in-this-tutorial"></a>Tópicos neste tutorial

Os tópicos neste tutorial foram concebidos para ser lida sequencialmente, com cada tópico Criar sobre o que foi discutido no tópico anterior.

[Criação de um Cmdlet sem parâmetros](./creating-a-cmdlet-without-parameters.md) esta secção descreve como criar um cmdlet que obtém informações do computador local sem o uso de parâmetros e, em seguida, escreve as informações para o pipeline.

[Adicionar parâmetros de entrada de linha de comandos desse processo](./adding-parameters-that-process-command-line-input.md) esta secção descreve como adicionar um parâmetro para o cmdlet Get-Proc para que o cmdlet pode processar a entrada com base nos objetos explícitos transferidos para o cmdlet. A implementação descrita aqui obtém processos com base no respetivo nome e, em seguida, escreve as informações para o pipeline.

[Adicionar parâmetros de entrada do Pipeline esse processo](./adding-parameters-that-process-pipeline-input.md) esta secção descreve como adicionar um parâmetro para o cmdlet Get-Proc para que o cmdlet pode processar objetos passados para ele através do pipeline. O cmdlet de implementação descrito aqui obtém processos com base nos objetos passados para o cmdlet e, em seguida, escreve as informações para o pipeline.

[Adicionar um relatório de erros de não terminação ao seu Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) esta secção descreve como adicionar relatórios para um cmdlet de erros de não terminação. A implementação descrita aqui Deteta erros de não terminação que ocorrem durante o processamento de entrada e grava um registo de erro no fluxo de erro.

## <a name="see-also"></a>Veja Também

[Criação de um Cmdlet sem parâmetros](./creating-a-cmdlet-without-parameters.md)

[Adicionar parâmetros que processam a entrada da linha de comandos](./adding-parameters-that-process-command-line-input.md)

[Adicionar parâmetros do que a entrada de Pipeline de processo](./adding-parameters-that-process-pipeline-input.md)

[Adicionar ao seu Cmdlet do relatório de erros de não terminação](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
