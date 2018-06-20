---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 08f431c27cd0ee769518b5246af2fa95aa499d54
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34217996"
---
# <a name="new-temporaryfile"></a><span data-ttu-id="6ce2f-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="6ce2f-102">New-TemporaryFile</span></span>
<span data-ttu-id="6ce2f-103">Por vezes nos scripts, terá de criar um ficheiro temporário.</span><span class="sxs-lookup"><span data-stu-id="6ce2f-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="6ce2f-104">Pode facilmente fazê-com o **New-TemporaryFile** cmdlet:</span><span class="sxs-lookup"><span data-stu-id="6ce2f-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="6ce2f-105">PS c:\\ &gt; $tempFile = New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="6ce2f-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="6ce2f-106">PS c:\\ &gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="6ce2f-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="6ce2f-107">C:\\utilizadores\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="6ce2f-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>
