---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: 90e0ab3579e1840598cc3050c27db0b73ba6f69d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="new-temporaryfile"></a><span data-ttu-id="6044d-102">Novo TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="6044d-102">New-TemporaryFile</span></span>
<span data-ttu-id="6044d-103">Por vezes nos scripts, terá de criar um ficheiro temporário.</span><span class="sxs-lookup"><span data-stu-id="6044d-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="6044d-104">Pode facilmente fazê-com o **New-TemporaryFile** cmdlet:</span><span class="sxs-lookup"><span data-stu-id="6044d-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="6044d-105">PS c:\\ &gt; $tempFile = New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="6044d-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="6044d-106">PS c:\\ &gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="6044d-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="6044d-107">C:\\utilizadores\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="6044d-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>

