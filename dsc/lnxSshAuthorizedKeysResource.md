---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: DSC de Linux nxSshAuthorizedKeys recursos
ms.openlocfilehash: f48ecec39ffe24cee99ca08ad9d050b36c5e04bf
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a><span data-ttu-id="0d13b-103">DSC de Linux nxSshAuthorizedKeys recursos</span><span class="sxs-lookup"><span data-stu-id="0d13b-103">DSC for Linux nxSshAuthorizedKeys Resource</span></span>

<span data-ttu-id="0d13b-104">O **nxAuthorizedKeys** recursos no PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir autorizado ssh chaves para um utilizador especificado.</span><span class="sxs-lookup"><span data-stu-id="0d13b-104">The **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage authorized ssh keys for a specified user.</span></span>

## <a name="syntax"></a><span data-ttu-id="0d13b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d13b-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="0d13b-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="0d13b-106">Properties</span></span>

|  <span data-ttu-id="0d13b-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="0d13b-107">Property</span></span> |  <span data-ttu-id="0d13b-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d13b-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="0d13b-109">KeyComment</span><span class="sxs-lookup"><span data-stu-id="0d13b-109">KeyComment</span></span>| <span data-ttu-id="0d13b-110">Um comentário exclusivo para a chave.</span><span class="sxs-lookup"><span data-stu-id="0d13b-110">A unique comment for the key.</span></span> <span data-ttu-id="0d13b-111">Isto é utilizado para identificar exclusivamente chaves.</span><span class="sxs-lookup"><span data-stu-id="0d13b-111">This is used to uniquely identify keys.</span></span>| 
| <span data-ttu-id="0d13b-112">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="0d13b-112">Ensure</span></span>| <span data-ttu-id="0d13b-113">Especifica se a chave está definida.</span><span class="sxs-lookup"><span data-stu-id="0d13b-113">Specifies whether the key is defined.</span></span> <span data-ttu-id="0d13b-114">Defina esta propriedade para "Ausente", certifique-se de que a chave não existe no ficheiro de chaves autorizados do utilizador.</span><span class="sxs-lookup"><span data-stu-id="0d13b-114">Set this property to "Absent" to ensure the key does not exist in the user’s authorized keys file.</span></span> <span data-ttu-id="0d13b-115">Defina-o para "Presente" para garantir que a chave está definida no ficheiro de chave autorizados do utilizador.</span><span class="sxs-lookup"><span data-stu-id="0d13b-115">Set it to "Present" to ensure the key is defined in the user’s authorized key file.</span></span>| 
| <span data-ttu-id="0d13b-116">Nome de utilizador</span><span class="sxs-lookup"><span data-stu-id="0d13b-116">Username</span></span>| <span data-ttu-id="0d13b-117">O nome de utilizador para gerir ssh autorizado chaves para.</span><span class="sxs-lookup"><span data-stu-id="0d13b-117">The username to manage ssh authorized keys for.</span></span> <span data-ttu-id="0d13b-118">Se não definido, o utilizador predefinido é de "raiz".</span><span class="sxs-lookup"><span data-stu-id="0d13b-118">If not defined, the default user is "root".</span></span>| 
| <span data-ttu-id="0d13b-119">Tecla</span><span class="sxs-lookup"><span data-stu-id="0d13b-119">Key</span></span>| <span data-ttu-id="0d13b-120">O conteúdo da chave.</span><span class="sxs-lookup"><span data-stu-id="0d13b-120">The contents of the key.</span></span> <span data-ttu-id="0d13b-121">Isto é necessário se **Certifique-se** está definido como "Apresente".</span><span class="sxs-lookup"><span data-stu-id="0d13b-121">This is required if **Ensure** is set to "Present".</span></span>| 
| <span data-ttu-id="0d13b-122">dependsOn</span><span class="sxs-lookup"><span data-stu-id="0d13b-122">DependsOn</span></span> | <span data-ttu-id="0d13b-123">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="0d13b-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0d13b-124">Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e o respetivo tipo é **ResourceType**, a sintaxe para utilizar esta a propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="0d13b-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="0d13b-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d13b-125">Example</span></span>

<span data-ttu-id="0d13b-126">O exemplo seguinte define um público ssh autorizado chave para o utilizador "monuser".</span><span class="sxs-lookup"><span data-stu-id="0d13b-126">The following example defines a public ssh authorized key for the user "monuser".</span></span>

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

