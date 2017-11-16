---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: 4185d9395f2f3e5ba1c8daa0c365cb2bf322936b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="6c3f8-102">Tem de GET-ChildItem - parâmetro de profundidade</span><span class="sxs-lookup"><span data-stu-id="6c3f8-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="6c3f8-103">**Get-ChildItem** tem agora um **– profundidade** parâmetro a utilizar com **-Recurse** para limitar a recursão:</span><span class="sxs-lookup"><span data-stu-id="6c3f8-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="6c3f8-104">PS c:\\utilizadores\\slee\\transfere\\exemplo&gt; Get-ChildItem-Recurse - profundidade 0</span><span class="sxs-lookup"><span data-stu-id="6c3f8-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="6c3f8-105">Diretório: C\\utilizadores\\slee\\transfere\\exemplo</span><span class="sxs-lookup"><span data-stu-id="6c3f8-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="6c3f8-106">Nome de comprimento de LastWriteTime modo</span><span class="sxs-lookup"><span data-stu-id="6c3f8-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="6c3f8-107">---d 4/14/2015 as 17:36:00 Depth0</span><span class="sxs-lookup"><span data-stu-id="6c3f8-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="6c3f8-108">-a---4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="6c3f8-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="6c3f8-109">-a---4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="6c3f8-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="6c3f8-110">-a---4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="6c3f8-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="6c3f8-111">PS c:\\utilizadores\\slee\\transfere\\exemplo&gt; Get-ChildItem-Recurse - profundidade 1</span><span class="sxs-lookup"><span data-stu-id="6c3f8-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="6c3f8-112">Diretório: C\\utilizadores\\slee\\transfere\\exemplo</span><span class="sxs-lookup"><span data-stu-id="6c3f8-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="6c3f8-113">Nome de comprimento de LastWriteTime modo</span><span class="sxs-lookup"><span data-stu-id="6c3f8-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="6c3f8-114">---d 4/14/2015 as 17:36:00 Depth0</span><span class="sxs-lookup"><span data-stu-id="6c3f8-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="6c3f8-115">-a---4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="6c3f8-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="6c3f8-116">-a---4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="6c3f8-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="6c3f8-117">-a---4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="6c3f8-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="6c3f8-118">Diretório: C\\utilizadores\\slee\\transfere\\exemplo\\Depth0</span><span class="sxs-lookup"><span data-stu-id="6c3f8-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="6c3f8-119">Nome de comprimento de LastWriteTime modo</span><span class="sxs-lookup"><span data-stu-id="6c3f8-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="6c3f8-120">---d 4/14/2015 5:33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="6c3f8-120">d----- 4/14/2015 5:33 PM Depth1</span></span>

