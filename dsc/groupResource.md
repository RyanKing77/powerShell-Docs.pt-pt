---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Recurso do grupo de DSC
ms.openlocfilehash: 6a4732439bb45e36fa9201975f12194442611002
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-group-resource"></a><span data-ttu-id="c6215-103">Recurso do grupo de DSC</span><span class="sxs-lookup"><span data-stu-id="c6215-103">DSC Group Resource</span></span>

> <span data-ttu-id="c6215-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c6215-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="c6215-105">O recurso do grupo no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir grupos locais no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="c6215-105">The Group resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="c6215-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c6215-106">Syntax</span></span>

```
Group [string] #ResourceName
{
    GroupName          = [string]
    [ Credential       = [PSCredential] ]
    [ Description      = [string[]] ]
    [ Ensure           = [string] { Absent | Present }  ]
    [ Members          = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn        = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="c6215-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c6215-107">Properties</span></span>

|  <span data-ttu-id="c6215-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="c6215-108">Property</span></span>  |  <span data-ttu-id="c6215-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6215-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="c6215-110">GroupName</span><span class="sxs-lookup"><span data-stu-id="c6215-110">GroupName</span></span>| <span data-ttu-id="c6215-111">O nome do grupo para o qual pretende garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="c6215-111">The name of the group for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="c6215-112">credencial</span><span class="sxs-lookup"><span data-stu-id="c6215-112">Credential</span></span>| <span data-ttu-id="c6215-113">As credenciais necessárias para aceder a recursos remotos.</span><span class="sxs-lookup"><span data-stu-id="c6215-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="c6215-114">**Tenha em atenção**: esta conta tem de ter as permissões adequadas do Active Directory para adicionar todas as contas não local ao grupo; caso contrário, ocorrerá um erro quando a configuração é executada no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="c6215-114">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>
| <span data-ttu-id="c6215-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6215-115">Description</span></span>| <span data-ttu-id="c6215-116">A descrição do grupo.</span><span class="sxs-lookup"><span data-stu-id="c6215-116">The description of the group.</span></span>|
| <span data-ttu-id="c6215-117">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="c6215-117">Ensure</span></span>| <span data-ttu-id="c6215-118">Indica se o grupo existe.</span><span class="sxs-lookup"><span data-stu-id="c6215-118">Indicates if the group exists.</span></span> <span data-ttu-id="c6215-119">Defina esta propriedade para "Ausente", certifique-se de que o grupo não existe.</span><span class="sxs-lookup"><span data-stu-id="c6215-119">Set this property to "Absent" to ensure that the group does not exist.</span></span> <span data-ttu-id="c6215-120">Defini-la para "Apresentar" (o valor predefinido) assegura que o grupo existe.</span><span class="sxs-lookup"><span data-stu-id="c6215-120">Setting it to "Present" (the default value) ensures that the group exists.</span></span>|
| <span data-ttu-id="c6215-121">Membros</span><span class="sxs-lookup"><span data-stu-id="c6215-121">Members</span></span>| <span data-ttu-id="c6215-122">Utilize esta propriedade para substituir a associação do grupo atual com os membros especificados.</span><span class="sxs-lookup"><span data-stu-id="c6215-122">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="c6215-123">O valor desta propriedade é uma matriz de cadeias de formato *domínio*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="c6215-123">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="c6215-124">Se definir esta propriedade numa configuração, não utilizar o **MembersToExclude** ou **MembersToInclude** propriedade.</span><span class="sxs-lookup"><span data-stu-id="c6215-124">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="c6215-125">Se o fizer, gera um erro.</span><span class="sxs-lookup"><span data-stu-id="c6215-125">Doing so generates an error.</span></span>|
| <span data-ttu-id="c6215-126">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="c6215-126">MembersToExclude</span></span>| <span data-ttu-id="c6215-127">Utilize esta propriedade para remover membros da associação do grupo.</span><span class="sxs-lookup"><span data-stu-id="c6215-127">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="c6215-128">O valor desta propriedade é uma matriz de cadeias de formato *domínio*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="c6215-128">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="c6215-129">Se definir esta propriedade numa configuração, não utilize o **membros** propriedade.</span><span class="sxs-lookup"><span data-stu-id="c6215-129">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="c6215-130">Se o fizer, gera um erro.</span><span class="sxs-lookup"><span data-stu-id="c6215-130">Doing so generates an error.</span></span>|
| <span data-ttu-id="c6215-131">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="c6215-131">MembersToInclude</span></span>| <span data-ttu-id="c6215-132">Utilize esta propriedade para adicionar membros à associação do grupo existente.</span><span class="sxs-lookup"><span data-stu-id="c6215-132">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="c6215-133">O valor desta propriedade é uma matriz de cadeias de formato *domínio*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="c6215-133">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="c6215-134">Se definir esta propriedade numa configuração, não utilize o **membros** propriedade.</span><span class="sxs-lookup"><span data-stu-id="c6215-134">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="c6215-135">Se o fizer, irá gerar um erro.</span><span class="sxs-lookup"><span data-stu-id="c6215-135">Doing so will generate an error.</span></span>|
| <span data-ttu-id="c6215-136">dependsOn</span><span class="sxs-lookup"><span data-stu-id="c6215-136">DependsOn</span></span> | <span data-ttu-id="c6215-137">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="c6215-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c6215-138">Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é ' DependsOn = "[ ResourceName ResourceType]"'.</span><span class="sxs-lookup"><span data-stu-id="c6215-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1"></a><span data-ttu-id="c6215-139">Exemplo 1</span><span class="sxs-lookup"><span data-stu-id="c6215-139">Example 1</span></span>

<span data-ttu-id="c6215-140">O exemplo seguinte mostra como Certifique-se de que um grupo denominado "TestGroup" está ausente.</span><span class="sxs-lookup"><span data-stu-id="c6215-140">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span>

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2"></a><span data-ttu-id="c6215-141">Exemplo 2</span><span class="sxs-lookup"><span data-stu-id="c6215-141">Example 2</span></span>

<span data-ttu-id="c6215-142">O exemplo seguinte mostra como adicionar um utilizador do Active Directory para o grupo de administradores locais como parte de uma compilação de laboratório multi máquina em que já estiver a utilizar um PSCredential para a conta de administrador Local.</span><span class="sxs-lookup"><span data-stu-id="c6215-142">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Adminstrator account.</span></span>
<span data-ttu-id="c6215-143">Como também é utilizado para a conta de administrador de domínio (após a promoção de domínio), em seguida, é necessário converter este PSCredential existente para uma credencial de domínio amigável.</span><span class="sxs-lookup"><span data-stu-id="c6215-143">As this is also used for the Domain Admin Account (after Domain promotion), we then need to convert this existing PSCredential to a Domain Friendly credential.</span></span>
<span data-ttu-id="c6215-144">Em seguida, iremos pode adicionar um utilizador de domínio para o grupo de administradores Local no servidor membro.</span><span class="sxs-lookup"><span data-stu-id="c6215-144">Then we can add a Domain User to the Local Administrators Group on the Member server.</span></span>

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
        @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'
        }
    )
}

$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup {
    GroupName='Administrators'
    Ensure= 'Present'
    MembersToInclude= "$domain\$($Node.AdminAccount)"
    Credential = $dCredential
    PsDscRunAsCredential = $DCredential
}
```

## <a name="example-3"></a><span data-ttu-id="c6215-145">Exemplo 3</span><span class="sxs-lookup"><span data-stu-id="c6215-145">Example 3</span></span>

<span data-ttu-id="c6215-146">O exemplo seguinte mostra como garantir que um grupo local, TigerTeamAdmins, no servidor TigerTeamSource.Contoso.Com não contém uma conta de domínio específico, Contoso\JerryG.</span><span class="sxs-lookup"><span data-stu-id="c6215-146">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>

```powershell
Configuration SecureTigerTeamSrouce {
  Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

  Node TigerTeamSource.Contoso.Com {
    Group TigerTeamAdmins {
       GroupName        = 'TigerTeamAdmins'
       Ensure           = 'Present'
       MembersToExclude = "Contoso\JerryG"
    }
  }
}
```