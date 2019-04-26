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
# <a name="how-to-write-a-cmdlet"></a>Como escrever um cmdlet

Este artigo mostra como escrever um cmdlet. O `Send-Greeting` cmdlet obtém um nome de utilizador único como entrada e, em seguida, escreve uma saudação a esse utilizador. Embora o cmdlet não faz muito trabalho, este exemplo demonstra as secções principais de um cmdlet.

## <a name="steps-to-write-a-cmdlet"></a>Passos para escrever um cmdlet

1. Para declarar a classe como um cmdlet, utilize o **Cmdlet** atributo. O **Cmdlet** atributo especifica o verbo e substantivo para o nome do cmdlet.

   Para obter mais informações sobre o **Cmdlet** de atributos, consulte [declaração CmdletAttribute](cmdlet-attribute-declaration.md).

2. Especifique o nome da classe.

3. Especifique que o cmdlet deriva de qualquer uma das seguintes classes:

   * [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)
   * [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

4. Para definir os parâmetros do cmdlet, utilize o **parâmetro** atributo. Neste caso, apenas um necessário o parâmetro for especificado.

   Para obter mais informações sobre o **parâmetro** de atributos, consulte [ParameterAttribute declaração](parameter-attribute-declaration.md).

5. Substitua a método que processa a entrada de processamento de entrada. Neste caso, o [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método é substituído.

6. Para escrever a saudação, utilize o método [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).
   A saudação é apresentada no seguinte formato:

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a>Exemplo

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

## <a name="see-also"></a>Consulte também

[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)

[System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[Declaração CmdletAttribute](cmdlet-attribute-declaration.md)

[Declaração de ParameterAttribute](parameter-attribute-declaration.md)

[Escrever um Cmdlet do Windows PowerShell](writing-a-windows-powershell-cmdlet.md)