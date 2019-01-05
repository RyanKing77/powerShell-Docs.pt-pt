---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: DSC para Linux nxSshAuthorizedKeys recursos
ms.openlocfilehash: d4cdb727a94a5e89e8401769f24977d49bcf4929
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048816"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a><span data-ttu-id="02d25-103">DSC para Linux nxSshAuthorizedKeys recursos</span><span class="sxs-lookup"><span data-stu-id="02d25-103">DSC for Linux nxSshAuthorizedKeys Resource</span></span>

<span data-ttu-id="02d25-104">O **nxAuthorizedKeys** recursos no PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir autorizado ssh chaves para um utilizador especificado.</span><span class="sxs-lookup"><span data-stu-id="02d25-104">The **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage authorized ssh keys for a specified user.</span></span>

## <a name="syntax"></a><span data-ttu-id="02d25-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="02d25-105">Syntax</span></span>

```
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="02d25-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="02d25-106">Properties</span></span>

|  <span data-ttu-id="02d25-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="02d25-107">Property</span></span> |  <span data-ttu-id="02d25-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="02d25-108">Description</span></span> |
|---|---|
| <span data-ttu-id="02d25-109">KeyComment</span><span class="sxs-lookup"><span data-stu-id="02d25-109">KeyComment</span></span>| <span data-ttu-id="02d25-110">Um comentário exclusivo para a chave.</span><span class="sxs-lookup"><span data-stu-id="02d25-110">A unique comment for the key.</span></span> <span data-ttu-id="02d25-111">Isto é utilizado para identificar exclusivamente as chaves.</span><span class="sxs-lookup"><span data-stu-id="02d25-111">This is used to uniquely identify keys.</span></span>|
| <span data-ttu-id="02d25-112">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="02d25-112">Ensure</span></span>| <span data-ttu-id="02d25-113">Especifica se a chave está definida.</span><span class="sxs-lookup"><span data-stu-id="02d25-113">Specifies whether the key is defined.</span></span> <span data-ttu-id="02d25-114">Defina esta propriedade para "Ausente", certifique-se de que a chave não existir no ficheiro de chaves autorizado do utilizador.</span><span class="sxs-lookup"><span data-stu-id="02d25-114">Set this property to "Absent" to ensure the key does not exist in the user’s authorized keys file.</span></span> <span data-ttu-id="02d25-115">Defini-lo como "Presente" para garantir que a chave é definida no ficheiro de chave autorizados do utilizador.</span><span class="sxs-lookup"><span data-stu-id="02d25-115">Set it to "Present" to ensure the key is defined in the user’s authorized key file.</span></span>|
| <span data-ttu-id="02d25-116">Nome de utilizador</span><span class="sxs-lookup"><span data-stu-id="02d25-116">Username</span></span>| <span data-ttu-id="02d25-117">O nome de utilizador para gerir ssh autorizado chaves para.</span><span class="sxs-lookup"><span data-stu-id="02d25-117">The username to manage ssh authorized keys for.</span></span> <span data-ttu-id="02d25-118">Se não definido, o utilizador predefinido é "raiz".</span><span class="sxs-lookup"><span data-stu-id="02d25-118">If not defined, the default user is "root".</span></span>|
| <span data-ttu-id="02d25-119">Tecla</span><span class="sxs-lookup"><span data-stu-id="02d25-119">Key</span></span>| <span data-ttu-id="02d25-120">O conteúdo da chave.</span><span class="sxs-lookup"><span data-stu-id="02d25-120">The contents of the key.</span></span> <span data-ttu-id="02d25-121">Isto é necessário se **Certifique-se** está definido como "Presente".</span><span class="sxs-lookup"><span data-stu-id="02d25-121">This is required if **Ensure** is set to "Present".</span></span>|
| <span data-ttu-id="02d25-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="02d25-122">DependsOn</span></span> | <span data-ttu-id="02d25-123">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="02d25-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="02d25-124">Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e seu tipo é **ResourceType**, a sintaxe para usar isso a propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="02d25-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="02d25-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="02d25-125">Example</span></span>

<span data-ttu-id="02d25-126">O exemplo seguinte define uma pública ssh autorizada chave para o utilizador "monuser".</span><span class="sxs-lookup"><span data-stu-id="02d25-126">The following example defines a public ssh authorized key for the user "monuser".</span></span>

```
Import-DSCResource -Module nx

Node $node {

nxSshAuthorizedKeys myKey{
   KeyComment = "myKey"
   Ensure = "Present"
   Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
   UserName = "monuser"
}
}
```