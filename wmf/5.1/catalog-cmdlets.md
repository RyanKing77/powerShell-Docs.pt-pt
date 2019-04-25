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
# <a name="catalog-cmdlets"></a><span data-ttu-id="9db2f-103">Cmdlets Catalog</span><span class="sxs-lookup"><span data-stu-id="9db2f-103">Catalog Cmdlets</span></span>

<span data-ttu-id="9db2f-104">Adicionámos dois cmdlets novos no [Microsoft.Powershell.Secuity](https://technet.microsoft.com/library/hh847877.aspx) módulo para gerar e validar os arquivos de catálogo do windows.</span><span class="sxs-lookup"><span data-stu-id="9db2f-104">We have added two new cmdlets in [Microsoft.Powershell.Secuity](https://technet.microsoft.com/library/hh847877.aspx) module to generate and validate windows catalog files.</span></span>

## <a name="new-filecatalog"></a><span data-ttu-id="9db2f-105">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="9db2f-105">New-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="9db2f-106">`New-FileCatalog` cria um ficheiro de catálogo do windows para o conjunto de pastas e arquivos.</span><span class="sxs-lookup"><span data-stu-id="9db2f-106">`New-FileCatalog` creates a windows catalog file for set of folders and files.</span></span> <span data-ttu-id="9db2f-107">Um arquivo de catálogo contém hashes para todos os ficheiros em caminhos especificados.</span><span class="sxs-lookup"><span data-stu-id="9db2f-107">A catalog file contains hashes for all files in specified paths.</span></span> <span data-ttu-id="9db2f-108">Os utilizadores possam distribuir o conjunto de pastas, juntamente com correspondente no ficheiro de catálogo que representa essas pastas.</span><span class="sxs-lookup"><span data-stu-id="9db2f-108">Users can distribute the set of folders along with corresponding the catalog file that represents those folders.</span></span> <span data-ttu-id="9db2f-109">Um arquivo de catálogo pode ser utilizado pelo destinatário de conteúdo ao validar se todas as alterações efetuadas às pastas após o catálogo foi criado.</span><span class="sxs-lookup"><span data-stu-id="9db2f-109">A catalog file can be used by the recipient of content to validate whether any changes were made to the folders after the catalog was created.</span></span>

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<span data-ttu-id="9db2f-110">Damos suporte a criação de catálogo de versão 1 e 2.</span><span class="sxs-lookup"><span data-stu-id="9db2f-110">We support creating catalog version 1 and 2.</span></span> <span data-ttu-id="9db2f-111">Versão 1 utiliza o algoritmo de hash SHA1 para criar hashes de ficheiro e versão 2 usa SHA256.</span><span class="sxs-lookup"><span data-stu-id="9db2f-111">Version 1 uses SHA1 hashing algorithm to create file hashes and version 2 uses SHA256.</span></span> <span data-ttu-id="9db2f-112">Versão de catálogo 2 não é suportada no *Windows Server 2008 R2* e *Windows 7*.</span><span class="sxs-lookup"><span data-stu-id="9db2f-112">Catalog version 2 is not supported on *Windows Server 2008 R2* and *Windows 7*.</span></span> <span data-ttu-id="9db2f-113">É recomendado que utilize a versão de catálogo 2, se utilizar plataformas *Windows 8*, *Windows Server 2012* e acima.</span><span class="sxs-lookup"><span data-stu-id="9db2f-113">It is recommended to use catalog version 2 if using platforms *Windows 8*, *Windows Server 2012* and above.</span></span>

<span data-ttu-id="9db2f-114">Para utilizar este comando num módulo existente, especifique as variáveis CatalogFilePath e o caminho de acordo com a localização de manifesto do módulo.</span><span class="sxs-lookup"><span data-stu-id="9db2f-114">To use this command on an existing module, specify the CatalogFilePath and Path variables to match the location of the module manifest.</span></span> <span data-ttu-id="9db2f-115">No exemplo abaixo, o manifesto de módulo é em C:\Program Programas\Windows PowerShell\Modules\Pester.</span><span class="sxs-lookup"><span data-stu-id="9db2f-115">In the example below, the module manifest is in C:\Program Files\Windows PowerShell\Modules\Pester.</span></span>

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="9db2f-116">Esta ação cria o arquivo de catálogo.</span><span class="sxs-lookup"><span data-stu-id="9db2f-116">This creates the catalog file.</span></span>

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

<span data-ttu-id="9db2f-117">Para verificar a integridade de um arquivo de catálogo (Pester.cat no acima exemplo) deve ser assinado com o [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9db2f-117">To verify the integrity of a catalog file (Pester.cat in above exmaple) it should be signed using the [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span></span>


## <a name="test-filecatalog"></a><span data-ttu-id="9db2f-118">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="9db2f-118">Test-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="9db2f-119">`Test-FileCatalog` valida o catálogo que representa um conjunto de pastas.</span><span class="sxs-lookup"><span data-stu-id="9db2f-119">`Test-FileCatalog` validates the catalog representing a set of folders.</span></span>

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="9db2f-120">Este cmdlet compara os hashes de todos os ficheiros e os caminhos relativos presentes no ficheiro de catálogo com aqueles guardado no disco.</span><span class="sxs-lookup"><span data-stu-id="9db2f-120">This cmdlet compares the hashes of all files and their relative paths found in the catalog file with ones saved to disk.</span></span> <span data-ttu-id="9db2f-121">Se detetar qualquer erro de correspondência entre os caminhos de hashes de ficheiro e devolve um Estado de `ValidationFailed`.</span><span class="sxs-lookup"><span data-stu-id="9db2f-121">If it detects any mismatch between file hashes and paths it returns a status of `ValidationFailed`.</span></span>
<span data-ttu-id="9db2f-122">Os utilizadores podem obter todos os esta informação utilizando o `Detailed` mudar.</span><span class="sxs-lookup"><span data-stu-id="9db2f-122">Users can retrieve all this information using the `Detailed` switch.</span></span> <span data-ttu-id="9db2f-123">O estado da assinatura do catálogo é apresentado como o `Signature` campo, o que é a mesmo como chamar o [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) cmdlet no arquivo de catálogo.</span><span class="sxs-lookup"><span data-stu-id="9db2f-123">The signing status of the catalog is displayed as the `Signature` field, which is same as calling the [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) cmdlet on the catalog file.</span></span>
<span data-ttu-id="9db2f-124">Os utilizadores também podem ignorar qualquer ficheiro durante a validação utilizando o `FilesToSkip` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9db2f-124">Users can also skip any file during validation by using the `FilesToSkip` parameter.</span></span>
