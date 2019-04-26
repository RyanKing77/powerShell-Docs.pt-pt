---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso WindowsFeatureSet de DSC
ms.openlocfilehash: 8b7c7e72dd58459bd19cb723e5790a82841515c0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076791"
---
# <a name="dsc-windowsfeatureset-resource"></a><span data-ttu-id="c196c-103">Recurso WindowsFeatureSet de DSC</span><span class="sxs-lookup"><span data-stu-id="c196c-103">DSC WindowsFeatureSet Resource</span></span>

> <span data-ttu-id="c196c-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c196c-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="c196c-105">O **WindowsFeatureSet** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para se certificar de que funções e funcionalidades são adicionadas ou removidas num nó de destino.</span><span class="sxs-lookup"><span data-stu-id="c196c-105">The **WindowsFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>
<span data-ttu-id="c196c-106">Este recurso é um [recursos compostos](../../../resources/authoringResourceComposite.md) que chama o [recurso WindowsFeature](windowsfeatureResource.md) para cada funcionalidade especificada no `Name` propriedade.</span><span class="sxs-lookup"><span data-stu-id="c196c-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsFeature resource](windowsfeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="c196c-107">Utilize este recurso quando pretender configurar um número de recursos do Windows para o mesmo Estado.</span><span class="sxs-lookup"><span data-stu-id="c196c-107">Use this resource when you want to configure a number of Windows Features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="c196c-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c196c-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="c196c-109">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c196c-109">Properties</span></span>

|  <span data-ttu-id="c196c-110">Propriedade</span><span class="sxs-lookup"><span data-stu-id="c196c-110">Property</span></span>  |  <span data-ttu-id="c196c-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="c196c-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="c196c-112">Nome</span><span class="sxs-lookup"><span data-stu-id="c196c-112">Name</span></span>| <span data-ttu-id="c196c-113">Os nomes das funções ou funcionalidades que pretende garantir que são adicionados ou removidos.</span><span class="sxs-lookup"><span data-stu-id="c196c-113">The names of the roles or features that you want to ensure are added or removed.</span></span> <span data-ttu-id="c196c-114">Este é o mesmo que o **Name** propriedade da [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet e não o nome a apresentar das funções ou funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="c196c-114">This is the same as the **Name** property of the [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet, and not the display name of the roles or features.</span></span>|
| <span data-ttu-id="c196c-115">Credencial</span><span class="sxs-lookup"><span data-stu-id="c196c-115">Credential</span></span>| <span data-ttu-id="c196c-116">As credenciais a utilizar para adicionar ou remover as funções ou funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="c196c-116">The credentials to use to add or remove the roles or features.</span></span>|
| <span data-ttu-id="c196c-117">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="c196c-117">Ensure</span></span>| <span data-ttu-id="c196c-118">Indica se as funções ou funcionalidades são adicionadas.</span><span class="sxs-lookup"><span data-stu-id="c196c-118">Indicates whether the roles or features are added.</span></span> <span data-ttu-id="c196c-119">Para se certificar de que as funções ou funcionalidades foram adicionados, defina esta propriedade para "Presente" para se certificar de que as funções ou funcionalidades são removidas, defina a propriedade como "Ausente".</span><span class="sxs-lookup"><span data-stu-id="c196c-119">To ensure that the roles or features are added, set this property to "Present" To ensure that the roles or features are removed, set the property to "Absent".</span></span>|
| <span data-ttu-id="c196c-120">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="c196c-120">IncludeAllSubFeature</span></span>| <span data-ttu-id="c196c-121">Defina esta propriedade como **$true** para incluir todas as necessárias subfuncionalidades com os recursos que especificar com o **nome** propriedade.</span><span class="sxs-lookup"><span data-stu-id="c196c-121">Set this property to **$true** to include all required subfeatures with of the features you specify with the **Name** property.</span></span>|
| <span data-ttu-id="c196c-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="c196c-122">LogPath</span></span>| <span data-ttu-id="c196c-123">O caminho para um ficheiro de registo onde pretende que o fornecedor de recursos para iniciar a operação.</span><span class="sxs-lookup"><span data-stu-id="c196c-123">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="c196c-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c196c-124">DependsOn</span></span>| <span data-ttu-id="c196c-125">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="c196c-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c196c-126">Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será __ResourceName__ e seu tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="c196c-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="c196c-127">Origem</span><span class="sxs-lookup"><span data-stu-id="c196c-127">Source</span></span>| <span data-ttu-id="c196c-128">Indica a localização do ficheiro de origem a utilizar para instalação, se necessário.</span><span class="sxs-lookup"><span data-stu-id="c196c-128">Indicates the location of the source file to use for installation, if necessary.</span></span>|

## <a name="example"></a><span data-ttu-id="c196c-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c196c-129">Example</span></span>

<span data-ttu-id="c196c-130">A seguinte configuração garante que o **servidor Web** (IIS) e **servidor SMTP** funcionalidades e todas as subfuncionalidades de cada um, são instaladas.</span><span class="sxs-lookup"><span data-stu-id="c196c-130">The following configuration ensures that the **Web-Server** (IIS) and **SMTP Server** features, and all subfeatures of each, are installed.</span></span>

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
