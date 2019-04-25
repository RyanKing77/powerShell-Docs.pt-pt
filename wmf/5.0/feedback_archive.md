---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: db9c630bcb8e9e0da423c779976739f1ae76f13e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057439"
---
# <a name="archive-cmdlets"></a><span data-ttu-id="a407e-102">Archive cmdlets</span><span class="sxs-lookup"><span data-stu-id="a407e-102">Archive cmdlets</span></span>

<span data-ttu-id="a407e-103">Dois novos cmdlets **arquivo Compress** e **Expand-arquivo**, vou comprimir e expanda arquivos ZIP.</span><span class="sxs-lookup"><span data-stu-id="a407e-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="a407e-104">Arquivo de comprimir</span><span class="sxs-lookup"><span data-stu-id="a407e-104">Compress-Archive</span></span>
<span data-ttu-id="a407e-105">O **Compress arquivo** cmdlet cria um novo ficheiro de arquivo de ficheiros especificados.</span><span class="sxs-lookup"><span data-stu-id="a407e-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="a407e-106">Um ficheiro de arquivo permite que vários arquivos para ser empacotado e, opcionalmente, compactados num único arquivo para manipulação mais fácil e de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="a407e-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="a407e-107">Um ficheiro de arquivo pode ser compactado usando um algoritmo de compressão especificado no **- CompressionLevel** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a407e-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="a407e-108">Expanda-arquivo</span><span class="sxs-lookup"><span data-stu-id="a407e-108">Expand-Archive</span></span>
<span data-ttu-id="a407e-109">O **Expand-arquivo** cmdlet extrai ficheiros a partir de um ficheiro de arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="a407e-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="a407e-110">Um ficheiro de arquivo permite que vários arquivos para ser empacotado e, opcionalmente, compactados num único arquivo para manipulação mais fácil e de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="a407e-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```
