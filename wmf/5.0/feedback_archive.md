---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9ca12ad3f0729a2e9595d7ca5ccf9041e47658a3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218098"
---
# <a name="archive-cmdlets"></a><span data-ttu-id="6a039-102">Cmdlets de arquivo</span><span class="sxs-lookup"><span data-stu-id="6a039-102">Archive cmdlets</span></span>

<span data-ttu-id="6a039-103">Dois novos cmdlets, **comprimir arquivo** e **expansão arquivo**, permitem comprimir e expanda ficheiros ZIP.</span><span class="sxs-lookup"><span data-stu-id="6a039-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="6a039-104">Arquivo de comprimir</span><span class="sxs-lookup"><span data-stu-id="6a039-104">Compress-Archive</span></span>
<span data-ttu-id="6a039-105">O **comprimir arquivo** cmdlet cria um novo ficheiro de arquivo de ficheiros especificados.</span><span class="sxs-lookup"><span data-stu-id="6a039-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="6a039-106">Um ficheiro de arquivo permite vários ficheiros de ser compactadas e opcionalmente comprimidos num único ficheiro de processamento mais fácil e de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="6a039-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="6a039-107">Um ficheiro de arquivo pode ser comprimido utilizando um algoritmo de compressão especificado no **- CompressionLevel** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6a039-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="6a039-108">Arquivo expanda</span><span class="sxs-lookup"><span data-stu-id="6a039-108">Expand-Archive</span></span>
<span data-ttu-id="6a039-109">O **expansão arquivo** cmdlet extrai os ficheiros a partir de um ficheiro de arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="6a039-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="6a039-110">Um ficheiro de arquivo permite vários ficheiros de ser compactadas e opcionalmente comprimidos num único ficheiro de processamento mais fácil e de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="6a039-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```
