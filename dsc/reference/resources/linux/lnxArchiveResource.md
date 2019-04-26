---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: DSC para Linux nxArchive recursos
ms.openlocfilehash: 800954478f149e29c22d1a88304c3be9950f109a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078049"
---
# <a name="dsc-for-linux-nxarchive-resource"></a><span data-ttu-id="dd363-103">DSC para Linux nxArchive recursos</span><span class="sxs-lookup"><span data-stu-id="dd363-103">DSC for Linux nxArchive Resource</span></span>

<span data-ttu-id="dd363-104">O **nxArchive** recursos no PowerShell Desired State Configuration (DSC) fornece um mecanismo para descompactar os ficheiros de arquivo (. tar,. zip) num caminho específico num nó de Linux.</span><span class="sxs-lookup"><span data-stu-id="dd363-104">The **nxArchive** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.tar, .zip) files at a specific path on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="dd363-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dd363-105">Syntax</span></span>

```
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="dd363-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="dd363-106">Properties</span></span>

|  <span data-ttu-id="dd363-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="dd363-107">Property</span></span> |  <span data-ttu-id="dd363-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd363-108">Description</span></span> |
|---|---|
| <span data-ttu-id="dd363-109">SourcePath</span><span class="sxs-lookup"><span data-stu-id="dd363-109">SourcePath</span></span>| <span data-ttu-id="dd363-110">Especifica o caminho de origem do ficheiro de arquivo.</span><span class="sxs-lookup"><span data-stu-id="dd363-110">Specifies the source path of the archive file.</span></span> <span data-ttu-id="dd363-111">Isso deve ser um. tar,. zip, ou. GZ.</span><span class="sxs-lookup"><span data-stu-id="dd363-111">This should be a .tar, .zip, or .tar.gz file.</span></span> |
| <span data-ttu-id="dd363-112">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="dd363-112">DestinationPath</span></span>| <span data-ttu-id="dd363-113">Especifica a localização onde pretende Certifique-se de que o conteúdo do arquivo é extraído.</span><span class="sxs-lookup"><span data-stu-id="dd363-113">Specifies the location where you want to ensure the archive contents are extracted.</span></span>|
| <span data-ttu-id="dd363-114">Checksum</span><span class="sxs-lookup"><span data-stu-id="dd363-114">Checksum</span></span>| <span data-ttu-id="dd363-115">Define o tipo a utilizar ao determinar se o arquivo de origem foi atualizado.</span><span class="sxs-lookup"><span data-stu-id="dd363-115">Defines the type to use when determining whether the source archive has been updated.</span></span> <span data-ttu-id="dd363-116">Os valores são: "ctime", "mtime", ou "md5".</span><span class="sxs-lookup"><span data-stu-id="dd363-116">Values are: "ctime", "mtime", or "md5".</span></span> <span data-ttu-id="dd363-117">O valor predefinido é "md5".</span><span class="sxs-lookup"><span data-stu-id="dd363-117">The default value is "md5".</span></span>|
| <span data-ttu-id="dd363-118">Force</span><span class="sxs-lookup"><span data-stu-id="dd363-118">Force</span></span>| <span data-ttu-id="dd363-119">Determinadas operações de arquivo (como substituir um ficheiro ou eliminar um diretório que não está vazio) irão resultar num erro.</span><span class="sxs-lookup"><span data-stu-id="dd363-119">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="dd363-120">Utilizar o **força** propriedade substitui esses erros.</span><span class="sxs-lookup"><span data-stu-id="dd363-120">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="dd363-121">O valor predefinido é **$false**.</span><span class="sxs-lookup"><span data-stu-id="dd363-121">The default value is **$false**.</span></span>|
| <span data-ttu-id="dd363-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="dd363-122">DependsOn</span></span> | <span data-ttu-id="dd363-123">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="dd363-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="dd363-124">Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e seu tipo é **ResourceType**, a sintaxe para usar isso a propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="dd363-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="dd363-125">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="dd363-125">Ensure</span></span>| <span data-ttu-id="dd363-126">Determina se deve verificar se o conteúdo do arquivo existe no **destino**.</span><span class="sxs-lookup"><span data-stu-id="dd363-126">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="dd363-127">Defina esta propriedade para "Presente" para garantir que existe o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="dd363-127">Set this property to "Present" to ensure the contents exist.</span></span> <span data-ttu-id="dd363-128">Defini-lo como "Ausente", certifique-se de que não existam.</span><span class="sxs-lookup"><span data-stu-id="dd363-128">Set it to "Absent" to ensure they do not exist.</span></span> <span data-ttu-id="dd363-129">O valor predefinido é "Presente".</span><span class="sxs-lookup"><span data-stu-id="dd363-129">The default value is "Present".</span></span>|

## <a name="example"></a><span data-ttu-id="dd363-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dd363-130">Example</span></span>

<span data-ttu-id="dd363-131">O exemplo seguinte mostra como utilizar o **nxArchive** recurso para garantir que o conteúdo de um ficheiro de arquivo chamado `website.tar` existem e são extraídos num determinado destino.</span><span class="sxs-lookup"><span data-stu-id="dd363-131">The following example shows how to use the **nxArchive** resource to ensure that the contents of an archive file called `website.tar` exist and are extracted at a given destination.</span></span>

```
Import-DSCResource -Module nx

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = “http://release.contoso.com/releases/website.tar”
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = “mtime”
}

nxArchive SyncWebDir
{
   SourcePath = “/usr/release/staging/website.tar”
   DestinationPath = “/usr/local/apache2/htdocs/”
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
}
```