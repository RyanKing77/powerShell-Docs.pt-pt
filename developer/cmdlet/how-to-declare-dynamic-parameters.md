---
title: Como declarar parâmetros dinâmicos | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db04f1df-def5-4456-8869-336024cda723
caps.latest.revision: 8
ms.openlocfilehash: a9c530cdc66302eb6b3d9d2b284eeb486c3b2ba9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847972"
---
# <a name="how-to-declare-dynamic-parameters"></a>How to Declare Dynamic Parameters (Como Declarar Parâmetros Dinâmicos)

Este exemplo mostra como definir parâmetros dinâmicos que são adicionados ao cmdlet em tempo de execução. Neste exemplo, o `Department` parâmetro é adicionado ao cmdlet sempre que o utilizador Especifica os `Employee` mudar o parâmetro. Para obter mais informações sobre parâmetros dinâmicos, consulte [parâmetros dinâmicos de Cmdlet](./cmdlet-dynamic-parameters.md).

## <a name="to-define-dynamic-parameters"></a>Para definir os parâmetros dinâmicos

1. Na declaração da classe cmdlet, adicione a [System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) interface conforme mostrado.

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. Chamar o [System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) método, que retorna o objeto no qual os parâmetros dinâmicos são definidos. Neste exemplo, o método é chamado quando o `Employee` parâmetro for especificado.

   ```csharp
   public object GetDynamicParameters()
   {
       if (employee)
       {
         context= new SendGreetingCommandDynamicParameters();
         return context;
       }
       return null;
   }
   private SendGreetingCommandDynamicParameters context;
   ```

3. Declare uma classe que define os parâmetros dinâmicos para ser adicionado. Pode usar os atributos que utilizou para declarar os parâmetros do cmdlet estático para declarar parâmetros dinâmicos.

   ```csharp
   public class SendGreetingCommandDynamicParameters
   {
     [Parameter]
     [ValidateSet ("Marketing", "Sales", "Development")]
     public string Department
     {
       get { return department; }
       set { department = value; }
     }
     private string department;
   }
   ```

## <a name="example"></a>Exemplo

Neste exemplo, o `Department` adicionado o parâmetro sempre que o utilizador Especifica os `Employee` parâmetro. O `Department` parâmetro é um parâmetro opcional, e o atributo ValidateSet é utilizado para especificar os argumentos permitidos.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;     // PowerShell assembly.

namespace SendGreeting
{
  // Declare the cmdlet class that supports the
  // IDynamicParameters interface.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet, IDynamicParameters
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    [Parameter]
    [Alias ("FTE")]
    public SwitchParameter Employee
    {
      get { return employee; }
      set { employee = value; }
    }
    private Boolean employee;

    // Implement GetDynamicParameters to
    // retrieve the dynamic parameter.
    public object GetDynamicParameters()
    {
      if (employee)
      {
        context= new SendGreetingCommandDynamicParameters();
        return context;
      }
      return null;
   }
   private SendGreetingCommandDynamicParameters context;

    // Overide the ProcessRecord method to process the
    // supplied user name and write out a greeting to
    // the user by calling the WriteObject method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "! ");
      if (employee)
      {
        WriteObject("Department: " + context.Department);
      }
    }
  }

  // Define the dynamic parameters to be added
  public class SendGreetingCommandDynamicParameters
  {
    [Parameter]
    [ValidateSet ("Marketing", "Sales", "Development")]
    public string Department
    {
      get { return department; }
      set { department = value; }
    }
    private string department;
  }
}
```

## <a name="see-also"></a>Veja Também

[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Parâmetros de cmdlet dinâmico](./cmdlet-dynamic-parameters.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)