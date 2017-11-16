---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
title: "Cmdlets de catálogo"
ms.openlocfilehash: f0869e8c174ab127996866775ad20d056f877345
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/27/2017
---
# <a name="catalog-cmdlets"></a><span data-ttu-id="14be1-103">Cmdlets de catálogo</span><span class="sxs-lookup"><span data-stu-id="14be1-103">Catalog Cmdlets</span></span>  

<span data-ttu-id="14be1-104">Foram adicionados dois novos cmdlets no [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) módulo para gerar e validar os ficheiros de catálogo do windows.</span><span class="sxs-lookup"><span data-stu-id="14be1-104">We have added two new cmdlets in [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) module to generate and validate windows catalog files.</span></span>  

## <a name="new-filecatalog"></a><span data-ttu-id="14be1-105">Novo FileCatalog</span><span class="sxs-lookup"><span data-stu-id="14be1-105">New-FileCatalog</span></span> 
--------------------------------

<span data-ttu-id="14be1-106">`New-FileCatalog`cria um ficheiro de catálogo do windows para o conjunto de ficheiros e pastas.</span><span class="sxs-lookup"><span data-stu-id="14be1-106">`New-FileCatalog` creates a windows catalog file for set of folders and files.</span></span> <span data-ttu-id="14be1-107">Um ficheiro de catálogo contém hashes para todos os ficheiros em caminhos especificados.</span><span class="sxs-lookup"><span data-stu-id="14be1-107">A catalog file contains hashes for all files in specified paths.</span></span> <span data-ttu-id="14be1-108">Os utilizadores possam distribuir o conjunto de pastas, juntamente com correspondente o ficheiro de catálogo que representa essas pastas.</span><span class="sxs-lookup"><span data-stu-id="14be1-108">Users can distribute the set of folders along with corresponding the catalog file that represents those folders.</span></span> <span data-ttu-id="14be1-109">Um ficheiro de catálogo pode ser utilizado pelo destinatário do conteúdo para validar se quaisquer alterações efetuadas para as pastas após o catálogo foi criado.</span><span class="sxs-lookup"><span data-stu-id="14be1-109">A catalog file can be used by the recipient of content to validate whether any changes were made to the folders after the catalog was created.</span></span>    

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<span data-ttu-id="14be1-110">Fornecemos suporte a criação de catálogo de versão 1 e 2.</span><span class="sxs-lookup"><span data-stu-id="14be1-110">We support creating catalog version 1 and 2.</span></span> <span data-ttu-id="14be1-111">Versão 1 utiliza o algoritmo de hash SHA1 para criar os hashes de ficheiro e versão 2 utiliza SHA256.</span><span class="sxs-lookup"><span data-stu-id="14be1-111">Version 1 uses SHA1 hashing algorithm to create file hashes and version 2 uses SHA256.</span></span> <span data-ttu-id="14be1-112">Versão 2 do catálogo não é suportada em *Windows Server 2008 R2* e *Windows 7*.</span><span class="sxs-lookup"><span data-stu-id="14be1-112">Catalog version 2 is not supported on *Windows Server 2008 R2* and *Windows 7*.</span></span> <span data-ttu-id="14be1-113">Recomenda-se para utilizar a versão 2 do catálogo se utilizar plataformas *Windows 8*, *Windows Server 2012* e superior.</span><span class="sxs-lookup"><span data-stu-id="14be1-113">It is recommended to use catalog version 2 if using platforms *Windows 8*, *Windows Server 2012* and above.</span></span>  

<span data-ttu-id="14be1-114">Para utilizar este comando num módulo existente, especifique as variáveis CatalogFilePath e o caminho para corresponder a localização do manifesto do módulo.</span><span class="sxs-lookup"><span data-stu-id="14be1-114">To use this command on an existing module, specify the CatalogFilePath and Path variables to match the location of the module manifest.</span></span> <span data-ttu-id="14be1-115">No exemplo abaixo, o manifesto de módulo está em c:\Programas\Microsoft Files\Windows PowerShell\Modules\Pester.</span><span class="sxs-lookup"><span data-stu-id="14be1-115">In the example below, the module manifest is in C:\Program Files\Windows PowerShell\Modules\Pester.</span></span> 

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="14be1-116">Esta ação cria o ficheiro de catálogo.</span><span class="sxs-lookup"><span data-stu-id="14be1-116">This creates the catalog file.</span></span> 

![](../images/CatalogFile1.jpg)  

![](../images/CatalogFile2.jpg) 

<span data-ttu-id="14be1-117">Para verificar a integridade de um ficheiro de catálogo (Pester.cat no acima exemplo) deve ser assinado com o [conjunto AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="14be1-117">To verify the integrity of a catalog file (Pester.cat in above exmaple) it should be signed using the [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span></span>   


## <a name="test-filecatalog"></a><span data-ttu-id="14be1-118">Teste FileCatalog</span><span class="sxs-lookup"><span data-stu-id="14be1-118">Test-FileCatalog</span></span> 
--------------------------------

<span data-ttu-id="14be1-119">`Test-FileCatalog`valida o catálogo que representa um conjunto de pastas.</span><span class="sxs-lookup"><span data-stu-id="14be1-119">`Test-FileCatalog` validates the catalog representing a set of folders.</span></span> 

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="14be1-120">Este cmdlet compara os hashes de todos os ficheiros e os respetivos caminhos relativos encontrados no ficheiro de catálogo com aqueles guardado no disco.</span><span class="sxs-lookup"><span data-stu-id="14be1-120">This cmdlet compares the hashes of all files and their relative paths found in the catalog file with ones saved to disk.</span></span> <span data-ttu-id="14be1-121">Se detetar qualquer erro de correspondência entre os hashes de ficheiros e caminhos devolve um Estado de `ValidationFailed`.</span><span class="sxs-lookup"><span data-stu-id="14be1-121">If it detects any mismatch between file hashes and paths it returns a status of `ValidationFailed`.</span></span> <span data-ttu-id="14be1-122">Os utilizadores podem obter todos os esta informação utilizando o `Detailed` mudar.</span><span class="sxs-lookup"><span data-stu-id="14be1-122">Users can retrieve all this information using the `Detailed` switch.</span></span> <span data-ttu-id="14be1-123">O estado da assinatura do catálogo é apresentado como o `Signature` campo, o que é igual ao chamar o [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) cmdlet no ficheiro de catálogo.</span><span class="sxs-lookup"><span data-stu-id="14be1-123">The signing status of the catalog is displayed as the `Signature` field, which is same as calling the [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) cmdlet on the catalog file.</span></span> <span data-ttu-id="14be1-124">Os utilizadores também podem ignorar qualquer ficheiro durante a validação utilizando o `FilesToSkip` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="14be1-124">Users can also skip any file during validation by using the `FilesToSkip` parameter.</span></span> 

