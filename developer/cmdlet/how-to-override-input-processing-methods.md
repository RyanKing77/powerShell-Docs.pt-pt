---
title: Como substituir os métodos de processamento de entrada | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: eff40a01b60985788ae0e21156fec7ec4e27fcf1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846754"
---
# <a name="how-to-override-input-processing-methods"></a>How to Override Input Processing Methods (Como Substituir Métodos de Processamento de Entrada)

Estes exemplos mostram como substituir a entrada métodos dentro de um cmdlet de processamento. Esses métodos são utilizados para efetuar as seguintes operações:

- O [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método é usado para realizar operações de inicialização única que são válidas para todos os objetos processados pelo cmdlet. O tempo de execução do Windows PowerShell chama esse método apenas uma vez.

- O [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método é usado para processar objetos passados para o cmdlet. O tempo de execução do Windows PowerShell chama esse método para cada objeto passado para o cmdlet.

- O [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método é usado para realizar operações de processamento de postagem de uso individual. O tempo de execução do Windows PowerShell chama esse método apenas uma vez.

## <a name="to-override-the-beginprocessing-method"></a>Substituir o método BeginProcessing

- Declarar uma substituição protegida do [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método.

A seguinte classe imprime uma mensagem de exemplo. Para usar essa classe, altere o verbo e substantivo no atributo de Cmdlet, altere o nome da classe para refletir o novo verbo e substantivo e, em seguida, adicione a funcionalidade necessária para a substituição do [System.Management.Automation.Cmdlet.Beginprocessing ](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "BeginProcessingClass")]
public class TestBeginProcessingClassTemplate : Cmdlet
{
  // Override the BeginProcessing method to add preprocessing
  //operations to the cmdlet.
  protected override void BeginProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the BeginProcessing template.");
  }
}
```

## <a name="to-override-the-processrecord-method"></a>Substituir o método ProcessRecord

- Declarar uma substituição protegida do [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.

A seguinte classe imprime uma mensagem de exemplo. Para usar essa classe, altere o verbo e substantivo no atributo de Cmdlet, altere o nome da classe para refletir o novo verbo e substantivo e, em seguida, adicione a funcionalidade necessária para a substituição do [System.Management.Automation.Cmdlet.Processrecord* ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "ProcessRecordClass")]
public class TestProcessRecordClassTemplate : Cmdlet
{
    // Override the ProcessRecord method to add processing
    //operations to the cmdlet.
    protected override void ProcessRecord()
    {
        // Replace the WriteObject method with the logic required
        // by your cmdlet. It is used here to generate the following
        // output:
        // "This is a test of the ProcessRecord template."
        WriteObject("This is a test of the ProcessRecord template.");
    }
}

```

## <a name="to-override-the-endprocessing-method"></a>Substituir o método EndProcessing

- Declarar uma substituição protegida do [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método.

A seguinte classe imprime um exemplo. Para usar essa classe, altere o verbo e substantivo no atributo de Cmdlet, altere o nome da classe para refletir o novo verbo e substantivo e, em seguida, adicione a funcionalidade necessária para a substituição do [System.Management.Automation.Cmdlet.Endprocessing* ](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "EndProcessingClass")]
public class TestEndProcessingClassTemplate : Cmdlet
{
  // Override the EndProcessing method to add postprocessing
  //operations to the cmdlet.
  protected override void EndProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the EndProcessing template.");
  }
}
```

## <a name="see-also"></a>Veja Também

[System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
