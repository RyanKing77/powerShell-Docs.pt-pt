---
title: Métodos de processamento de entrada de cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- virtual methods (PowerShell SDK]
ms.assetid: b0bb8172-c9fa-454b-9f1b-57c3fe60671b
caps.latest.revision: 12
ms.openlocfilehash: dfaaa19fd3d4eb65a3fd335fb984a69874688f27
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850653"
---
# <a name="cmdlet-input-processing-methods"></a>Cmdlet Input Processing Methods (Métodos de Processamento de Entrada de Cmdlets)

Cmdlets tem de substituir um ou mais dos métodos descritos neste tópico para realizarem o seu trabalho a processar entrada. Esses métodos permitem que o cmdlet efetuar o pré-processamento operações de entrada operações de processamento e operações de processamento pós-cópia. Esses métodos também permitem que parar o processamento de cmdlet.

## <a name="pre-processing-tasks"></a>Tarefas de pré-processamento

Cmdlets deve substituir o [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) método adicionar quaisquer operações de pré-processamento que são válidas para todos os registos que serão processados posteriormente pelo cmdlet. Quando o Windows PowerShell processa um pipeline de comando, Windows PowerShell chama esse método uma vez para cada instância do cmdlet no pipeline. Para obter mais informações sobre como o Windows PowerShell invoca o pipeline de comando, consulte [ciclo de vida de processamento Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

O código a seguir mostra uma implementação o [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) método.

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the BeginProcessing template."
  WriteObject("This is a test of the BeginProcessing template.");
}
```

Para obter um exemplo mais detalhado de como usar o [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) método, consulte [SelectStr Tutorial](./selectstr-tutorial.md). Neste tutorial, o **selecione Str** cmdlet utiliza o [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) método para gerar a expressão regular que é utilizada para procurar a entrada de processamento de registos.

## <a name="input-processing-tasks"></a>Tarefas de processamento de entrada

Cmdlets pode substituir o [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método para processar a entrada que é enviada para o cmdlet. Quando o Windows PowerShell processa um pipeline de comando, o Windows PowerShell chama esse método para cada registo de entrada que é processado pelo cmdlet. Para obter mais informações sobre como o Windows PowerShell invoca o pipeline de comando, consulte [ciclo de vida de processamento Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).
Cmdlets pode substituir o [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método para processar a entrada que é enviada para o cmdlet. Quando o Windows PowerShell processa um pipeline de comando, o Windows PowerShell chama esse método para cada registo de entrada que é processado pelo cmdlet. Para obter mais informações sobre como o Windows PowerShell invoca o pipeline de comando, consulte [ciclo de vida de processamento Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

O código a seguir mostra uma implementação o [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método.

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the ProcessRecord template."
  WriteObject("This is a test of the ProcessRecord template.");
}
```

Para obter um exemplo mais detalhado de como usar o [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método, consulte [SelectStr Tutorial](./selectstr-tutorial.md).

## <a name="post-processing-tasks"></a>Tarefas pós-processamento

Cmdlets deve substituir o [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) método adicionar quaisquer operações de pós-processamento que são válidas para todos os registos que foram processados pelo cmdlet. Por exemplo, o seu cmdlet poderá ter de limpar a variáveis de objeto depois de terminar de processamento.

Quando o Windows PowerShell processa um pipeline de comando, Windows PowerShell chama esse método uma vez para cada instância do cmdlet no pipeline. No entanto, é importante lembrar-se de que o tempo de execução do Windows PowerShell não irá chamar o [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) método se o cmdlet é cancelado midway por meio de seu processamento de entrada ou se acabar o erro ocorre em qualquer parte do cmdlet. Por esse motivo, um cmdlet que necessita de limpeza do objeto deve implementar o concluída [System.Idisposable](/dotnet/api/System.IDisposable) padrão, incluindo um finalizador, para que o tempo de execução possa chamar ambos o [ System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) e [System.Idisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) métodos no final do processamento. Para obter mais informações sobre como o Windows PowerShell invoca o pipeline de comando, consulte [ciclo de vida de processamento Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).
Quando o Windows PowerShell processa um pipeline de comando, Windows PowerShell chama esse método uma vez para cada instância do cmdlet no pipeline. No entanto, é importante lembrar-se de que o tempo de execução do Windows PowerShell não irá chamar o [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) método se o cmdlet é cancelado midway por meio de seu processamento de entrada ou se acabar o erro ocorre em qualquer parte do cmdlet. Por esse motivo, um cmdlet que necessita de limpeza do objeto deve implementar o concluída [System.Idisposable](/dotnet/api/System.IDisposable) padrão, incluindo um finalizador, para que o tempo de execução possa chamar ambos o [ System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) e [System.Idisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) métodos no final do processamento. Para obter mais informações sobre como o Windows PowerShell invoca o pipeline de comando, consulte [ciclo de vida de processamento Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

O código a seguir mostra uma implementação o [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método.

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the EndProcessing template."
  WriteObject("This is a test of the EndProcessing template.");
}
```

Para obter um exemplo mais detalhado de como usar o [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método, consulte [SelectStr Tutorial](./selectstr-tutorial.md).

## <a name="see-also"></a>Veja Também

[System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)

[System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)

[System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)

[System.Idisposable](/dotnet/api/System.IDisposable)

[Shell do Windows PowerShell SDK](../windows-powershell-reference.md)
