---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 385bb7223b19c8ace8088ba469e543721a527b99
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057530"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="5ff2b-102">Instruções de desinstalação</span><span class="sxs-lookup"><span data-stu-id="5ff2b-102">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="5ff2b-103">Usando a linha de comandos</span><span class="sxs-lookup"><span data-stu-id="5ff2b-103">Using Command Prompt</span></span>
1.  <span data-ttu-id="5ff2b-104">Abra **Prompt de comando.**</span><span class="sxs-lookup"><span data-stu-id="5ff2b-104">Open **Command Prompt.**</span></span>
2.  <span data-ttu-id="5ff2b-105">Executar o [Windows Update autónomo iniciador](https://support.microsoft.com/en-us/kb/934307) conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="5ff2b-105">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="5ff2b-106">No Windows Server 2012 R2 e Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="5ff2b-106">On Windows Server 2012 R2 and Windows 8.1:</span></span>
```powershell
wusa /uninstall /kb:3134758
```
<span data-ttu-id="5ff2b-107">No Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="5ff2b-107">On Windows Server 2012:</span></span>
```powershell
wusa /uninstall /kb:3134759
```
<span data-ttu-id="5ff2b-108">No Windows Server 2008 R2 SP1 e Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="5ff2b-108">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="5ff2b-109">Usando o painel de controlo</span><span class="sxs-lookup"><span data-stu-id="5ff2b-109">Using Control Panel</span></span>
1.  <span data-ttu-id="5ff2b-110">Abra **painel de controlo.**</span><span class="sxs-lookup"><span data-stu-id="5ff2b-110">Open **Control Panel.**</span></span>
2.  <span data-ttu-id="5ff2b-111">Abra **programas**, em seguida, abra **desinstalar um programa.**</span><span class="sxs-lookup"><span data-stu-id="5ff2b-111">Open **Programs**, then open **Uninstall a program.**</span></span>
3.  <span data-ttu-id="5ff2b-112">Clique em **ver atualizações instaladas.**</span><span class="sxs-lookup"><span data-stu-id="5ff2b-112">Click **View installed updates.**</span></span>
4.  <span data-ttu-id="5ff2b-113">Selecione **Windows Management Framework 5.0** na lista de atualizações instaladas.</span><span class="sxs-lookup"><span data-stu-id="5ff2b-113">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="5ff2b-114">Isso corresponde à *KB3134758*, *KB3134759*, ou *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="5ff2b-114">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="5ff2b-115">Clique em **desinstalar.**</span><span class="sxs-lookup"><span data-stu-id="5ff2b-115">Click **Uninstall.**</span></span>
