---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
description: Fornece um mecanismo para gerir grupos locais no nó de destino.
title: Recurso GroupSet de DSC
ms.openlocfilehash: 6fa8e9637da896848e859dc60a42add12e973b34
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/30/2018
ms.locfileid: "50226122"
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="c850c-104">Recurso GroupSet de DSC</span><span class="sxs-lookup"><span data-stu-id="c850c-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="c850c-105">Aplica-se a: O Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c850c-105">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="c850c-106">O **GroupSet** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir grupos locais no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="c850c-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="c850c-107">Este recurso é um [recursos compostos](authoringResourceComposite.md) que chama o [grupo de recursos](groupResource.md) para cada grupo especificado no `GroupName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c850c-107">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="c850c-108">Utilize este recurso quando deseja adicionar e/ou remova a mesma lista de membros de mais de um grupo, remover mais de um grupo ou adicionar mais de um grupo com a mesma lista de membros.</span><span class="sxs-lookup"><span data-stu-id="c850c-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

## <a name="syntax"></a><span data-ttu-id="c850c-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c850c-109">Syntax</span></span>

```
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="c850c-110">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c850c-110">Properties</span></span>

|  <span data-ttu-id="c850c-111">Propriedade</span><span class="sxs-lookup"><span data-stu-id="c850c-111">Property</span></span>  |  <span data-ttu-id="c850c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c850c-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="c850c-113">GroupName</span><span class="sxs-lookup"><span data-stu-id="c850c-113">GroupName</span></span>| <span data-ttu-id="c850c-114">Os nomes dos grupos para o qual pretende garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="c850c-114">The names of the groups for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="c850c-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="c850c-115">MembersToExclude</span></span>| <span data-ttu-id="c850c-116">Use essa propriedade para remover membros da associação existente dos grupos.</span><span class="sxs-lookup"><span data-stu-id="c850c-116">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="c850c-117">O valor desta propriedade é uma matriz de cadeias de caracteres do formulário *domínio*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="c850c-117">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="c850c-118">Se definir esta propriedade numa configuração, não utilize o **membros** propriedade.</span><span class="sxs-lookup"><span data-stu-id="c850c-118">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="c850c-119">Se o fizer, irá gerar um erro.</span><span class="sxs-lookup"><span data-stu-id="c850c-119">Doing so will generate an error.</span></span>|
| <span data-ttu-id="c850c-120">Credencial</span><span class="sxs-lookup"><span data-stu-id="c850c-120">Credential</span></span>| <span data-ttu-id="c850c-121">As credenciais necessárias para aceder a recursos remotos.</span><span class="sxs-lookup"><span data-stu-id="c850c-121">The credentials required to access remote resources.</span></span> <span data-ttu-id="c850c-122">**Tenha em atenção**: esta conta tem de ter as permissões adequadas do Active Directory para adicionar todas as contas de não-local para o grupo; caso contrário, ocorrerá um erro.</span><span class="sxs-lookup"><span data-stu-id="c850c-122">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span>
| <span data-ttu-id="c850c-123">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="c850c-123">Ensure</span></span>| <span data-ttu-id="c850c-124">Indica se os grupos de existem.</span><span class="sxs-lookup"><span data-stu-id="c850c-124">Indicates whether the groups exist.</span></span> <span data-ttu-id="c850c-125">Defina esta propriedade para "Ausente", certifique-se de que os grupos não existem.</span><span class="sxs-lookup"><span data-stu-id="c850c-125">Set this property to "Absent" to ensure that the groups do not exist.</span></span> <span data-ttu-id="c850c-126">Defini-la para "Apresentar" (o valor predefinido) garante que os grupos de existam.</span><span class="sxs-lookup"><span data-stu-id="c850c-126">Setting it to "Present" (the default value) ensures that the groups exist.</span></span>|
| <span data-ttu-id="c850c-127">Membros</span><span class="sxs-lookup"><span data-stu-id="c850c-127">Members</span></span>| <span data-ttu-id="c850c-128">Use essa propriedade para substituir a associação do grupo atual com os membros especificados.</span><span class="sxs-lookup"><span data-stu-id="c850c-128">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="c850c-129">O valor desta propriedade é uma matriz de cadeias de caracteres do formulário *domínio*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="c850c-129">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="c850c-130">Se definir esta propriedade numa configuração, não utilizar o **MembersToExclude** ou **MembersToInclude** propriedade.</span><span class="sxs-lookup"><span data-stu-id="c850c-130">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="c850c-131">Se o fizer, irá gerar um erro.</span><span class="sxs-lookup"><span data-stu-id="c850c-131">Doing so will generate an error.</span></span>|
| <span data-ttu-id="c850c-132">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="c850c-132">MembersToInclude</span></span>| <span data-ttu-id="c850c-133">Use essa propriedade para adicionar membros para a associação existente do grupo.</span><span class="sxs-lookup"><span data-stu-id="c850c-133">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="c850c-134">O valor desta propriedade é uma matriz de cadeias de caracteres do formulário *domínio*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="c850c-134">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="c850c-135">Se definir esta propriedade numa configuração, não utilize o **membros** propriedade.</span><span class="sxs-lookup"><span data-stu-id="c850c-135">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="c850c-136">Se o fizer, irá gerar um erro.</span><span class="sxs-lookup"><span data-stu-id="c850c-136">Doing so will generate an error.</span></span>|
| <span data-ttu-id="c850c-137">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c850c-137">DependsOn</span></span> | <span data-ttu-id="c850c-138">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="c850c-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c850c-139">Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será __ResourceName__ e seu tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é "DependsOn ="[ ResourceName ResourceType]"'.</span><span class="sxs-lookup"><span data-stu-id="c850c-139">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1-ensuring-groups-are-present"></a><span data-ttu-id="c850c-140">Exemplo 1: Grupos de garantir que estão presentes</span><span class="sxs-lookup"><span data-stu-id="c850c-140">Example 1: Ensuring Groups are present</span></span>

<span data-ttu-id="c850c-141">O exemplo seguinte mostra como Certifique-se de que existem dois grupos, chamado "myGroup" e "myOtherGroup".</span><span class="sxs-lookup"><span data-stu-id="c850c-141">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

```powershell
configuration GroupSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        GroupSet GroupSetTest
        {
            GroupName        = @("myGroup", "myOtherGroup")
            Ensure           = "Present"
            MembersToInclude = @("contoso\alice", "contoso\bob")
            MembersToExclude = $("contoso\john")
            Credential       = Get-Credential
        }
    }
}
$cd = @{
    AllNodes = @(
        @{
            NodeName                    = 'localhost'
            PSDscAllowPlainTextPassword = $true
            PSDscAllowDomainUser        = $true
        }
    )
}

GroupSetTest -ConfigurationData $cd
```

> [!NOTE] 
> <span data-ttu-id="c850c-142">Este exemplo utiliza credenciais de texto sem formatação para manter a simplicidade.</span><span class="sxs-lookup"><span data-stu-id="c850c-142">This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="c850c-143">Para obter informações sobre como encriptar as credenciais no arquivo MOF de configuração, consulte [proteger o ficheiro MOF](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="c850c-143">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](secureMOF.md).</span></span>
