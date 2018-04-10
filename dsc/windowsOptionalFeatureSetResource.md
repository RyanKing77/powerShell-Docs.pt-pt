---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Recursos do DSC WindowsOptionalFeatureSet
ms.openlocfilehash: 3329e0d0f1988a2ee20eb848da943ff1b22bd4df
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="b7a59-103">Recursos do DSC WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="b7a59-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="b7a59-104">Aplica-se a: O Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b7a59-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="b7a59-105">O **WindowsOptionalFeatureSet** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para se certificar de que as funcionalidades opcionais estão ativadas num nó de destino.</span><span class="sxs-lookup"><span data-stu-id="b7a59-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>
<span data-ttu-id="b7a59-106">Este recurso é um [recursos composto](authoringResourceComposite.md) que chama o [WindowsOptionalFeature recursos](windowsOptionalFeatureResource.md) para cada funcionalidade especificada no `Name` propriedade.</span><span class="sxs-lookup"><span data-stu-id="b7a59-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="b7a59-107">Utilize este recurso quando pretender configurar um número de funcionalidades opcionais do Windows para o estado do mesmo.</span><span class="sxs-lookup"><span data-stu-id="b7a59-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="b7a59-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7a59-108">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="b7a59-109">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b7a59-109">Properties</span></span>

|  <span data-ttu-id="b7a59-110">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b7a59-110">Property</span></span>  |  <span data-ttu-id="b7a59-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7a59-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="b7a59-112">Nome</span><span class="sxs-lookup"><span data-stu-id="b7a59-112">Name</span></span>| <span data-ttu-id="b7a59-113">Indica o nome das funcionalidades que pretende para se certificar de que estão ativadas ou desativadas.</span><span class="sxs-lookup"><span data-stu-id="b7a59-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span>|
| <span data-ttu-id="b7a59-114">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="b7a59-114">Ensure</span></span>| <span data-ttu-id="b7a59-115">Especifica se as funcionalidades estão ativadas.</span><span class="sxs-lookup"><span data-stu-id="b7a59-115">Specifies whether the features are enabled.</span></span> <span data-ttu-id="b7a59-116">Para garantir que as funcionalidades estão ativadas, defina esta propriedade como "Ativar" para se certificar de que as funcionalidades estão desativadas, definir a propriedade para "Desativar".</span><span class="sxs-lookup"><span data-stu-id="b7a59-116">To ensure that the features are enabled, set this property to "Enable" To ensure that the features are disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="b7a59-117">Origem</span><span class="sxs-lookup"><span data-stu-id="b7a59-117">Source</span></span>| <span data-ttu-id="b7a59-118">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="b7a59-118">Not implemented.</span></span>|
| <span data-ttu-id="b7a59-119">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="b7a59-119">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="b7a59-120">Especifica se o DISM contacta Windows Update (WU) quando a procurar ficheiros de origem para ativar funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="b7a59-120">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="b7a59-121">Se $true, DISM não contactar WU.</span><span class="sxs-lookup"><span data-stu-id="b7a59-121">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="b7a59-122">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="b7a59-122">RemoveFilesOnDisable</span></span>| <span data-ttu-id="b7a59-123">Definido como **$true** para remover todos os ficheiros associados as funcionalidades quando estão desativadas (ou seja, quando **Certifique-se** está definido para "Ausente").</span><span class="sxs-lookup"><span data-stu-id="b7a59-123">Set to **$true** to remove all files associated with the features when they are disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="b7a59-124">Nível de Registo</span><span class="sxs-lookup"><span data-stu-id="b7a59-124">LogLevel</span></span>| <span data-ttu-id="b7a59-125">O nível de saída máximo apresentado nos registos.</span><span class="sxs-lookup"><span data-stu-id="b7a59-125">The maximum output level shown in the logs.</span></span> <span data-ttu-id="b7a59-126">Os valores aceites são: "ErrorsOnly" (apenas erros são registados), "ErrorsAndWarning" (erros e avisos são registados) e "ErrorsAndWarningAndInformation" (erros, avisos e informações de depuração são registados).</span><span class="sxs-lookup"><span data-stu-id="b7a59-126">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="b7a59-127">LogPath</span><span class="sxs-lookup"><span data-stu-id="b7a59-127">LogPath</span></span>| <span data-ttu-id="b7a59-128">O caminho para um ficheiro de registo onde pretende que o fornecedor de recursos para iniciar a operação.</span><span class="sxs-lookup"><span data-stu-id="b7a59-128">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="b7a59-129">dependsOn</span><span class="sxs-lookup"><span data-stu-id="b7a59-129">DependsOn</span></span>| <span data-ttu-id="b7a59-130">Especifica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="b7a59-130">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b7a59-131">Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="b7a59-131">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|