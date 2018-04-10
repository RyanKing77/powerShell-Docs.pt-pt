---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: modelo de exemplo de uma escrita do problema ou limitação conhecida
ms.openlocfilehash: cecf31127aaa1942471877a2056230ab592bd095
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
><span data-ttu-id="e1b96-103">Nota: forneça um título descritivo proposto e uma breve descrição</span><span class="sxs-lookup"><span data-stu-id="e1b96-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="e1b96-104">Exemplo: Erros de ExecutionPolicy errada</span><span class="sxs-lookup"><span data-stu-id="e1b96-104">Example: Erroneous ExecutionPolicy errors</span></span> ##
<span data-ttu-id="e1b96-105">No Windows 7, a utilização de módulos do PowerShell e recursos de DSC poderá resultar em erros comunicados sobre ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="e1b96-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="e1b96-106">Resolução</span><span class="sxs-lookup"><span data-stu-id="e1b96-106">Resolution</span></span>

<span data-ttu-id="e1b96-107">Para resolver, defina o **ExecutionPolicy** para **RemoteSigned** executando o seguinte comando numa sessão do PowerShell elevada (executar como administrador):</span><span class="sxs-lookup"><span data-stu-id="e1b96-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```