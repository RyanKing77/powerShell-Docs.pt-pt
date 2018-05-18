---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: DSC de Linux nxArchive recursos
ms.openlocfilehash: 800954478f149e29c22d1a88304c3be9950f109a
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-for-linux-nxarchive-resource"></a><span data-ttu-id="c3837-103">DSC de Linux nxArchive recursos</span><span class="sxs-lookup"><span data-stu-id="c3837-103">DSC for Linux nxArchive Resource</span></span>

<span data-ttu-id="c3837-104">O **nxArchive** recursos no PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para descompactar os ficheiros de arquivo (. tar,. zip) de um caminho específico num nó de Linux.</span><span class="sxs-lookup"><span data-stu-id="c3837-104">The **nxArchive** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.tar, .zip) files at a specific path on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="c3837-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3837-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="c3837-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c3837-106">Properties</span></span>

|  <span data-ttu-id="c3837-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="c3837-107">Property</span></span> |  <span data-ttu-id="c3837-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3837-108">Description</span></span> |
|---|---|
| <span data-ttu-id="c3837-109">SourcePath</span><span class="sxs-lookup"><span data-stu-id="c3837-109">SourcePath</span></span>| <span data-ttu-id="c3837-110">Especifica o caminho de origem do ficheiro de arquivo.</span><span class="sxs-lookup"><span data-stu-id="c3837-110">Specifies the source path of the archive file.</span></span> <span data-ttu-id="c3837-111">Isto deve ser um tar. zip, ou. ficheiro.tar.GZ.</span><span class="sxs-lookup"><span data-stu-id="c3837-111">This should be a .tar, .zip, or .tar.gz file.</span></span> |
| <span data-ttu-id="c3837-112">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="c3837-112">DestinationPath</span></span>| <span data-ttu-id="c3837-113">Especifica a localização onde pretende Certifique-se de que o conteúdo de arquivo é extraído.</span><span class="sxs-lookup"><span data-stu-id="c3837-113">Specifies the location where you want to ensure the archive contents are extracted.</span></span>|
| <span data-ttu-id="c3837-114">Soma de verificação</span><span class="sxs-lookup"><span data-stu-id="c3837-114">Checksum</span></span>| <span data-ttu-id="c3837-115">Define o tipo a utilizar ao determinar se o arquivo de origem tiver sido atualizado.</span><span class="sxs-lookup"><span data-stu-id="c3837-115">Defines the type to use when determining whether the source archive has been updated.</span></span> <span data-ttu-id="c3837-116">Os valores são: "ctime", "mtime" ou "md5".</span><span class="sxs-lookup"><span data-stu-id="c3837-116">Values are: "ctime", "mtime", or "md5".</span></span> <span data-ttu-id="c3837-117">O valor predefinido é "md5".</span><span class="sxs-lookup"><span data-stu-id="c3837-117">The default value is "md5".</span></span>|
| <span data-ttu-id="c3837-118">Force</span><span class="sxs-lookup"><span data-stu-id="c3837-118">Force</span></span>| <span data-ttu-id="c3837-119">Determinadas operações de ficheiros (como substituir um ficheiro ou eliminar um diretório que não está vazio) resultará num erro.</span><span class="sxs-lookup"><span data-stu-id="c3837-119">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="c3837-120">Utilizar o **Force** propriedade substitui esses erros.</span><span class="sxs-lookup"><span data-stu-id="c3837-120">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="c3837-121">O valor predefinido é **$false**.</span><span class="sxs-lookup"><span data-stu-id="c3837-121">The default value is **$false**.</span></span>|
| <span data-ttu-id="c3837-122">dependsOn</span><span class="sxs-lookup"><span data-stu-id="c3837-122">DependsOn</span></span> | <span data-ttu-id="c3837-123">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="c3837-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c3837-124">Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e o respetivo tipo é **ResourceType**, a sintaxe para utilizar esta a propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="c3837-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="c3837-125">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="c3837-125">Ensure</span></span>| <span data-ttu-id="c3837-126">Determina se deve verificar se o conteúdo do arquivo existe no **destino**.</span><span class="sxs-lookup"><span data-stu-id="c3837-126">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="c3837-127">Defina esta propriedade para "Presente" para garantir que existe o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="c3837-127">Set this property to "Present" to ensure the contents exist.</span></span> <span data-ttu-id="c3837-128">Defina-o para "Ausente", certifique-se de que não existam.</span><span class="sxs-lookup"><span data-stu-id="c3837-128">Set it to "Absent" to ensure they do not exist.</span></span> <span data-ttu-id="c3837-129">O valor predefinido é "Presente".</span><span class="sxs-lookup"><span data-stu-id="c3837-129">The default value is "Present".</span></span>|

## <a name="example"></a><span data-ttu-id="c3837-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c3837-130">Example</span></span>

<span data-ttu-id="c3837-131">O exemplo seguinte mostra como utilizar o **nxArchive** recursos para se certificar de que o conteúdo de um ficheiro de arquivo chamado `website.tar` existe e que são extraídos num destino indicado.</span><span class="sxs-lookup"><span data-stu-id="c3837-131">The following example shows how to use the **nxArchive** resource to ensure that the contents of an archive file called `website.tar` exist and are extracted at a given destination.</span></span>

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