---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
title: modelo de exemplo de um writeup conhecido de problema ou limitação
ms.openlocfilehash: 8c1004e16f78913174af2e519e451f6fd9f30ff7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055552"
---
 ><span data-ttu-id="5eef7-103">Nota: fornecer um título descritivo proposto e uma breve descrição</span><span class="sxs-lookup"><span data-stu-id="5eef7-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="5eef7-104">Exemplo: Erros de ExecutionPolicy errados</span><span class="sxs-lookup"><span data-stu-id="5eef7-104">Example: Erroneous ExecutionPolicy errors</span></span>
<span data-ttu-id="5eef7-105">No Windows 7, a utilização de módulos do PowerShell e recursos de DSC pode resultar em erros comunicados sobre ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="5eef7-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="5eef7-106">Resolução</span><span class="sxs-lookup"><span data-stu-id="5eef7-106">Resolution</span></span>

<span data-ttu-id="5eef7-107">Para resolver, definir o **ExecutionPolicy** ao **RemoteSigned** executando o seguinte comando numa sessão do PowerShell elevada (executar como administrador):</span><span class="sxs-lookup"><span data-stu-id="5eef7-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```
