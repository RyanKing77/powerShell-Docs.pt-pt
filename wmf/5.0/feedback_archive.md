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
# <a name="archive-cmdlets"></a>Archive cmdlets

Dois novos cmdlets **arquivo Compress** e **Expand-arquivo**, vou comprimir e expanda arquivos ZIP.

## <a name="compress-archive"></a>Arquivo de comprimir
O **Compress arquivo** cmdlet cria um novo ficheiro de arquivo de ficheiros especificados. Um ficheiro de arquivo permite que vários arquivos para ser empacotado e, opcionalmente, compactados num único arquivo para manipulação mais fácil e de armazenamento. Um ficheiro de arquivo pode ser compactado usando um algoritmo de compressão especificado no **- CompressionLevel** parâmetro.
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a>Expanda-arquivo
O **Expand-arquivo** cmdlet extrai ficheiros a partir de um ficheiro de arquivo especificado. Um ficheiro de arquivo permite que vários arquivos para ser empacotado e, opcionalmente, compactados num único arquivo para manipulação mais fácil e de armazenamento.
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```
