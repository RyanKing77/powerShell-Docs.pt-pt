---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 0c450d765531c18c0b73c5c64262e9895f92068a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="archive-cmdlets"></a><span data-ttu-id="2b9d4-102">Cmdlets de arquivo</span><span class="sxs-lookup"><span data-stu-id="2b9d4-102">Archive cmdlets</span></span>

<span data-ttu-id="2b9d4-103">Dois novos cmdlets, **comprimir arquivo** e **expansão arquivo**, permitem comprimir e expanda ficheiros ZIP.</span><span class="sxs-lookup"><span data-stu-id="2b9d4-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="2b9d4-104">Arquivo de comprimir</span><span class="sxs-lookup"><span data-stu-id="2b9d4-104">Compress-Archive</span></span>
<span data-ttu-id="2b9d4-105">O **comprimir arquivo** cmdlet cria um novo ficheiro de arquivo de ficheiros especificados.</span><span class="sxs-lookup"><span data-stu-id="2b9d4-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="2b9d4-106">Um ficheiro de arquivo permite vários ficheiros de ser compactadas e opcionalmente comprimidos num único ficheiro de processamento mais fácil e de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="2b9d4-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="2b9d4-107">Um ficheiro de arquivo pode ser comprimido utilizando um algoritmo de compressão especificado no **- CompressionLevel** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="2b9d4-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="2b9d4-108">Arquivo expanda</span><span class="sxs-lookup"><span data-stu-id="2b9d4-108">Expand-Archive</span></span>
<span data-ttu-id="2b9d4-109">O **expansão arquivo** cmdlet extrai os ficheiros a partir de um ficheiro de arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="2b9d4-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="2b9d4-110">Um ficheiro de arquivo permite vários ficheiros de ser compactadas e opcionalmente comprimidos num único ficheiro de processamento mais fácil e de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="2b9d4-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```