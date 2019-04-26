---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso WindowsProcess de DSC
ms.openlocfilehash: cee93ab283ded407d6e032161125aa6d6ac98827
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076774"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="5ed5d-103">Recurso WindowsProcess de DSC</span><span class="sxs-lookup"><span data-stu-id="5ed5d-103">DSC WindowsProcess Resource</span></span>

<span data-ttu-id="5ed5d-104">_Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="5ed5d-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="5ed5d-105">O **WindowsProcess** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para configurar os processos num nó de destino.</span><span class="sxs-lookup"><span data-stu-id="5ed5d-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="5ed5d-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ed5d-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="5ed5d-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="5ed5d-107">Properties</span></span>

| <span data-ttu-id="5ed5d-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="5ed5d-108">Property</span></span> | <span data-ttu-id="5ed5d-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ed5d-109">Description</span></span> |
| --- | --- |
| <span data-ttu-id="5ed5d-110">Argumentos</span><span class="sxs-lookup"><span data-stu-id="5ed5d-110">Arguments</span></span>| <span data-ttu-id="5ed5d-111">Indica uma cadeia de argumentos transmitidos para o processo como-é.</span><span class="sxs-lookup"><span data-stu-id="5ed5d-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="5ed5d-112">Se precisar de passar argumentos vários, colocá-los nessa cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5ed5d-112">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="5ed5d-113">Caminho</span><span class="sxs-lookup"><span data-stu-id="5ed5d-113">Path</span></span>| <span data-ttu-id="5ed5d-114">O caminho para o executável do processo.</span><span class="sxs-lookup"><span data-stu-id="5ed5d-114">The path to the process executable.</span></span> <span data-ttu-id="5ed5d-115">Se esta o nome de ficheiro do ficheiro executável (não o caminho totalmente qualificado), o recurso de DSC irá procurar o ambiente **caminho** variável (`$env:Path`) para localizar o ficheiro executável.</span><span class="sxs-lookup"><span data-stu-id="5ed5d-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the executable file.</span></span> <span data-ttu-id="5ed5d-116">Se o valor desta propriedade é um caminho totalmente qualificado, DSC não irá utilizar o **caminho** variável de ambiente para encontrar o ficheiro e irá gerar um erro se o caminho não existir.</span><span class="sxs-lookup"><span data-stu-id="5ed5d-116">If the value of this property is a fully qualified path, DSC will not use the **Path** environment variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="5ed5d-117">Não são permitidos caminhos relativos.</span><span class="sxs-lookup"><span data-stu-id="5ed5d-117">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="5ed5d-118">Credencial</span><span class="sxs-lookup"><span data-stu-id="5ed5d-118">Credential</span></span>| <span data-ttu-id="5ed5d-119">Indica as credenciais para iniciar o processo.</span><span class="sxs-lookup"><span data-stu-id="5ed5d-119">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="5ed5d-120">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="5ed5d-120">Ensure</span></span>| <span data-ttu-id="5ed5d-121">Indica se o processo exista.</span><span class="sxs-lookup"><span data-stu-id="5ed5d-121">Indicates if the process exists.</span></span> <span data-ttu-id="5ed5d-122">Defina esta propriedade para "Presente" para garantir que existe o processo.</span><span class="sxs-lookup"><span data-stu-id="5ed5d-122">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="5ed5d-123">Caso contrário, defina-o como "Ausente".</span><span class="sxs-lookup"><span data-stu-id="5ed5d-123">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="5ed5d-124">A predefinição é "Presente".</span><span class="sxs-lookup"><span data-stu-id="5ed5d-124">The default is "Present".</span></span>|
| <span data-ttu-id="5ed5d-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="5ed5d-125">DependsOn</span></span> | <span data-ttu-id="5ed5d-126">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="5ed5d-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5ed5d-127">Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será **ResourceName** e seu tipo é **ResourceType**, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="5ed5d-127">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"` .</span></span>|
| <span data-ttu-id="5ed5d-128">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="5ed5d-128">StandardErrorPath</span></span>| <span data-ttu-id="5ed5d-129">Indica o caminho do diretório para escrever o erro padrão.</span><span class="sxs-lookup"><span data-stu-id="5ed5d-129">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="5ed5d-130">Qualquer arquivo existente será substituído.</span><span class="sxs-lookup"><span data-stu-id="5ed5d-130">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="5ed5d-131">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="5ed5d-131">StandardInputPath</span></span>| <span data-ttu-id="5ed5d-132">Indica a localização de entrada padrão.</span><span class="sxs-lookup"><span data-stu-id="5ed5d-132">Indicates the standard input location.</span></span>|
| <span data-ttu-id="5ed5d-133">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="5ed5d-133">StandardOutputPath</span></span>| <span data-ttu-id="5ed5d-134">Indica a localização para guardar a saída padrão.</span><span class="sxs-lookup"><span data-stu-id="5ed5d-134">Indicates the location to write the standard output.</span></span> <span data-ttu-id="5ed5d-135">Qualquer arquivo existente será substituído.</span><span class="sxs-lookup"><span data-stu-id="5ed5d-135">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="5ed5d-136">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="5ed5d-136">WorkingDirectory</span></span>| <span data-ttu-id="5ed5d-137">Indica a localização que será utilizada como diretório de trabalho atual para o processo.</span><span class="sxs-lookup"><span data-stu-id="5ed5d-137">Indicates the location that will be used as the current working directory for the process.</span></span>|