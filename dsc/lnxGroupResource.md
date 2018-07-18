---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: DSC para Linux nxGroup recursos
ms.openlocfilehash: c61b6ab4a8c56d085b5297dcfc7582187d54f946
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093607"
---
# <a name="dsc-for-linux-nxgroup-resource"></a><span data-ttu-id="735fb-103">DSC para Linux nxGroup recursos</span><span class="sxs-lookup"><span data-stu-id="735fb-103">DSC for Linux nxGroup Resource</span></span>

<span data-ttu-id="735fb-104">O **nxGroup** recursos no PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir grupos locais num nó de Linux.</span><span class="sxs-lookup"><span data-stu-id="735fb-104">The **nxGroup** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="735fb-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="735fb-105">Syntax</span></span>

```
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present } ]
    [ Members = <string[]> ]
    [ MembersToInclude = <string[]> ]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="735fb-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="735fb-106">Properties</span></span>

|  <span data-ttu-id="735fb-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="735fb-107">Property</span></span> |  <span data-ttu-id="735fb-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="735fb-108">Description</span></span> |
|---|---|
| <span data-ttu-id="735fb-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="735fb-109">GroupName</span></span>| <span data-ttu-id="735fb-110">Especifica o nome do grupo para o qual pretende garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="735fb-110">Specifies the name of the group for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="735fb-111">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="735fb-111">Ensure</span></span>| <span data-ttu-id="735fb-112">Determina se deve verificar se o grupo existe.</span><span class="sxs-lookup"><span data-stu-id="735fb-112">Determines whether to check if the group exists.</span></span> <span data-ttu-id="735fb-113">Defina esta propriedade para "Presente" para garantir que o grupo existe.</span><span class="sxs-lookup"><span data-stu-id="735fb-113">Set this property to "Present" to ensure the group exists.</span></span> <span data-ttu-id="735fb-114">Defini-lo como "Ausente", certifique-se de que o grupo não existe.</span><span class="sxs-lookup"><span data-stu-id="735fb-114">Set it to "Absent" to ensure the group does not exist.</span></span> <span data-ttu-id="735fb-115">O valor predefinido é "Presente".</span><span class="sxs-lookup"><span data-stu-id="735fb-115">The default value is "Present".</span></span>|
| <span data-ttu-id="735fb-116">Membros</span><span class="sxs-lookup"><span data-stu-id="735fb-116">Members</span></span>| <span data-ttu-id="735fb-117">Especifica os membros que formam o grupo.</span><span class="sxs-lookup"><span data-stu-id="735fb-117">Specifies the members that form the group.</span></span>|
| <span data-ttu-id="735fb-118">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="735fb-118">MembersToInclude</span></span>| <span data-ttu-id="735fb-119">Especifica os utilizadores que pretende garantir que são membros do grupo.</span><span class="sxs-lookup"><span data-stu-id="735fb-119">Specifies the users who you want to ensure are members of the group.</span></span>|
| <span data-ttu-id="735fb-120">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="735fb-120">MembersToExclude</span></span>| <span data-ttu-id="735fb-121">Especifica os utilizadores que pretende garantir que não são membros do grupo.</span><span class="sxs-lookup"><span data-stu-id="735fb-121">Specifies the users who you want to ensure are not members of the group.</span></span>|
| <span data-ttu-id="735fb-122">PreferredGroupID</span><span class="sxs-lookup"><span data-stu-id="735fb-122">PreferredGroupID</span></span>| <span data-ttu-id="735fb-123">Define o id de grupo para o valor fornecido se possível.</span><span class="sxs-lookup"><span data-stu-id="735fb-123">Sets the group id to the provided value if possible.</span></span> <span data-ttu-id="735fb-124">Se o id de grupo está atualmente em utilização, é utilizado o seguinte id de grupo disponíveis.</span><span class="sxs-lookup"><span data-stu-id="735fb-124">If the group id is currently in use, the next available group id is used.</span></span>|
| <span data-ttu-id="735fb-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="735fb-125">DependsOn</span></span> | <span data-ttu-id="735fb-126">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="735fb-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="735fb-127">Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e seu tipo é **ResourceType**, a sintaxe para usar isso a propriedade é `DependsOn = '[ResourceType]ResourceName'`.</span><span class="sxs-lookup"><span data-stu-id="735fb-127">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="735fb-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="735fb-128">Example</span></span>

<span data-ttu-id="735fb-129">O exemplo seguinte garante que o utilizador 'monuser' existe e é um membro do grupo 'DBusers'.</span><span class="sxs-lookup"><span data-stu-id="735fb-129">The following example ensures that the user 'monuser' exists and is a member of the group 'DBusers'.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node {
    nxUser UserExample {
       UserName = 'monuser'
       Description = 'Monitoring user'
       Password = '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
       Ensure = 'Present'
       HomeDirectory = '/home/monuser'
    }

    nxGroup GroupExample {
       GroupName = 'DBusers'
       Ensure = 'Present'
       MembersToInclude = 'monuser'
       DependsOn = '[nxUser]UserExample'
    }
}
```