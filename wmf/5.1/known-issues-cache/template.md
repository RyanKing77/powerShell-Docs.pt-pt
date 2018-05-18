---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
title: modelo de exemplo de uma escrita do problema ou limitação conhecida
ms.openlocfilehash: 453d4e40b906ebcab7314f04e138ded271338846
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
><span data-ttu-id="e479c-103">Nota: forneça um título descritivo proposto e uma breve descrição</span><span class="sxs-lookup"><span data-stu-id="e479c-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="e479c-104">Exemplo: Erros de ExecutionPolicy errada</span><span class="sxs-lookup"><span data-stu-id="e479c-104">Example: Erroneous ExecutionPolicy errors</span></span> ##
<span data-ttu-id="e479c-105">No Windows 7, a utilização de módulos do PowerShell e recursos de DSC poderá resultar em erros comunicados sobre ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="e479c-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="e479c-106">Resolução</span><span class="sxs-lookup"><span data-stu-id="e479c-106">Resolution</span></span>

<span data-ttu-id="e479c-107">Para resolver, defina o **ExecutionPolicy** para **RemoteSigned** executando o seguinte comando numa sessão do PowerShell elevada (executar como administrador):</span><span class="sxs-lookup"><span data-stu-id="e479c-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```
