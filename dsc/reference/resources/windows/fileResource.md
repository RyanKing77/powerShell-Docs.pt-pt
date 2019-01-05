---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso do ficheiro de DSC
ms.openlocfilehash: e5f7a91e5f19c8c7bbada090804d8f29a7cfedd5
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048750"
---
# <a name="dsc-file-resource"></a><span data-ttu-id="eb995-103">Recurso do ficheiro de DSC</span><span class="sxs-lookup"><span data-stu-id="eb995-103">DSC File Resource</span></span>

> <span data-ttu-id="eb995-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="eb995-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="eb995-105">O recurso de arquivo no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir ficheiros e pastas no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="eb995-105">The File resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span>

><span data-ttu-id="eb995-106">**Nota:** Se o **MatchSource** estiver definida como **$false** (que é o valor predefinido), o conteúdo seja copiado é colocadas em cache na primeira vez que a configuração é aplicada.</span><span class="sxs-lookup"><span data-stu-id="eb995-106">**Note:** If the **MatchSource** property is set to **$false** (which is the default value), the contents to be copied are cached the first time the configuration is applied.</span></span>
><span data-ttu-id="eb995-107">Aplicativos subsequentes da configuração não verifica para ficheiros atualizados e/ou pastas no caminho especificado por **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="eb995-107">Subsequent applications of the configuration will not check for updated files and/or folders in the path specified by **SourcePath**.</span></span> <span data-ttu-id="eb995-108">Se pretende procurar atualizações para os ficheiros de e/ou pastas no **SourcePath** sempre que a configuração é aplicada, defina **MatchSource** para **$true**.</span><span class="sxs-lookup"><span data-stu-id="eb995-108">If you want to check for updates to the files and/or folders in **SourcePath** every time the configuration is applied, set **MatchSource** to **$true**.</span></span>

## <a name="syntax"></a><span data-ttu-id="eb995-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb995-109">Syntax</span></span>
```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a><span data-ttu-id="eb995-110">Propriedades</span><span class="sxs-lookup"><span data-stu-id="eb995-110">Properties</span></span>

|  <span data-ttu-id="eb995-111">Propriedade</span><span class="sxs-lookup"><span data-stu-id="eb995-111">Property</span></span>  |  <span data-ttu-id="eb995-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb995-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="eb995-113">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="eb995-113">DestinationPath</span></span>| <span data-ttu-id="eb995-114">Indica a localização onde pretende garantir que o estado para um ficheiro ou diretório.</span><span class="sxs-lookup"><span data-stu-id="eb995-114">Indicates the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="eb995-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="eb995-115">Attributes</span></span>| <span data-ttu-id="eb995-116">Especifica o estado pretendido dos atributos do ficheiro de destino ou diretório.</span><span class="sxs-lookup"><span data-stu-id="eb995-116">Specifies the desired state of the attributes for the targeted file or directory.</span></span>|
| <span data-ttu-id="eb995-117">Soma de verificação</span><span class="sxs-lookup"><span data-stu-id="eb995-117">Checksum</span></span>| <span data-ttu-id="eb995-118">Indica o tipo de soma de verificação a utilizar ao determinar se dois arquivos são os mesmos.</span><span class="sxs-lookup"><span data-stu-id="eb995-118">Indicates the checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="eb995-119">Se __soma de verificação__ não for especificada, apenas o nome de ficheiro ou diretório é utilizado para comparação.</span><span class="sxs-lookup"><span data-stu-id="eb995-119">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="eb995-120">Valores válidos incluem: SHA-1, SHA-256, SHA-512, colunas createdDate e modifiedDate.</span><span class="sxs-lookup"><span data-stu-id="eb995-120">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span></span>|
| <span data-ttu-id="eb995-121">Conteúdos</span><span class="sxs-lookup"><span data-stu-id="eb995-121">Contents</span></span>| <span data-ttu-id="eb995-122">Especifica o conteúdo de um arquivo, como uma determinada cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="eb995-122">Specifies the contents of a file, such as a particular string.</span></span>|
| <span data-ttu-id="eb995-123">Credencial</span><span class="sxs-lookup"><span data-stu-id="eb995-123">Credential</span></span>| <span data-ttu-id="eb995-124">Indica as credenciais que são necessárias para aceder aos recursos, tais como ficheiros de origem, se esse acesso for necessário.</span><span class="sxs-lookup"><span data-stu-id="eb995-124">Indicates the credentials that are required to access resources, such as source files, if such access is required.</span></span>|
| <span data-ttu-id="eb995-125">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="eb995-125">Ensure</span></span>| <span data-ttu-id="eb995-126">Indica se o ficheiro ou diretório existe.</span><span class="sxs-lookup"><span data-stu-id="eb995-126">Indicates if the file or directory exists.</span></span> <span data-ttu-id="eb995-127">Defina esta propriedade como "Ausente", certifique-se de que o ficheiro ou diretório não existe.</span><span class="sxs-lookup"><span data-stu-id="eb995-127">Set this property to "Absent" to ensure that the file or directory does not exist.</span></span> <span data-ttu-id="eb995-128">Defini-lo como "Presente" para se certificar de que o ficheiro ou diretório existe.</span><span class="sxs-lookup"><span data-stu-id="eb995-128">Set it to "Present" to ensure that the file or directory does exist.</span></span> <span data-ttu-id="eb995-129">A predefinição é "Presente".</span><span class="sxs-lookup"><span data-stu-id="eb995-129">The default is "Present".</span></span>|
| <span data-ttu-id="eb995-130">Force</span><span class="sxs-lookup"><span data-stu-id="eb995-130">Force</span></span>| <span data-ttu-id="eb995-131">Determinadas operações de arquivo (como substituir um ficheiro ou eliminar um diretório que não está vazio) irão resultar num erro.</span><span class="sxs-lookup"><span data-stu-id="eb995-131">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="eb995-132">Usando a propriedade de força substitui esses erros.</span><span class="sxs-lookup"><span data-stu-id="eb995-132">Using the Force property overrides such errors.</span></span> <span data-ttu-id="eb995-133">O valor predefinido é __$false__.</span><span class="sxs-lookup"><span data-stu-id="eb995-133">The default value is __$false__.</span></span>|
| <span data-ttu-id="eb995-134">Recurse</span><span class="sxs-lookup"><span data-stu-id="eb995-134">Recurse</span></span>| <span data-ttu-id="eb995-135">Indica se são incluídos os subdiretórios.</span><span class="sxs-lookup"><span data-stu-id="eb995-135">Indicates if subdirectories are included.</span></span> <span data-ttu-id="eb995-136">Defina esta propriedade como __$true__ para indicar que pretende que o subdiretórios a serem incluídos.</span><span class="sxs-lookup"><span data-stu-id="eb995-136">Set this property to __$true__ to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="eb995-137">A predefinição é __$false__.</span><span class="sxs-lookup"><span data-stu-id="eb995-137">The default is __$false__.</span></span> <span data-ttu-id="eb995-138">**Tenha em atenção**: Esta propriedade só é válida quando o tipo de propriedade é definido como diretório.</span><span class="sxs-lookup"><span data-stu-id="eb995-138">**Note**: This property is only valid when the Type property is set to Directory.</span></span>|
| <span data-ttu-id="eb995-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="eb995-139">DependsOn</span></span> | <span data-ttu-id="eb995-140">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="eb995-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="eb995-141">Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será __ResourceName__ e seu tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="eb995-141">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="eb995-142">SourcePath</span><span class="sxs-lookup"><span data-stu-id="eb995-142">SourcePath</span></span>| <span data-ttu-id="eb995-143">Indica o caminho a partir da qual pretende copiar o recurso de ficheiro ou pasta.</span><span class="sxs-lookup"><span data-stu-id="eb995-143">Indicates the path from which to copy the file or folder resource.</span></span>|
| <span data-ttu-id="eb995-144">Tipo</span><span class="sxs-lookup"><span data-stu-id="eb995-144">Type</span></span>| <span data-ttu-id="eb995-145">Indica se o recurso a ser configurado é um diretório ou de um ficheiro.</span><span class="sxs-lookup"><span data-stu-id="eb995-145">Indicates if the resource being configured is a directory or a file.</span></span> <span data-ttu-id="eb995-146">Defina esta propriedade para o "Diretório" para indicar que o recurso é um diretório.</span><span class="sxs-lookup"><span data-stu-id="eb995-146">Set this property to "Directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="eb995-147">Defini-lo como "File" para indicar que o recurso é um ficheiro.</span><span class="sxs-lookup"><span data-stu-id="eb995-147">Set it to "File" to indicate that the resource is a file.</span></span> <span data-ttu-id="eb995-148">O valor predefinido é "Arquivo".</span><span class="sxs-lookup"><span data-stu-id="eb995-148">The default value is “File”.</span></span>|
| <span data-ttu-id="eb995-149">MatchSource</span><span class="sxs-lookup"><span data-stu-id="eb995-149">MatchSource</span></span>| <span data-ttu-id="eb995-150">Se definido como o valor predefinido __$false__, em seguida, todos os ficheiros de origem (por exemplo, ficheiros A, B e C) serão adicionados para o destino na primeira vez que a configuração é aplicada.</span><span class="sxs-lookup"><span data-stu-id="eb995-150">If set to the default value of __$false__, then any files on the source (say, files A, B, and C) will be added to the destination the first time the configuration is applied.</span></span> <span data-ttu-id="eb995-151">Se for adicionado um novo ficheiro (D) para a origem, este será não ser adicionado para o destino, mesmo quando a configuração é novamente aplicada mais tarde.</span><span class="sxs-lookup"><span data-stu-id="eb995-151">If a new file (D) is added to the source, it will not be added to the destination, even when the configuration is re-applied later.</span></span> <span data-ttu-id="eb995-152">Se o valor for __$true__, em seguida, sempre que a configuração é aplicada, são adicionados novos ficheiros, em seguida, foi encontrados na origem (por exemplo, ficheiro D neste exemplo) para o destino.</span><span class="sxs-lookup"><span data-stu-id="eb995-152">If the value is __$true__, then each time the configuration is applied, new files subsequently found on the source (such as file D in this example) are added to the destination.</span></span> <span data-ttu-id="eb995-153">O valor predefinido é **$false**.</span><span class="sxs-lookup"><span data-stu-id="eb995-153">The default value is **$false**.</span></span>|

## <a name="example"></a><span data-ttu-id="eb995-154">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eb995-154">Example</span></span>

<span data-ttu-id="eb995-155">O exemplo seguinte mostra como usar o recurso de ficheiro para garantir que um diretório com o caminho `C:\Users\Public\Documents\DSCDemo\DemoSource` numa origem de computador (por exemplo, o servidor de "pull") também está presente (juntamente com todos os subdiretórios) no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="eb995-155">The following example shows how to use the File resource to ensure that a directory with the path `C:\Users\Public\Documents\DSCDemo\DemoSource` on a source computer (such as the “pull” server) is also present (along with all subdirectories) on the target node.</span></span> <span data-ttu-id="eb995-156">Ele também escreve uma mensagem confirmatory para o log quando estiver concluído e inclui uma instrução para se certificar de que a operação de verificação de ficheiros é executada antes da operação de registo.</span><span class="sxs-lookup"><span data-stu-id="eb995-156">It also writes a confirmatory message to the log when complete and includes a statement to ensure that the file-checking operation runs prior to the logging operation.</span></span>

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```