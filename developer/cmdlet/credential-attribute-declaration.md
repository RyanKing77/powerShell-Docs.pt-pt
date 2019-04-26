---
title: Declaração de atributo de credenciais | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: 49a62ccb09f06f77862d4737199e58293e7fbe0a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068322"
---
# <a name="credential-attribute-declaration"></a><span data-ttu-id="9158a-102">Credential Attribute Declaration (Declaração do Atributo Credential)</span><span class="sxs-lookup"><span data-stu-id="9158a-102">Credential Attribute Declaration</span></span>

<span data-ttu-id="9158a-103">O atributo de credencial é um atributo opcional que pode ser utilizado com parâmetros de credencial do tipo [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) para que uma cadeia de caracteres também pode ser passada como um argumento para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9158a-103">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="9158a-104">Quando esse atributo é adicionado a uma declaração de parâmetro, o Windows PowerShell converte a entrada de cadeia de caracteres num [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) objeto.</span><span class="sxs-lookup"><span data-stu-id="9158a-104">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="9158a-105">Por exemplo, o [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet utiliza este atributo para ter o PowerShell de Windows gerar a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) objeto devolvido pelo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9158a-105">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="9158a-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9158a-106">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="9158a-107">Observações</span><span class="sxs-lookup"><span data-stu-id="9158a-107">Remarks</span></span>

- <span data-ttu-id="9158a-108">Normalmente, este atributo é utilizado por parâmetros do tipo [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) para que uma cadeia de caracteres também pode ser passada como um argumento para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9158a-108">Typically this attribute is used by parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="9158a-109">Quando um [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) objeto é passado para o parâmetro, o Windows PowerShell não faz nada.</span><span class="sxs-lookup"><span data-stu-id="9158a-109">When a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="9158a-110">Ao criar o [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) objeto, o Windows PowerShell utiliza o anfitrião atual para exibir as instruções adequadas para o usuário.</span><span class="sxs-lookup"><span data-stu-id="9158a-110">When creating the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="9158a-111">Por exemplo, a predefinição o Host apresenta um aviso para um nome de utilizador e palavra-passe quando este atributo é utilizado.</span><span class="sxs-lookup"><span data-stu-id="9158a-111">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="9158a-112">No entanto, se está a ser utilizado um host personalizado que define uma linha de comandos diferente, em seguida, seria exibida nessa linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="9158a-112">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="9158a-113">Este atributo é utilizado com o atributo de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9158a-113">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="9158a-114">Para obter mais informações sobre esse atributo, consulte [declaração de atributo de parâmetro](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="9158a-114">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="9158a-115">O atributo de credencial é definido pela [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="9158a-115">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="9158a-116">Veja Também</span><span class="sxs-lookup"><span data-stu-id="9158a-116">See Also</span></span>

[<span data-ttu-id="9158a-117">Aliases de parâmetro</span><span class="sxs-lookup"><span data-stu-id="9158a-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="9158a-118">Declaração de atributo de parâmetro</span><span class="sxs-lookup"><span data-stu-id="9158a-118">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="9158a-119">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9158a-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
