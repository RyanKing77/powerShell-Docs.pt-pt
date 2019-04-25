---
title: Como criar um Snap-in do PowerShell do Windows | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], examples
ms.assetid: 71bd9b2c-5f2e-4aa8-b5fe-08c956540d37
caps.latest.revision: 10
ms.openlocfilehash: 43199544dc02ccae4b61053c30d6ed36576adfcf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067999"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a><span data-ttu-id="6c1ab-102">How to Create a Windows PowerShell Snap-in (Como Criar um Snap-in do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="6c1ab-102">How to Create a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="6c1ab-103">Um snap-in do Windows PowerShell fornece um mecanismo para registrar os conjuntos de cmdlets e outro fornecedor de Windows PowerShell com o shell, assim, expandindo a funcionalidade de shell.</span><span class="sxs-lookup"><span data-stu-id="6c1ab-103">A Windows PowerShell snap-in provides a mechanism for registering sets of cmdlets and another Windows PowerShell provider with the shell, thus extending the functionality of the shell.</span></span> <span data-ttu-id="6c1ab-104">Um snap-in do Windows PowerShell pode registar todos os cmdlets e provedores num único assembly, ou pode registar-se uma lista de cmdlets e provedores específicos.</span><span class="sxs-lookup"><span data-stu-id="6c1ab-104">A Windows PowerShell snap-in can register all the cmdlets and providers in a single assembly, or it can register a specific list of cmdlets and providers.</span></span>

<span data-ttu-id="6c1ab-105">Assemblies do snap-in devem ser instalados num diretório protegido, tal como seriam com outros sistemas operacionais.</span><span class="sxs-lookup"><span data-stu-id="6c1ab-105">Snap-in assemblies should be installed in a protected directory, just as they would be with other operating systems.</span></span> <span data-ttu-id="6c1ab-106">Caso contrário, os utilizadores mal intencionados podem substituir um assembly com código não seguro.</span><span class="sxs-lookup"><span data-stu-id="6c1ab-106">Otherwise, malicious users can replace an assembly with unsafe code.</span></span>

## <a name="windows-powershell-snap-in-classes"></a><span data-ttu-id="6c1ab-107">Classes de Snap-in do PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="6c1ab-107">Windows PowerShell Snap-in Classes</span></span>

<span data-ttu-id="6c1ab-108">Windows PowerShell todos os snap-in de classes derivar a [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) ou [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.</span><span class="sxs-lookup"><span data-stu-id="6c1ab-108">All Windows PowerShell snap-in classes derive from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.</span></span>

## <a name="examples"></a><span data-ttu-id="6c1ab-109">Exemplos</span><span class="sxs-lookup"><span data-stu-id="6c1ab-109">Examples</span></span>

<span data-ttu-id="6c1ab-110">[Escrever um Snap-in do PowerShell Windows](./writing-a-windows-powershell-snap-in.md): Este exemplo mostra como criar um snap-in que é utilizado para registar todos os cmdlets e provedores num assembly.</span><span class="sxs-lookup"><span data-stu-id="6c1ab-110">[Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md): This example shows how to create a snap-in that is used to register all the cmdlets and providers in an assembly.</span></span>

<span data-ttu-id="6c1ab-111">[Escrever um Snap-in do PowerShell do Windows personalizados](./writing-a-custom-windows-powershell-snap-in.md): Este exemplo mostra como criar um personalizada snap-in que é utilizado para registar um conjunto específico de cmdlets e provedores que poderão ou poderão não existir num único assembly.</span><span class="sxs-lookup"><span data-stu-id="6c1ab-111">[Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md): This example shows how to create a custom snap-in that is used to register a specific set of cmdlets and providers that might or might not exist in a single assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="6c1ab-112">Veja Também</span><span class="sxs-lookup"><span data-stu-id="6c1ab-112">See Also</span></span>

[<span data-ttu-id="6c1ab-113">System.Management.Automation.PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="6c1ab-113">System.Management.Automation.PSSnapIn</span></span>](/dotnet/api/System.Management.Automation.PSSnapIn)

[<span data-ttu-id="6c1ab-114">System.Management.Automation.Custompssnapin</span><span class="sxs-lookup"><span data-stu-id="6c1ab-114">System.Management.Automation.Custompssnapin</span></span>](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[<span data-ttu-id="6c1ab-115">Cmdlets de registo</span><span class="sxs-lookup"><span data-stu-id="6c1ab-115">Registering Cmdlets</span></span>](./registering-cmdlets.md)

[<span data-ttu-id="6c1ab-116">Shell do Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6c1ab-116">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
