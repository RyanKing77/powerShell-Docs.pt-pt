---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recursos do DSC WindowsProcess
ms.openlocfilehash: c34d3cb1d4d9b899b45fba7b4b148a7c977f5365
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="35acc-103">Recursos do DSC WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="35acc-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="35acc-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="35acc-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="35acc-105">O **WindowsProcess** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para configurar processos num nó de destino.</span><span class="sxs-lookup"><span data-stu-id="35acc-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="35acc-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="35acc-106">Syntax</span></span>

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="35acc-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="35acc-107">Properties</span></span>
|  <span data-ttu-id="35acc-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="35acc-108">Property</span></span>  |  <span data-ttu-id="35acc-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="35acc-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="35acc-110">Argumentos</span><span class="sxs-lookup"><span data-stu-id="35acc-110">Arguments</span></span>| <span data-ttu-id="35acc-111">Indica uma cadeia de argumentos transmitidos para o processo que-é.</span><span class="sxs-lookup"><span data-stu-id="35acc-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="35acc-112">Se tiver de passar vários argumentos, colocá-los a todos nesta cadeia.</span><span class="sxs-lookup"><span data-stu-id="35acc-112">If you need to pass several arguments, put them all in this string.</span></span>| 
| <span data-ttu-id="35acc-113">Caminho</span><span class="sxs-lookup"><span data-stu-id="35acc-113">Path</span></span>| <span data-ttu-id="35acc-114">O caminho para o executável do processo.</span><span class="sxs-lookup"><span data-stu-id="35acc-114">The path to the process executable.</span></span> <span data-ttu-id="35acc-115">Se o nome de ficheiro do executável (não o caminho completamente qualificado), os recursos de DSC irá procurar o ambiente **caminho** variável (`$env:Path`) para localizar o ficheiro executável.</span><span class="sxs-lookup"><span data-stu-id="35acc-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the executable file.</span></span> <span data-ttu-id="35acc-116">Se o valor desta propriedade é um caminho completamente qualificado, DSC não utilizará o **caminho** variável de ambiente para localizar o ficheiro e irá gerar um erro se o caminho não existe.</span><span class="sxs-lookup"><span data-stu-id="35acc-116">If the value of this property is a fully qualified path, DSC will not use the **Path** environment variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="35acc-117">Não são permitidos caminhos relativos.</span><span class="sxs-lookup"><span data-stu-id="35acc-117">Relative paths are not allowed.</span></span>| 
| <span data-ttu-id="35acc-118">credencial</span><span class="sxs-lookup"><span data-stu-id="35acc-118">Credential</span></span>| <span data-ttu-id="35acc-119">Indica as credenciais para iniciar o processo.</span><span class="sxs-lookup"><span data-stu-id="35acc-119">Indicates the credentials for starting the process.</span></span>| 
| <span data-ttu-id="35acc-120">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="35acc-120">Ensure</span></span>| <span data-ttu-id="35acc-121">Indica se o processo exista.</span><span class="sxs-lookup"><span data-stu-id="35acc-121">Indicates if the process exists.</span></span> <span data-ttu-id="35acc-122">Defina esta propriedade para "Presente" para se certificar de que o processo exista.</span><span class="sxs-lookup"><span data-stu-id="35acc-122">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="35acc-123">Caso contrário, defina-o para "Ausente".</span><span class="sxs-lookup"><span data-stu-id="35acc-123">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="35acc-124">A predefinição é "Presente".</span><span class="sxs-lookup"><span data-stu-id="35acc-124">The default is "Present".</span></span>| 
| <span data-ttu-id="35acc-125">dependsOn</span><span class="sxs-lookup"><span data-stu-id="35acc-125">DependsOn</span></span> | <span data-ttu-id="35acc-126">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="35acc-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="35acc-127">Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é ' DependsOn = "[ ResourceName ResourceType]"'.</span><span class="sxs-lookup"><span data-stu-id="35acc-127">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`\` .</span></span>| 
| <span data-ttu-id="35acc-128">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="35acc-128">StandardErrorPath</span></span>| <span data-ttu-id="35acc-129">Indica o caminho do diretório para escrever o erro padrão.</span><span class="sxs-lookup"><span data-stu-id="35acc-129">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="35acc-130">Não existe qualquer ficheiro existente será substituído.</span><span class="sxs-lookup"><span data-stu-id="35acc-130">Any existing file there will be overwritten.</span></span>| 
| <span data-ttu-id="35acc-131">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="35acc-131">StandardInputPath</span></span>| <span data-ttu-id="35acc-132">Indica a localização de entrada padrão.</span><span class="sxs-lookup"><span data-stu-id="35acc-132">Indicates the standard input location.</span></span>| 
| <span data-ttu-id="35acc-133">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="35acc-133">StandardOutputPath</span></span>| <span data-ttu-id="35acc-134">Indica a localização para guardar a saída padrão.</span><span class="sxs-lookup"><span data-stu-id="35acc-134">Indicates the location to write the standard output.</span></span> <span data-ttu-id="35acc-135">Não existe qualquer ficheiro existente será substituído.</span><span class="sxs-lookup"><span data-stu-id="35acc-135">Any existing file there will be overwritten.</span></span>| 
| <span data-ttu-id="35acc-136">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="35acc-136">WorkingDirectory</span></span>| <span data-ttu-id="35acc-137">Indica a localização que será utilizada como o atual diretório de trabalho para o processo.</span><span class="sxs-lookup"><span data-stu-id="35acc-137">Indicates the location that will be used as the current working directory for the process.</span></span>| 

