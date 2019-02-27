---
title: Escrever um Snap-in do PowerShell do Windows | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], PSSnapin example
ms.assetid: 875024f4-e02b-4416-80b9-af5e5b50aad6
caps.latest.revision: 7
ms.openlocfilehash: ee8a6538fa6ad4d0f480f2dac46fe0f823a38be8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845249"
---
# <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="9e932-102">Writing a Windows PowerShell Snap-in (Escrever um Snap-in do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="9e932-102">Writing a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="9e932-103">Este exemplo mostra como escrever um snap-in do Windows PowerShell que pode ser utilizado para registar todos os cmdlets e fornecedores de Windows PowerShell num assembly.</span><span class="sxs-lookup"><span data-stu-id="9e932-103">This example shows how to write a Windows PowerShell snap-in that can be used to register all the cmdlets and Windows PowerShell providers in an assembly.</span></span>

<span data-ttu-id="9e932-104">Com esse tipo de snap-in, não selecionar quais cmdlets e fornecedores de que pretende registar.</span><span class="sxs-lookup"><span data-stu-id="9e932-104">With this type of snap-in, you do not select which cmdlets and providers you want to register.</span></span> <span data-ttu-id="9e932-105">Para escrever um snap-in que permite-lhe selecionar o que está registado, consulte [escrever um Snap-in do PowerShell do Windows personalizada](./writing-a-custom-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="9e932-105">To write a snap-in that allows you to select what is registered, see [Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span></span>

### <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="9e932-106">Writing a Windows PowerShell Snap-in (Escrever um Snap-in do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="9e932-106">Writing a Windows PowerShell Snap-in</span></span>

1. <span data-ttu-id="9e932-107">Adicione o atributo RunInstallerAttribute.</span><span class="sxs-lookup"><span data-stu-id="9e932-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="9e932-108">Criar uma classe pública que deriva de [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) classe.</span><span class="sxs-lookup"><span data-stu-id="9e932-108">Create a public class that derives from the [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) class.</span></span>

    <span data-ttu-id="9e932-109">Neste exemplo, o nome da classe é "GetProcPSSnapIn01".</span><span class="sxs-lookup"><span data-stu-id="9e932-109">In this example, the class name is "GetProcPSSnapIn01".</span></span>

3. <span data-ttu-id="9e932-110">Adicione uma propriedade pública para o nome do snap-in (obrigatório).</span><span class="sxs-lookup"><span data-stu-id="9e932-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="9e932-111">Quando atribuir nomes snap-ins, não use nenhum dos seguintes carateres: #.</span><span class="sxs-lookup"><span data-stu-id="9e932-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="9e932-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span><span class="sxs-lookup"><span data-stu-id="9e932-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span></span> <span data-ttu-id="9e932-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="9e932-113">@ \` \*</span></span>

    <span data-ttu-id="9e932-114">Neste exemplo, o nome do snap-in é "GetProcPSSnapIn01".</span><span class="sxs-lookup"><span data-stu-id="9e932-114">In this example, the name of the snap-in is "GetProcPSSnapIn01".</span></span>

4. <span data-ttu-id="9e932-115">Adicione uma propriedade pública para o fornecedor do snap-in (obrigatório).</span><span class="sxs-lookup"><span data-stu-id="9e932-115">Add a public property for the vendor of the snap-in (required).</span></span>

    <span data-ttu-id="9e932-116">Neste exemplo, o fornecedor é "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="9e932-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="9e932-117">Adicione uma propriedade pública para o recurso do fornecedor do snap-in (opcional).</span><span class="sxs-lookup"><span data-stu-id="9e932-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

    <span data-ttu-id="9e932-118">Neste exemplo, o recurso de fornecedor é "GetProcPSSnapIn01, Microsoft".</span><span class="sxs-lookup"><span data-stu-id="9e932-118">In this example, the vendor resource is "GetProcPSSnapIn01,Microsoft".</span></span>

6. <span data-ttu-id="9e932-119">Adicione uma propriedade pública para a descrição do snap-in (obrigatório).</span><span class="sxs-lookup"><span data-stu-id="9e932-119">Add a public property for the description of the snap-in (required).</span></span>

    <span data-ttu-id="9e932-120">Neste exemplo, a descrição é "Este é um snap-in do Windows PowerShell que registra o cmdlet get-proc".</span><span class="sxs-lookup"><span data-stu-id="9e932-120">In this example, the description is "This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

7. <span data-ttu-id="9e932-121">Adicione uma propriedade pública para o recurso de descrição do snap-in (opcional).</span><span class="sxs-lookup"><span data-stu-id="9e932-121">Add a public property for the description resource of the snap-in (optional).</span></span>

    <span data-ttu-id="9e932-122">Neste exemplo, o recurso de fornecedor é "GetProcPSSnapIn01, este é um snap-in do Windows PowerShell que registra o cmdlet get-proc".</span><span class="sxs-lookup"><span data-stu-id="9e932-122">In this example, the vendor resource is "GetProcPSSnapIn01,This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

## <a name="example"></a><span data-ttu-id="9e932-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9e932-123">Example</span></span>

<span data-ttu-id="9e932-124">Este exemplo mostra como escrever um snap-in do Windows PowerShell que pode ser utilizado para registar o cmdlet Get-Proc no shell do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9e932-124">This example shows how to write a Windows PowerShell snap-in that can be used to register the Get-Proc cmdlet in the Windows PowerShell shell.</span></span> <span data-ttu-id="9e932-125">Lembre-se de que neste exemplo, o assembly completo conteria apenas a GetProcPSSnapIn01 snap-in de classe e a classe do cmdlet Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="9e932-125">Be aware that in this example, the complete assembly would contain only the GetProcPSSnapIn01 snap-in class and the Get-Proc cmdlet class.</span></span>

```csharp
[RunInstaller(true)]
public class GetProcPSSnapIn01 : PSSnapIn
{
  /// <summary>
  /// Create an instance of the GetProcPSSnapIn01 class.
  /// </summary>
  public GetProcPSSnapIn01()
         : base()
  {
  }

  /// <summary>
  /// Specify the name of the PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "GetProcPSSnapIn01";
    }
  }

  /// <summary>
  /// Specify the vendor for the PowerShell snap-in.
  /// </summary>
  public override string Vendor
  {
    get
    {
      return "Microsoft";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the vendor.
  /// Use the format: resourceBaseName,VendorName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
      return "GetProcPSSnapIn01,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the description.
  /// Use the format: resourceBaseName,Description.
  /// </summary>
  public override string DescriptionResource
  {
    get
    {
      return "GetProcPSSnapIn01,This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="9e932-126">Veja Também</span><span class="sxs-lookup"><span data-stu-id="9e932-126">See Also</span></span>

[<span data-ttu-id="9e932-127">Como registar os Cmdlets, fornecedores e alojar aplicações</span><span class="sxs-lookup"><span data-stu-id="9e932-127">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="9e932-128">Como registar os Cmdlets, fornecedores e alojar aplicações</span><span class="sxs-lookup"><span data-stu-id="9e932-128">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="9e932-129">Shell do Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="9e932-129">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
