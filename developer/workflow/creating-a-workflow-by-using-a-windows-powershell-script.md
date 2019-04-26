---
title: A criação de um fluxo de trabalho usando um Script do PowerShell do Windows | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080378"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a>Creating a Workflow by Using a Windows PowerShell Script (Criar um Fluxo de Trabalho Através de um Script do Windows PowerShell)

Pode criar um fluxo de trabalho ao escrever um script do Windows PowerShell. Para criar um fluxo de trabalho, utilize a palavra-chave de fluxo de trabalho seguida de um nome para o fluxo de trabalho antes do corpo do script. Por exemplo:

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

Encontre o fluxo de trabalho da mesma forma que faria com qualquer outro comando do Windows PowerShell.

## <a name="implementing-parallel-and-sequence"></a>Implementando Parallel e Sequence

[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) suporta a execução das atividades em paralelo. Para implementar esta capacidade num script do Windows PowerShell, utilize o `parallel` palavra-chave à frente de um bloco de scripts. Também pode utilizar o `foreach -parallel` construção para iterar uma coleção de objetos em paralelo. Para executar um grupo de atividades por ordem sequencial dentro de um bloco paralelo, coloque esse grupo de atividades num bloco de script e precedência sobre o bloco com a palavra-chave de sequência.

## <a name="joining-computers-to-a-domain"></a>Associar computadores a um domínio

O seguinte script cria um fluxo de trabalho que verifica o estado do domínio de um grupo de computadores especificadas pelo utilizador, associa-a um domínio, se já não estão associados e, em seguida, verifica o estado novamente. Esta é uma versão de script do fluxo de trabalho XAML explicado [criar um fluxo de trabalho com o Windows PowerShell atividades](./creating-a-workflow-with-windows-powershell-activities.md).

```powershell
workflow Join-Domain
{
    param([string[]] $ComputerName, [PSCredential] $DomainCred, [PsCredential] $MachineCred)

    foreach -parallel($Computer in $ComputerName)
    {
        sequence {
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        Add-Computer -PSComputerName $Computer -PSCredential $DomainCred
        Restart-Computer -ComputerName $Computer -Credential $MachineCred -For PowerShell -Force -Wait -PSComputerName ""
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        }
    }
 }

```