---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 64a29aa87507e65a182837df538c5e695c420cb3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="3e70e-102">Instruções de desinstalação</span><span class="sxs-lookup"><span data-stu-id="3e70e-102">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="3e70e-103">Utilizando a linha de comandos</span><span class="sxs-lookup"><span data-stu-id="3e70e-103">Using Command Prompt</span></span>
1.  <span data-ttu-id="3e70e-104">Abra **linha de comandos.**</span><span class="sxs-lookup"><span data-stu-id="3e70e-104">Open **Command Prompt.**</span></span>
2.  <span data-ttu-id="3e70e-105">Execute o [iniciador de autónomo do Windows Update](https://support.microsoft.com/en-us/kb/934307) conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="3e70e-105">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="3e70e-106">No Windows Server 2012 R2 e Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="3e70e-106">On Windows Server 2012 R2 and Windows 8.1:</span></span>
```powershell
wusa /uninstall /kb:3134758
```
<span data-ttu-id="3e70e-107">No Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="3e70e-107">On Windows Server 2012:</span></span>
```powershell
wusa /uninstall /kb:3134759
```
<span data-ttu-id="3e70e-108">No Windows Server 2008 R2 SP1 e Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="3e70e-108">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="3e70e-109">Utilizando o painel de controlo</span><span class="sxs-lookup"><span data-stu-id="3e70e-109">Using Control Panel</span></span>
1.  <span data-ttu-id="3e70e-110">Abra **painel de controlo.**</span><span class="sxs-lookup"><span data-stu-id="3e70e-110">Open **Control Panel.**</span></span>
2.  <span data-ttu-id="3e70e-111">Abrir **programas**, em seguida, abra **desinstalar um programa.**</span><span class="sxs-lookup"><span data-stu-id="3e70e-111">Open **Programs**, then open **Uninstall a program.**</span></span>
3.  <span data-ttu-id="3e70e-112">Clique em **ver atualizações instaladas.**</span><span class="sxs-lookup"><span data-stu-id="3e70e-112">Click **View installed updates.**</span></span>
4.  <span data-ttu-id="3e70e-113">Selecione **Windows Management Framework 5.0** da lista de atualizações instaladas.</span><span class="sxs-lookup"><span data-stu-id="3e70e-113">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="3e70e-114">Isto corresponde à *KB3134758*, *KB3134759*, ou *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="3e70e-114">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="3e70e-115">Clique em **desinstalar.**</span><span class="sxs-lookup"><span data-stu-id="3e70e-115">Click **Uninstall.**</span></span>
