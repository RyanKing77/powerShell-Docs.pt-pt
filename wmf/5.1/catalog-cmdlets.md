---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Cmdlets Catalog
ms.openlocfilehash: ec5fc866fe27a894b23b93d3ea46ad9c0cba288e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057664"
---
# <a name="catalog-cmdlets"></a>Cmdlets Catalog

Adicionámos dois cmdlets novos no [Microsoft.Powershell.Secuity](https://technet.microsoft.com/library/hh847877.aspx) módulo para gerar e validar os arquivos de catálogo do windows.

## <a name="new-filecatalog"></a>New-FileCatalog
--------------------------------

`New-FileCatalog` cria um ficheiro de catálogo do windows para o conjunto de pastas e arquivos. Um arquivo de catálogo contém hashes para todos os ficheiros em caminhos especificados. Os utilizadores possam distribuir o conjunto de pastas, juntamente com correspondente no ficheiro de catálogo que representa essas pastas. Um arquivo de catálogo pode ser utilizado pelo destinatário de conteúdo ao validar se todas as alterações efetuadas às pastas após o catálogo foi criado.

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
Damos suporte a criação de catálogo de versão 1 e 2. Versão 1 utiliza o algoritmo de hash SHA1 para criar hashes de ficheiro e versão 2 usa SHA256. Versão de catálogo 2 não é suportada no *Windows Server 2008 R2* e *Windows 7*. É recomendado que utilize a versão de catálogo 2, se utilizar plataformas *Windows 8*, *Windows Server 2012* e acima.

Para utilizar este comando num módulo existente, especifique as variáveis CatalogFilePath e o caminho de acordo com a localização de manifesto do módulo. No exemplo abaixo, o manifesto de módulo é em C:\Program Programas\Windows PowerShell\Modules\Pester.

![](../images/NewFileCatalog.jpg)

Esta ação cria o arquivo de catálogo.

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

Para verificar a integridade de um arquivo de catálogo (Pester.cat no acima exemplo) deve ser assinado com o [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.


## <a name="test-filecatalog"></a>Test-FileCatalog
--------------------------------

`Test-FileCatalog` valida o catálogo que representa um conjunto de pastas.

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

Este cmdlet compara os hashes de todos os ficheiros e os caminhos relativos presentes no ficheiro de catálogo com aqueles guardado no disco. Se detetar qualquer erro de correspondência entre os caminhos de hashes de ficheiro e devolve um Estado de `ValidationFailed`.
Os utilizadores podem obter todos os esta informação utilizando o `Detailed` mudar. O estado da assinatura do catálogo é apresentado como o `Signature` campo, o que é a mesmo como chamar o [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) cmdlet no arquivo de catálogo.
Os utilizadores também podem ignorar qualquer ficheiro durante a validação utilizando o `FilesToSkip` parâmetro.
