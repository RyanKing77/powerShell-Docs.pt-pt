---
title: Exemplo de GetProcessSample02 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 481f557d-3344-4d33-b2da-4736a0165181
caps.latest.revision: 7
ms.openlocfilehash: fa4cd8a724793e71b615c84a5c5a833aa92c93fc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849512"
---
# <a name="getprocesssample02-sample"></a><span data-ttu-id="7bc59-102">GetProcessSample02 Sample (Exemplo GetProcessSample02)</span><span class="sxs-lookup"><span data-stu-id="7bc59-102">GetProcessSample02 Sample</span></span>

<span data-ttu-id="7bc59-103">Este exemplo mostra como escrever um cmdlet que obtém os processos no computador local.</span><span class="sxs-lookup"><span data-stu-id="7bc59-103">This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="7bc59-104">Ele fornece um `Name` parâmetro que pode ser utilizado para especificar os processos a serem obtidas.</span><span class="sxs-lookup"><span data-stu-id="7bc59-104">It provides a `Name` parameter that can be used to specify the processes to be retrieved.</span></span> <span data-ttu-id="7bc59-105">Este cmdlet é uma versão simplificada do `Get-Process` cmdlet fornecido pelo Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="7bc59-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="7bc59-106">Como criar o exemplo com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7bc59-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="7bc59-107">Windows PowerShell 2.0 SDK instalado, navegue para a pasta de GetProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="7bc59-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample02 folder.</span></span> <span data-ttu-id="7bc59-108">A localização predefinida é C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="7bc59-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span></span>

2. <span data-ttu-id="7bc59-109">Faça duplo clique no ícone para o ficheiro de solução (. sln).</span><span class="sxs-lookup"><span data-stu-id="7bc59-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="7bc59-110">Esta ação abre o projeto de exemplo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7bc59-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="7bc59-111">Na **crie** menu, selecione **compilar solução**.</span><span class="sxs-lookup"><span data-stu-id="7bc59-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="7bc59-112">A biblioteca para o exemplo será criada nas pastas de \bin ou \bin\debug do padrão.</span><span class="sxs-lookup"><span data-stu-id="7bc59-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="7bc59-113">Como executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="7bc59-113">How to run the sample</span></span>

1. <span data-ttu-id="7bc59-114">Crie a seguinte pasta de módulo:</span><span class="sxs-lookup"><span data-stu-id="7bc59-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. <span data-ttu-id="7bc59-115">Copie o assembly de exemplo para a pasta de módulo.</span><span class="sxs-lookup"><span data-stu-id="7bc59-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="7bc59-116">Inicie o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7bc59-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="7bc59-117">Execute o seguinte comando para carregar o assembly para o Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="7bc59-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module getprossessample02`

5. <span data-ttu-id="7bc59-118">Execute o seguinte comando para executar o cmdlet:</span><span class="sxs-lookup"><span data-stu-id="7bc59-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="7bc59-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7bc59-119">Requirements</span></span>

<span data-ttu-id="7bc59-120">Este exemplo requer o Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="7bc59-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="7bc59-121">Demonstra</span><span class="sxs-lookup"><span data-stu-id="7bc59-121">Demonstrates</span></span>

<span data-ttu-id="7bc59-122">Este exemplo demonstra o seguinte.</span><span class="sxs-lookup"><span data-stu-id="7bc59-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="7bc59-123">Declarar uma classe cmdlet usando o atributo de Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7bc59-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="7bc59-124">Declarar um parâmetro de cmdlet usando o atributo de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7bc59-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="7bc59-125">Especificando a posição do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7bc59-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="7bc59-126">Declarar um atributo de validação para o parâmetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="7bc59-126">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="7bc59-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7bc59-127">Example</span></span>

<span data-ttu-id="7bc59-128">Este exemplo mostra uma implementação do cmdlet Get-Proc que inclui um `Name` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7bc59-128">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;     // Windows PowerShell namespace

  #region GetProcCommand

  /// <summary>
  /// This class implements the get-proc cmdlet.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Parameters

    /// <summary>
    /// The names of the processes retrieved by the cmdlet.
    /// </summary>
    private string[] processNames;

    /// <summary>
    /// Gets or sets the list of process names on which
    /// the Get-Proc cmdlet will work.
    /// </summary>
    [Parameter(Position = 0)]
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
    /// associated process objects to the pipeline.
    /// </summary>
    protected override void ProcessRecord()
    {
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames...).
    } // End ProcessRecord.
    #endregion Cmdlet Overrides
  } // End GetProcCommand class.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="7bc59-129">Veja Também</span><span class="sxs-lookup"><span data-stu-id="7bc59-129">See Also</span></span>

[<span data-ttu-id="7bc59-130">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7bc59-130">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
