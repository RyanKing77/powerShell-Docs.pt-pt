---
title: Nomenclatura dos ficheiros de ajuda | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082186"
---
# <a name="naming-help-files"></a><span data-ttu-id="cd9ca-102">Naming Help Files (Atribuir Nomes a Ficheiros de Ajuda)</span><span class="sxs-lookup"><span data-stu-id="cd9ca-102">Naming Help Files</span></span>

<span data-ttu-id="cd9ca-103">Este tópico explica como atribuir um nome um arquivo de ajuda baseados em XML para que o [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet pode encontrá-lo.</span><span class="sxs-lookup"><span data-stu-id="cd9ca-103">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="cd9ca-104">Os requisitos de nome diferem para cada tipo de comando.</span><span class="sxs-lookup"><span data-stu-id="cd9ca-104">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="cd9ca-105">Arquivos de ajuda do cmdlet</span><span class="sxs-lookup"><span data-stu-id="cd9ca-105">Cmdlet Help Files</span></span>

<span data-ttu-id="cd9ca-106">O ficheiro de ajuda para um C# cmdlet deve ser nomeado para o assembly no qual o cmdlet está definido.</span><span class="sxs-lookup"><span data-stu-id="cd9ca-106">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="cd9ca-107">Utilize o seguinte formato de nome de ficheiro:</span><span class="sxs-lookup"><span data-stu-id="cd9ca-107">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="cd9ca-108">O formato de nome de assemblagem é necessário, mesmo quando o assembly é um módulo aninhado.</span><span class="sxs-lookup"><span data-stu-id="cd9ca-108">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="cd9ca-109">Por exemplo, o [Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet é definido no Microsoft.PowerShell.Diagnostics.dll assembly.</span><span class="sxs-lookup"><span data-stu-id="cd9ca-109">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="cd9ca-110">O `Get-Help` cmdlet procura um tópico de ajuda para o `Get-WinEvent` cmdlet apenas no ficheiro Microsoft.PowerShell.Diagnostics.dll help.xml no diretório de módulo.</span><span class="sxs-lookup"><span data-stu-id="cd9ca-110">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="cd9ca-111">Arquivos de ajuda do fornecedor</span><span class="sxs-lookup"><span data-stu-id="cd9ca-111">Provider Help files</span></span>

<span data-ttu-id="cd9ca-112">O ficheiro de ajuda para um fornecedor de Windows PowerShell tem de ser o nome para o assembly no qual o fornecedor é definido.</span><span class="sxs-lookup"><span data-stu-id="cd9ca-112">The help file for a Windows PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="cd9ca-113">Utilize o seguinte formato de nome de ficheiro:</span><span class="sxs-lookup"><span data-stu-id="cd9ca-113">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="cd9ca-114">O formato de nome de assemblagem é necessário, mesmo quando o assembly é um módulo aninhado.</span><span class="sxs-lookup"><span data-stu-id="cd9ca-114">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="cd9ca-115">Por exemplo, o fornecedor do certificado é definido no Microsoft.PowerShell.Security.dll assembly.</span><span class="sxs-lookup"><span data-stu-id="cd9ca-115">For example, the Certificate provider is defined in the Microsoft.PowerShell.Security.dll assembly.</span></span> <span data-ttu-id="cd9ca-116">O `Get-Help` cmdlet vai para um tópico de ajuda para o fornecedor de certificados apenas no ficheiro Microsoft.PowerShell.Security.dll help.xml no diretório de módulo.</span><span class="sxs-lookup"><span data-stu-id="cd9ca-116">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the Microsoft.PowerShell.Security.dll-help.xml file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="cd9ca-117">Arquivos de ajuda de função</span><span class="sxs-lookup"><span data-stu-id="cd9ca-117">Function Help Files</span></span>

<span data-ttu-id="cd9ca-118">As funções podem ser documentadas com o [ajuda baseada no comentário](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) ou documentados num arquivo de ajuda do XML.</span><span class="sxs-lookup"><span data-stu-id="cd9ca-118">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="cd9ca-119">Quando a função está documentada num arquivo XML, a função tem de ter um `.ExternalHelp` comentar a palavra-chave que associa a função com o arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="cd9ca-119">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="cd9ca-120">Caso contrário, o `Get-Help` cmdlet não é possível localizar o ficheiro de ajuda.</span><span class="sxs-lookup"><span data-stu-id="cd9ca-120">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="cd9ca-121">Não existem não requisitos técnicos para o nome de um arquivo de ajuda de função.</span><span class="sxs-lookup"><span data-stu-id="cd9ca-121">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="cd9ca-122">No entanto, uma prática recomendada é nomear o arquivo de ajuda para o módulo de script em que a função é definida.</span><span class="sxs-lookup"><span data-stu-id="cd9ca-122">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="cd9ca-123">Por exemplo, a seguinte função é definida no ficheiro MyModule.psm1.</span><span class="sxs-lookup"><span data-stu-id="cd9ca-123">For example, the following function is defined in the MyModule.psm1 file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="cd9ca-124">Arquivos de ajuda do comando CIM</span><span class="sxs-lookup"><span data-stu-id="cd9ca-124">CIM Command Help Files</span></span>

<span data-ttu-id="cd9ca-125">O ficheiro de ajuda para um comando CIM tem de ser o nome do ficheiro de CDXML no qual o comando CIM é definido.</span><span class="sxs-lookup"><span data-stu-id="cd9ca-125">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="cd9ca-126">Utilize o seguinte formato de nome de ficheiro:</span><span class="sxs-lookup"><span data-stu-id="cd9ca-126">Use the following file name format:</span></span>

```
<FileName>.cdxml-help.xml
```

<span data-ttu-id="cd9ca-127">Comandos CIM são definidos em ficheiros CDXML que podem ser incluídos nos módulos como módulos aninhados.</span><span class="sxs-lookup"><span data-stu-id="cd9ca-127">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="cd9ca-128">Quando o comando CIM é importado para a sessão como uma função, o Windows PowerShell adiciona uma `.ExternalHelp` comentário palavra-chave para a definição de função que associa a função com uma ajuda XML do ficheiro que tem o nome do ficheiro de CDXML no qual o comando CIM é definido.</span><span class="sxs-lookup"><span data-stu-id="cd9ca-128">When the CIM command is imported into the session as a function, Windows PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="cd9ca-129">Arquivos de ajuda do fluxo de trabalho de script</span><span class="sxs-lookup"><span data-stu-id="cd9ca-129">Script Workflow Help Files</span></span>

<span data-ttu-id="cd9ca-130">Os fluxos de trabalho de script que estão incluídos nos módulos podem ser documentados em arquivos de ajuda baseados em XML.</span><span class="sxs-lookup"><span data-stu-id="cd9ca-130">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="cd9ca-131">Não existem não requisitos técnicos para o nome de ficheiro de ajuda.</span><span class="sxs-lookup"><span data-stu-id="cd9ca-131">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="cd9ca-132">No entanto, uma prática recomendada é nomear o arquivo de ajuda para o módulo de script no qual o fluxo de trabalho do script é definido.</span><span class="sxs-lookup"><span data-stu-id="cd9ca-132">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="cd9ca-133">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="cd9ca-133">For example:</span></span>

```
<ScriptModule>.psm1-help.xml
```

<span data-ttu-id="cd9ca-134">Ao contrário de outros comandos de script, fluxos de trabalho de script não requerem um `.ExternalHelp` comentar a palavra-chave para associá-las com um arquivo de ajuda.</span><span class="sxs-lookup"><span data-stu-id="cd9ca-134">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="cd9ca-135">Em vez disso, o Windows PowerShell os subdiretórios específicos da cultura da interface do Usuário do diretório de módulo para arquivos de ajuda baseados em XML de pesquisa e procura de ajuda para o fluxo de trabalho de script em todos os ficheiros.</span><span class="sxs-lookup"><span data-stu-id="cd9ca-135">Instead, Windows PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="cd9ca-136">`.ExternalHelp` Confirmar palavra-chave são ignorados.</span><span class="sxs-lookup"><span data-stu-id="cd9ca-136">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="cd9ca-137">Uma vez que o `.ExternalHelp` palavra-chave de comentário é ignorada, a `Get-Help` cmdlet pode encontrar ajuda para fluxos de trabalho de script apenas quando eles são incluídos nos módulos.</span><span class="sxs-lookup"><span data-stu-id="cd9ca-137">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>