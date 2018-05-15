---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: Cmdlets de resolução de problemas
ms.openlocfilehash: 6295a5b99aa19db933569638d84e490ad81eedc7
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.contentlocale: pt-PT
ms.lasthandoff: 05/10/2018
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="9e98a-103">Cmdlets de resolução de problemas</span><span class="sxs-lookup"><span data-stu-id="9e98a-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="9e98a-104">Como resolver "Aviso: Falha ao transferir o pacote 'nome do seu pacote'" problema?</span><span class="sxs-lookup"><span data-stu-id="9e98a-104">How to resolve "WARNING: Package 'your package name' failed to download" issue?</span></span>

<span data-ttu-id="9e98a-105">Foi reportado que instalar módulo módulo de atualização, por vezes, falha ou em algumas máquinas.</span><span class="sxs-lookup"><span data-stu-id="9e98a-105">It is reported that Install-Module or Update-Module sometimes fails on some machines.</span></span>
<span data-ttu-id="9e98a-106">Com base na nossa investigação, é algo com a ligação de rede.</span><span class="sxs-lookup"><span data-stu-id="9e98a-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="9e98a-107">Foi actualizado recentemente fornecedor NuGet para que pode transferir pacotes de forma fiável.</span><span class="sxs-lookup"><span data-stu-id="9e98a-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="9e98a-108">Pode seguir as instruções abaixo para instalar a compilação mais recente do fornecedor do NuGet e, em seguida, instalar ou atualizar o seu módulo.</span><span class="sxs-lookup"><span data-stu-id="9e98a-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="9e98a-109">Vamos utilizar o módulo de 'Azure' como um exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="9e98a-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```