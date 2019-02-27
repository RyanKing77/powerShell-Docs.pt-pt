---
title: Escrever um Snap-in do PowerShell do Windows personalizados | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], custom PSSnapin example
- cmdlets [PowerShell SDK], specified in snap-ins
ms.assetid: 55c8b5cb-8ee2-4080-afc4-3f09c9f20128
caps.latest.revision: 6
ms.openlocfilehash: 20b7fdce1d31e3dee4598a7595962fca1c99d80a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851955"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a><span data-ttu-id="77698-102">Writing a Custom Windows PowerShell Snap-in (Escrever um Snap-in Personalizado do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="77698-102">Writing a Custom Windows PowerShell Snap-in</span></span>

<span data-ttu-id="77698-103">Este exemplo mostra como escrever um snap-in do Windows PowerShell que registra cmdlets específicos.</span><span class="sxs-lookup"><span data-stu-id="77698-103">This example shows how to write a Windows PowerShell snap-in that registers specific cmdlets.</span></span>

<span data-ttu-id="77698-104">Com esse tipo de snap-in, especifique quais cmdlets, fornecedores, tipos ou formatos para se registar.</span><span class="sxs-lookup"><span data-stu-id="77698-104">With this type of snap-in, you specify which cmdlets, providers, types, or formats to register.</span></span> <span data-ttu-id="77698-105">Para obter mais informações sobre como escrever um snap-in que registra todos os cmdlets e provedores num assembly, consulte [escrever um Snap-in do PowerShell Windows](./writing-a-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="77698-105">For more information about how to write a snap-in that registers all the cmdlets and providers in an assembly, see [Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md).</span></span>

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a><span data-ttu-id="77698-106">Para escrever um Snap-in do PowerShell do Windows, que registra cmdlets específicos.</span><span class="sxs-lookup"><span data-stu-id="77698-106">To write a Windows PowerShell Snap-in that registers specific cmdlets.</span></span>

1. <span data-ttu-id="77698-107">Adicione o atributo RunInstallerAttribute.</span><span class="sxs-lookup"><span data-stu-id="77698-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="77698-108">Criar uma classe pública que deriva de [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classe.</span><span class="sxs-lookup"><span data-stu-id="77698-108">Create a public class that derives from the [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class.</span></span>

   <span data-ttu-id="77698-109">Neste exemplo, o nome da classe é "CustomPSSnapinTest".</span><span class="sxs-lookup"><span data-stu-id="77698-109">In this example, the class name is "CustomPSSnapinTest".</span></span>

3. <span data-ttu-id="77698-110">Adicione uma propriedade pública para o nome do snap-in (obrigatório).</span><span class="sxs-lookup"><span data-stu-id="77698-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="77698-111">Quando atribuir nomes snap-ins, não use nenhum dos seguintes carateres: #.</span><span class="sxs-lookup"><span data-stu-id="77698-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="77698-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ?</span><span class="sxs-lookup"><span data-stu-id="77698-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ?</span></span> <span data-ttu-id="77698-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="77698-113">@ \` \*</span></span>

   <span data-ttu-id="77698-114">Neste exemplo, o nome do snap-in é "CustomPSSnapInTest".</span><span class="sxs-lookup"><span data-stu-id="77698-114">In this example, the name of the snap-in is "CustomPSSnapInTest".</span></span>

4. <span data-ttu-id="77698-115">Adicione uma propriedade pública para o fornecedor do snap-in (obrigatório).</span><span class="sxs-lookup"><span data-stu-id="77698-115">Add a public property for the vendor of the snap-in (required).</span></span>

   <span data-ttu-id="77698-116">Neste exemplo, o fornecedor é "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="77698-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="77698-117">Adicione uma propriedade pública para o recurso do fornecedor do snap-in (opcional).</span><span class="sxs-lookup"><span data-stu-id="77698-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

   <span data-ttu-id="77698-118">Neste exemplo, o recurso de fornecedor é "CustomPSSnapInTest, Microsoft".</span><span class="sxs-lookup"><span data-stu-id="77698-118">In this example, the vendor resource is "CustomPSSnapInTest,Microsoft".</span></span>

6. <span data-ttu-id="77698-119">Adicione uma propriedade pública para a descrição do snap-in (obrigatório).</span><span class="sxs-lookup"><span data-stu-id="77698-119">Add a public property for the description of the snap-in (required).</span></span>

   <span data-ttu-id="77698-120">Neste exemplo, a descrição é: "Este é um personalizado Windows PowerShell snap-in que inclui os cmdlets de teste CustomSnapinTest e teste-HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="77698-120">In this example, the description is: "This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

7. <span data-ttu-id="77698-121">Adicione uma propriedade pública para o recurso de descrição do snap-in (opcional).</span><span class="sxs-lookup"><span data-stu-id="77698-121">Add a public property for the description resource of the snap-in (optional).</span></span>

   <span data-ttu-id="77698-122">Neste exemplo, o recurso de fornecedor é "CustomPSSnapInTest, este é um personalizado Windows PowerShell snap-in que inclui os cmdlets de teste-HelloWorld e CustomSnapinTest de teste".</span><span class="sxs-lookup"><span data-stu-id="77698-122">In this example, the vendor resource is "CustomPSSnapInTest, This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

8. <span data-ttu-id="77698-123">Especifique os cmdlets que pertencem ao personalizado snap-in (opcional) com o [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) classe.</span><span class="sxs-lookup"><span data-stu-id="77698-123">Specify the cmdlets that belong to the custom snap-in (optional) using the [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) class.</span></span> <span data-ttu-id="77698-124">As informações adicionadas aqui incluem o nome do cmdlet, seu tipo de .NET e o nome de ficheiro de ajuda do cmdlet (o formato do nome de ficheiro de ajuda do cmdlet deve ser name.dll help.xml).</span><span class="sxs-lookup"><span data-stu-id="77698-124">The information added here includes the name of the cmdlet, its .NET type, and the cmdlet Help file name (the format of the cmdlet Help file name should be name.dll-help.xml).</span></span>

   <span data-ttu-id="77698-125">Este exemplo adiciona os cmdlets de teste-HelloWorld e TestCustomSnapinTest.</span><span class="sxs-lookup"><span data-stu-id="77698-125">This example adds the Test-HelloWorld and TestCustomSnapinTest cmdlets.</span></span>

9. <span data-ttu-id="77698-126">Especifica os provedores que pertencem ao personalizado snap-in (opcional).</span><span class="sxs-lookup"><span data-stu-id="77698-126">Specify the providers that belong to the custom snap-in (optional).</span></span>

   <span data-ttu-id="77698-127">Neste exemplo não especifique quaisquer fornecedores.</span><span class="sxs-lookup"><span data-stu-id="77698-127">This example does not specify any providers.</span></span>

10. <span data-ttu-id="77698-128">Especifica os tipos que pertencem ao personalizado snap-in (opcional).</span><span class="sxs-lookup"><span data-stu-id="77698-128">Specify the types that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="77698-129">Neste exemplo não especifica todos os tipos.</span><span class="sxs-lookup"><span data-stu-id="77698-129">This example does not specify any types.</span></span>

11. <span data-ttu-id="77698-130">Especifique os formatos que pertencem ao personalizado snap-in (opcional).</span><span class="sxs-lookup"><span data-stu-id="77698-130">Specify the formats that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="77698-131">Neste exemplo não especifique quaisquer formatos.</span><span class="sxs-lookup"><span data-stu-id="77698-131">This example does not specify any formats.</span></span>

## <a name="example"></a><span data-ttu-id="77698-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="77698-132">Example</span></span>

<span data-ttu-id="77698-133">Este exemplo mostra como escrever um snap-in personalizado Windows PowerShell que pode ser utilizado para registar os cmdlets de teste CustomSnapinTest e teste-HelloWorld.</span><span class="sxs-lookup"><span data-stu-id="77698-133">This example shows how to write a Custom Windows PowerShell snap-in that can be used to register the Test-HelloWorld and Test-CustomSnapinTest cmdlets.</span></span> <span data-ttu-id="77698-134">Lembre-se de que neste exemplo, o assembly completo pode conter outros cmdlets e fornecedores que não poderiam ser registados por este snap-in.</span><span class="sxs-lookup"><span data-stu-id="77698-134">Be aware that in this example, the complete assembly could contain other cmdlets and providers that would not be registered by this snap-in.</span></span>

```csharp
[RunInstaller(true)]
public class CustomPSSnapinTest : CustomPSSnapIn
{
  /// <summary>
  /// Creates an instance of CustomPSSnapInTest class.
  /// </summary>
  public CustomPSSnapinTest()
          : base()
  {
  }

  /// <summary>
  /// Specify the name of the custom PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "CustomPSSnapInTest";
    }
  }

  /// <summary>
  /// Specify the vendor for the custom PowerShell snap-in.
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
  /// Use the format: resourceBaseName,resourceName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
        return "CustomPSSnapInTest,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the custom PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
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
        return "CustomPSSnapInTest,This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
    }
  }

  /// <summary>
  /// Specify the cmdlets that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<CmdletConfigurationEntry> _cmdlets;
  public override Collection<CmdletConfigurationEntry> Cmdlets
  {
    get
    {
      if (_cmdlets == null)
      {
        _cmdlets = new Collection<CmdletConfigurationEntry>();
        _cmdlets.Add(new CmdletConfigurationEntry("test-customsnapintest", typeof(TestCustomSnapinTest), "TestCmdletHelp.dll-help.xml"));
        _cmdlets.Add(new CmdletConfigurationEntry("test-helloworld", typeof(TestHelloWorld), "HelloWorldHelp.dll-help.xml"));
      }

      return _cmdlets;
    }
  }

  /// <summary>
  /// Specify the providers that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<ProviderConfigurationEntry> _providers;
  public override Collection<ProviderConfigurationEntry> Providers
  {
    get
    {
      if (_providers == null)
      {
        _providers = new Collection<ProviderConfigurationEntry>();
      }

      return _providers;
    }
  }

  /// <summary>
  /// Specify the types that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<TypeConfigurationEntry> _types;
  public override Collection<TypeConfigurationEntry> Types
  {
    get
    {
      if (_types == null)
      {
        _types = new Collection<TypeConfigurationEntry>();
      }

      return _types;
    }
  }

  /// <summary>
  /// Specify the formats that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<FormatConfigurationEntry> _formats;
  public override Collection<FormatConfigurationEntry> Formats
  {
    get
    {
      if (_formats == null)
      {
        _formats = new Collection<FormatConfigurationEntry>();
      }

      return _formats;
    }
  }
}
```

<span data-ttu-id="77698-135">Para obter mais informações sobre como registar o snap-ins, consulte [como registrar Cmdlets, fornecedores e alojar aplicações](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) no [Guia do programador do Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md).</span><span class="sxs-lookup"><span data-stu-id="77698-135">For more information about registering snap-ins, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) in the [Windows PowerShell Programmer's Guide](../prog-guide/windows-powershell-programmer-s-guide.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="77698-136">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="77698-136">See Also</span></span>

[<span data-ttu-id="77698-137">Como registar os Cmdlets, fornecedores e alojar aplicações</span><span class="sxs-lookup"><span data-stu-id="77698-137">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="77698-138">Como registar os Cmdlets, fornecedores e alojar aplicações</span><span class="sxs-lookup"><span data-stu-id="77698-138">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="77698-139">Shell do Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="77698-139">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
