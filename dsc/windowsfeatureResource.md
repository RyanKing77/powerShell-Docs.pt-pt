---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Recursos do DSC WindowsFeature
ms.openlocfilehash: e22f40d5a30b470bc322bd7fa3a065e6806d5cd5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-windowsfeature-resource"></a><span data-ttu-id="a9d72-103">Recursos do DSC WindowsFeature</span><span class="sxs-lookup"><span data-stu-id="a9d72-103">DSC WindowsFeature Resource</span></span>

> <span data-ttu-id="a9d72-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a9d72-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="a9d72-105">O **WindowsFeature** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para se certificar de que as funções e funcionalidades são adicionadas ou removidas num nó de destino.</span><span class="sxs-lookup"><span data-stu-id="a9d72-105">The **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="a9d72-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a9d72-106">Syntax</span></span>

```
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Source = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="a9d72-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="a9d72-107">Properties</span></span>

|  <span data-ttu-id="a9d72-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="a9d72-108">Property</span></span>  |  <span data-ttu-id="a9d72-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="a9d72-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="a9d72-110">Nome</span><span class="sxs-lookup"><span data-stu-id="a9d72-110">Name</span></span>| <span data-ttu-id="a9d72-111">Indica o nome da função ou funcionalidade que pretende para se certificar de que é adicionado ou removido.</span><span class="sxs-lookup"><span data-stu-id="a9d72-111">Indicates the name of the role or feature that you want to ensure is added or removed.</span></span> <span data-ttu-id="a9d72-112">Este é o mesmo que o __nome__ propriedade do [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet e não o nome a apresentar da função ou funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="a9d72-112">This is the same as the __Name__ property from the [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, and not the display name of the role or feature.</span></span>|
| <span data-ttu-id="a9d72-113">credencial</span><span class="sxs-lookup"><span data-stu-id="a9d72-113">Credential</span></span>| <span data-ttu-id="a9d72-114">Indica as credenciais a utilizar para adicionar ou remover a função ou funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="a9d72-114">Indicates the credentials to use to add or remove the role or feature.</span></span>|
| <span data-ttu-id="a9d72-115">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="a9d72-115">Ensure</span></span>| <span data-ttu-id="a9d72-116">Indica se a função ou funcionalidade é adicionada.</span><span class="sxs-lookup"><span data-stu-id="a9d72-116">Indicates if the role or feature is added.</span></span> <span data-ttu-id="a9d72-117">Para garantir que a função ou funcionalidade adicionado, defina esta propriedade como "Apresente" para se certificar de que a função ou funcionalidade for removida, defina a propriedade para "Ausente".</span><span class="sxs-lookup"><span data-stu-id="a9d72-117">To ensure that the role or feature is added, set this property to "Present" To ensure that the role or feature is removed, set the property to "Absent".</span></span>|
| <span data-ttu-id="a9d72-118">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="a9d72-118">IncludeAllSubFeature</span></span>| <span data-ttu-id="a9d72-119">Defina esta propriedade como __$true__ para garantir o estado de todos requeridos subfuncionalidades com o estado da funcionalidade especificar com o __nome__ propriedade.</span><span class="sxs-lookup"><span data-stu-id="a9d72-119">Set this property to __$true__ to ensure the state of all required subfeatures with the state of the feature you specify with the __Name__ property.</span></span>|
| <span data-ttu-id="a9d72-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="a9d72-120">LogPath</span></span>| <span data-ttu-id="a9d72-121">Indica o caminho para um ficheiro de registo onde pretende que o fornecedor de recursos para iniciar a operação.</span><span class="sxs-lookup"><span data-stu-id="a9d72-121">Indicates the path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="a9d72-122">dependsOn</span><span class="sxs-lookup"><span data-stu-id="a9d72-122">DependsOn</span></span>| <span data-ttu-id="a9d72-123">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="a9d72-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a9d72-124">Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a9d72-124">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="a9d72-125">Origem</span><span class="sxs-lookup"><span data-stu-id="a9d72-125">Source</span></span>| <span data-ttu-id="a9d72-126">Indica a localização do ficheiro de origem a utilizar para instalação, se necessário.</span><span class="sxs-lookup"><span data-stu-id="a9d72-126">Indicates the location of the source file to use for installation, if necessary.</span></span>|

## <a name="example"></a><span data-ttu-id="a9d72-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a9d72-127">Example</span></span>
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```