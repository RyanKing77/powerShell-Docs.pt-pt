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
ms.openlocfilehash: 2fc1a3947ca6076387ea85d7f8ba9018ed7385a0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849533"
---
# <a name="how-to-write-a-cmdlet"></a><span data-ttu-id="e174e-102">Como escrever um cmdlet</span><span class="sxs-lookup"><span data-stu-id="e174e-102">How to write a cmdlet</span></span>

<span data-ttu-id="e174e-103">Este artigo mostra como escrever um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e174e-103">This article shows how to write a cmdlet.</span></span> <span data-ttu-id="e174e-104">O **Send saudação** cmdlet obtém um nome de utilizador único como entrada e, em seguida, escreve uma saudação a esse utilizador.</span><span class="sxs-lookup"><span data-stu-id="e174e-104">The **Send-Greeting** cmdlet takes a single user name as input and then writes a greeting to that user.</span></span> <span data-ttu-id="e174e-105">Embora o cmdlet não faz muito trabalho, este exemplo demonstra as secções principais de um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e174e-105">Although the cmdlet does not do much work, this example demonstrates the major sections of a cmdlet.</span></span>

## <a name="steps-to-write-a-cmdlet"></a><span data-ttu-id="e174e-106">Passos para escrever um cmdlet</span><span class="sxs-lookup"><span data-stu-id="e174e-106">Steps to write a cmdlet</span></span>

1. <span data-ttu-id="e174e-107">Para declarar a classe como um cmdlet, utilize o **Cmdlet** atributo.</span><span class="sxs-lookup"><span data-stu-id="e174e-107">To declare the class as a cmdlet, use the **Cmdlet** attribute.</span></span> <span data-ttu-id="e174e-108">O **Cmdlet** atributo especifica o verbo e substantivo para o nome do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e174e-108">The **Cmdlet** attribute specifies the verb and the noun for the cmdlet name.</span></span>

   <span data-ttu-id="e174e-109">Para obter mais informações sobre o **Cmdlet** de atributos, consulte [declaração CmdletAttribute](cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="e174e-109">For more information about the **Cmdlet** attribute, see [CmdletAttribute Declaration](cmdlet-attribute-declaration.md).</span></span>

2. <span data-ttu-id="e174e-110">Especifique o nome da classe.</span><span class="sxs-lookup"><span data-stu-id="e174e-110">Specify the name of the class.</span></span>

3. <span data-ttu-id="e174e-111">Especifique que o cmdlet deriva de qualquer uma das seguintes classes:</span><span class="sxs-lookup"><span data-stu-id="e174e-111">Specify that the cmdlet derives from either of the following classes:</span></span>

   * [<span data-ttu-id="e174e-112">System.Management.Automation.Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e174e-112">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)
   * [<span data-ttu-id="e174e-113">System.Management.Automation.PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="e174e-113">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

4. <span data-ttu-id="e174e-114">Para definir os parâmetros do cmdlet, utilize o **parâmetro** atributo.</span><span class="sxs-lookup"><span data-stu-id="e174e-114">To define the parameters for the cmdlet, use the **Parameter** attribute.</span></span> <span data-ttu-id="e174e-115">Neste caso, apenas um necessário o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="e174e-115">In this case, only one required parameter is specified.</span></span>

   <span data-ttu-id="e174e-116">Para obter mais informações sobre o **parâmetro** de atributos, consulte [ParameterAttribute declaração](parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="e174e-116">For more information about the **Parameter** attribute, see [ParameterAttribute Declaration](parameter-attribute-declaration.md).</span></span>

5. <span data-ttu-id="e174e-117">Substitua a método que processa a entrada de processamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="e174e-117">Override the input processing method that processes the input.</span></span> <span data-ttu-id="e174e-118">Neste caso, o [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método é substituído.</span><span class="sxs-lookup"><span data-stu-id="e174e-118">In this case, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden.</span></span>

6. <span data-ttu-id="e174e-119">Para escrever a saudação, utilize o método [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span><span class="sxs-lookup"><span data-stu-id="e174e-119">To write the greeting, use the method [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span></span>
   <span data-ttu-id="e174e-120">A saudação é apresentada no seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="e174e-120">The greeting is displayed in the following format:</span></span>

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a><span data-ttu-id="e174e-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e174e-121">Example</span></span>

```csharp
using System.Management.Automation;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify and
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

## <a name="see-also"></a><span data-ttu-id="e174e-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e174e-122">See also</span></span>

[<span data-ttu-id="e174e-123">System.Management.Automation.Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e174e-123">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)

[<span data-ttu-id="e174e-124">System.Management.Automation.PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="e174e-124">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

[<span data-ttu-id="e174e-125">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="e174e-125">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="e174e-126">System.Management.Automation.Cmdlet.WriteObject</span><span class="sxs-lookup"><span data-stu-id="e174e-126">System.Management.Automation.Cmdlet.WriteObject</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[<span data-ttu-id="e174e-127">Declaração CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="e174e-127">CmdletAttribute Declaration</span></span>](cmdlet-attribute-declaration.md)

[<span data-ttu-id="e174e-128">Declaração de ParameterAttribute</span><span class="sxs-lookup"><span data-stu-id="e174e-128">ParameterAttribute Declaration</span></span>](parameter-attribute-declaration.md)

[<span data-ttu-id="e174e-129">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e174e-129">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)
