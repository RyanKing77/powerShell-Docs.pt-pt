---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: DSC de Linux nxFile recursos
ms.openlocfilehash: e4916414e4de29ab15d9c82c492671ebc16d5412
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxfile-resource"></a><span data-ttu-id="8d2b9-103">DSC de Linux nxFile recursos</span><span class="sxs-lookup"><span data-stu-id="8d2b9-103">DSC for Linux nxFile Resource</span></span>

<span data-ttu-id="8d2b9-104">O **nxFile** recursos no PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir ficheiros e diretórios num nó de Linux.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-104">The **nxFile** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage files and directories on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="8d2b9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d2b9-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="8d2b9-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="8d2b9-106">Properties</span></span>

|  <span data-ttu-id="8d2b9-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="8d2b9-107">Property</span></span> |  <span data-ttu-id="8d2b9-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d2b9-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="8d2b9-109">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="8d2b9-109">DestinationPath</span></span>| <span data-ttu-id="8d2b9-110">Especifica a localização onde pretende garantir o estado de um ficheiro ou diretório.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>| 
| <span data-ttu-id="8d2b9-111">SourcePath</span><span class="sxs-lookup"><span data-stu-id="8d2b9-111">SourcePath</span></span>| <span data-ttu-id="8d2b9-112">Especifica o caminho a partir dos quais pretende copiar o recurso do ficheiro ou pasta.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-112">Specifies the path from which to copy the file or folder resource.</span></span> <span data-ttu-id="8d2b9-113">Este caminho pode ser um caminho local, ou um `http/https/ftp` URL.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-113">This path may be a local path, or an `http/https/ftp` URL.</span></span> <span data-ttu-id="8d2b9-114">Remoto `http/https/ftp` URLs só são suportadas quando o valor da **tipo** propriedade é o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-114">Remote `http/https/ftp` URLs are only supported when the value of the **Type** property is file.</span></span>| 
| <span data-ttu-id="8d2b9-115">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="8d2b9-115">Ensure</span></span>| <span data-ttu-id="8d2b9-116">Determina se deve verificar se o ficheiro existe.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-116">Determines whether to check if the file exists.</span></span> <span data-ttu-id="8d2b9-117">Defina esta propriedade para "Presente" para garantir que o ficheiro existe.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-117">Set this property to "Present" to ensure the file exists.</span></span> <span data-ttu-id="8d2b9-118">Defina-o para "Ausente", certifique-se de que o ficheiro não existe.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-118">Set it to "Absent" to ensure the file does not exist.</span></span> <span data-ttu-id="8d2b9-119">O valor predefinido é "Presente".</span><span class="sxs-lookup"><span data-stu-id="8d2b9-119">The default value is "Present".</span></span>| 
| <span data-ttu-id="8d2b9-120">Tipo</span><span class="sxs-lookup"><span data-stu-id="8d2b9-120">Type</span></span>| <span data-ttu-id="8d2b9-121">Especifica se o recurso que está a ser configurado é um diretório ou um ficheiro.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-121">Specifies whether the resource being configured is a directory or a file.</span></span> <span data-ttu-id="8d2b9-122">Defina esta propriedade para "diretório" para indicar que o recurso é um diretório.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-122">Set this property to "directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="8d2b9-123">Defina-o para "do ficheiro" para indicar que o recurso é um ficheiro.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-123">Set it to "file" to indicate that the resource is a file.</span></span> <span data-ttu-id="8d2b9-124">O valor predefinido é "ficheiros"</span><span class="sxs-lookup"><span data-stu-id="8d2b9-124">The default value is "file"</span></span>| 
| <span data-ttu-id="8d2b9-125">Conteúdos</span><span class="sxs-lookup"><span data-stu-id="8d2b9-125">Contents</span></span>| <span data-ttu-id="8d2b9-126">Especifica o conteúdo de um ficheiro, como uma cadeia específica.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-126">Specifies the contents of a file, such as a particular string.</span></span>| 
| <span data-ttu-id="8d2b9-127">Soma de verificação</span><span class="sxs-lookup"><span data-stu-id="8d2b9-127">Checksum</span></span>| <span data-ttu-id="8d2b9-128">Define o tipo a utilizar ao determinar se os dois ficheiros são as mesmas.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-128">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="8d2b9-129">Se **soma de verificação** não for especificado, apenas o nome de ficheiro ou diretório é utilizado para comparação.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-129">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="8d2b9-130">Os valores são: "ctime", "mtime" ou "md5".</span><span class="sxs-lookup"><span data-stu-id="8d2b9-130">Values are: "ctime", "mtime", or "md5".</span></span>| 
| <span data-ttu-id="8d2b9-131">Recurse</span><span class="sxs-lookup"><span data-stu-id="8d2b9-131">Recurse</span></span>| <span data-ttu-id="8d2b9-132">Indica se subdiretórios estão incluídos.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-132">Indicates if subdirectories are included.</span></span> <span data-ttu-id="8d2b9-133">Defina esta propriedade como **$true** para indicar que pretende que o subdiretórios a incluir.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-133">Set this property to **$true** to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="8d2b9-134">A predefinição é **$false**.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-134">The default is **$false**.</span></span> <span data-ttu-id="8d2b9-135">**Nota:** esta propriedade só é válido quando o **tipo** propriedade está definida para o diretório.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-135">**Note:** This property is only valid when the **Type** property is set to directory.</span></span>| 
| <span data-ttu-id="8d2b9-136">Force</span><span class="sxs-lookup"><span data-stu-id="8d2b9-136">Force</span></span>| <span data-ttu-id="8d2b9-137">Determinadas operações de ficheiros (como substituir um ficheiro ou eliminar um diretório que não está vazio) resultará num erro.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-137">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="8d2b9-138">Utilizar o **Force** propriedade substitui esses erros.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-138">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="8d2b9-139">O valor predefinido é **$false**.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-139">The default value is **$false**.</span></span>| 
| <span data-ttu-id="8d2b9-140">Ligações</span><span class="sxs-lookup"><span data-stu-id="8d2b9-140">Links</span></span>| <span data-ttu-id="8d2b9-141">Especifica o comportamento pretendido para as ligações simbólicas.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-141">Specifies the desired behavior for symbolic links.</span></span> <span data-ttu-id="8d2b9-142">Definir esta propriedade para "seguir", siga as ligações simbólicas e atuar sobre o destino de ligações (por exemplo.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-142">Set this property to "follow" to follow symbolic links and act on the links target (for example.</span></span> <span data-ttu-id="8d2b9-143">Copie o ficheiro em vez da ligação).</span><span class="sxs-lookup"><span data-stu-id="8d2b9-143">copy the file instead of the link).</span></span> <span data-ttu-id="8d2b9-144">Definir esta propriedade para "Gerir" para atuar na ligação (por exemplo.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-144">Set this property to "manage" to act on the link (for example.</span></span> <span data-ttu-id="8d2b9-145">Copie a ligação próprio).</span><span class="sxs-lookup"><span data-stu-id="8d2b9-145">copy the link itself).</span></span> <span data-ttu-id="8d2b9-146">Defina esta propriedade para "Ignorar" para ignorar as ligações simbólicas.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-146">Set this property to "ignore" to ignore symbolic links.</span></span>| 
| <span data-ttu-id="8d2b9-147">Grupo</span><span class="sxs-lookup"><span data-stu-id="8d2b9-147">Group</span></span>| <span data-ttu-id="8d2b9-148">O nome do **grupo** possuir o ficheiro ou diretório.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-148">The name of the **Group** to own the file or directory.</span></span>| 
| <span data-ttu-id="8d2b9-149">Modo</span><span class="sxs-lookup"><span data-stu-id="8d2b9-149">Mode</span></span>| <span data-ttu-id="8d2b9-150">Especifica as permissões pretendidas para o recurso, octal ou simbólica notação.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-150">Specifies the desired permissions for the resource, in octal or symbolic notation.</span></span> <span data-ttu-id="8d2b9-151">(por exemplo, 777 ou rwxrwxrwx).</span><span class="sxs-lookup"><span data-stu-id="8d2b9-151">(for example, 777 or rwxrwxrwx).</span></span> <span data-ttu-id="8d2b9-152">Se utilizar a notação simbólica, não fornecem o primeiro caráter que indica o diretório ou ficheiro.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-152">If using symbolic notation, do not provide the first character which indicates directory or file.</span></span>| 
| <span data-ttu-id="8d2b9-153">dependsOn</span><span class="sxs-lookup"><span data-stu-id="8d2b9-153">DependsOn</span></span> | <span data-ttu-id="8d2b9-154">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-154">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8d2b9-155">Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e o respetivo tipo é **ResourceType**, a sintaxe para utilizar esta a propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-155">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="additional-information"></a><span data-ttu-id="8d2b9-156">Informações Adicionais</span><span class="sxs-lookup"><span data-stu-id="8d2b9-156">Additional Information</span></span>


<span data-ttu-id="8d2b9-157">Linux e Windows utilizar carateres de quebra de linha diferente nos ficheiros de texto por predefinição e isto pode causar resultados inesperados quando configurar alguns ficheiros num computador com Linux __nxFile__.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-157">Linux and Windows use different line break characters in text files by default, and this can cause unexpected results when configuring some files on a Linux computer with __nxFile__.</span></span> <span data-ttu-id="8d2b9-158">Existem várias formas de gerir o conteúdo de um ficheiro de Linux ao evitando problemas causados por carateres de quebra de linha inesperado:</span><span class="sxs-lookup"><span data-stu-id="8d2b9-158">There are multiple ways to manage the content of a Linux file while avoiding issues caused by unexpected line break characters:</span></span>

<span data-ttu-id="8d2b9-159">Passo 1: Copiar o ficheiro de uma origem remota (http, https ou ftp): Crie um ficheiro no Linux com os conteúdos pretendidos e testar num servidor web ou de ftp acessível a principais irá configurar.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-159">Step 1: Copy the file from a remote source (http, https, or ftp): create a file on Linux with the desired contents, and stage it on a web or ftp server accessible the node(s) you will configure.</span></span> <span data-ttu-id="8d2b9-160">Definir o __SourcePath__ propriedade no __nxFile__ recursos com o URL de web ou de ftp para o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-160">Define the __SourcePath__ property in the __nxFile__ resource with the web or ftp URL to the file.</span></span>

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


<span data-ttu-id="8d2b9-161">Passo 2: Ler o conteúdo do ficheiro no script PowerShell com [Get-Content](https://technet.microsoft.com/en-us/library/hh849787.aspx) após a definição de __$OFS__ propriedade para utilizar o caráter de quebra de linha do Linux.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-161">Step 2: Read the file contents in the PowerShell script with [Get-Content](https://technet.microsoft.com/en-us/library/hh849787.aspx) after setting the __$OFS__ property to use the Linux line-break character.</span></span>


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


<span data-ttu-id="8d2b9-162">Passo 3: Utilize uma função do PowerShell para substituir as quebras de linha do Windows com carateres de quebra de linha do Linux.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-162">Step 3: Use a PowerShell function to replace Windows line breaks with Linux line-break characters.</span></span>

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

## <a name="example"></a><span data-ttu-id="8d2b9-163">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8d2b9-163">Example</span></span>

<span data-ttu-id="8d2b9-164">O exemplo seguinte assegura que o diretório `/opt/mydir` existir, e se um ficheiro com conteúdo especificado existe este diretório.</span><span class="sxs-lookup"><span data-stu-id="8d2b9-164">The following example ensures that the directory `/opt/mydir` exists, and that a file with specified contents exists this directory.</span></span>

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

