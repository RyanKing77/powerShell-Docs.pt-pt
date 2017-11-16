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

