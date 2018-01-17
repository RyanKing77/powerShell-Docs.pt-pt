---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recursos do DSC WindowsOptionalFeature
ms.openlocfilehash: d9b8cc316255f06d2de71fedc47ce4472cc8b382
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="f19aa-103">Recursos do DSC WindowsOptionalFeature</span><span class="sxs-lookup"><span data-stu-id="f19aa-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="f19aa-104">Aplica-se a: O Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f19aa-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="f19aa-105">O **WindowsOptionalFeature** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para se certificar de que as funcionalidades opcionais estão ativadas num nó de destino.</span><span class="sxs-lookup"><span data-stu-id="f19aa-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="f19aa-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f19aa-106">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a><span data-ttu-id="f19aa-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="f19aa-107">Properties</span></span>

|  <span data-ttu-id="f19aa-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="f19aa-108">Property</span></span>  |  <span data-ttu-id="f19aa-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="f19aa-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="f19aa-110">Nome</span><span class="sxs-lookup"><span data-stu-id="f19aa-110">Name</span></span>| <span data-ttu-id="f19aa-111">Indica o nome da funcionalidade que pretende para se certificar de que está ativado ou desativado.</span><span class="sxs-lookup"><span data-stu-id="f19aa-111">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span>| 
| <span data-ttu-id="f19aa-112">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="f19aa-112">Ensure</span></span>| <span data-ttu-id="f19aa-113">Especifica se a funcionalidade está ativada.</span><span class="sxs-lookup"><span data-stu-id="f19aa-113">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="f19aa-114">Para garantir que a funcionalidade está ativada, defina esta propriedade como "Ativar" para se certificar de que a funcionalidade está desativada, defina a propriedade para "Desativar".</span><span class="sxs-lookup"><span data-stu-id="f19aa-114">To ensure that the feature is enabled, set this property to "Enable" To ensure that the feature is disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="f19aa-115">Origem</span><span class="sxs-lookup"><span data-stu-id="f19aa-115">Source</span></span>| <span data-ttu-id="f19aa-116">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="f19aa-116">Not implemented.</span></span>|
| <span data-ttu-id="f19aa-117">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="f19aa-117">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="f19aa-118">Especifica se o DISM contacta Windows Update (WU) quando procurar os ficheiros de origem ativar uma funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="f19aa-118">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="f19aa-119">Se $true, DISM não contactar WU.</span><span class="sxs-lookup"><span data-stu-id="f19aa-119">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="f19aa-120">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="f19aa-120">RemoveFilesOnDisable</span></span>| <span data-ttu-id="f19aa-121">Definido como **$true** para remover todos os ficheiros associados a funcionalidade quando está desativado (ou seja, quando **Certifique-se** está definido para "Ausente").</span><span class="sxs-lookup"><span data-stu-id="f19aa-121">Set to **$true** to remove all files associated with the feature when it is disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="f19aa-122">Nível de Registo</span><span class="sxs-lookup"><span data-stu-id="f19aa-122">LogLevel</span></span>| <span data-ttu-id="f19aa-123">O nível de saída máximo apresentado nos registos.</span><span class="sxs-lookup"><span data-stu-id="f19aa-123">The maximum output level shown in the logs.</span></span> <span data-ttu-id="f19aa-124">Os valores aceites são: "ErrorsOnly" (apenas erros são registados), "ErrorsAndWarning" (erros e avisos são registados) e "ErrorsAndWarningAndInformation" (erros, avisos e informações de depuração são registados).</span><span class="sxs-lookup"><span data-stu-id="f19aa-124">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="f19aa-125">LogPath</span><span class="sxs-lookup"><span data-stu-id="f19aa-125">LogPath</span></span>| <span data-ttu-id="f19aa-126">O caminho para um ficheiro de registo onde pretende que o fornecedor de recursos para iniciar a operação.</span><span class="sxs-lookup"><span data-stu-id="f19aa-126">The path to a log file where you want the resource provider to log the operation.</span></span>| 
| <span data-ttu-id="f19aa-127">dependsOn</span><span class="sxs-lookup"><span data-stu-id="f19aa-127">DependsOn</span></span>| <span data-ttu-id="f19aa-128">Especifica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="f19aa-128">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f19aa-129">Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="f19aa-129">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
 



