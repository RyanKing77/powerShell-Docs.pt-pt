---
ms.date: 06/12/2017
contributor: manikb
keywords: cmdlet do powershell do galeria, psget
title: Cmdlets de resolução de problemas
ms.openlocfilehash: f5cd9c0cc23fef5891bf02c10b6541ab0f9d418a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084186"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="1c4f8-103">Cmdlets de resolução de problemas</span><span class="sxs-lookup"><span data-stu-id="1c4f8-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="1c4f8-104">Como resolver "Aviso: Não foi possível transferir o pacote 'nome do seu pacote' "problema</span><span class="sxs-lookup"><span data-stu-id="1c4f8-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="1c4f8-105">É reportado que `Install-Module` ou `Update-Module` falhar, às vezes, em algumas máquinas.</span><span class="sxs-lookup"><span data-stu-id="1c4f8-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span>
<span data-ttu-id="1c4f8-106">Com base na nossa investigação, é algo a ver com a ligação de rede.</span><span class="sxs-lookup"><span data-stu-id="1c4f8-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="1c4f8-107">Recentemente atualizámos fornecedor NuGet, de modo a que pode transferir pacotes de forma fiável.</span><span class="sxs-lookup"><span data-stu-id="1c4f8-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="1c4f8-108">Pode seguir as instruções abaixo para instalar a compilação mais recente do fornecedor NuGet e, em seguida, instalar ou atualizar o seu módulo.</span><span class="sxs-lookup"><span data-stu-id="1c4f8-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="1c4f8-109">Vamos utilizar o módulo "Azure" como exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="1c4f8-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```
