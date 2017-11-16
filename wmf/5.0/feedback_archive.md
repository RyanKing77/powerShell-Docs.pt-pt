---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: 7ad4a00f7beba0de70696d88cd5448c7c638c50c
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/27/2017
---
# <a name="archive-cmdlets"></a><span data-ttu-id="abf0e-102">Cmdlets de arquivo</span><span class="sxs-lookup"><span data-stu-id="abf0e-102">Archive cmdlets</span></span>

<span data-ttu-id="abf0e-103">Dois novos cmdlets, **comprimir arquivo** e **expansão arquivo**, permitem comprimir e expanda ficheiros ZIP.</span><span class="sxs-lookup"><span data-stu-id="abf0e-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="abf0e-104">Arquivo de comprimir</span><span class="sxs-lookup"><span data-stu-id="abf0e-104">Compress-Archive</span></span>
<span data-ttu-id="abf0e-105">O **comprimir arquivo** cmdlet cria um novo ficheiro de arquivo de ficheiros especificados.</span><span class="sxs-lookup"><span data-stu-id="abf0e-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="abf0e-106">Um ficheiro de arquivo permite vários ficheiros de ser compactadas e opcionalmente comprimidos num único ficheiro de processamento mais fácil e de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="abf0e-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="abf0e-107">Um ficheiro de arquivo pode ser comprimido utilizando um algoritmo de compressão especificado no **- CompressionLevel** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="abf0e-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>] 
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="abf0e-108">Arquivo expanda</span><span class="sxs-lookup"><span data-stu-id="abf0e-108">Expand-Archive</span></span>
<span data-ttu-id="abf0e-109">O **expansão arquivo** cmdlet extrai os ficheiros a partir de um ficheiro de arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="abf0e-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="abf0e-110">Um ficheiro de arquivo permite vários ficheiros de ser compactadas e opcionalmente comprimidos num único ficheiro de processamento mais fácil e de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="abf0e-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```

