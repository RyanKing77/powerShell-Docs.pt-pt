---
title: Exemplo de GetProcessSample04 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa2aa4c4-3457-4601-806a-801afe3dcc80
caps.latest.revision: 6
ms.openlocfilehash: 095bebf868efd00f8eeaec979a5606f140714cb1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068033"
---
# <a name="getprocesssample04-sample"></a><span data-ttu-id="ac188-102">GetProcessSample04 Sample (Exemplo GetProcessSample04)</span><span class="sxs-lookup"><span data-stu-id="ac188-102">GetProcessSample04 Sample</span></span>

<span data-ttu-id="ac188-103">Este exemplo mostra como implementar um cmdlet que obtém os processos no computador local.</span><span class="sxs-lookup"><span data-stu-id="ac188-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="ac188-104">Gera um erro de não terminação se ocorrer um erro ao obter um processo.</span><span class="sxs-lookup"><span data-stu-id="ac188-104">It generates a nonterminating error if an error occurs while retrieving a process.</span></span> <span data-ttu-id="ac188-105">Este cmdlet é uma versão simplificada do `Get-Process` cmdlet fornecido pelo Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="ac188-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="ac188-106">Como criar o exemplo com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ac188-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="ac188-107">Windows PowerShell 2.0 SDK instalado, navegue para a pasta de GetProcessSample04.</span><span class="sxs-lookup"><span data-stu-id="ac188-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample04 folder.</span></span> <span data-ttu-id="ac188-108">A localização predefinida é C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span><span class="sxs-lookup"><span data-stu-id="ac188-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span></span>

2. <span data-ttu-id="ac188-109">Faça duplo clique no ícone para o ficheiro de solução (. sln).</span><span class="sxs-lookup"><span data-stu-id="ac188-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="ac188-110">Esta ação abre o projeto de exemplo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ac188-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="ac188-111">Na **crie** menu, selecione **compilar solução**.</span><span class="sxs-lookup"><span data-stu-id="ac188-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="ac188-112">A biblioteca para o exemplo será criada nas pastas de \bin ou \bin\debug do padrão.</span><span class="sxs-lookup"><span data-stu-id="ac188-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="ac188-113">Como executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ac188-113">How to run the sample</span></span>

1. <span data-ttu-id="ac188-114">Crie a seguinte pasta de módulo:</span><span class="sxs-lookup"><span data-stu-id="ac188-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. <span data-ttu-id="ac188-115">Copie o assembly de exemplo para a pasta de módulo.</span><span class="sxs-lookup"><span data-stu-id="ac188-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="ac188-116">Inicie o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ac188-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="ac188-117">Execute o seguinte comando para carregar o assembly para o Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="ac188-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample04`

5. <span data-ttu-id="ac188-118">Execute o seguinte comando para executar o cmdlet:</span><span class="sxs-lookup"><span data-stu-id="ac188-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="ac188-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ac188-119">Requirements</span></span>

<span data-ttu-id="ac188-120">Este exemplo requer o Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="ac188-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="ac188-121">Demonstra</span><span class="sxs-lookup"><span data-stu-id="ac188-121">Demonstrates</span></span>

<span data-ttu-id="ac188-122">Este exemplo demonstra o seguinte.</span><span class="sxs-lookup"><span data-stu-id="ac188-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="ac188-123">Declarar uma classe cmdlet usando o atributo de Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ac188-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="ac188-124">Declarar um parâmetro de cmdlet usando o atributo de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ac188-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="ac188-125">Especificando a posição do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ac188-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="ac188-126">Especificando-se de que o parâmetro pega a entrada do pipeline.</span><span class="sxs-lookup"><span data-stu-id="ac188-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="ac188-127">A entrada pode ser realizada a partir de um objeto ou um valor de uma propriedade de um objeto cujo nome de propriedade é o mesmo que o nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ac188-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="ac188-128">Declarar um atributo de validação para o parâmetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="ac188-128">Declaring a validation attribute for the parameter input.</span></span>

- <span data-ttu-id="ac188-129">Interceptando um erro de não terminação e escrever uma mensagem de erro no fluxo de erro.</span><span class="sxs-lookup"><span data-stu-id="ac188-129">Trapping a nonterminating error and writing an error message to the error stream.</span></span>

## <a name="example"></a><span data-ttu-id="ac188-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ac188-130">Example</span></span>

<span data-ttu-id="ac188-131">Este exemplo mostra como criar um cmdlet que manipula erros de não terminação e escreve mensagens de erro para a sequência de erro.</span><span class="sxs-lookup"><span data-stu-id="ac188-131">This sample shows how to create a cmdlet that handles nonterminating errors and writes error messages to the error stream.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
    using System;
    using System.Diagnostics;
    using System.Management.Automation;      // Windows PowerShell namespace.
   #region GetProcCommand

   /// <summary>
   /// This class implements the get-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Parameters

       /// <summary>
       /// The names of the processes to act on.
       /// </summary>
       private string[] processNames;

      /// <summary>
      /// Gets or sets the list of process names on
      /// which the Get-Proc cmdlet will work.
      /// </summary>
      [Parameter(
         Position = 0,
         ValueFromPipeline = true,
         ValueFromPipelineByPropertyName = true)]
      [ValidateNotNullOrEmpty]
      public string[] Name
      {
         get { return this.processNames; }
         set { this.processNames = value; }
      }

      #endregion Parameters

      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes specified by the Name
      /// parameter. Then, the WriteObject method writes the
      /// associated processes to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
          // If no process names are passed to cmdlet, get all
          // processes.
          if (this.processNames == null)
          {
              WriteObject(Process.GetProcesses(), true);
          }
          else
          {
              // If process names are passed to the cmdlet, get and write
              // the associated processes.
              // If a nonterminating error occurs while retrieving processes,
              // call the WriteError method to send an error record to the
              // error stream.
              foreach (string name in this.processNames)
              {
                  Process[] processes;

                  try
                  {
                      processes = Process.GetProcessesByName(name);
                  }
                  catch (InvalidOperationException ex)
                  {
                      WriteError(new ErrorRecord(
                         ex,
                         "UnableToAccessProcessByName",
                         ErrorCategory.InvalidOperation,
                         name));
                      continue;
                  }

                  WriteObject(processes, true);
              } // foreach (string name...
          } // else
      } // ProcessRecord

      #endregion Overrides
    } // End GetProcCommand class.

   #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="ac188-132">Veja Também</span><span class="sxs-lookup"><span data-stu-id="ac188-132">See Also</span></span>

[<span data-ttu-id="ac188-133">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ac188-133">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
