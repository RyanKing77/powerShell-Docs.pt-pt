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
ms.openlocfilehash: 7f8d25e03707052b1d5b62e245caae360da11d0b
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794948"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="17896-102">Cmdlet Input Processing Methods (Métodos de Processamento de Entrada de Cmdlets)</span><span class="sxs-lookup"><span data-stu-id="17896-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="17896-103">Cmdlets tem de substituir um ou mais dos métodos descritos neste tópico para realizarem o seu trabalho a processar entrada.</span><span class="sxs-lookup"><span data-stu-id="17896-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span> <span data-ttu-id="17896-104">Esses métodos permitem que o cmdlet efetuar o pré-processamento operações de entrada operações de processamento e operações de processamento pós-cópia.</span><span class="sxs-lookup"><span data-stu-id="17896-104">These methods allow the cmdlet to perform pre-processing operations, input processing operations, and post-processing operations.</span></span> <span data-ttu-id="17896-105">Esses métodos também permitem que parar o processamento de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="17896-105">These methods also allow you to stop cmdlet processing.</span></span>

## <a name="pre-processing-tasks"></a><span data-ttu-id="17896-106">Tarefas de pré-processamento</span><span class="sxs-lookup"><span data-stu-id="17896-106">Pre-Processing Tasks</span></span>

<span data-ttu-id="17896-107">Cmdlets deve substituir o [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) método adicionar quaisquer operações de pré-processamento que são válidas para todos os registos que serão processados posteriormente pelo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="17896-107">Cmdlets should override the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span> <span data-ttu-id="17896-108">Quando o Windows PowerShell processa um pipeline de comando, Windows PowerShell chama esse método uma vez para cada instância do cmdlet no pipeline.</span><span class="sxs-lookup"><span data-stu-id="17896-108">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="17896-109">Para obter mais informações sobre como o Windows PowerShell invoca o pipeline de comando, consulte [ciclo de vida de processamento Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="17896-109">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="17896-110">O código a seguir mostra uma implementação o [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) método.</span><span class="sxs-lookup"><span data-stu-id="17896-110">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method.</span></span>

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

<span data-ttu-id="17896-111">Para obter um exemplo mais detalhado de como usar o [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) método, consulte [SelectStr Tutorial](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="17896-111">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span> <span data-ttu-id="17896-112">Neste tutorial, o **selecione Str** cmdlet utiliza o [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) método para gerar a expressão regular que é utilizada para procurar a entrada de processamento de registos.</span><span class="sxs-lookup"><span data-stu-id="17896-112">In this tutorial, the **Select-Str** cmdlet uses the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method to generate the regular expression that is used to search the input processing records.</span></span>

## <a name="input-processing-tasks"></a><span data-ttu-id="17896-113">Tarefas de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="17896-113">Input Processing Tasks</span></span>

<span data-ttu-id="17896-114">Cmdlets pode substituir o [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método para processar a entrada que é enviada para o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="17896-114">Cmdlets can override the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method to process the input that is sent to the cmdlet.</span></span> <span data-ttu-id="17896-115">Quando o Windows PowerShell processa um pipeline de comando, o Windows PowerShell chama esse método para cada registo de entrada que é processado pelo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="17896-115">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method for each input record that is processed by the cmdlet.</span></span> <span data-ttu-id="17896-116">Para obter mais informações sobre como o Windows PowerShell invoca o pipeline de comando, consulte [ciclo de vida de processamento Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="17896-116">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="17896-117">O código a seguir mostra uma implementação o [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método.</span><span class="sxs-lookup"><span data-stu-id="17896-117">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method.</span></span>

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

<span data-ttu-id="17896-118">Para obter um exemplo mais detalhado de como usar o [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método, consulte [SelectStr Tutorial](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="17896-118">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span>

## <a name="post-processing-tasks"></a><span data-ttu-id="17896-119">Tarefas pós-processamento</span><span class="sxs-lookup"><span data-stu-id="17896-119">Post-Processing Tasks</span></span>

<span data-ttu-id="17896-120">Cmdlets deve substituir o [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) método adicionar quaisquer operações de pós-processamento que são válidas para todos os registos que foram processados pelo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="17896-120">Cmdlets should override the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span> <span data-ttu-id="17896-121">Por exemplo, o seu cmdlet poderá ter de limpar a variáveis de objeto depois de terminar de processamento.</span><span class="sxs-lookup"><span data-stu-id="17896-121">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="17896-122">Quando o Windows PowerShell processa um pipeline de comando, Windows PowerShell chama esse método uma vez para cada instância do cmdlet no pipeline.</span><span class="sxs-lookup"><span data-stu-id="17896-122">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="17896-123">No entanto, é importante lembrar-se de que o tempo de execução do Windows PowerShell não irá chamar o [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) método se o cmdlet é cancelado midway por meio de seu processamento de entrada ou se acabar o erro ocorre em qualquer parte do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="17896-123">However, it is important to remember that the Windows PowerShell runtime will not call the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="17896-124">Por esse motivo, um cmdlet que necessita de limpeza do objeto deve implementar o concluída [System.Idisposable](/dotnet/api/System.IDisposable) padrão, incluindo um finalizador, para que o tempo de execução possa chamar ambos o [ System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) e [System.Idisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) métodos no final do processamento.</span><span class="sxs-lookup"><span data-stu-id="17896-124">For this reason, a cmdlet that requires object cleanup should implement the complete [System.Idisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) and [System.Idisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span> <span data-ttu-id="17896-125">Para obter mais informações sobre como o Windows PowerShell invoca o pipeline de comando, consulte [ciclo de vida de processamento Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="17896-125">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="17896-126">O código a seguir mostra uma implementação o [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método.</span><span class="sxs-lookup"><span data-stu-id="17896-126">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method.</span></span>

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

<span data-ttu-id="17896-127">Para obter um exemplo mais detalhado de como usar o [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método, consulte [SelectStr Tutorial](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="17896-127">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="17896-128">Veja Também</span><span class="sxs-lookup"><span data-stu-id="17896-128">See Also</span></span>

[<span data-ttu-id="17896-129">System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="17896-129">System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)

[<span data-ttu-id="17896-130">System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="17896-130">System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)

[<span data-ttu-id="17896-131">System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="17896-131">System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)

[<span data-ttu-id="17896-132">System.Idisposable</span><span class="sxs-lookup"><span data-stu-id="17896-132">System.Idisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="17896-133">Shell do Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="17896-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
