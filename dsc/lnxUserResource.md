---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: DSC de Linux nxUser recursos
ms.openlocfilehash: 222bd2191cf5c5f0a90ba947275ffde47d22ec86
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxuser-resource"></a><span data-ttu-id="50d20-103">DSC de Linux nxUser recursos</span><span class="sxs-lookup"><span data-stu-id="50d20-103">DSC for Linux nxUser Resource</span></span>

<span data-ttu-id="50d20-104">O **nxUser** recursos no PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir utilizadores locais num nó de Linux.</span><span class="sxs-lookup"><span data-stu-id="50d20-104">The **nxUser** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage local users on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="50d20-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="50d20-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="50d20-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="50d20-106">Properties</span></span>

|  <span data-ttu-id="50d20-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="50d20-107">Property</span></span> |  <span data-ttu-id="50d20-108">Indica o nome de conta para o qual pretende garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="50d20-108">Indicates the account name for which you want to ensure a specific state.</span></span> |
|---|---|
| <span data-ttu-id="50d20-109">UserName</span><span class="sxs-lookup"><span data-stu-id="50d20-109">UserName</span></span>| <span data-ttu-id="50d20-110">Especifica a localização onde pretende garantir o estado de um ficheiro ou diretório.</span><span class="sxs-lookup"><span data-stu-id="50d20-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="50d20-111">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="50d20-111">Ensure</span></span>| <span data-ttu-id="50d20-112">Especifica se a conta existe.</span><span class="sxs-lookup"><span data-stu-id="50d20-112">Specifies whether the account exists.</span></span> <span data-ttu-id="50d20-113">Definir esta propriedade para "Presente" para garantir que a conta existe e defina-o para "Ausente", certifique-se de que a conta não existe.</span><span class="sxs-lookup"><span data-stu-id="50d20-113">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="50d20-114">FullName</span><span class="sxs-lookup"><span data-stu-id="50d20-114">FullName</span></span>| <span data-ttu-id="50d20-115">Uma cadeia que contém o nome completo a utilizar para a conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="50d20-115">A string that contains the full name to use for the user account.</span></span>|
| <span data-ttu-id="50d20-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="50d20-116">Description</span></span>| <span data-ttu-id="50d20-117">A descrição da conta de utilizador.</span><span class="sxs-lookup"><span data-stu-id="50d20-117">The description for the user account.</span></span>|
| <span data-ttu-id="50d20-118">Palavra-passe</span><span class="sxs-lookup"><span data-stu-id="50d20-118">Password</span></span>| <span data-ttu-id="50d20-119">O hash da palavra-passe de utilizadores no formato adequado para o computador Linux.</span><span class="sxs-lookup"><span data-stu-id="50d20-119">The hash of the users password in the appropriate form for the Linux computer.</span></span> <span data-ttu-id="50d20-120">Normalmente, trata-se um salted SHA-256, ou um hash SHA-512.</span><span class="sxs-lookup"><span data-stu-id="50d20-120">Typically, this is a salted SHA-256, or SHA-512 hash.</span></span> <span data-ttu-id="50d20-121">Debian e Ubuntu Linux, este valor pode ser gerado com o comando mkpasswd.</span><span class="sxs-lookup"><span data-stu-id="50d20-121">On Debian and Ubuntu Linux, this value can be generated with the mkpasswd command.</span></span> <span data-ttu-id="50d20-122">Para outros distros Linux, o método de crypt da biblioteca de Crypt do Python pode ser utilizado para gerar o hash.</span><span class="sxs-lookup"><span data-stu-id="50d20-122">For other Linux distros, the crypt method of Python’s Crypt library can be used to generate the hash.</span></span>|
| <span data-ttu-id="50d20-123">Desativado</span><span class="sxs-lookup"><span data-stu-id="50d20-123">Disabled</span></span>| <span data-ttu-id="50d20-124">Indica se a conta está ativada.</span><span class="sxs-lookup"><span data-stu-id="50d20-124">Indicates whether the account is enabled.</span></span> <span data-ttu-id="50d20-125">Defina esta propriedade como **$true** para se certificar de que esta conta está desativada e defina-o como **$false** para se certificar de que está ativada.</span><span class="sxs-lookup"><span data-stu-id="50d20-125">Set this property to **$true** to ensure that this account is disabled, and set it to **$false** to ensure that it is enabled.</span></span>|
| <span data-ttu-id="50d20-126">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="50d20-126">PasswordChangeRequired</span></span>| <span data-ttu-id="50d20-127">Indica se o utilizador pode alterar a palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="50d20-127">Indicates whether the user can change the password.</span></span> <span data-ttu-id="50d20-128">Defina esta propriedade como **$true** para se certificar de que o utilizador não é possível alterar a palavra-passe e defina-o como **$false** para permitir ao utilizador alterar a palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="50d20-128">Set this property to **$true** to ensure that the user cannot change the password, and set it to **$false** to allow the user to change the password.</span></span> <span data-ttu-id="50d20-129">O valor predefinido é **$false**.</span><span class="sxs-lookup"><span data-stu-id="50d20-129">The default value is **$false**.</span></span> <span data-ttu-id="50d20-130">Esta propriedade é avaliada apenas se a conta de utilizador não existia anteriormente e está a ser criada.</span><span class="sxs-lookup"><span data-stu-id="50d20-130">This property is only evaluated if the user account did not exist previously and is being created.</span></span>|
| <span data-ttu-id="50d20-131">HomeDirectory</span><span class="sxs-lookup"><span data-stu-id="50d20-131">HomeDirectory</span></span>| <span data-ttu-id="50d20-132">O diretório de raiz para o utilizador.</span><span class="sxs-lookup"><span data-stu-id="50d20-132">The home directory for the user.</span></span>|
| <span data-ttu-id="50d20-133">GroupID</span><span class="sxs-lookup"><span data-stu-id="50d20-133">GroupID</span></span>| <span data-ttu-id="50d20-134">O ID do grupo principal para o utilizador.</span><span class="sxs-lookup"><span data-stu-id="50d20-134">The primary group ID for the user.</span></span>|
| <span data-ttu-id="50d20-135">dependsOn</span><span class="sxs-lookup"><span data-stu-id="50d20-135">DependsOn</span></span> | <span data-ttu-id="50d20-136">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="50d20-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="50d20-137">Por exemplo, se o ID do bloco de script de configuração de recursos que pretende executar primeiro é "ResourceName" e o respetivo tipo é "ResourceType", a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="50d20-137">For example, if the ID of the resource configuration script block that you want to run first is "ResourceName" and its type is "ResourceType", the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="50d20-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="50d20-138">Example</span></span>

<span data-ttu-id="50d20-139">O exemplo seguinte assegura que o utilizador "monuser" existe e se é um membro do grupo "DBusers".</span><span class="sxs-lookup"><span data-stu-id="50d20-139">The following example ensures that the user "monuser" exists and is a member of the group "DBusers".</span></span>

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