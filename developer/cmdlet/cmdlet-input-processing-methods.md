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
ms.openlocfilehash: a28c8d3df19bc72bf338d6abc4e02768c5097209
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670311"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="1877c-102">Cmdlet Input Processing Methods (Métodos de Processamento de Entrada de Cmdlets)</span><span class="sxs-lookup"><span data-stu-id="1877c-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="1877c-103">Cmdlets tem de substituir um ou mais dos métodos descritos neste tópico para realizarem o seu trabalho a processar entrada.</span><span class="sxs-lookup"><span data-stu-id="1877c-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span>
<span data-ttu-id="1877c-104">Esses métodos permitem que o cmdlet para efetuar operações de processamento prévio de, o processamento de entrada e o pós-processamento.</span><span class="sxs-lookup"><span data-stu-id="1877c-104">These methods allow the cmdlet to perform operations of pre-processing, input processing, and post-processing.</span></span>
<span data-ttu-id="1877c-105">Esses métodos também permitem que parar o processamento de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1877c-105">These methods also allow you to stop cmdlet processing.</span></span>
<span data-ttu-id="1877c-106">Para obter um exemplo mais detalhado de como usar esses métodos, consulte [SelectStr Tutorial](selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="1877c-106">For a more detailed example of how to use these methods, see [SelectStr Tutorial](selectstr-tutorial.md).</span></span>

## <a name="pre-processing-operations"></a><span data-ttu-id="1877c-107">Operações de pré-processamento</span><span class="sxs-lookup"><span data-stu-id="1877c-107">Pre-Processing Operations</span></span>

<span data-ttu-id="1877c-108">Cmdlets deve substituir a [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método adicionar quaisquer operações de pré-processamento que são válidas para todos os registos que serão processados posteriormente pelo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1877c-108">Cmdlets should override the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span>
<span data-ttu-id="1877c-109">Quando o PowerShell processa um pipeline de comando, PowerShell chama esse método uma vez para cada instância do cmdlet no pipeline.</span><span class="sxs-lookup"><span data-stu-id="1877c-109">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="1877c-110">Para obter mais informações sobre como o PowerShell invoca o pipeline de comando, consulte [ciclo de vida de processamento Cmdlet](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="1877c-110">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="1877c-111">O código a seguir mostra uma implementação do método BeginProcessing.</span><span class="sxs-lookup"><span data-stu-id="1877c-111">The following code shows an implementation of the BeginProcessing method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a><span data-ttu-id="1877c-112">Operações de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="1877c-112">Input Processing Operations</span></span>

<span data-ttu-id="1877c-113">Cmdlets pode substituir a [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método para processar a entrada que é enviada para o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1877c-113">Cmdlets can override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the input that is sent to the cmdlet.</span></span>
<span data-ttu-id="1877c-114">Quando o PowerShell processa um pipeline de comando, o PowerShell chama esse método para cada registo de entrada que é processado pelo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1877c-114">When PowerShell processes a command pipeline, PowerShell calls this method for each input record that is processed by the cmdlet.</span></span>
<span data-ttu-id="1877c-115">Para obter mais informações sobre como o PowerShell invoca o pipeline de comando, consulte [ciclo de vida de processamento Cmdlet](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="1877c-115">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="1877c-116">O código a seguir mostra uma implementação do método ProcessRecord.</span><span class="sxs-lookup"><span data-stu-id="1877c-116">The following code shows an implementation of the ProcessRecord method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a><span data-ttu-id="1877c-117">Operações de pós-processamento</span><span class="sxs-lookup"><span data-stu-id="1877c-117">Post-Processing Operations</span></span>

<span data-ttu-id="1877c-118">Cmdlets deve substituir a [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método adicionar quaisquer operações de pós-processamento que são válidas para todos os registos que foram processados pelo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1877c-118">Cmdlets should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span>
<span data-ttu-id="1877c-119">Por exemplo, o seu cmdlet poderá ter de limpar a variáveis de objeto depois de terminar de processamento.</span><span class="sxs-lookup"><span data-stu-id="1877c-119">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="1877c-120">Quando o PowerShell processa um pipeline de comando, PowerShell chama esse método uma vez para cada instância do cmdlet no pipeline.</span><span class="sxs-lookup"><span data-stu-id="1877c-120">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="1877c-121">No entanto, é importante lembrar-se de que o tempo de execução do PowerShell não irá chamar o método EndProcessing se o cmdlet é cancelado midway por meio de seu processamento de entrada ou se ocorrer um erro de terminação em qualquer parte do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1877c-121">However, it is important to remember that the PowerShell runtime will not call the EndProcessing method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span>
<span data-ttu-id="1877c-122">Por esse motivo, um cmdlet que necessita de limpeza do objeto deve implementar o concluída [System.IDisposable](/dotnet/api/System.IDisposable) padrão, incluindo um finalizador, para que o tempo de execução possa chamar os dois o EndProcessing e [ System](/dotnet/api/System.IDisposable.Dispose) métodos no final do processamento.</span><span class="sxs-lookup"><span data-stu-id="1877c-122">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the EndProcessing and [System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>
<span data-ttu-id="1877c-123">Para obter mais informações sobre como o PowerShell invoca o pipeline de comando, consulte [ciclo de vida de processamento Cmdlet](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="1877c-123">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="1877c-124">O código a seguir mostra uma implementação do método EndProcessing.</span><span class="sxs-lookup"><span data-stu-id="1877c-124">The following code shows an implementation of the EndProcessing method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a><span data-ttu-id="1877c-125">Veja Também</span><span class="sxs-lookup"><span data-stu-id="1877c-125">See Also</span></span>

[<span data-ttu-id="1877c-126">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="1877c-126">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="1877c-127">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="1877c-127">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="1877c-128">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="1877c-128">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="1877c-129">Tutorial de SelectStr</span><span class="sxs-lookup"><span data-stu-id="1877c-129">SelectStr Tutorial</span></span>](selectstr-tutorial.md)

[<span data-ttu-id="1877c-130">System.IDisposable</span><span class="sxs-lookup"><span data-stu-id="1877c-130">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="1877c-131">Shell do Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1877c-131">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
