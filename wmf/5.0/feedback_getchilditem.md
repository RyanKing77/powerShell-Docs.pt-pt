---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: cc5d2d799c1292f68de5fb2360fcba220c2c010b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085300"
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="9d41d-102">Tem de GET-ChildItem - parâmetro de profundidade</span><span class="sxs-lookup"><span data-stu-id="9d41d-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="9d41d-103">**Get-ChildItem** tem agora um **– profundidade** parâmetro, que utiliza com o **– Recurse** para limitar a recursão:</span><span class="sxs-lookup"><span data-stu-id="9d41d-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="9d41d-104">PS c:\\usuários\\slee\\Downloads\\exemplo&gt; Get-ChildItem-Recurse - profundidade de 0</span><span class="sxs-lookup"><span data-stu-id="9d41d-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="9d41d-105">Diretório: C:\\usuários\\slee\\Downloads\\exemplo</span><span class="sxs-lookup"><span data-stu-id="9d41d-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="9d41d-106">Nome de comprimento de LastWriteTime de modo</span><span class="sxs-lookup"><span data-stu-id="9d41d-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="9d41d-107">---1!d 4/14/2015 5 36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="9d41d-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="9d41d-108">-a---4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="9d41d-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="9d41d-109">-a---4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="9d41d-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="9d41d-110">-a---4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="9d41d-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="9d41d-111">PS c:\\usuários\\slee\\Downloads\\exemplo&gt; Get-ChildItem-Recurse - 1 de profundidade</span><span class="sxs-lookup"><span data-stu-id="9d41d-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="9d41d-112">Diretório: C:\\usuários\\slee\\Downloads\\exemplo</span><span class="sxs-lookup"><span data-stu-id="9d41d-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="9d41d-113">Nome de comprimento de LastWriteTime de modo</span><span class="sxs-lookup"><span data-stu-id="9d41d-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="9d41d-114">---1!d 4/14/2015 5 36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="9d41d-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="9d41d-115">-a---4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="9d41d-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="9d41d-116">-a---4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="9d41d-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="9d41d-117">-a---4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="9d41d-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="9d41d-118">Diretório: C:\\usuários\\slee\\Downloads\\exemplo\\Depth0</span><span class="sxs-lookup"><span data-stu-id="9d41d-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="9d41d-119">Nome de comprimento de LastWriteTime de modo</span><span class="sxs-lookup"><span data-stu-id="9d41d-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="9d41d-120">---1!d 4/14/2015 5 33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="9d41d-120">d----- 4/14/2015 5:33 PM Depth1</span></span>
