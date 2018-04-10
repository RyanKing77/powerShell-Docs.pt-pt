---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Recursos de DSC ficheiro
ms.openlocfilehash: 7964eabe5f4585600ae80f3e5ff7439c0d954769
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-file-resource"></a><span data-ttu-id="a6f2c-103">Recursos de DSC ficheiro</span><span class="sxs-lookup"><span data-stu-id="a6f2c-103">DSC File Resource</span></span>

> <span data-ttu-id="a6f2c-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a6f2c-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="a6f2c-105">O recurso de ficheiros no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir ficheiros e pastas no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-105">The File resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span>

><span data-ttu-id="a6f2c-106">**Nota:** se o **MatchSource** propriedade está definida como **$false** (que é o valor predefinido), o conteúdo a ser copiado é colocadas em cache na primeira vez que a configuração é aplicada.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-106">**Note:** If the **MatchSource** property is set to **$false** (which is the default value), the contents to be copied are cached the first time the configuration is applied.</span></span>
><span data-ttu-id="a6f2c-107">Aplicações subsequentes da configuração não verifica os ficheiros atualizados e/ou pastas no caminho especificado por **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-107">Subsequent applications of the configuration will not check for updated files and/or folders in the path specified by **SourcePath**.</span></span> <span data-ttu-id="a6f2c-108">Se quiser verificar a existência de atualizações a ficheiros e/ou pastas **SourcePath** sempre que a configuração é aplicada, defina **MatchSource** para **$true**.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-108">If you want to check for updates to the files and/or folders in **SourcePath** every time the configuration is applied, set **MatchSource** to **$true**.</span></span>

## <a name="syntax"></a><span data-ttu-id="a6f2c-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6f2c-109">Syntax</span></span>
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

## <a name="properties"></a><span data-ttu-id="a6f2c-110">Propriedades</span><span class="sxs-lookup"><span data-stu-id="a6f2c-110">Properties</span></span>

|  <span data-ttu-id="a6f2c-111">Propriedade</span><span class="sxs-lookup"><span data-stu-id="a6f2c-111">Property</span></span>  |  <span data-ttu-id="a6f2c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6f2c-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="a6f2c-113">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="a6f2c-113">DestinationPath</span></span>| <span data-ttu-id="a6f2c-114">Indica a localização onde pretende garantir o estado de um ficheiro ou diretório.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-114">Indicates the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="a6f2c-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="a6f2c-115">Attributes</span></span>| <span data-ttu-id="a6f2c-116">Especifica o estado pretendido de atributos para o destino de ficheiro ou diretório.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-116">Specifies the desired state of the attributes for the targeted file or directory.</span></span>|
| <span data-ttu-id="a6f2c-117">Soma de verificação</span><span class="sxs-lookup"><span data-stu-id="a6f2c-117">Checksum</span></span>| <span data-ttu-id="a6f2c-118">Indica o tipo de soma de verificação a utilizar ao determinar se os dois ficheiros são as mesmas.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-118">Indicates the checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="a6f2c-119">Se __soma de verificação__ não for especificado, apenas o nome de ficheiro ou diretório é utilizado para comparação.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-119">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="a6f2c-120">Os valores válidos incluem: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-120">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span></span>|
| <span data-ttu-id="a6f2c-121">Conteúdos</span><span class="sxs-lookup"><span data-stu-id="a6f2c-121">Contents</span></span>| <span data-ttu-id="a6f2c-122">Especifica o conteúdo de um ficheiro, como uma cadeia específica.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-122">Specifies the contents of a file, such as a particular string.</span></span>|
| <span data-ttu-id="a6f2c-123">credencial</span><span class="sxs-lookup"><span data-stu-id="a6f2c-123">Credential</span></span>| <span data-ttu-id="a6f2c-124">Indica as credenciais que são necessárias para aceder a recursos, tais como ficheiros de origem, se for necessário esse acesso.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-124">Indicates the credentials that are required to access resources, such as source files, if such access is required.</span></span>|
| <span data-ttu-id="a6f2c-125">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="a6f2c-125">Ensure</span></span>| <span data-ttu-id="a6f2c-126">Indica se o ficheiro ou diretório existe.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-126">Indicates if the file or directory exists.</span></span> <span data-ttu-id="a6f2c-127">Defina esta propriedade para "Ausente", certifique-se de que o ficheiro ou diretório não existe.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-127">Set this property to "Absent" to ensure that the file or directory does not exist.</span></span> <span data-ttu-id="a6f2c-128">Defina-o para "Presente" para se certificar de que o ficheiro ou diretório existe.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-128">Set it to "Present" to ensure that the file or directory does exist.</span></span> <span data-ttu-id="a6f2c-129">A predefinição é "Presente".</span><span class="sxs-lookup"><span data-stu-id="a6f2c-129">The default is "Present".</span></span>|
| <span data-ttu-id="a6f2c-130">Force</span><span class="sxs-lookup"><span data-stu-id="a6f2c-130">Force</span></span>| <span data-ttu-id="a6f2c-131">Determinadas operações de ficheiros (como substituir um ficheiro ou eliminar um diretório que não está vazio) resultará num erro.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-131">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="a6f2c-132">Utilizando a propriedade de imposição substitui esses erros.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-132">Using the Force property overrides such errors.</span></span> <span data-ttu-id="a6f2c-133">O valor predefinido é __$false__.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-133">The default value is __$false__.</span></span>|
| <span data-ttu-id="a6f2c-134">Recurse</span><span class="sxs-lookup"><span data-stu-id="a6f2c-134">Recurse</span></span>| <span data-ttu-id="a6f2c-135">Indica se subdiretórios estão incluídos.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-135">Indicates if subdirectories are included.</span></span> <span data-ttu-id="a6f2c-136">Defina esta propriedade como __$true__ para indicar que pretende que o subdiretórios a incluir.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-136">Set this property to __$true__ to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="a6f2c-137">A predefinição é __$false__.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-137">The default is __$false__.</span></span> <span data-ttu-id="a6f2c-138">**Tenha em atenção**: Esta propriedade só é válida quando a propriedade Type é definida ao diretório.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-138">**Note**: This property is only valid when the Type property is set to Directory.</span></span>|
| <span data-ttu-id="a6f2c-139">dependsOn</span><span class="sxs-lookup"><span data-stu-id="a6f2c-139">DependsOn</span></span> | <span data-ttu-id="a6f2c-140">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a6f2c-141">Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-141">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="a6f2c-142">SourcePath</span><span class="sxs-lookup"><span data-stu-id="a6f2c-142">SourcePath</span></span>| <span data-ttu-id="a6f2c-143">Indica o caminho a partir dos quais pretende copiar o recurso do ficheiro ou pasta.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-143">Indicates the path from which to copy the file or folder resource.</span></span>|
| <span data-ttu-id="a6f2c-144">Tipo</span><span class="sxs-lookup"><span data-stu-id="a6f2c-144">Type</span></span>| <span data-ttu-id="a6f2c-145">Indica se o recurso que está a ser configurado um diretório ou um ficheiro.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-145">Indicates if the resource being configured is a directory or a file.</span></span> <span data-ttu-id="a6f2c-146">Defina esta propriedade para "Diretório" para indicar que o recurso é um diretório.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-146">Set this property to "Directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="a6f2c-147">Defina-o para "Ficheiro" para indicar que o recurso é um ficheiro.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-147">Set it to "File" to indicate that the resource is a file.</span></span> <span data-ttu-id="a6f2c-148">O valor predefinido é "Ficheiro".</span><span class="sxs-lookup"><span data-stu-id="a6f2c-148">The default value is “File”.</span></span>|
| <span data-ttu-id="a6f2c-149">MatchSource</span><span class="sxs-lookup"><span data-stu-id="a6f2c-149">MatchSource</span></span>| <span data-ttu-id="a6f2c-150">Se definir o valor predefinido de __$false__, em seguida, todos os ficheiros de origem (diga, os ficheiros A, B e C) serão adicionados para o destino na primeira vez que a configuração é aplicada.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-150">If set to the default value of __$false__, then any files on the source (say, files A, B, and C) will be added to the destination the first time the configuration is applied.</span></span> <span data-ttu-id="a6f2c-151">Se for adicionado um novo ficheiro (D) para a origem, que será não ser adicionado para o destino, mesmo quando a configuração é novamente aplicada mais tarde.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-151">If a new file (D) is added to the source, it will not be added to the destination, even when the configuration is re-applied later.</span></span> <span data-ttu-id="a6f2c-152">Se o valor for __$true__, em seguida, sempre que a configuração é aplicada, são adicionados novos ficheiros, subsequentemente, foi encontrados na origem (por exemplo, o ficheiro D neste exemplo) para o destino.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-152">If the value is __$true__, then each time the configuration is applied, new files subsequently found on the source (such as file D in this example) are added to the destination.</span></span> <span data-ttu-id="a6f2c-153">O valor predefinido é **$false**.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-153">The default value is **$false**.</span></span>|

## <a name="example"></a><span data-ttu-id="a6f2c-154">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a6f2c-154">Example</span></span>

<span data-ttu-id="a6f2c-155">O exemplo seguinte mostra como utilizar o recurso do ficheiro para garantir que um diretório com o caminho `C:\Users\Public\Documents\DSCDemo\DemoSource` numa origem de computador (por exemplo, o servidor "solicitação") encontra-se também (juntamente com todos os subdiretórios) no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-155">The following example shows how to use the File resource to ensure that a directory with the path `C:\Users\Public\Documents\DSCDemo\DemoSource` on a source computer (such as the “pull” server) is also present (along with all subdirectories) on the target node.</span></span> <span data-ttu-id="a6f2c-156">Também escreve uma mensagem confirmatory no registo concluído e inclui uma instrução para se certificar de que a operação de verificação do ficheiro é executado antes da operação de registo.</span><span class="sxs-lookup"><span data-stu-id="a6f2c-156">It also writes a confirmatory message to the log when complete and includes a statement to ensure that the file-checking operation runs prior to the logging operation.</span></span>

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