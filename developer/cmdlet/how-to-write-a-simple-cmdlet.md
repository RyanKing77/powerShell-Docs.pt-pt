---
title: Como escrever um Simple Cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 01/15/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137543d8-0012-4cba-bcd6-98b25aac83bb
caps.latest.revision: 9
ms.openlocfilehash: 8271512d06047f3ff5e45f81d971ffe2c1f6afd7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067744"
---
# <a name="how-to-write-a-cmdlet"></a><span data-ttu-id="c90b1-102">Como escrever um cmdlet</span><span class="sxs-lookup"><span data-stu-id="c90b1-102">How to write a cmdlet</span></span>

<span data-ttu-id="c90b1-103">Este artigo mostra como escrever um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c90b1-103">This article shows how to write a cmdlet.</span></span> <span data-ttu-id="c90b1-104">O `Send-Greeting` cmdlet obtém um nome de utilizador único como entrada e, em seguida, escreve uma saudação a esse utilizador.</span><span class="sxs-lookup"><span data-stu-id="c90b1-104">The `Send-Greeting` cmdlet takes a single user name as input and then writes a greeting to that user.</span></span> <span data-ttu-id="c90b1-105">Embora o cmdlet não faz muito trabalho, este exemplo demonstra as secções principais de um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c90b1-105">Although the cmdlet does not do much work, this example demonstrates the major sections of a cmdlet.</span></span>

## <a name="steps-to-write-a-cmdlet"></a><span data-ttu-id="c90b1-106">Passos para escrever um cmdlet</span><span class="sxs-lookup"><span data-stu-id="c90b1-106">Steps to write a cmdlet</span></span>

1. <span data-ttu-id="c90b1-107">Para declarar a classe como um cmdlet, utilize o **Cmdlet** atributo.</span><span class="sxs-lookup"><span data-stu-id="c90b1-107">To declare the class as a cmdlet, use the **Cmdlet** attribute.</span></span> <span data-ttu-id="c90b1-108">O **Cmdlet** atributo especifica o verbo e substantivo para o nome do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c90b1-108">The **Cmdlet** attribute specifies the verb and the noun for the cmdlet name.</span></span>

   <span data-ttu-id="c90b1-109">Para obter mais informações sobre o **Cmdlet** de atributos, consulte [declaração CmdletAttribute](cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c90b1-109">For more information about the **Cmdlet** attribute, see [CmdletAttribute Declaration](cmdlet-attribute-declaration.md).</span></span>

2. <span data-ttu-id="c90b1-110">Especifique o nome da classe.</span><span class="sxs-lookup"><span data-stu-id="c90b1-110">Specify the name of the class.</span></span>

3. <span data-ttu-id="c90b1-111">Especifique que o cmdlet deriva de qualquer uma das seguintes classes:</span><span class="sxs-lookup"><span data-stu-id="c90b1-111">Specify that the cmdlet derives from either of the following classes:</span></span>

   * [<span data-ttu-id="c90b1-112">System.Management.Automation.Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c90b1-112">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)
   * [<span data-ttu-id="c90b1-113">System.Management.Automation.PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="c90b1-113">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

4. <span data-ttu-id="c90b1-114">Para definir os parâmetros do cmdlet, utilize o **parâmetro** atributo.</span><span class="sxs-lookup"><span data-stu-id="c90b1-114">To define the parameters for the cmdlet, use the **Parameter** attribute.</span></span> <span data-ttu-id="c90b1-115">Neste caso, apenas um necessário o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="c90b1-115">In this case, only one required parameter is specified.</span></span>

   <span data-ttu-id="c90b1-116">Para obter mais informações sobre o **parâmetro** de atributos, consulte [ParameterAttribute declaração](parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c90b1-116">For more information about the **Parameter** attribute, see [ParameterAttribute Declaration](parameter-attribute-declaration.md).</span></span>

5. <span data-ttu-id="c90b1-117">Substitua a método que processa a entrada de processamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="c90b1-117">Override the input processing method that processes the input.</span></span> <span data-ttu-id="c90b1-118">Neste caso, o [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método é substituído.</span><span class="sxs-lookup"><span data-stu-id="c90b1-118">In this case, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden.</span></span>

6. <span data-ttu-id="c90b1-119">Para escrever a saudação, utilize o método [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span><span class="sxs-lookup"><span data-stu-id="c90b1-119">To write the greeting, use the method [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span></span>
   <span data-ttu-id="c90b1-120">A saudação é apresentada no seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="c90b1-120">The greeting is displayed in the following format:</span></span>

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a><span data-ttu-id="c90b1-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c90b1-121">Example</span></span>

```csharp
using System.Management.Automation;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify the
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory=true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="c90b1-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c90b1-122">See also</span></span>

[<span data-ttu-id="c90b1-123">System.Management.Automation.Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c90b1-123">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)

[<span data-ttu-id="c90b1-124">System.Management.Automation.PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="c90b1-124">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

[<span data-ttu-id="c90b1-125">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="c90b1-125">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="c90b1-126">System.Management.Automation.Cmdlet.WriteObject</span><span class="sxs-lookup"><span data-stu-id="c90b1-126">System.Management.Automation.Cmdlet.WriteObject</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[<span data-ttu-id="c90b1-127">Declaração CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="c90b1-127">CmdletAttribute Declaration</span></span>](cmdlet-attribute-declaration.md)

[<span data-ttu-id="c90b1-128">Declaração de ParameterAttribute</span><span class="sxs-lookup"><span data-stu-id="c90b1-128">ParameterAttribute Declaration</span></span>](parameter-attribute-declaration.md)

[<span data-ttu-id="c90b1-129">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c90b1-129">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)