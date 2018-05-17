---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9ca12ad3f0729a2e9595d7ca5ccf9041e47658a3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="archive-cmdlets"></a>Cmdlets de arquivo

Dois novos cmdlets, **comprimir arquivo** e **expansão arquivo**, permitem comprimir e expanda ficheiros ZIP.

## <a name="compress-archive"></a>Arquivo de comprimir
O **comprimir arquivo** cmdlet cria um novo ficheiro de arquivo de ficheiros especificados. Um ficheiro de arquivo permite vários ficheiros de ser compactadas e opcionalmente comprimidos num único ficheiro de processamento mais fácil e de armazenamento. Um ficheiro de arquivo pode ser comprimido utilizando um algoritmo de compressão especificado no **- CompressionLevel** parâmetro.
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a>Arquivo expanda
O **expansão arquivo** cmdlet extrai os ficheiros a partir de um ficheiro de arquivo especificado. Um ficheiro de arquivo permite vários ficheiros de ser compactadas e opcionalmente comprimidos num único ficheiro de processamento mais fácil e de armazenamento.
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```
