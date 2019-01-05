---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: DSC para Linux nxFile recursos
ms.openlocfilehash: 80969ba2ea6247fcd616a301d951403a840c851d
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048822"
---
# <a name="dsc-for-linux-nxfile-resource"></a><span data-ttu-id="382ab-103">DSC para Linux nxFile recursos</span><span class="sxs-lookup"><span data-stu-id="382ab-103">DSC for Linux nxFile Resource</span></span>

<span data-ttu-id="382ab-104">O **nxFile** recursos no PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir ficheiros e diretórios num nó de Linux.</span><span class="sxs-lookup"><span data-stu-id="382ab-104">The **nxFile** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and directories on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="382ab-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="382ab-105">Syntax</span></span>

```
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Ensure = <string> { Absent | Present }  ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="382ab-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="382ab-106">Properties</span></span>

|  <span data-ttu-id="382ab-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="382ab-107">Property</span></span> |  <span data-ttu-id="382ab-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="382ab-108">Description</span></span> |
|---|---|
| <span data-ttu-id="382ab-109">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="382ab-109">DestinationPath</span></span>| <span data-ttu-id="382ab-110">Especifica a localização onde pretende garantir que o estado para um ficheiro ou diretório.</span><span class="sxs-lookup"><span data-stu-id="382ab-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="382ab-111">SourcePath</span><span class="sxs-lookup"><span data-stu-id="382ab-111">SourcePath</span></span>| <span data-ttu-id="382ab-112">Especifica o caminho a partir da qual pretende copiar o recurso de ficheiro ou pasta.</span><span class="sxs-lookup"><span data-stu-id="382ab-112">Specifies the path from which to copy the file or folder resource.</span></span> <span data-ttu-id="382ab-113">Este caminho pode ser um caminho local, ou um `http/https/ftp` URL.</span><span class="sxs-lookup"><span data-stu-id="382ab-113">This path may be a local path, or an `http/https/ftp` URL.</span></span> <span data-ttu-id="382ab-114">Remoto `http/https/ftp` URLs só são suportados quando o valor do **tipo** propriedade é o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="382ab-114">Remote `http/https/ftp` URLs are only supported when the value of the **Type** property is file.</span></span>|
| <span data-ttu-id="382ab-115">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="382ab-115">Ensure</span></span>| <span data-ttu-id="382ab-116">Determina se deve verificar se o ficheiro existe.</span><span class="sxs-lookup"><span data-stu-id="382ab-116">Determines whether to check if the file exists.</span></span> <span data-ttu-id="382ab-117">Defina esta propriedade para "Presente" para garantir que o ficheiro existe.</span><span class="sxs-lookup"><span data-stu-id="382ab-117">Set this property to "Present" to ensure the file exists.</span></span> <span data-ttu-id="382ab-118">Defini-lo como "Ausente", certifique-se de que o ficheiro não existe.</span><span class="sxs-lookup"><span data-stu-id="382ab-118">Set it to "Absent" to ensure the file does not exist.</span></span> <span data-ttu-id="382ab-119">O valor predefinido é "Presente".</span><span class="sxs-lookup"><span data-stu-id="382ab-119">The default value is "Present".</span></span>|
| <span data-ttu-id="382ab-120">Tipo</span><span class="sxs-lookup"><span data-stu-id="382ab-120">Type</span></span>| <span data-ttu-id="382ab-121">Especifica se o recurso a ser configurado é um diretório ou um ficheiro.</span><span class="sxs-lookup"><span data-stu-id="382ab-121">Specifies whether the resource being configured is a directory or a file.</span></span> <span data-ttu-id="382ab-122">Defina esta propriedade para o "diretório" para indicar que o recurso é um diretório.</span><span class="sxs-lookup"><span data-stu-id="382ab-122">Set this property to "directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="382ab-123">Defina-o para "file" para indicar que o recurso é um ficheiro.</span><span class="sxs-lookup"><span data-stu-id="382ab-123">Set it to "file" to indicate that the resource is a file.</span></span> <span data-ttu-id="382ab-124">O valor predefinido é "file"</span><span class="sxs-lookup"><span data-stu-id="382ab-124">The default value is "file"</span></span>|
| <span data-ttu-id="382ab-125">Conteúdos</span><span class="sxs-lookup"><span data-stu-id="382ab-125">Contents</span></span>| <span data-ttu-id="382ab-126">Especifica o conteúdo de um arquivo, como uma determinada cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="382ab-126">Specifies the contents of a file, such as a particular string.</span></span>|
| <span data-ttu-id="382ab-127">Soma de verificação</span><span class="sxs-lookup"><span data-stu-id="382ab-127">Checksum</span></span>| <span data-ttu-id="382ab-128">Define o tipo a utilizar ao determinar se dois arquivos são os mesmos.</span><span class="sxs-lookup"><span data-stu-id="382ab-128">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="382ab-129">Se **soma de verificação** não for especificada, apenas o nome de ficheiro ou diretório é utilizado para comparação.</span><span class="sxs-lookup"><span data-stu-id="382ab-129">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="382ab-130">Os valores são: "ctime", "mtime", ou "md5".</span><span class="sxs-lookup"><span data-stu-id="382ab-130">Values are: "ctime", "mtime", or "md5".</span></span>|
| <span data-ttu-id="382ab-131">Recurse</span><span class="sxs-lookup"><span data-stu-id="382ab-131">Recurse</span></span>| <span data-ttu-id="382ab-132">Indica se são incluídos os subdiretórios.</span><span class="sxs-lookup"><span data-stu-id="382ab-132">Indicates if subdirectories are included.</span></span> <span data-ttu-id="382ab-133">Defina esta propriedade como **$true** para indicar que pretende que o subdiretórios a serem incluídos.</span><span class="sxs-lookup"><span data-stu-id="382ab-133">Set this property to **$true** to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="382ab-134">A predefinição é **$false**.</span><span class="sxs-lookup"><span data-stu-id="382ab-134">The default is **$false**.</span></span> <span data-ttu-id="382ab-135">**Nota:** Esta propriedade só é válido quando o **tipo** propriedade está definida como o diretório.</span><span class="sxs-lookup"><span data-stu-id="382ab-135">**Note:** This property is only valid when the **Type** property is set to directory.</span></span>|
| <span data-ttu-id="382ab-136">Force</span><span class="sxs-lookup"><span data-stu-id="382ab-136">Force</span></span>| <span data-ttu-id="382ab-137">Determinadas operações de arquivo (como substituir um ficheiro ou eliminar um diretório que não está vazio) irão resultar num erro.</span><span class="sxs-lookup"><span data-stu-id="382ab-137">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="382ab-138">Utilizar o **força** propriedade substitui esses erros.</span><span class="sxs-lookup"><span data-stu-id="382ab-138">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="382ab-139">O valor predefinido é **$false**.</span><span class="sxs-lookup"><span data-stu-id="382ab-139">The default value is **$false**.</span></span>|
| <span data-ttu-id="382ab-140">Ligações</span><span class="sxs-lookup"><span data-stu-id="382ab-140">Links</span></span>| <span data-ttu-id="382ab-141">Especifica o comportamento desejado para links simbólicos.</span><span class="sxs-lookup"><span data-stu-id="382ab-141">Specifies the desired behavior for symbolic links.</span></span> <span data-ttu-id="382ab-142">Defina esta propriedade de "seguir" seguir links simbólicos e tomar decisões sobre o destino de ligações (por exemplo.</span><span class="sxs-lookup"><span data-stu-id="382ab-142">Set this property to "follow" to follow symbolic links and act on the links target (for example.</span></span> <span data-ttu-id="382ab-143">Copie o ficheiro em vez da ligação).</span><span class="sxs-lookup"><span data-stu-id="382ab-143">copy the file instead of the link).</span></span> <span data-ttu-id="382ab-144">Defina esta propriedade para "Gerir" para tomar decisões sobre a ligação (por exemplo.</span><span class="sxs-lookup"><span data-stu-id="382ab-144">Set this property to "manage" to act on the link (for example.</span></span> <span data-ttu-id="382ab-145">Copie a ligação em si).</span><span class="sxs-lookup"><span data-stu-id="382ab-145">copy the link itself).</span></span> <span data-ttu-id="382ab-146">Defina esta propriedade para "Ignorar" Ignorar links simbólicos.</span><span class="sxs-lookup"><span data-stu-id="382ab-146">Set this property to "ignore" to ignore symbolic links.</span></span>|
| <span data-ttu-id="382ab-147">Grupo</span><span class="sxs-lookup"><span data-stu-id="382ab-147">Group</span></span>| <span data-ttu-id="382ab-148">O nome da **grupo** para o proprietário do ficheiro ou diretório.</span><span class="sxs-lookup"><span data-stu-id="382ab-148">The name of the **Group** to own the file or directory.</span></span>|
| <span data-ttu-id="382ab-149">Modo</span><span class="sxs-lookup"><span data-stu-id="382ab-149">Mode</span></span>| <span data-ttu-id="382ab-150">Especifica as permissões pretendidas para o recurso na notação octal ou simbólica.</span><span class="sxs-lookup"><span data-stu-id="382ab-150">Specifies the desired permissions for the resource, in octal or symbolic notation.</span></span> <span data-ttu-id="382ab-151">(por exemplo, 777 ou rwxrwxrwx).</span><span class="sxs-lookup"><span data-stu-id="382ab-151">(for example, 777 or rwxrwxrwx).</span></span> <span data-ttu-id="382ab-152">Se utilizar a notação simbólica, não fornecem o primeiro caráter que indica o arquivo ou diretório.</span><span class="sxs-lookup"><span data-stu-id="382ab-152">If using symbolic notation, do not provide the first character which indicates directory or file.</span></span>|
| <span data-ttu-id="382ab-153">DependsOn</span><span class="sxs-lookup"><span data-stu-id="382ab-153">DependsOn</span></span> | <span data-ttu-id="382ab-154">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="382ab-154">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="382ab-155">Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e seu tipo é **ResourceType**, a sintaxe para usar isso a propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="382ab-155">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="382ab-156">Informações Adicionais</span><span class="sxs-lookup"><span data-stu-id="382ab-156">Additional Information</span></span>


<span data-ttu-id="382ab-157">Linux e Windows utilizam carateres de quebra de linha de diferentes em arquivos de texto por padrão, e isso pode causar resultados inesperados quando configurar alguns ficheiros num computador Linux com __nxFile__.</span><span class="sxs-lookup"><span data-stu-id="382ab-157">Linux and Windows use different line break characters in text files by default, and this can cause unexpected results when configuring some files on a Linux computer with __nxFile__.</span></span> <span data-ttu-id="382ab-158">Existem várias formas de gerir o conteúdo de um ficheiro do Linux, evitando problemas causados por carateres de quebra de linha inesperado:</span><span class="sxs-lookup"><span data-stu-id="382ab-158">There are multiple ways to manage the content of a Linux file while avoiding issues caused by unexpected line break characters:</span></span>

<span data-ttu-id="382ab-159">Passo 1: Copie o ficheiro a partir de uma origem remota (http, https ou ftp): Crie um ficheiro no Linux com o conteúdo pretendido e testá-los num servidor de ftp ou web acessível o nó (s) que irá configurar.</span><span class="sxs-lookup"><span data-stu-id="382ab-159">Step 1: Copy the file from a remote source (http, https, or ftp): create a file on Linux with the desired contents, and stage it on a web or ftp server accessible the node(s) you will configure.</span></span> <span data-ttu-id="382ab-160">Definir o __SourcePath__ propriedade na __nxFile__ recursos com o URL de web ou de ftp para o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="382ab-160">Define the __SourcePath__ property in the __nxFile__ resource with the web or ftp URL to the file.</span></span>

```
Import-DSCResource -Module nx
Node $Node
{
nxFile resolvConf
{
    SourcePath = "http://10.185.85.11/conf/resolv.conf"
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"

}

}
```


<span data-ttu-id="382ab-161">Passo 2: Ler o conteúdo do ficheiro do script do PowerShell com [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) após a definição a __$OFS__ propriedade para utilizar o caractere de quebra de linha de Linux.</span><span class="sxs-lookup"><span data-stu-id="382ab-161">Step 2: Read the file contents in the PowerShell script with [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) after setting the __$OFS__ property to use the Linux line-break character.</span></span>


```
Import-DSCResource -Module nx
Node $Node
{
$OFS = "`n"
$Contents = Get-Content C:\temp\resolv.conf

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"
    Contents = "$Contents"
}

}
```


<span data-ttu-id="382ab-162">Passo 3: Utilize uma função do PowerShell para substituir Windows quebras de linha com carateres de quebra de linha de Linux.</span><span class="sxs-lookup"><span data-stu-id="382ab-162">Step 3: Use a PowerShell function to replace Windows line breaks with Linux line-break characters.</span></span>

```
Function LinuxString($inputStr){
    $outputStr = $inputStr.Replace("`r`n","`n")
    $ouputStr += "`n"
    Return $outputStr
}

Import-DSCResource -Module nx
Node $Node
{

$Contents = @'
search contoso.com
domain contoso.com
nameserver 10.185.85.11
'@

$Contents = LinuxString $Contents

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"
    Contents = $Contents

}
}
```

## <a name="example"></a><span data-ttu-id="382ab-163">Exemplo</span><span class="sxs-lookup"><span data-stu-id="382ab-163">Example</span></span>

<span data-ttu-id="382ab-164">O exemplo seguinte, garante que o diretório `/opt/mydir` existe, e se um ficheiro com conteúdo especificado existe neste diretório.</span><span class="sxs-lookup"><span data-stu-id="382ab-164">The following example ensures that the directory `/opt/mydir` exists, and that a file with specified contents exists this directory.</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxFile DirectoryExample
{
   Ensure = "Present"
   DestinationPath = "/opt/mydir"
   Type = "Directory"
}

nxFile FileExample
{
    Ensure = "Present"
    Destinationpath = "/opt/mydir/myfile"
    Contents=@"
#!/bin/bash`necho "hello world"`n
"@
    Mode = “755”
    DependsOn = "[nxFile]DirectoryExample"
}
}
```