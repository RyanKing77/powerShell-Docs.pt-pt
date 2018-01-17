---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
description: "Fornece um mecanismo para gerir grupos locais no nó de destino."
title: Recursos do DSC GroupSet
ms.openlocfilehash: 158cb28747c5fe1987eb62b2cc0f6d6f6fb14332
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="b4af4-104">Recursos do DSC GroupSet</span><span class="sxs-lookup"><span data-stu-id="b4af4-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="b4af4-105">Aplica-se a: Windows do Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b4af4-105">Applies To: Windows Windows PowerShell 5.0</span></span>

<span data-ttu-id="b4af4-106">O **GroupSet** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir grupos locais no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="b4af4-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="b4af4-107">Este recurso se encontra um [recursos composto](authoringResourceComposite.md) que chama o [grupo recursos](groupResource.md) para cada grupo especificado no `GroupName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b4af4-107">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="b4af4-108">Utilize este recurso quando se pretende adicionar e/ou remover a mesma lista de membros de mais de um grupo, remover mais do que um grupo ou adicione mais de um grupo com a mesma lista de membros.</span><span class="sxs-lookup"><span data-stu-id="b4af4-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

##<a name="syntax"></a><span data-ttu-id="b4af4-109">Sintaxe # #</span><span class="sxs-lookup"><span data-stu-id="b4af4-109">Syntax##</span></span>
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

## <a name="properties"></a><span data-ttu-id="b4af4-110">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b4af4-110">Properties</span></span>

|  <span data-ttu-id="b4af4-111">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b4af4-111">Property</span></span>  |  <span data-ttu-id="b4af4-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="b4af4-112">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="b4af4-113">GroupName</span><span class="sxs-lookup"><span data-stu-id="b4af4-113">GroupName</span></span>| <span data-ttu-id="b4af4-114">Os nomes dos grupos para os quais pretender certificar-se num estado específico.</span><span class="sxs-lookup"><span data-stu-id="b4af4-114">The names of the groups for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="b4af4-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="b4af4-115">MembersToExclude</span></span>| <span data-ttu-id="b4af4-116">Utilize esta propriedade para remover membros da associação dos grupos.</span><span class="sxs-lookup"><span data-stu-id="b4af4-116">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="b4af4-117">O valor desta propriedade é uma matriz de cadeias de formato *domínio*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="b4af4-117">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="b4af4-118">Se definir esta propriedade numa configuração, não utilize o **membros** propriedade.</span><span class="sxs-lookup"><span data-stu-id="b4af4-118">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="b4af4-119">Se o fizer, irá gerar um erro.</span><span class="sxs-lookup"><span data-stu-id="b4af4-119">Doing so will generate an error.</span></span>| 
| <span data-ttu-id="b4af4-120">credencial</span><span class="sxs-lookup"><span data-stu-id="b4af4-120">Credential</span></span>| <span data-ttu-id="b4af4-121">As credenciais necessárias para aceder a recursos remotos.</span><span class="sxs-lookup"><span data-stu-id="b4af4-121">The credentials required to access remote resources.</span></span> <span data-ttu-id="b4af4-122">**Tenha em atenção**: esta conta tem de ter as permissões adequadas do Active Directory para adicionar todas as contas não local ao grupo; caso contrário, ocorrerá um erro.</span><span class="sxs-lookup"><span data-stu-id="b4af4-122">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span>
| <span data-ttu-id="b4af4-123">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="b4af4-123">Ensure</span></span>| <span data-ttu-id="b4af4-124">Indica se os grupos de existirem.</span><span class="sxs-lookup"><span data-stu-id="b4af4-124">Indicates whether the groups exist.</span></span> <span data-ttu-id="b4af4-125">Defina esta propriedade para "Ausente", certifique-se de que os grupos não existir.</span><span class="sxs-lookup"><span data-stu-id="b4af4-125">Set this property to "Absent" to ensure that the groups do not exist.</span></span> <span data-ttu-id="b4af4-126">Defini-la para "Apresentar" (o valor predefinido) assegura que os grupos de existirem.</span><span class="sxs-lookup"><span data-stu-id="b4af4-126">Setting it to "Present" (the default value) ensures that the groups exist.</span></span>| 
| <span data-ttu-id="b4af4-127">Membros</span><span class="sxs-lookup"><span data-stu-id="b4af4-127">Members</span></span>| <span data-ttu-id="b4af4-128">Utilize esta propriedade para substituir a associação do grupo atual com os membros especificados.</span><span class="sxs-lookup"><span data-stu-id="b4af4-128">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="b4af4-129">O valor desta propriedade é uma matriz de cadeias de formato *domínio*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="b4af4-129">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="b4af4-130">Se definir esta propriedade numa configuração, não utilizar o **MembersToExclude** ou **MembersToInclude** propriedade.</span><span class="sxs-lookup"><span data-stu-id="b4af4-130">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="b4af4-131">Se o fizer, irá gerar um erro.</span><span class="sxs-lookup"><span data-stu-id="b4af4-131">Doing so will generate an error.</span></span>| 
| <span data-ttu-id="b4af4-132">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="b4af4-132">MembersToInclude</span></span>| <span data-ttu-id="b4af4-133">Utilize esta propriedade para adicionar membros à associação do grupo existente.</span><span class="sxs-lookup"><span data-stu-id="b4af4-133">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="b4af4-134">O valor desta propriedade é uma matriz de cadeias de formato *domínio*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="b4af4-134">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="b4af4-135">Se definir esta propriedade numa configuração, não utilize o **membros** propriedade.</span><span class="sxs-lookup"><span data-stu-id="b4af4-135">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="b4af4-136">Se o fizer, irá gerar um erro.</span><span class="sxs-lookup"><span data-stu-id="b4af4-136">Doing so will generate an error.</span></span>| 
| <span data-ttu-id="b4af4-137">dependsOn</span><span class="sxs-lookup"><span data-stu-id="b4af4-137">DependsOn</span></span> | <span data-ttu-id="b4af4-138">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="b4af4-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b4af4-139">Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é ' DependsOn = "[ ResourceName ResourceType]"'.</span><span class="sxs-lookup"><span data-stu-id="b4af4-139">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>| 

## <a name="example-1"></a><span data-ttu-id="b4af4-140">Exemplo 1</span><span class="sxs-lookup"><span data-stu-id="b4af4-140">Example 1</span></span>

<span data-ttu-id="b4af4-141">O exemplo seguinte mostra como Certifique-se de que existem dois grupos chamado "myGroup" e "myOtherGroup".</span><span class="sxs-lookup"><span data-stu-id="b4af4-141">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span> 

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

><span data-ttu-id="b4af4-142">**Nota:** este exemplo utiliza credenciais de texto simples de simplicidade.</span><span class="sxs-lookup"><span data-stu-id="b4af4-142">**Note:** This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="b4af4-143">Para obter informações sobre como encriptar as credenciais no ficheiro MOF configuração, consulte [proteger o ficheiro MOF](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="b4af4-143">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](secureMOF.md).</span></span>


