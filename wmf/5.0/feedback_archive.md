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