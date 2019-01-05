---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso WindowsOptionalFeatureSet de DSC
ms.openlocfilehash: c27d026e01bbb443a82112e37f1d199fb3482e49
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048412"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="2bd39-103">Recurso WindowsOptionalFeatureSet de DSC</span><span class="sxs-lookup"><span data-stu-id="2bd39-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="2bd39-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2bd39-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="2bd39-105">O **WindowsOptionalFeatureSet** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para garantir que as funcionalidades opcionais estão ativadas num nó de destino.</span><span class="sxs-lookup"><span data-stu-id="2bd39-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>
<span data-ttu-id="2bd39-106">Este recurso é um [recursos compostos](../../../resources/authoringResourceComposite.md) que chama o [recurso WindowsOptionalFeature](windowsOptionalFeatureResource.md) para cada funcionalidade especificada no `Name` propriedade.</span><span class="sxs-lookup"><span data-stu-id="2bd39-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="2bd39-107">Utilize este recurso quando pretender configurar um número de funcionalidades opcionais do Windows para o mesmo Estado.</span><span class="sxs-lookup"><span data-stu-id="2bd39-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="2bd39-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2bd39-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="2bd39-109">Propriedades</span><span class="sxs-lookup"><span data-stu-id="2bd39-109">Properties</span></span>

|  <span data-ttu-id="2bd39-110">Propriedade</span><span class="sxs-lookup"><span data-stu-id="2bd39-110">Property</span></span>  |  <span data-ttu-id="2bd39-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="2bd39-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="2bd39-112">Nome</span><span class="sxs-lookup"><span data-stu-id="2bd39-112">Name</span></span>| <span data-ttu-id="2bd39-113">Indica o nome dos recursos que deseja garantir que estão ativadas ou desativadas.</span><span class="sxs-lookup"><span data-stu-id="2bd39-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span>|
| <span data-ttu-id="2bd39-114">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="2bd39-114">Ensure</span></span>| <span data-ttu-id="2bd39-115">Especifica se as funcionalidades estão ativadas.</span><span class="sxs-lookup"><span data-stu-id="2bd39-115">Specifies whether the features are enabled.</span></span> <span data-ttu-id="2bd39-116">Para garantir que os recursos são ativados, defina esta propriedade para "Ativar" para se certificar de que os recursos estão desativados, defina a propriedade "Desativar".</span><span class="sxs-lookup"><span data-stu-id="2bd39-116">To ensure that the features are enabled, set this property to "Enable" To ensure that the features are disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="2bd39-117">Origem</span><span class="sxs-lookup"><span data-stu-id="2bd39-117">Source</span></span>| <span data-ttu-id="2bd39-118">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="2bd39-118">Not implemented.</span></span>|
| <span data-ttu-id="2bd39-119">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="2bd39-119">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="2bd39-120">Especifica se o DISM contacta Windows Update (WU) ao pesquisar os ficheiros de origem ativar funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="2bd39-120">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="2bd39-121">Se $true, DISM não entre em contato com WU.</span><span class="sxs-lookup"><span data-stu-id="2bd39-121">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="2bd39-122">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="2bd39-122">RemoveFilesOnDisable</span></span>| <span data-ttu-id="2bd39-123">Definido como **$true** para remover todos os ficheiros associados os recursos quando estão desativadas (ou seja, quando **Certifique-se** está definido para "Ausente").</span><span class="sxs-lookup"><span data-stu-id="2bd39-123">Set to **$true** to remove all files associated with the features when they are disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="2bd39-124">Nível de Registo</span><span class="sxs-lookup"><span data-stu-id="2bd39-124">LogLevel</span></span>| <span data-ttu-id="2bd39-125">O nível de saída máximo apresentado nos registos.</span><span class="sxs-lookup"><span data-stu-id="2bd39-125">The maximum output level shown in the logs.</span></span> <span data-ttu-id="2bd39-126">Os valores aceites são: "ErrorsOnly" (apenas erros são registados), "ErrorsAndWarning" (erros e avisos são registados) e "ErrorsAndWarningAndInformation" (erros, avisos e informações de depuração são registados).</span><span class="sxs-lookup"><span data-stu-id="2bd39-126">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="2bd39-127">LogPath</span><span class="sxs-lookup"><span data-stu-id="2bd39-127">LogPath</span></span>| <span data-ttu-id="2bd39-128">O caminho para um ficheiro de registo onde pretende que o fornecedor de recursos para iniciar a operação.</span><span class="sxs-lookup"><span data-stu-id="2bd39-128">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="2bd39-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="2bd39-129">DependsOn</span></span>| <span data-ttu-id="2bd39-130">Especifica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="2bd39-130">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="2bd39-131">Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será __ResourceName__ e seu tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="2bd39-131">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
