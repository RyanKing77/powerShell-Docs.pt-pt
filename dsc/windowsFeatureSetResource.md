---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Recursos do DSC WindowsFeatureSet
ms.openlocfilehash: a6fecba0397b88ce39f6f1a1be6cc366c8a983a6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-windowsfeatureset-resource"></a><span data-ttu-id="be6b7-103">Recursos do DSC WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="be6b7-103">DSC WindowsFeatureSet Resource</span></span>

> <span data-ttu-id="be6b7-104">Aplica-se a: O Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="be6b7-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="be6b7-105">O **WindowsFeatureSet** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para se certificar de que as funções e funcionalidades são adicionadas ou removidas num nó de destino.</span><span class="sxs-lookup"><span data-stu-id="be6b7-105">The **WindowsFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>
<span data-ttu-id="be6b7-106">Este recurso é um [recursos composto](authoringResourceComposite.md) que chama o [WindowsFeature recursos](windowsfeatureResource.md) para cada funcionalidade especificada no `Name` propriedade.</span><span class="sxs-lookup"><span data-stu-id="be6b7-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsFeature resource](windowsfeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="be6b7-107">Utilize este recurso quando pretender configurar um número de funcionalidades do Windows para o estado do mesmo.</span><span class="sxs-lookup"><span data-stu-id="be6b7-107">Use this resource when you want to configure a number of Windows Features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="be6b7-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="be6b7-108">Syntax</span></span>

```
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [bool] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="be6b7-109">Propriedades</span><span class="sxs-lookup"><span data-stu-id="be6b7-109">Properties</span></span>

|  <span data-ttu-id="be6b7-110">Propriedade</span><span class="sxs-lookup"><span data-stu-id="be6b7-110">Property</span></span>  |  <span data-ttu-id="be6b7-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="be6b7-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="be6b7-112">Nome</span><span class="sxs-lookup"><span data-stu-id="be6b7-112">Name</span></span>| <span data-ttu-id="be6b7-113">Os nomes das funções ou funcionalidades que pretende para se certificar de que são adicionados ou removidos.</span><span class="sxs-lookup"><span data-stu-id="be6b7-113">The names of the roles or features that you want to ensure are added or removed.</span></span> <span data-ttu-id="be6b7-114">Este é o mesmo que o **nome** propriedade o [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet e não o nome a apresentar das funções ou funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="be6b7-114">This is the same as the **Name** property of the [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet, and not the display name of the roles or features.</span></span>|
| <span data-ttu-id="be6b7-115">credencial</span><span class="sxs-lookup"><span data-stu-id="be6b7-115">Credential</span></span>| <span data-ttu-id="be6b7-116">As credenciais a utilizar para adicionar ou remover as funções ou funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="be6b7-116">The credentials to use to add or remove the roles or features.</span></span>|
| <span data-ttu-id="be6b7-117">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="be6b7-117">Ensure</span></span>| <span data-ttu-id="be6b7-118">Indica se as funções ou funcionalidades são adicionadas.</span><span class="sxs-lookup"><span data-stu-id="be6b7-118">Indicates whether the roles or features are added.</span></span> <span data-ttu-id="be6b7-119">Para garantir que as funções ou funcionalidades são adicionados, defina esta propriedade como "Apresente" para garantir que as funções ou funcionalidades, definir a propriedade para "Ausente".</span><span class="sxs-lookup"><span data-stu-id="be6b7-119">To ensure that the roles or features are added, set this property to "Present" To ensure that the roles or features are removed, set the property to "Absent".</span></span>|
| <span data-ttu-id="be6b7-120">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="be6b7-120">IncludeAllSubFeature</span></span>| <span data-ttu-id="be6b7-121">Defina esta propriedade como **$true** para incluir todos requeridas subfuncionalidades com as funcionalidades que especificar com o **nome** propriedade.</span><span class="sxs-lookup"><span data-stu-id="be6b7-121">Set this property to **$true** to include all required subfeatures with of the features you specify with the **Name** property.</span></span>|
| <span data-ttu-id="be6b7-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="be6b7-122">LogPath</span></span>| <span data-ttu-id="be6b7-123">O caminho para um ficheiro de registo onde pretende que o fornecedor de recursos para iniciar a operação.</span><span class="sxs-lookup"><span data-stu-id="be6b7-123">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="be6b7-124">dependsOn</span><span class="sxs-lookup"><span data-stu-id="be6b7-124">DependsOn</span></span>| <span data-ttu-id="be6b7-125">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="be6b7-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="be6b7-126">Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="be6b7-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="be6b7-127">Origem</span><span class="sxs-lookup"><span data-stu-id="be6b7-127">Source</span></span>| <span data-ttu-id="be6b7-128">Indica a localização do ficheiro de origem a utilizar para instalação, se necessário.</span><span class="sxs-lookup"><span data-stu-id="be6b7-128">Indicates the location of the source file to use for installation, if necessary.</span></span>|

## <a name="example"></a><span data-ttu-id="be6b7-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="be6b7-129">Example</span></span>

<span data-ttu-id="be6b7-130">A seguinte configuração assegura que o **servidor Web** (IIS) e **servidor SMTP** funcionalidades e todas as subfuncionalidades de cada um, são instaladas.</span><span class="sxs-lookup"><span data-stu-id="be6b7-130">The following configuration ensures that the **Web-Server** (IIS) and **SMTP Server** features, and all subfeatures of each, are installed.</span></span>

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        }
    }
}
```