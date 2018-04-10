---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: DSC de Linux nxGroup recursos
ms.openlocfilehash: 750b7c38a38fb8a7781585a3a7776f832ee62495
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxgroup-resource"></a><span data-ttu-id="b5541-103">DSC de Linux nxGroup recursos</span><span class="sxs-lookup"><span data-stu-id="b5541-103">DSC for Linux nxGroup Resource</span></span>

<span data-ttu-id="b5541-104">O **nxGroup** recursos no PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir grupos locais num nó de Linux.</span><span class="sxs-lookup"><span data-stu-id="b5541-104">The **nxGroup** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="b5541-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b5541-105">Syntax</span></span>

```powershell
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Members = <string[]> ]
    [ MebersToInclude = <string[]>]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}

```

## <a name="properties"></a><span data-ttu-id="b5541-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b5541-106">Properties</span></span>

|  <span data-ttu-id="b5541-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b5541-107">Property</span></span> |  <span data-ttu-id="b5541-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5541-108">Description</span></span> |
|---|---|
| <span data-ttu-id="b5541-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="b5541-109">GroupName</span></span>| <span data-ttu-id="b5541-110">Especifica o nome do grupo para o qual pretende garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="b5541-110">Specifies the name of the group for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="b5541-111">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="b5541-111">Ensure</span></span>| <span data-ttu-id="b5541-112">Determina se deve verificar se o grupo existe.</span><span class="sxs-lookup"><span data-stu-id="b5541-112">Determines whether to check if the group exists.</span></span> <span data-ttu-id="b5541-113">Defina esta propriedade para "Presente" para garantir que o grupo existe.</span><span class="sxs-lookup"><span data-stu-id="b5541-113">Set this property to "Present" to ensure the group exists.</span></span> <span data-ttu-id="b5541-114">Defina-o para "Ausente", certifique-se de que o grupo não existe.</span><span class="sxs-lookup"><span data-stu-id="b5541-114">Set it to "Absent" to ensure the group does not exist.</span></span> <span data-ttu-id="b5541-115">O valor predefinido é "Presente".</span><span class="sxs-lookup"><span data-stu-id="b5541-115">The default value is "Present".</span></span>|
| <span data-ttu-id="b5541-116">Membros</span><span class="sxs-lookup"><span data-stu-id="b5541-116">Members</span></span>| <span data-ttu-id="b5541-117">Especifica os membros que formam o grupo.</span><span class="sxs-lookup"><span data-stu-id="b5541-117">Specifies the members that form the group.</span></span>|
| <span data-ttu-id="b5541-118">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="b5541-118">MembersToInclude</span></span>| <span data-ttu-id="b5541-119">Especifica os utilizadores que pretende para se certificar de que são membros do grupo.</span><span class="sxs-lookup"><span data-stu-id="b5541-119">Specifies the users who you want to ensure are members of the group.</span></span>|
| <span data-ttu-id="b5541-120">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="b5541-120">MembersToExclude</span></span>| <span data-ttu-id="b5541-121">Especifica os utilizadores que pretende para se certificar de que não são membros do grupo.</span><span class="sxs-lookup"><span data-stu-id="b5541-121">Specifies the users who you want to ensure are not members of the group.</span></span>|
| <span data-ttu-id="b5541-122">PreferredGroupID</span><span class="sxs-lookup"><span data-stu-id="b5541-122">PreferredGroupID</span></span>| <span data-ttu-id="b5541-123">Define o id de grupo para o valor fornecido se possível.</span><span class="sxs-lookup"><span data-stu-id="b5541-123">Sets the group id to the provided value if possible.</span></span> <span data-ttu-id="b5541-124">Se o id de grupo está a ser utilizada, o seguinte id de grupo disponível é utilizado.</span><span class="sxs-lookup"><span data-stu-id="b5541-124">If the group id is currently in use, the next available group id is used.</span></span>|
| <span data-ttu-id="b5541-125">dependsOn</span><span class="sxs-lookup"><span data-stu-id="b5541-125">DependsOn</span></span> | <span data-ttu-id="b5541-126">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="b5541-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b5541-127">Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e o respetivo tipo é **ResourceType**, a sintaxe para utilizar esta a propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="b5541-127">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="b5541-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b5541-128">Example</span></span>

<span data-ttu-id="b5541-129">O exemplo seguinte assegura que o utilizador "monuser" existe e se é um membro do grupo "DBusers".</span><span class="sxs-lookup"><span data-stu-id="b5541-129">The following example ensures that the user “monuser” exists and is a member of the group "DBusers".</span></span>

```
Import-DSCResource -Module nx

Node $node {

nxUser UserExample{
   UserName = "monuser"
   Description = "Monitoring user"
   Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
   Ensure = "Present"
   HomeDirectory = "/home/monuser"
}

nxGroup GroupExample{
   GroupName = "DBusers"
   Ensure = "Present"
   MembersToInclude = "monuser"
   DependsOn = "[nxUser]UserExample"
}
}
```