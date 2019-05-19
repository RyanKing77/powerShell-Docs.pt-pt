---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Desinstalar o WMF 5.0
ms.openlocfilehash: f562a4a4506bfdede6b23bd186b80f40cc9e45ca
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856190"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="c1754-103">Instruções de desinstalação</span><span class="sxs-lookup"><span data-stu-id="c1754-103">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="c1754-104">Usando a linha de comandos</span><span class="sxs-lookup"><span data-stu-id="c1754-104">Using Command Prompt</span></span>

1. <span data-ttu-id="c1754-105">Abra **Prompt de comando.**</span><span class="sxs-lookup"><span data-stu-id="c1754-105">Open **Command Prompt.**</span></span>
2. <span data-ttu-id="c1754-106">Executar o [Windows Update autónomo iniciador](https://support.microsoft.com/en-us/kb/934307) conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="c1754-106">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="c1754-107">No Windows Server 2012 R2 e Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="c1754-107">On Windows Server 2012 R2 and Windows 8.1:</span></span>

```powershell
wusa /uninstall /kb:3134758
```

<span data-ttu-id="c1754-108">No Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="c1754-108">On Windows Server 2012:</span></span>

```powershell
wusa /uninstall /kb:3134759
```

<span data-ttu-id="c1754-109">No Windows Server 2008 R2 SP1 e Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="c1754-109">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>

```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="c1754-110">Usando o painel de controlo</span><span class="sxs-lookup"><span data-stu-id="c1754-110">Using Control Panel</span></span>

1. <span data-ttu-id="c1754-111">Abra **painel de controlo.**</span><span class="sxs-lookup"><span data-stu-id="c1754-111">Open **Control Panel.**</span></span>
2. <span data-ttu-id="c1754-112">Abra **programas**, em seguida, abra **desinstalar um programa.**</span><span class="sxs-lookup"><span data-stu-id="c1754-112">Open **Programs**, then open **Uninstall a program.**</span></span>
3. <span data-ttu-id="c1754-113">Clique em **ver atualizações instaladas.**</span><span class="sxs-lookup"><span data-stu-id="c1754-113">Click **View installed updates.**</span></span>
4. <span data-ttu-id="c1754-114">Selecione **Windows Management Framework 5.0** na lista de atualizações instaladas.</span><span class="sxs-lookup"><span data-stu-id="c1754-114">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="c1754-115">Isso corresponde à *KB3134758*, *KB3134759*, ou *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="c1754-115">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="c1754-116">Clique em **desinstalar.**</span><span class="sxs-lookup"><span data-stu-id="c1754-116">Click **Uninstall.**</span></span>
