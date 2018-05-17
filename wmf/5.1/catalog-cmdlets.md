---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Cmdlets Catalog
ms.openlocfilehash: 7eaca09667af0eb5d719f23e987bb112e8514978
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="catalog-cmdlets"></a>Cmdlets de catálogo

Foram adicionados dois novos cmdlets no [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) módulo para gerar e validar os ficheiros de catálogo do windows.

## <a name="new-filecatalog"></a>New-FileCatalog
--------------------------------

`New-FileCatalog` cria um ficheiro de catálogo do windows para o conjunto de ficheiros e pastas. Um ficheiro de catálogo contém hashes para todos os ficheiros em caminhos especificados. Os utilizadores possam distribuir o conjunto de pastas, juntamente com correspondente o ficheiro de catálogo que representa essas pastas. Um ficheiro de catálogo pode ser utilizado pelo destinatário do conteúdo para validar se quaisquer alterações efetuadas para as pastas após o catálogo foi criado.

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
Fornecemos suporte a criação de catálogo de versão 1 e 2. Versão 1 utiliza o algoritmo de hash SHA1 para criar os hashes de ficheiro e versão 2 utiliza SHA256. Versão 2 do catálogo não é suportada em *Windows Server 2008 R2* e *Windows 7*. Recomenda-se para utilizar a versão 2 do catálogo se utilizar plataformas *Windows 8*, *Windows Server 2012* e superior.

Para utilizar este comando num módulo existente, especifique as variáveis CatalogFilePath e o caminho para corresponder a localização do manifesto do módulo. No exemplo abaixo, o manifesto de módulo está em c:\Programas\Microsoft Files\Windows PowerShell\Modules\Pester.

![](../images/NewFileCatalog.jpg)

Esta ação cria o ficheiro de catálogo.

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

Para verificar a integridade de um ficheiro de catálogo (Pester.cat no acima exemplo) deve ser assinado com o [conjunto AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.


## <a name="test-filecatalog"></a>Teste FileCatalog
--------------------------------

`Test-FileCatalog` valida o catálogo que representa um conjunto de pastas.

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

Este cmdlet compara os hashes de todos os ficheiros e os respetivos caminhos relativos encontrados no ficheiro de catálogo com aqueles guardado no disco. Se detetar qualquer erro de correspondência entre os hashes de ficheiros e caminhos devolve um Estado de `ValidationFailed`.
Os utilizadores podem obter todos os esta informação utilizando o `Detailed` mudar. O estado da assinatura do catálogo é apresentado como o `Signature` campo, o que é igual ao chamar o [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) cmdlet no ficheiro de catálogo.
Os utilizadores também podem ignorar qualquer ficheiro durante a validação utilizando o `FilesToSkip` parâmetro.
