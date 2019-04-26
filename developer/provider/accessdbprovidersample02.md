---
title: AccessDBProviderSample02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aaf9351e-157f-4d48-8b8f-1fd64855b682
caps.latest.revision: 10
ms.openlocfilehash: d291e401bbf3da998735ebb00f1eb35521f9a19c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081063"
---
# <a name="accessdbprovidersample02"></a><span data-ttu-id="fae4f-102">AccessDBProviderSample02</span><span class="sxs-lookup"><span data-stu-id="fae4f-102">AccessDBProviderSample02</span></span>

<span data-ttu-id="fae4f-103">Este exemplo demonstra como substituir a [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) e [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)métodos para oferecer suporte a chamadas para o `New-PSDrive` e `Remove-PSDrive` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="fae4f-103">This sample shows how to overwrite the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods to support calls to the `New-PSDrive` and `Remove-PSDrive` cmdlets.</span></span> <span data-ttu-id="fae4f-104">A classe de fornecedor neste exemplo deriva do [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="fae4f-104">The provider class in this sample derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="fae4f-105">Demonstra</span><span class="sxs-lookup"><span data-stu-id="fae4f-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fae4f-106">Sua classe de fornecedor será provavelmente derivam de uma das seguintes classes e, possivelmente, implementar outras interfaces de fornecedor:</span><span class="sxs-lookup"><span data-stu-id="fae4f-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="fae4f-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="fae4f-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="fae4f-108">Ver [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="fae4f-108">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="fae4f-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="fae4f-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="fae4f-110">Ver [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="fae4f-110">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="fae4f-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="fae4f-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="fae4f-112">Ver [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="fae4f-112">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="fae4f-113">Para obter mais informações sobre como escolher a classe de fornecedor que derivar de com base nos recursos de fornecedor, consulte [conceber Windows PowerShell Fornecedor_de_e](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="fae4f-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="fae4f-114">Este exemplo demonstra o seguinte:</span><span class="sxs-lookup"><span data-stu-id="fae4f-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="fae4f-115">Declarando o `CmdletProvider` atributo.</span><span class="sxs-lookup"><span data-stu-id="fae4f-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="fae4f-116">Definir uma classe de fornecedor que orienta a partir da [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="fae4f-116">Defining a provider class that drives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span>

- <span data-ttu-id="fae4f-117">Substituir a [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) método para suportar a criação de novas unidades.</span><span class="sxs-lookup"><span data-stu-id="fae4f-117">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to support creating new drives.</span></span> <span data-ttu-id="fae4f-118">(Este exemplo não mostra como adicionar parâmetros dinâmicos para a `New-PSDrive` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="fae4f-118">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="fae4f-119">Substituir a [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) método para oferecer suporte a remover unidades existentes.</span><span class="sxs-lookup"><span data-stu-id="fae4f-119">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

## <a name="example"></a><span data-ttu-id="fae4f-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fae4f-120">Example</span></span>

<span data-ttu-id="fae4f-121">Este exemplo demonstra como substituir a [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) e [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)métodos.</span><span class="sxs-lookup"><span data-stu-id="fae4f-121">This sample shows how to overwrite the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods.</span></span> <span data-ttu-id="fae4f-122">Para este fornecedor de exemplo, quando é criada uma unidade de suas informações de ligação são armazenadas num `AccessDBPsDriveInfo` objeto.</span><span class="sxs-lookup"><span data-stu-id="fae4f-122">For this sample provider, when a drive is created its connection information is stored in an `AccessDBPsDriveInfo` object.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System;
  using System.Data;
  using System.Data.Odbc;
  using System.IO;
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  #region AccessDBProvider

  /// <summary>
  /// This sample implements a Windows PowerShell provider class
  /// that acts upon an Access database.
  /// </summary>
  /// <remarks>
  /// This example demonstrates only the drive overrides used to
  /// add and remove drives from the database.</remarks>
  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : DriveCmdletProvider
  {
    #region Drive Manipulation

    /// <summary>
    /// The Windows PowerShell engine calls this method when the
    /// New-PSDrive cmdlet is run and the path to this provider is
    /// specified. This method creates a connection to the database
    /// file and sets the Connection property of the PSDriveInfo object.
    /// </summary>
    /// <param name="drive">
    /// Information describing the drive to create.
    /// </param>
    /// <returns>An accessDBPSDriveInfo object that represents
    /// the new drive.</returns>
    protected override PSDriveInfo NewDrive(PSDriveInfo drive)
    {
      // Check if the drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   null));

        return null;
      }

      // Check if the drive root is not null or empty
      // and if it is an existing file.
      if (String.IsNullOrEmpty(drive.Root) || (File.Exists(drive.Root) == false))
      {
        WriteError(new ErrorRecord(
                   new ArgumentException("drive.Root"),
                   "NoRoot",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Create a new drive and create an ODBC connection to the new drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = new AccessDBPSDriveInfo(drive);
      OdbcConnectionStringBuilder builder = new OdbcConnectionStringBuilder();

      builder.Driver = "Microsoft Access Driver (*.mdb)";
      builder.Add("DBQ", drive.Root);

      OdbcConnection conn = new OdbcConnection(builder.ConnectionString);
      conn.Open();
      accessDBPSDriveInfo.Connection = conn;

      return accessDBPSDriveInfo;
    } // End NewDrive.

    /// <summary>
    /// The Windows PowerShell engine calls this method when the
    /// Remove-PSDrive cmdlet is run and the path to this provider is
    /// specified. This method closes the ODBC connection of the drive.
    /// </summary>
    /// <param name="drive">The drive to remove.</param>
    /// <returns>An accessDBPSDriveInfo object that represents
    /// the removed drive.</returns>
    protected override PSDriveInfo RemoveDrive(PSDriveInfo drive)
    {
      // Check if drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Close the ODBC connection to the drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = drive as AccessDBPSDriveInfo;

      if (accessDBPSDriveInfo == null)
      {
         return null;
      }

      accessDBPSDriveInfo.Connection.Close();

      return accessDBPSDriveInfo;
    } // End RemoveDrive.

    #endregion Drive Manipulation
  } // End AccessDBProvider class.

  #endregion AccessDBProvider

  #region AccessDBPSDriveInfo

  /// <summary>
  /// Any state associated with the drive is held here. In this
  /// case, the state information is the connection to the database.
  /// </summary>
  internal class AccessDBPSDriveInfo : PSDriveInfo
  {
    /// <summary>
    /// A reference to the connection to the database.
    /// </summary>
    private OdbcConnection connection;

    /// <summary>
    /// Initializes a new instance of the AccessDBPSDriveInfo class.
    /// The constructor takes a single argument.
    /// </summary>
    /// <param name="driveInfo">Drive defined by this provider</param>
    public AccessDBPSDriveInfo(PSDriveInfo driveInfo)
           : base(driveInfo)
    {
    }

    /// <summary>
    /// Gets or sets the ODBC connection information.
    /// </summary>
    public OdbcConnection Connection
    {
        get { return this.connection; }
        set { this.connection = value; }
    }
  } // End AccessDBPSDriveInfo class.

  #endregion AccessDBPSDriveInfo
}
```

## <a name="see-also"></a><span data-ttu-id="fae4f-123">Veja Também</span><span class="sxs-lookup"><span data-stu-id="fae4f-123">See Also</span></span>

[<span data-ttu-id="fae4f-124">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="fae4f-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="fae4f-125">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="fae4f-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="fae4f-126">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="fae4f-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="fae4f-127">Estruturar o seu fornecedor do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fae4f-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)