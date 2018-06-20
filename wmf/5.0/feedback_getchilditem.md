---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: d9f1ca10c948b06b234e17f688b8f899ed41c5d6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221906"
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="afdf9-102">Tem de GET-ChildItem - parâmetro de profundidade</span><span class="sxs-lookup"><span data-stu-id="afdf9-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="afdf9-103">**Get-ChildItem** tem agora um **– profundidade** parâmetro a utilizar com **-Recurse** para limitar a recursão:</span><span class="sxs-lookup"><span data-stu-id="afdf9-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="afdf9-104">PS c:\\utilizadores\\slee\\transfere\\exemplo&gt; Get-ChildItem-Recurse - profundidade 0</span><span class="sxs-lookup"><span data-stu-id="afdf9-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="afdf9-105">Diretório: C\\utilizadores\\slee\\transfere\\exemplo</span><span class="sxs-lookup"><span data-stu-id="afdf9-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="afdf9-106">Nome de comprimento de LastWriteTime modo</span><span class="sxs-lookup"><span data-stu-id="afdf9-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="afdf9-107">---d 4/14/2015 as 17:36:00 Depth0</span><span class="sxs-lookup"><span data-stu-id="afdf9-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="afdf9-108">-a---4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="afdf9-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="afdf9-109">-a---4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="afdf9-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="afdf9-110">-a---4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="afdf9-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="afdf9-111">PS c:\\utilizadores\\slee\\transfere\\exemplo&gt; Get-ChildItem-Recurse - profundidade 1</span><span class="sxs-lookup"><span data-stu-id="afdf9-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="afdf9-112">Diretório: C\\utilizadores\\slee\\transfere\\exemplo</span><span class="sxs-lookup"><span data-stu-id="afdf9-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="afdf9-113">Nome de comprimento de LastWriteTime modo</span><span class="sxs-lookup"><span data-stu-id="afdf9-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="afdf9-114">---d 4/14/2015 as 17:36:00 Depth0</span><span class="sxs-lookup"><span data-stu-id="afdf9-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="afdf9-115">-a---4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="afdf9-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="afdf9-116">-a---4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="afdf9-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="afdf9-117">-a---4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="afdf9-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="afdf9-118">Diretório: C\\utilizadores\\slee\\transfere\\exemplo\\Depth0</span><span class="sxs-lookup"><span data-stu-id="afdf9-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="afdf9-119">Nome de comprimento de LastWriteTime modo</span><span class="sxs-lookup"><span data-stu-id="afdf9-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="afdf9-120">---d 4/14/2015 5:33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="afdf9-120">d----- 4/14/2015 5:33 PM Depth1</span></span>
