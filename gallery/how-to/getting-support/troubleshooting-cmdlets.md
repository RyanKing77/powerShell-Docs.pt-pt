---
ms.date: 06/12/2017
contributor: manikb
keywords: cmdlet do powershell do galeria, psget
title: Cmdlets de resolução de problemas
ms.openlocfilehash: e8890cb6bbe661b8524d83cabf91483acbde8095
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="a345b-103">Cmdlets de resolução de problemas</span><span class="sxs-lookup"><span data-stu-id="a345b-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="a345b-104">Como resolver "Aviso: Falha ao transferir o pacote 'nome do seu pacote'" problema?</span><span class="sxs-lookup"><span data-stu-id="a345b-104">How to resolve "WARNING: Package 'your package name' failed to download" issue?</span></span>

<span data-ttu-id="a345b-105">Foi reportado que instalar módulo módulo de atualização, por vezes, falha ou em algumas máquinas.</span><span class="sxs-lookup"><span data-stu-id="a345b-105">It is reported that Install-Module or Update-Module sometimes fails on some machines.</span></span>
<span data-ttu-id="a345b-106">Com base na nossa investigação, é algo com a ligação de rede.</span><span class="sxs-lookup"><span data-stu-id="a345b-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="a345b-107">Foi actualizado recentemente fornecedor NuGet para que pode transferir pacotes de forma fiável.</span><span class="sxs-lookup"><span data-stu-id="a345b-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="a345b-108">Pode seguir as instruções abaixo para instalar a compilação mais recente do fornecedor do NuGet e, em seguida, instalar ou atualizar o seu módulo.</span><span class="sxs-lookup"><span data-stu-id="a345b-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="a345b-109">Vamos utilizar o módulo de 'Azure' como um exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="a345b-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```