---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: aa2e9540af8b3d4c5de5e00377a84e0e5edd6e4a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057861"
---
# <a name="new-temporaryfile"></a><span data-ttu-id="81295-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="81295-102">New-TemporaryFile</span></span>
<span data-ttu-id="81295-103">Por vezes, nos seus scripts, tem de criar um arquivo temporário.</span><span class="sxs-lookup"><span data-stu-id="81295-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="81295-104">Pode fazê-lo com facilidade, o **New-TemporaryFile** cmdlet:</span><span class="sxs-lookup"><span data-stu-id="81295-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="81295-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="81295-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="81295-106">PS C:\\&gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="81295-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="81295-107">C:\\usuários\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="81295-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>
