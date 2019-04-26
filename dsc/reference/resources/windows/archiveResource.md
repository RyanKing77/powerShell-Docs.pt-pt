---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso Archive de DSC
ms.openlocfilehash: d5ccd242d000a0907c6768f30923764be6bf20a3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077556"
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="bb804-103">Recurso Archive de DSC</span><span class="sxs-lookup"><span data-stu-id="bb804-103">DSC Archive Resource</span></span>

> <span data-ttu-id="bb804-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bb804-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="bb804-105">O recurso de arquivo no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para descompactar os ficheiros de arquivo (. zip) num caminho específico.</span><span class="sxs-lookup"><span data-stu-id="bb804-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

## <a name="syntax"></a><span data-ttu-id="bb804-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb804-106">Syntax</span></span>
```MOF
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
}
```

## <a name="properties"></a><span data-ttu-id="bb804-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="bb804-107">Properties</span></span>

|  <span data-ttu-id="bb804-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="bb804-108">Property</span></span>  |  <span data-ttu-id="bb804-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="bb804-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="bb804-110">Destino</span><span class="sxs-lookup"><span data-stu-id="bb804-110">Destination</span></span>| <span data-ttu-id="bb804-111">Especifica a localização onde pretende Certifique-se de que o conteúdo do arquivo é extraído.</span><span class="sxs-lookup"><span data-stu-id="bb804-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span>|
| <span data-ttu-id="bb804-112">Caminho</span><span class="sxs-lookup"><span data-stu-id="bb804-112">Path</span></span>| <span data-ttu-id="bb804-113">Especifica o caminho de origem do ficheiro de arquivo.</span><span class="sxs-lookup"><span data-stu-id="bb804-113">Specifies the source path of the archive file.</span></span>|
| <span data-ttu-id="bb804-114">__Checksum__</span><span class="sxs-lookup"><span data-stu-id="bb804-114">__Checksum__</span></span>| <span data-ttu-id="bb804-115">Define o tipo a utilizar ao determinar se dois arquivos são os mesmos.</span><span class="sxs-lookup"><span data-stu-id="bb804-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="bb804-116">Se __soma de verificação__ não for especificada, apenas o nome de ficheiro ou diretório é utilizado para comparação.</span><span class="sxs-lookup"><span data-stu-id="bb804-116">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="bb804-117">Valores válidos incluem: SHA-1, SHA-256, SHA-512, colunas createdDate e modifiedDate, nenhum (predefinição).</span><span class="sxs-lookup"><span data-stu-id="bb804-117">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate, none (default).</span></span> <span data-ttu-id="bb804-118">Se especificar __soma de verificação__ sem __Validate__, a configuração irá falhar.</span><span class="sxs-lookup"><span data-stu-id="bb804-118">If you specify __Checksum__ without __Validate__, the configuration will fail.</span></span>|
| <span data-ttu-id="bb804-119">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="bb804-119">Ensure</span></span>| <span data-ttu-id="bb804-120">Determina se deve verificar se o conteúdo do arquivo existe no __destino__.</span><span class="sxs-lookup"><span data-stu-id="bb804-120">Determines whether to check if the content of the archive exists at the __Destination__.</span></span> <span data-ttu-id="bb804-121">Defina esta propriedade como __presente__ para garantir que existe o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="bb804-121">Set this property to __Present__ to ensure the contents exist.</span></span> <span data-ttu-id="bb804-122">Defina-o como __ausente__ para garantir que não existam.</span><span class="sxs-lookup"><span data-stu-id="bb804-122">Set it to __Absent__ to ensure they do not exist.</span></span> <span data-ttu-id="bb804-123">O valor predefinido é __presente__.</span><span class="sxs-lookup"><span data-stu-id="bb804-123">The default value is __Present__.</span></span>|
| <span data-ttu-id="bb804-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="bb804-124">DependsOn</span></span> | <span data-ttu-id="bb804-125">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="bb804-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="bb804-126">Por exemplo, se o ID de bloco de script de configuração de recursos que pretende executar primeiro for ResourceName e seu tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="bb804-126">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="bb804-127">Validar</span><span class="sxs-lookup"><span data-stu-id="bb804-127">Validate</span></span>| <span data-ttu-id="bb804-128">Usa a propriedade de soma de verificação para determinar se o arquivo corresponde à assinatura.</span><span class="sxs-lookup"><span data-stu-id="bb804-128">Uses the Checksum property to determine if the archive matches the signature.</span></span> <span data-ttu-id="bb804-129">Se especificar a soma de verificação sem validar, a configuração irá falhar.</span><span class="sxs-lookup"><span data-stu-id="bb804-129">If you specify Checksum without Validate, the configuration will fail.</span></span> <span data-ttu-id="bb804-130">Se especificar validar sem a soma de verificação, uma soma de verificação de SHA-256 é utilizada por predefinição.</span><span class="sxs-lookup"><span data-stu-id="bb804-130">If you specify Validate without Checksum, a SHA-256 checksum is used by default.</span></span>|
| <span data-ttu-id="bb804-131">Force</span><span class="sxs-lookup"><span data-stu-id="bb804-131">Force</span></span>| <span data-ttu-id="bb804-132">Determinadas operações de arquivo (como substituir um ficheiro ou eliminar um diretório que não está vazio) irão resultar num erro.</span><span class="sxs-lookup"><span data-stu-id="bb804-132">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="bb804-133">Usando a propriedade de força substitui esses erros.</span><span class="sxs-lookup"><span data-stu-id="bb804-133">Using the Force property overrides such errors.</span></span> <span data-ttu-id="bb804-134">O valor predefinido é False.</span><span class="sxs-lookup"><span data-stu-id="bb804-134">The default value is False.</span></span>|

## <a name="example"></a><span data-ttu-id="bb804-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bb804-135">Example</span></span>

<span data-ttu-id="bb804-136">O exemplo seguinte mostra como usar o recurso de arquivo para garantir que o conteúdo de um ficheiro de arquivo chamado Test.zip existe e que é extraído num determinado destino.</span><span class="sxs-lookup"><span data-stu-id="bb804-136">The following example shows how to use the Archive resource to ensure that the contents of an archive file called Test.zip exist and are extracted at a given destination.</span></span>

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```