---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: DSC para Linux nxUser recursos
ms.openlocfilehash: 1b02be1559957585a2a1733630cb93440e8182f9
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048391"
---
# <a name="dsc-for-linux-nxuser-resource"></a><span data-ttu-id="c7075-103">DSC para Linux nxUser recursos</span><span class="sxs-lookup"><span data-stu-id="c7075-103">DSC for Linux nxUser Resource</span></span>

<span data-ttu-id="c7075-104">O **nxUser** recursos no PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir utilizadores locais num nó de Linux.</span><span class="sxs-lookup"><span data-stu-id="c7075-104">The **nxUser** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local users on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="c7075-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c7075-105">Syntax</span></span>

```
nxUser <string> #ResourceName
{
    UserName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="c7075-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c7075-106">Properties</span></span>

|  <span data-ttu-id="c7075-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="c7075-107">Property</span></span> |  <span data-ttu-id="c7075-108">Indica o nome da conta para o qual pretende garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="c7075-108">Indicates the account name for which you want to ensure a specific state.</span></span> |
|---|---|
| <span data-ttu-id="c7075-109">UserName</span><span class="sxs-lookup"><span data-stu-id="c7075-109">UserName</span></span>| <span data-ttu-id="c7075-110">Especifica a localização onde pretende garantir que o estado para um ficheiro ou diretório.</span><span class="sxs-lookup"><span data-stu-id="c7075-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="c7075-111">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="c7075-111">Ensure</span></span>| <span data-ttu-id="c7075-112">Especifica se a conta existe.</span><span class="sxs-lookup"><span data-stu-id="c7075-112">Specifies whether the account exists.</span></span> <span data-ttu-id="c7075-113">Definir esta propriedade para "Presente" para se certificar de que a conta existe e defini-lo como "Ausente", certifique-se de que a conta não existe.</span><span class="sxs-lookup"><span data-stu-id="c7075-113">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="c7075-114">FullName</span><span class="sxs-lookup"><span data-stu-id="c7075-114">FullName</span></span>| <span data-ttu-id="c7075-115">Uma cadeia que contém o nome completo para utilizar para a conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="c7075-115">A string that contains the full name to use for the user account.</span></span>|
| <span data-ttu-id="c7075-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7075-116">Description</span></span>| <span data-ttu-id="c7075-117">A descrição da conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="c7075-117">The description for the user account.</span></span>|
| <span data-ttu-id="c7075-118">Palavra-passe</span><span class="sxs-lookup"><span data-stu-id="c7075-118">Password</span></span>| <span data-ttu-id="c7075-119">O hash da palavra-passe de utilizadores no formato adequado para o computador Linux.</span><span class="sxs-lookup"><span data-stu-id="c7075-119">The hash of the users password in the appropriate form for the Linux computer.</span></span> <span data-ttu-id="c7075-120">Normalmente, este é um SALT SHA-256, ou hash SHA-512.</span><span class="sxs-lookup"><span data-stu-id="c7075-120">Typically, this is a salted SHA-256, or SHA-512 hash.</span></span> <span data-ttu-id="c7075-121">No Debian e Ubuntu Linux, este valor pode ser gerado com o comando mkpasswd.</span><span class="sxs-lookup"><span data-stu-id="c7075-121">On Debian and Ubuntu Linux, this value can be generated with the mkpasswd command.</span></span> <span data-ttu-id="c7075-122">Para outras distribuições do Linux, o método crypt da biblioteca de Crypt do Python pode ser utilizado para gerar o hash.</span><span class="sxs-lookup"><span data-stu-id="c7075-122">For other Linux distros, the crypt method of Python’s Crypt library can be used to generate the hash.</span></span>|
| <span data-ttu-id="c7075-123">Desativada</span><span class="sxs-lookup"><span data-stu-id="c7075-123">Disabled</span></span>| <span data-ttu-id="c7075-124">Indica se a conta está ativada.</span><span class="sxs-lookup"><span data-stu-id="c7075-124">Indicates whether the account is enabled.</span></span> <span data-ttu-id="c7075-125">Defina esta propriedade como **$true** para se certificar de que esta conta está desativada e defini-lo como **$false** para se certificar de que está ativada.</span><span class="sxs-lookup"><span data-stu-id="c7075-125">Set this property to **$true** to ensure that this account is disabled, and set it to **$false** to ensure that it is enabled.</span></span>|
| <span data-ttu-id="c7075-126">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="c7075-126">PasswordChangeRequired</span></span>| <span data-ttu-id="c7075-127">Indica se o utilizador pode alterar a palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="c7075-127">Indicates whether the user can change the password.</span></span> <span data-ttu-id="c7075-128">Defina esta propriedade como **$true** para se certificar de que o utilizador não é possível alterar a palavra-passe e defini-lo como **$false** para permitir que o utilizador altere a palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="c7075-128">Set this property to **$true** to ensure that the user cannot change the password, and set it to **$false** to allow the user to change the password.</span></span> <span data-ttu-id="c7075-129">O valor predefinido é **$false**.</span><span class="sxs-lookup"><span data-stu-id="c7075-129">The default value is **$false**.</span></span> <span data-ttu-id="c7075-130">Esta propriedade é avaliada apenas se a conta de utilizador não existia anteriormente e está a ser criada.</span><span class="sxs-lookup"><span data-stu-id="c7075-130">This property is only evaluated if the user account did not exist previously and is being created.</span></span>|
| <span data-ttu-id="c7075-131">HomeDirectory</span><span class="sxs-lookup"><span data-stu-id="c7075-131">HomeDirectory</span></span>| <span data-ttu-id="c7075-132">O diretório de raiz para o utilizador.</span><span class="sxs-lookup"><span data-stu-id="c7075-132">The home directory for the user.</span></span>|
| <span data-ttu-id="c7075-133">GroupID</span><span class="sxs-lookup"><span data-stu-id="c7075-133">GroupID</span></span>| <span data-ttu-id="c7075-134">O ID de grupo principal para o utilizador.</span><span class="sxs-lookup"><span data-stu-id="c7075-134">The primary group ID for the user.</span></span>|
| <span data-ttu-id="c7075-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c7075-135">DependsOn</span></span> | <span data-ttu-id="c7075-136">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="c7075-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c7075-137">Por exemplo, se o ID do bloco de script de configuração de recursos que pretende executar primeiro é "ResourceName" e seu tipo é "ResourceType", a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="c7075-137">For example, if the ID of the resource configuration script block that you want to run first is "ResourceName" and its type is "ResourceType", the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="c7075-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c7075-138">Example</span></span>

<span data-ttu-id="c7075-139">O exemplo seguinte garante que o utilizador "monuser" existe e é um membro do grupo "DBusers".</span><span class="sxs-lookup"><span data-stu-id="c7075-139">The following example ensures that the user "monuser" exists and is a member of the group "DBusers".</span></span>

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