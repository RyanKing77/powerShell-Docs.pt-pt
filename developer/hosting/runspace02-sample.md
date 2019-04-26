---
title: Exemplo de Runspace02 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7630bb63-ef39-4abd-b795-8000f984c1e5
caps.latest.revision: 9
ms.openlocfilehash: 6352169cffbb8a8bf59a42f79979f5003c150fa4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082724"
---
# <a name="runspace02-sample"></a><span data-ttu-id="c6db3-102">Runspace02 Sample (Exemplo Runspace02)</span><span class="sxs-lookup"><span data-stu-id="c6db3-102">Runspace02 Sample</span></span>

<span data-ttu-id="c6db3-103">Este exemplo mostra como utilizar o [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe para executar o [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) e [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="c6db3-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously.</span></span> <span data-ttu-id="c6db3-104">O [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet devolve [Diagnostics](/dotnet/api/System.Diagnostics.Process) objetos para cada processo em execução no computador local e o `Sort-Object` classifica os objetos com base na respetiva [ System.Diagnostics.Process.Id\*](/dotnet/api/System.Diagnostics.Process.Id) propriedade.</span><span class="sxs-lookup"><span data-stu-id="c6db3-104">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects for each process running on the local computer, and the `Sort-Object` sorts the objects based on their [System.Diagnostics.Process.Id\*](/dotnet/api/System.Diagnostics.Process.Id) property.</span></span> <span data-ttu-id="c6db3-105">Os resultados desses comandos são apresentadas utilizando um [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) controle.</span><span class="sxs-lookup"><span data-stu-id="c6db3-105">The results of these commands is displayed by using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

## <a name="requirements"></a><span data-ttu-id="c6db3-106">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c6db3-106">Requirements</span></span>

<span data-ttu-id="c6db3-107">Este exemplo requer o Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="c6db3-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="c6db3-108">Demonstra</span><span class="sxs-lookup"><span data-stu-id="c6db3-108">Demonstrates</span></span>

<span data-ttu-id="c6db3-109">Este exemplo demonstra o seguinte.</span><span class="sxs-lookup"><span data-stu-id="c6db3-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="c6db3-110">Criar uma [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto para executar comandos.</span><span class="sxs-lookup"><span data-stu-id="c6db3-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run commands.</span></span>

- <span data-ttu-id="c6db3-111">Adicionar os comandos para o pipeline de [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.</span><span class="sxs-lookup"><span data-stu-id="c6db3-111">Adding commands to the pipeline of [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="c6db3-112">Executar os comandos de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="c6db3-112">Running the commands synchronously.</span></span>

- <span data-ttu-id="c6db3-113">Utilizar um [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) controle para exibir a saída dos comandos num aplicativo Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c6db3-113">Using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control to display the output of the commands in a Windows Forms application.</span></span>

## <a name="example"></a><span data-ttu-id="c6db3-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c6db3-114">Example</span></span>

<span data-ttu-id="c6db3-115">Este exemplo é executado o [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) e [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets de forma síncrona no espaço de execução padrão fornecido pelo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c6db3-115">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="c6db3-116">O resultado é apresentado num formulário com um [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) controle.</span><span class="sxs-lookup"><span data-stu-id="c6db3-116">The output is displayed in a form using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using System.Windows.Forms;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace02
  {
    /// <summary>
    /// This method creates the form where the output is displayed.
    /// </summary>
    private static void CreateForm()
    {
      Form form = new Form();
      DataGridView grid = new DataGridView();
      form.Controls.Add(grid);
      grid.Dock = DockStyle.Fill;

      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the command.
      using (PowerShell powershell = PowerShell.Create())
      {
        powershell.AddCommand("get-process").AddCommand("sort-object").AddArgument("ID");
        if (Runspace.DefaultRunspace == null)
        {
          Runspace.DefaultRunspace = powershell.Runspace;
        }

        Collection<PSObject> results = powershell.Invoke();

        // The generic collection needs to be re-wrapped in an ArrayList
        // for data-binding to work.
        ArrayList objects = new ArrayList();
        objects.AddRange(results);

        // The DataGridView will use the PSObjectTypeDescriptor type
        // to retrieve the properties.
        grid.DataSource = objects;
      }

      form.ShowDialog();
    }

    /// <summary>
    /// This sample uses a PowerShell object to run the Get-Process
    /// and Sort-Object cmdlets synchronously. Windows Forms and
    /// data binding are then used to display the results in a
    /// DataGridView control.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object.
    /// 2. Adding commands and arguments to the pipeline of
    ///    the PowerShell object.
    /// 3. Running the commands synchronously.
    /// 4. Using a DataGridView control to display the output
    ///    of the commands in a Windows Forms application.
    /// </remarks>
    private static void Main(string[] args)
    {
      Runspace02.CreateForm();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="c6db3-117">Veja Também</span><span class="sxs-lookup"><span data-stu-id="c6db3-117">See Also</span></span>

[<span data-ttu-id="c6db3-118">Escrever um aplicativo de Host de PowerShell do Windows</span><span class="sxs-lookup"><span data-stu-id="c6db3-118">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)