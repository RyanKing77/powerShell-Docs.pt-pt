---
title: Exemplo de Events01 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27d0ee5e-2589-4530-92ef-c09996b80994
caps.latest.revision: 10
ms.openlocfilehash: c9963819f1842d1245735dabc487babaa566c160
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068135"
---
# <a name="events01-sample"></a><span data-ttu-id="df71e-102">Events01 Sample (Exemplo Events01)</span><span class="sxs-lookup"><span data-stu-id="df71e-102">Events01 Sample</span></span>

<span data-ttu-id="df71e-103">Este exemplo mostra como criar um cmdlet que permite ao utilizador para se registrar para eventos gerados por [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher).</span><span class="sxs-lookup"><span data-stu-id="df71e-103">This sample shows how to create a cmdlet that allows the user to register for events that are raised by [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span> <span data-ttu-id="df71e-104">Com este cmdlet, os utilizadores podem registar uma ação a executar quando é criado um ficheiro num diretório específico.</span><span class="sxs-lookup"><span data-stu-id="df71e-104">With this cmdlet, users can register an action to execute when a file is created under a specific directory.</span></span> <span data-ttu-id="df71e-105">Este exemplo deriva de [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) classe base.</span><span class="sxs-lookup"><span data-stu-id="df71e-105">This sample derives from the [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="df71e-106">Como criar o exemplo com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="df71e-106">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="df71e-107">Windows PowerShell 2.0 SDK instalado, navegue para a pasta de Events01.</span><span class="sxs-lookup"><span data-stu-id="df71e-107">With the Windows PowerShell 2.0 SDK installed, navigate to the Events01 folder.</span></span> <span data-ttu-id="df71e-108">A localização predefinida é C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01.</span><span class="sxs-lookup"><span data-stu-id="df71e-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01.</span></span>

2. <span data-ttu-id="df71e-109">Faça duplo clique no ícone para o ficheiro de solução (. sln).</span><span class="sxs-lookup"><span data-stu-id="df71e-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="df71e-110">Esta ação abre o projeto de exemplo no Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="df71e-110">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="df71e-111">Na **crie** menu, selecione **compilar solução**.</span><span class="sxs-lookup"><span data-stu-id="df71e-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="df71e-112">A biblioteca para o exemplo será criada nas pastas de \bin ou \bin\debug do padrão.</span><span class="sxs-lookup"><span data-stu-id="df71e-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="df71e-113">Como executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="df71e-113">How to run the sample</span></span>

1. <span data-ttu-id="df71e-114">Crie a seguinte pasta de módulo:</span><span class="sxs-lookup"><span data-stu-id="df71e-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/events01`

2. <span data-ttu-id="df71e-115">Copie o ficheiro de biblioteca para o exemplo para a pasta de módulo.</span><span class="sxs-lookup"><span data-stu-id="df71e-115">Copy the library file for the sample to the module folder.</span></span>

3. <span data-ttu-id="df71e-116">Inicie o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df71e-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="df71e-117">Execute o seguinte comando para carregar o cmdlet para o Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="df71e-117">Run the following command to load the cmdlet into Windows PowerShell:</span></span>

    ```powershell
    import-module events01
    ```

5. <span data-ttu-id="df71e-118">Utilize o cmdlet Register-FileSystemEvent para registar uma ação que irá escrever uma mensagem quando é criado um ficheiro no diretório TEMP.</span><span class="sxs-lookup"><span data-stu-id="df71e-118">Use the Register-FileSystemEvent cmdlet to register an action that will write a message when a file is created under the TEMP directory.</span></span>

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. <span data-ttu-id="df71e-119">Criar um ficheiro no diretório TEMP do diretório e tenha em atenção que a ação é executada (é apresentada a mensagem).</span><span class="sxs-lookup"><span data-stu-id="df71e-119">Create a file under the TEMP directory and note that the action is executed (the message is displayed).</span></span>

<span data-ttu-id="df71e-120">Esta é uma saída de exemplo que resulta ao seguir estes passos.</span><span class="sxs-lookup"><span data-stu-id="df71e-120">This is a sample output that results by following these steps.</span></span>

```output
Id              Name            State      HasMoreData     Location             Command
--              ----            -----      -----------     --------             -------
1               26932870-d3b... NotStarted False                                 Write-Host "A f...

```

```powershell
Set-Content $env:temp\test.txt "This is a test file"
```

```output
A file was created in the TEMP directory
```

## <a name="requirements"></a><span data-ttu-id="df71e-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="df71e-121">Requirements</span></span>

<span data-ttu-id="df71e-122">Este exemplo requer o Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="df71e-122">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="df71e-123">Demonstra</span><span class="sxs-lookup"><span data-stu-id="df71e-123">Demonstrates</span></span>

<span data-ttu-id="df71e-124">Este exemplo demonstra o seguinte.</span><span class="sxs-lookup"><span data-stu-id="df71e-124">This sample demonstrates the following.</span></span>

- <span data-ttu-id="df71e-125">Como escrever um cmdlet para o registo de eventos.</span><span class="sxs-lookup"><span data-stu-id="df71e-125">How to write a cmdlet for event registration.</span></span> <span data-ttu-id="df71e-126">O cmdlet deriva a [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) classe, que fornece suporte para os parâmetros comuns Register-\* cmdlets de evento.</span><span class="sxs-lookup"><span data-stu-id="df71e-126">The cmdlet derives from the [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) class, which provides support for parameters common to the Register-\*Event cmdlets.</span></span> <span data-ttu-id="df71e-127">Cmdlets derivados [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) só precisa definir seus parâmetros específicos e substituir o `GetSourceObject` e `GetSourceObjectEventName` abstrair métodos.</span><span class="sxs-lookup"><span data-stu-id="df71e-127">Cmdlets that are derived from [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) need only to define their particular parameters and override the `GetSourceObject` and `GetSourceObjectEventName` abstract methods.</span></span>

## <a name="example"></a><span data-ttu-id="df71e-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df71e-128">Example</span></span>

<span data-ttu-id="df71e-129">Este exemplo mostra como se registrar para eventos gerados pelo [System.IO.FileSystemWatcher](https://msdn.microsoft.com/en-us/library/system.io.filesystemwatcher\(v=vs.110\).aspx).</span><span class="sxs-lookup"><span data-stu-id="df71e-129">This sample shows how to register for events raised by [System.IO.FileSystemWatcher](https://msdn.microsoft.com/en-us/library/system.io.filesystemwatcher\(v=vs.110\).aspx).</span></span>

```csharp
namespace Sample
{
    using System;
    using System.IO;
    using System.Management.Automation;
    using System.Management.Automation.Runspaces;
    using Microsoft.PowerShell.Commands;

    [Cmdlet(VerbsLifecycle.Register, "FileSystemEvent")]
    public class RegisterObjectEventCommand : ObjectEventRegistrationBase
    {
        /// <summary>The FileSystemWatcher that exposes the events.</summary>
        private FileSystemWatcher fileSystemWatcher = new FileSystemWatcher();

        /// <summary>Name of the event to which the cmdlet registers.</summary>
        private string eventName = null;

        /// <summary>
        /// Gets or sets the path that will be monitored by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = true, Position = 0)]
        public string Path
        {
            get
            {
                return this.fileSystemWatcher.Path;
            }

            set
            {
                this.fileSystemWatcher.Path = value;
            }
        }

        /// <summary>
        /// Gets or sets the name of the event to which the cmdlet registers.
        /// <para>
        /// Currently System.IO.FileSystemWatcher exposes 6 events: Changed, Created,
        /// Deleted, Disposed, Error, and Renamed. Check the MSDN documentation of
        /// FileSystemWatcher for details on each event.
        /// </para>
        /// </summary>
        [Parameter(Mandatory = true, Position = 1)]
        public string EventName
        {
            get
            {
                return this.eventName;
            }

            set
            {
                this.eventName = value;
            }
        }

        /// <summary>
        /// Gets or sets the filter that will be user by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = false)]
        public string Filter
        {
            get
            {
                return this.fileSystemWatcher.Filter;
            }

            set
            {
                this.fileSystemWatcher.Filter = value;
            }
        }

        /// <summary>
        /// Derived classes must implement this method to return the object that generates
        /// the events to be monitored.
        /// </summary>
        /// <returns> This sample returns an instance of System.IO.FileSystemWatcher</returns>
        protected override object GetSourceObject()
        {
            return this.fileSystemWatcher;
        }

        /// <summary>
        /// Derived classes must implement this method to return the name of the event to
        /// be monitored. This event must be exposed by the input object.
        /// </summary>
        /// <returns> This sample returns the event specified by the user with the -EventName parameter.</returns>
        protected override string GetSourceObjectEventName()
        {
            return this.eventName;
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="df71e-130">Veja Também</span><span class="sxs-lookup"><span data-stu-id="df71e-130">See Also</span></span>

[<span data-ttu-id="df71e-131">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="df71e-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)