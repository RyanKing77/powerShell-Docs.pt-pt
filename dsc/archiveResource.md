---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Recursos de DSC arquivo
ms.openlocfilehash: 458b4f0f20dc96dab62e709183c25ff57d971aae
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="8c60d-103">Recursos de DSC arquivo</span><span class="sxs-lookup"><span data-stu-id="8c60d-103">DSC Archive Resource</span></span>

> <span data-ttu-id="8c60d-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8c60d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="8c60d-105">O recurso de arquivo no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para descompactar os ficheiros de arquivo (. zip) de um caminho específico.</span><span class="sxs-lookup"><span data-stu-id="8c60d-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

## <a name="syntax"></a><span data-ttu-id="8c60d-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c60d-106">Syntax</span></span>
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

## <a name="properties"></a><span data-ttu-id="8c60d-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="8c60d-107">Properties</span></span>

|  <span data-ttu-id="8c60d-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="8c60d-108">Property</span></span>  |  <span data-ttu-id="8c60d-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="8c60d-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="8c60d-110">Destino</span><span class="sxs-lookup"><span data-stu-id="8c60d-110">Destination</span></span>| <span data-ttu-id="8c60d-111">Especifica a localização onde pretende Certifique-se de que o conteúdo de arquivo é extraído.</span><span class="sxs-lookup"><span data-stu-id="8c60d-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span>|
| <span data-ttu-id="8c60d-112">Caminho</span><span class="sxs-lookup"><span data-stu-id="8c60d-112">Path</span></span>| <span data-ttu-id="8c60d-113">Especifica o caminho de origem do ficheiro de arquivo.</span><span class="sxs-lookup"><span data-stu-id="8c60d-113">Specifies the source path of the archive file.</span></span>|
| <span data-ttu-id="8c60d-114">__Soma de verificação__</span><span class="sxs-lookup"><span data-stu-id="8c60d-114">__Checksum__</span></span>| <span data-ttu-id="8c60d-115">Define o tipo a utilizar ao determinar se os dois ficheiros são as mesmas.</span><span class="sxs-lookup"><span data-stu-id="8c60d-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="8c60d-116">Se __soma de verificação__ não for especificado, apenas o nome de ficheiro ou diretório é utilizado para comparação.</span><span class="sxs-lookup"><span data-stu-id="8c60d-116">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="8c60d-117">Os valores válidos incluem: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate, none (predefinição).</span><span class="sxs-lookup"><span data-stu-id="8c60d-117">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate, none (default).</span></span> <span data-ttu-id="8c60d-118">Se especificar __soma de verificação__ sem __validar__, a configuração irá falhar.</span><span class="sxs-lookup"><span data-stu-id="8c60d-118">If you specify __Checksum__ without __Validate__, the configuration will fail.</span></span>|
| <span data-ttu-id="8c60d-119">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="8c60d-119">Ensure</span></span>| <span data-ttu-id="8c60d-120">Determina se deve verificar se o conteúdo do arquivo existe no __destino__.</span><span class="sxs-lookup"><span data-stu-id="8c60d-120">Determines whether to check if the content of the archive exists at the __Destination__.</span></span> <span data-ttu-id="8c60d-121">Defina esta propriedade como __presente__ para garantir que existe o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="8c60d-121">Set this property to __Present__ to ensure the contents exist.</span></span> <span data-ttu-id="8c60d-122">Defina-o como __ausente__ para garantir que não existam.</span><span class="sxs-lookup"><span data-stu-id="8c60d-122">Set it to __Absent__ to ensure they do not exist.</span></span> <span data-ttu-id="8c60d-123">O valor predefinido é __presente__.</span><span class="sxs-lookup"><span data-stu-id="8c60d-123">The default value is __Present__.</span></span>|
| <span data-ttu-id="8c60d-124">dependsOn</span><span class="sxs-lookup"><span data-stu-id="8c60d-124">DependsOn</span></span> | <span data-ttu-id="8c60d-125">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="8c60d-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8c60d-126">Por exemplo, se o ID do bloco de script de configuração de recursos que pretende executar primeiro ResourceName e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="8c60d-126">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="8c60d-127">Validar</span><span class="sxs-lookup"><span data-stu-id="8c60d-127">Validate</span></span>| <span data-ttu-id="8c60d-128">Utiliza a propriedade de soma de verificação para determinar se o arquivo corresponde à assinatura.</span><span class="sxs-lookup"><span data-stu-id="8c60d-128">Uses the Checksum property to determine if the archive matches the signature.</span></span> <span data-ttu-id="8c60d-129">Se especificar sem validar de soma de verificação, a configuração irá falhar.</span><span class="sxs-lookup"><span data-stu-id="8c60d-129">If you specify Checksum without Validate, the configuration will fail.</span></span> <span data-ttu-id="8c60d-130">Se especificar validar sem soma de verificação, uma soma de verificação de SHA-256 é utilizada por predefinição.</span><span class="sxs-lookup"><span data-stu-id="8c60d-130">If you specify Validate without Checksum, a SHA-256 checksum is used by default.</span></span>|
| <span data-ttu-id="8c60d-131">Force</span><span class="sxs-lookup"><span data-stu-id="8c60d-131">Force</span></span>| <span data-ttu-id="8c60d-132">Determinadas operações de ficheiros (como substituir um ficheiro ou eliminar um diretório que não está vazio) resultará num erro.</span><span class="sxs-lookup"><span data-stu-id="8c60d-132">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="8c60d-133">Utilizando a propriedade de imposição substitui esses erros.</span><span class="sxs-lookup"><span data-stu-id="8c60d-133">Using the Force property overrides such errors.</span></span> <span data-ttu-id="8c60d-134">O valor predefinido é falso.</span><span class="sxs-lookup"><span data-stu-id="8c60d-134">The default value is False.</span></span>|

## <a name="example"></a><span data-ttu-id="8c60d-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8c60d-135">Example</span></span>

<span data-ttu-id="8c60d-136">O exemplo seguinte mostra como utilizar o recurso de arquivo para garantir que os conteúdos de um ficheiro de arquivo chamado Test.zip existem e que são extraídos num destino indicado.</span><span class="sxs-lookup"><span data-stu-id="8c60d-136">The following example shows how to use the Archive resource to ensure that the contents of an archive file called Test.zip exist and are extracted at a given destination.</span></span>

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```