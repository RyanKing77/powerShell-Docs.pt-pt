---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso ProcessSet de DSC
ms.openlocfilehash: 91a2d5b562864addcb8e11062916d291448bbf57
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048375"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="05261-103">Recurso WindowsProcess de DSC</span><span class="sxs-lookup"><span data-stu-id="05261-103">DSC WindowsProcess Resource</span></span>

<span data-ttu-id="05261-104">_Aplica-se a: Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="05261-104">_Applies To: Windows PowerShell 5.0_</span></span>

<span data-ttu-id="05261-105">O **ProcessSet** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para configurar os processos num nó de destino.</span><span class="sxs-lookup"><span data-stu-id="05261-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span> <span data-ttu-id="05261-106">Este recurso é um [recursos compostos](../../../resources/authoringResourceComposite.md) que chama o [recurso WindowsProcess](windowsProcessResource.md) para cada grupo especificado no `GroupName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="05261-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsProcess resource](windowsProcessResource.md) for each group specified in the `GroupName` parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="05261-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="05261-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="05261-108">Propriedades</span><span class="sxs-lookup"><span data-stu-id="05261-108">Properties</span></span>

| <span data-ttu-id="05261-109">Propriedade</span><span class="sxs-lookup"><span data-stu-id="05261-109">Property</span></span> | <span data-ttu-id="05261-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="05261-110">Description</span></span> |
| --- | --- |
| <span data-ttu-id="05261-111">Argumentos</span><span class="sxs-lookup"><span data-stu-id="05261-111">Arguments</span></span>| <span data-ttu-id="05261-112">Uma cadeia que contém os argumentos transmitidos para o processo como-é.</span><span class="sxs-lookup"><span data-stu-id="05261-112">A string that contains arguments to pass to the process as-is.</span></span> <span data-ttu-id="05261-113">Se precisar de passar argumentos vários, colocá-los nessa cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="05261-113">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="05261-114">Caminho</span><span class="sxs-lookup"><span data-stu-id="05261-114">Path</span></span>| <span data-ttu-id="05261-115">Os caminhos para os executáveis de processo.</span><span class="sxs-lookup"><span data-stu-id="05261-115">The paths to the process executables.</span></span> <span data-ttu-id="05261-116">Se estes forem os nomes dos ficheiros executáveis (caminhos totalmente qualificados), o recurso de DSC irá procurar o ambiente **caminho** variável (`$env:Path`) para localizar os ficheiros.</span><span class="sxs-lookup"><span data-stu-id="05261-116">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the files.</span></span> <span data-ttu-id="05261-117">Se os valores dessa propriedade são caminhos totalmente qualificados, DSC não irá utilizar o **caminho** variável de ambiente para encontrar os arquivos e irá gerar um erro se qualquer um dos caminhos não existirem.</span><span class="sxs-lookup"><span data-stu-id="05261-117">If the values of this property are fully qualified paths, DSC will not use the **Path** environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="05261-118">Não são permitidos caminhos relativos.</span><span class="sxs-lookup"><span data-stu-id="05261-118">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="05261-119">Credencial</span><span class="sxs-lookup"><span data-stu-id="05261-119">Credential</span></span>| <span data-ttu-id="05261-120">Indica as credenciais para iniciar o processo.</span><span class="sxs-lookup"><span data-stu-id="05261-120">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="05261-121">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="05261-121">Ensure</span></span>| <span data-ttu-id="05261-122">Especifica se os processos existe.</span><span class="sxs-lookup"><span data-stu-id="05261-122">Specifies whether the processes exists.</span></span> <span data-ttu-id="05261-123">Defina esta propriedade para "Presente" para garantir que existe o processo.</span><span class="sxs-lookup"><span data-stu-id="05261-123">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="05261-124">Caso contrário, defina-o como "Ausente".</span><span class="sxs-lookup"><span data-stu-id="05261-124">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="05261-125">A predefinição é "Presente".</span><span class="sxs-lookup"><span data-stu-id="05261-125">The default is "Present".</span></span>|
| <span data-ttu-id="05261-126">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="05261-126">StandardErrorPath</span></span>| <span data-ttu-id="05261-127">O caminho para o qual os processos de escrever o erro padrão.</span><span class="sxs-lookup"><span data-stu-id="05261-127">The path to which the processes write standard error.</span></span> <span data-ttu-id="05261-128">Qualquer arquivo existente será substituído.</span><span class="sxs-lookup"><span data-stu-id="05261-128">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="05261-129">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="05261-129">StandardInputPath</span></span>| <span data-ttu-id="05261-130">O fluxo a partir do qual o processo recebe a entrada padrão.</span><span class="sxs-lookup"><span data-stu-id="05261-130">The stream from which the process receives standard input.</span></span>|
| <span data-ttu-id="05261-131">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="05261-131">StandardOutputPath</span></span>| <span data-ttu-id="05261-132">O caminho do ficheiro para que os processos de escrever a saída padrão.</span><span class="sxs-lookup"><span data-stu-id="05261-132">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="05261-133">Qualquer arquivo existente será substituído.</span><span class="sxs-lookup"><span data-stu-id="05261-133">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="05261-134">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="05261-134">WorkingDirectory</span></span>| <span data-ttu-id="05261-135">A localização utilizada como diretório de trabalho atual para os processos.</span><span class="sxs-lookup"><span data-stu-id="05261-135">The location used as the current working directory for the processes.</span></span>|
| <span data-ttu-id="05261-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="05261-136">DependsOn</span></span> | <span data-ttu-id="05261-137">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="05261-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="05261-138">Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será **ResourceName** e seu tipo é **_ResourceType**, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="05261-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **_ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"` .</span></span>|
