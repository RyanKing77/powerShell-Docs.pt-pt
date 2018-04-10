---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 62cccabd7c63c6ba928fc2bf8addd3d11483e90f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="a48db-102">Tem de GET-ChildItem - parâmetro de profundidade</span><span class="sxs-lookup"><span data-stu-id="a48db-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="a48db-103">**Get-ChildItem** tem agora um **– profundidade** parâmetro a utilizar com **-Recurse** para limitar a recursão:</span><span class="sxs-lookup"><span data-stu-id="a48db-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="a48db-104">PS c:\\utilizadores\\slee\\transfere\\exemplo&gt; Get-ChildItem-Recurse - profundidade 0</span><span class="sxs-lookup"><span data-stu-id="a48db-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="a48db-105">Diretório: C\\utilizadores\\slee\\transfere\\exemplo</span><span class="sxs-lookup"><span data-stu-id="a48db-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="a48db-106">Nome de comprimento de LastWriteTime modo</span><span class="sxs-lookup"><span data-stu-id="a48db-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="a48db-107">---d 4/14/2015 as 17:36:00 Depth0</span><span class="sxs-lookup"><span data-stu-id="a48db-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="a48db-108">-a---4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="a48db-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="a48db-109">-a---4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="a48db-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="a48db-110">-a---4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="a48db-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="a48db-111">PS c:\\utilizadores\\slee\\transfere\\exemplo&gt; Get-ChildItem-Recurse - profundidade 1</span><span class="sxs-lookup"><span data-stu-id="a48db-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="a48db-112">Diretório: C\\utilizadores\\slee\\transfere\\exemplo</span><span class="sxs-lookup"><span data-stu-id="a48db-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="a48db-113">Nome de comprimento de LastWriteTime modo</span><span class="sxs-lookup"><span data-stu-id="a48db-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="a48db-114">---d 4/14/2015 as 17:36:00 Depth0</span><span class="sxs-lookup"><span data-stu-id="a48db-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="a48db-115">-a---4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="a48db-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="a48db-116">-a---4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="a48db-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="a48db-117">-a---4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="a48db-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="a48db-118">Diretório: C\\utilizadores\\slee\\transfere\\exemplo\\Depth0</span><span class="sxs-lookup"><span data-stu-id="a48db-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="a48db-119">Nome de comprimento de LastWriteTime modo</span><span class="sxs-lookup"><span data-stu-id="a48db-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="a48db-120">---d 4/14/2015 5:33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="a48db-120">d----- 4/14/2015 5:33 PM Depth1</span></span>