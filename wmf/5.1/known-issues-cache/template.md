---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
title: modelo de exemplo de um writeup conhecido de problema ou limitação
ms.openlocfilehash: 8c1004e16f78913174af2e519e451f6fd9f30ff7
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794501"
---
 ><span data-ttu-id="4f85c-103">Nota: fornecer um título descritivo proposto e uma breve descrição</span><span class="sxs-lookup"><span data-stu-id="4f85c-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="4f85c-104">Exemplo: Erros de ExecutionPolicy errados</span><span class="sxs-lookup"><span data-stu-id="4f85c-104">Example: Erroneous ExecutionPolicy errors</span></span>
<span data-ttu-id="4f85c-105">No Windows 7, a utilização de módulos do PowerShell e recursos de DSC pode resultar em erros comunicados sobre ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="4f85c-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="4f85c-106">Resolução</span><span class="sxs-lookup"><span data-stu-id="4f85c-106">Resolution</span></span>

<span data-ttu-id="4f85c-107">Para resolver, definir o **ExecutionPolicy** ao **RemoteSigned** executando o seguinte comando numa sessão do PowerShell elevada (executar como administrador):</span><span class="sxs-lookup"><span data-stu-id="4f85c-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```
