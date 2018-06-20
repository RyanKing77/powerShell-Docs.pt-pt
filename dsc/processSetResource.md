---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Recursos do DSC ProcessSet
ms.openlocfilehash: 412cf1076996126f0d9b7a9a8ebbc9bdb7ecf377
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189929"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="a75ad-103">Recursos do DSC WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="a75ad-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="a75ad-104">Aplica-se a: O Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a75ad-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="a75ad-105">O **ProcessSet** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para configurar processos num nó de destino.</span><span class="sxs-lookup"><span data-stu-id="a75ad-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span> <span data-ttu-id="a75ad-106">Este recurso é um [recursos composto](authoringResourceComposite.md) que chama o [WindowsProcess recursos](windowsProcessResource.md) para cada grupo especificado no `GroupName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a75ad-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsProcess resource](windowsProcessResource.md) for each group specified in the `GroupName` parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="a75ad-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a75ad-107">Syntax</span></span>

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="a75ad-108">Propriedades</span><span class="sxs-lookup"><span data-stu-id="a75ad-108">Properties</span></span>
|  <span data-ttu-id="a75ad-109">Propriedade</span><span class="sxs-lookup"><span data-stu-id="a75ad-109">Property</span></span>  |  <span data-ttu-id="a75ad-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="a75ad-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="a75ad-111">Argumentos</span><span class="sxs-lookup"><span data-stu-id="a75ad-111">Arguments</span></span>| <span data-ttu-id="a75ad-112">Uma cadeia que contém os argumentos transmitidos para o processo que-é.</span><span class="sxs-lookup"><span data-stu-id="a75ad-112">A string that contains arguments to pass to the process as-is.</span></span> <span data-ttu-id="a75ad-113">Se tiver de passar vários argumentos, colocá-los a todos nesta cadeia.</span><span class="sxs-lookup"><span data-stu-id="a75ad-113">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="a75ad-114">Caminho</span><span class="sxs-lookup"><span data-stu-id="a75ad-114">Path</span></span>| <span data-ttu-id="a75ad-115">Os caminhos para o processo de executáveis.</span><span class="sxs-lookup"><span data-stu-id="a75ad-115">The paths to the process executables.</span></span> <span data-ttu-id="a75ad-116">Se estes são os nomes dos ficheiros executáveis (caminhos completamente qualificados), os recursos de DSC pesquisará o ambiente **caminho** variável (`$env:Path`) para localizar os ficheiros.</span><span class="sxs-lookup"><span data-stu-id="a75ad-116">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the files.</span></span> <span data-ttu-id="a75ad-117">Se os valores desta propriedade caminhos completamente qualificados, DSC não utilizará o **caminho** variável de ambiente para encontrar os ficheiros e irá gerar um erro se qualquer um dos caminhos de não existir.</span><span class="sxs-lookup"><span data-stu-id="a75ad-117">If the values of this property are fully qualified paths, DSC will not use the **Path** environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="a75ad-118">Não são permitidos caminhos relativos.</span><span class="sxs-lookup"><span data-stu-id="a75ad-118">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="a75ad-119">credencial</span><span class="sxs-lookup"><span data-stu-id="a75ad-119">Credential</span></span>| <span data-ttu-id="a75ad-120">Indica as credenciais para iniciar o processo.</span><span class="sxs-lookup"><span data-stu-id="a75ad-120">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="a75ad-121">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="a75ad-121">Ensure</span></span>| <span data-ttu-id="a75ad-122">Especifica se os processos existe.</span><span class="sxs-lookup"><span data-stu-id="a75ad-122">Specifies whether the processes exists.</span></span> <span data-ttu-id="a75ad-123">Defina esta propriedade para "Presente" para se certificar de que o processo exista.</span><span class="sxs-lookup"><span data-stu-id="a75ad-123">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="a75ad-124">Caso contrário, defina-o para "Ausente".</span><span class="sxs-lookup"><span data-stu-id="a75ad-124">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="a75ad-125">A predefinição é "Presente".</span><span class="sxs-lookup"><span data-stu-id="a75ad-125">The default is "Present".</span></span>|
| <span data-ttu-id="a75ad-126">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="a75ad-126">StandardErrorPath</span></span>| <span data-ttu-id="a75ad-127">O caminho para os quais os processos de escrita de erro padrão.</span><span class="sxs-lookup"><span data-stu-id="a75ad-127">The path to which the processes write standard error.</span></span> <span data-ttu-id="a75ad-128">Não existe qualquer ficheiro existente será substituído.</span><span class="sxs-lookup"><span data-stu-id="a75ad-128">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="a75ad-129">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="a75ad-129">StandardInputPath</span></span>| <span data-ttu-id="a75ad-130">O fluxo a partir do qual o processo recebe entrada padrão.</span><span class="sxs-lookup"><span data-stu-id="a75ad-130">The stream from which the process receives standard input.</span></span>|
| <span data-ttu-id="a75ad-131">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="a75ad-131">StandardOutputPath</span></span>| <span data-ttu-id="a75ad-132">O caminho do ficheiro para que os processos de escrever a saída padrão.</span><span class="sxs-lookup"><span data-stu-id="a75ad-132">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="a75ad-133">Não existe qualquer ficheiro existente será substituído.</span><span class="sxs-lookup"><span data-stu-id="a75ad-133">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="a75ad-134">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="a75ad-134">WorkingDirectory</span></span>| <span data-ttu-id="a75ad-135">A localização utilizada como o atual diretório de trabalho para processos.</span><span class="sxs-lookup"><span data-stu-id="a75ad-135">The location used as the current working directory for the processes.</span></span>|
| <span data-ttu-id="a75ad-136">dependsOn</span><span class="sxs-lookup"><span data-stu-id="a75ad-136">DependsOn</span></span> | <span data-ttu-id="a75ad-137">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="a75ad-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a75ad-138">Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é **ResourceName** e o respetivo tipo é **_ResourceType**, a sintaxe para utilizar esta propriedade é ' DependsOn = "[ ResourceName ResourceType]"'.</span><span class="sxs-lookup"><span data-stu-id="a75ad-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **_ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\` .</span></span>|