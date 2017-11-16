---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
title: "modelo de exemplo de uma escrita do problema ou limitação conhecida"
ms.openlocfilehash: b93393b2c84e76a301e6406d1388e82e95a2959c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
><span data-ttu-id="a1051-103">Nota: forneça um título descritivo proposto e uma breve descrição</span><span class="sxs-lookup"><span data-stu-id="a1051-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="a1051-104">Exemplo: Erros de ExecutionPolicy errada</span><span class="sxs-lookup"><span data-stu-id="a1051-104">Example: Erroneous ExecutionPolicy errors</span></span> ##
<span data-ttu-id="a1051-105">No Windows 7, a utilização de módulos do PowerShell e recursos de DSC poderá resultar em erros comunicados sobre ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="a1051-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="a1051-106">Resolução</span><span class="sxs-lookup"><span data-stu-id="a1051-106">Resolution</span></span>

<span data-ttu-id="a1051-107">Para resolver, defina o **ExecutionPolicy** para **RemoteSigned** executando o seguinte comando numa sessão do PowerShell elevada (executar como administrador):</span><span class="sxs-lookup"><span data-stu-id="a1051-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

