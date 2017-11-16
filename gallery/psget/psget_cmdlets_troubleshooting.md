---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: psget_cmdlets_troubleshooting
ms.openlocfilehash: ccb39f44e8d11f1e2a912da0c4f18b700e836c91
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="a31c1-103">Como resolver "Aviso: Falha ao transferir o pacote 'nome do seu pacote'" problema?</span><span class="sxs-lookup"><span data-stu-id="a31c1-103">How to resolve "WARNING: Package 'your package name' failed to download" issue?</span></span>




<span data-ttu-id="a31c1-104">Foi reportado que instalar módulo módulo de atualização, por vezes, falha ou em algumas máquinas.</span><span class="sxs-lookup"><span data-stu-id="a31c1-104">It is reported that Install-Module or Update-Module sometimes fails on some machines.</span></span>
<span data-ttu-id="a31c1-105">Com base na nossa investigação, é algo com a ligação de rede.</span><span class="sxs-lookup"><span data-stu-id="a31c1-105">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="a31c1-106">Foi actualizado recentemente fornecedor NuGet para que pode transferir pacotes de forma fiável.</span><span class="sxs-lookup"><span data-stu-id="a31c1-106">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="a31c1-107">Pode seguir as instruções abaixo para instalar a compilação mais recente do fornecedor do NuGet e, em seguida, instalar ou atualizar o seu módulo.</span><span class="sxs-lookup"><span data-stu-id="a31c1-107">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="a31c1-108">Vamos utilizar o módulo de 'Azure' como um exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="a31c1-108">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

