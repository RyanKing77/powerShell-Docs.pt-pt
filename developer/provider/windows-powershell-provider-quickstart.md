---
title: Guia de introdução do Windows PowerShell fornecedor | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e879ba7-c334-460b-94a1-3e9b63d3d8de
caps.latest.revision: 5
ms.openlocfilehash: 151b7125afe1b0d386467a0e5f89225716857ac2
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054922"
---
# <a name="windows-powershell-provider-quickstart"></a><span data-ttu-id="5a800-102">Windows PowerShell Provider Quickstart (Guia de Início Rápido do Fornecedor do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="5a800-102">Windows PowerShell Provider Quickstart</span></span>

<span data-ttu-id="5a800-103">Este tópico explica como criar um fornecedor de Windows PowerShell com a funcionalidade básica de criação de uma nova unidade.</span><span class="sxs-lookup"><span data-stu-id="5a800-103">This topic explains how to create a Windows PowerShell provider that has basic functionality of creating a new drive.</span></span> <span data-ttu-id="5a800-104">Para obter informações gerais sobre fornecedores, consulte [descrição geral do fornecedor do Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5a800-104">For general information about providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="5a800-105">Para obter exemplos de fornecedores com a funcionalidade mais completa, consulte [Provider Samples](./provider-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5a800-105">For examples of providers with more complete functionality, see [Provider Samples](./provider-samples.md).</span></span>

## <a name="writing-a-basic-provider"></a><span data-ttu-id="5a800-106">Escrever um provedor básico</span><span class="sxs-lookup"><span data-stu-id="5a800-106">Writing a basic provider</span></span>

<span data-ttu-id="5a800-107">É a funcionalidade mais básica de um fornecedor de Windows PowerShell criar e remover unidades.</span><span class="sxs-lookup"><span data-stu-id="5a800-107">The most basic functionality of a Windows PowerShell provider is to create and remove drives.</span></span> <span data-ttu-id="5a800-108">Neste exemplo, podemos implementar o [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) e [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) métodos para o [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="5a800-108">In this example, we implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="5a800-109">Também verá como declarar uma classe de provedor.</span><span class="sxs-lookup"><span data-stu-id="5a800-109">You will also see how to declare a provider class.</span></span>

<span data-ttu-id="5a800-110">Quando escreve um fornecedor, pode especificar unidades-unidades padrão que são criados automaticamente quando o fornecedor está disponível.</span><span class="sxs-lookup"><span data-stu-id="5a800-110">When you write a provider, you can specify default drives-drives that are created automatically when the provider is available.</span></span> <span data-ttu-id="5a800-111">Também define um método para criar novas unidades que usar esse provedor.</span><span class="sxs-lookup"><span data-stu-id="5a800-111">You also define a method to create new drives that use that provider.</span></span>

<span data-ttu-id="5a800-112">Os exemplos fornecidos neste tópico baseiam-se a [AccessDBProviderSample02](./accessdbprovidersample02.md) exemplo, que faz parte de um exemplo maior que representa um banco de dados do Access como uma unidade do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5a800-112">The examples provided in this topic are based on the [AccessDBProviderSample02](./accessdbprovidersample02.md) sample, which is part of a larger sample that represents an Access database as a Windows PowerShell drive.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="5a800-113">Definindo o projeto</span><span class="sxs-lookup"><span data-stu-id="5a800-113">Setting up the project</span></span>

<span data-ttu-id="5a800-114">No Visual Studio, crie um projeto de biblioteca de classes chamado AccessDBProviderSample.</span><span class="sxs-lookup"><span data-stu-id="5a800-114">In Visual Studio, create a Class Library project named AccessDBProviderSample.</span></span> <span data-ttu-id="5a800-115">Conclua os seguintes passos para configurar o seu projeto para que o Windows PowerShell será iniciada e o fornecedor será carregado para a sessão, quando cria e inicie o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="5a800-115">Complete the following steps to configure your project so that Windows PowerShell will start, and the provider will be loaded into the session, when you build and start your project.</span></span>

##### <a name="configure-the-provider-project"></a><span data-ttu-id="5a800-116">Configurar o projeto de fornecedor</span><span class="sxs-lookup"><span data-stu-id="5a800-116">Configure the provider project</span></span>

1. <span data-ttu-id="5a800-117">Adicione o assembly de System.Management.Automation como uma referência ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="5a800-117">Add the System.Management.Automation assembly as a reference to your project.</span></span>

2. <span data-ttu-id="5a800-118">Clique em **projeto > AccessDBProviderSample propriedades > depurar**.</span><span class="sxs-lookup"><span data-stu-id="5a800-118">Click **Project > AccessDBProviderSample Properties > Debug**.</span></span> <span data-ttu-id="5a800-119">Na **projeto inicial**, clique em **programa externo de início**e navegue para o executável do Windows PowerShell (normalmente c:\Windows\System32\WindowsPowerShell\v1.0\\. powershell.exe).</span><span class="sxs-lookup"><span data-stu-id="5a800-119">In **Start project**, click **Start external program**, and navigate to the Windows PowerShell executable (typically c:\Windows\System32\WindowsPowerShell\v1.0\\.powershell.exe).</span></span>

3. <span data-ttu-id="5a800-120">Sob **opções de inicialização**, introduza o seguinte para o **argumentos de linha de comandos** caixa: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span><span class="sxs-lookup"><span data-stu-id="5a800-120">Under **Start Options**, enter the following into the **Command line arguments** box: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="5a800-121">Declarar a classe de fornecedor</span><span class="sxs-lookup"><span data-stu-id="5a800-121">Declaring the provider class</span></span>

<span data-ttu-id="5a800-122">O nosso fornecedor deriva de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="5a800-122">Our provider derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="5a800-123">A maioria dos fornecedores que fornecem a funcionalidade real (acessar e manipular itens, navegar o arquivo de dados e obter e definir o conteúdo de itens) derivam o [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="5a800-123">Most providers that provide real functionality (accessing and manipulating items, navigating the data store, and getting and setting content of items) derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="5a800-124">Para além de especificar que a classe deriva [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), deve decorá-lo com o [ System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) conforme mostrado no exemplo.</span><span class="sxs-lookup"><span data-stu-id="5a800-124">In addition to specifying that the class derives from [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), you must decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) as shown in the example.</span></span>

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

  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : DriveCmdletProvider
  {

}
}
```

### <a name="implementing-newdrive"></a><span data-ttu-id="5a800-125">Implementando NewDrive</span><span class="sxs-lookup"><span data-stu-id="5a800-125">Implementing NewDrive</span></span>

<span data-ttu-id="5a800-126">O [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) método é chamado pelo mecanismo do Windows PowerShell quando um usuário chama o [Microsoft.PowerShell.Commands.New-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive)cmdlet, especificando o nome do seu fornecedor.</span><span class="sxs-lookup"><span data-stu-id="5a800-126">The [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.New-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive) cmdlet specifying the name of your provider.</span></span> <span data-ttu-id="5a800-127">O parâmetro de PSDriveInfo é transmitido pelo mecanismo do Windows PowerShell e o método retorna a nova unidade para o motor do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5a800-127">The PSDriveInfo parameter is passed by the Windows PowerShell engine, and the method returns the new drive to the Windows PowerShell engine.</span></span> <span data-ttu-id="5a800-128">Este método tem de ser declarado dentro da classe criada acima.</span><span class="sxs-lookup"><span data-stu-id="5a800-128">This method must be declared within the class created above.</span></span>

<span data-ttu-id="5a800-129">O método primeiro verifica para se certificar de que o objeto de unidade e a raiz da unidade que foram transmitidos na existem, retornando `null` se qualquer um deles não o fizer.</span><span class="sxs-lookup"><span data-stu-id="5a800-129">The method first checks to make sure both the drive object and the drive root that were passed in exist, returning `null` if either of them do not.</span></span> <span data-ttu-id="5a800-130">Em seguida, utiliza um construtor da classe interna AccessDBPSDriveInfo para criar uma nova unidade e representa uma ligação à base de dados de acesso a unidade.</span><span class="sxs-lookup"><span data-stu-id="5a800-130">It then uses a constructor of the internal class AccessDBPSDriveInfo to create a new drive and a connection to the Access database the drive represents.</span></span>

```csharp
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
    }
```

<span data-ttu-id="5a800-131">Segue-se a classe interna AccessDBPSDriveInfo que inclui o construtor usado para criar uma nova unidade e contém as informações de estado para a unidade.</span><span class="sxs-lookup"><span data-stu-id="5a800-131">The following is the AccessDBPSDriveInfo internal class that includes the constructor used to create a new drive, and contains the state information for the drive.</span></span>

```csharp
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
  }
```

### <a name="implementing-removedrive"></a><span data-ttu-id="5a800-132">Implementando RemoveDrive</span><span class="sxs-lookup"><span data-stu-id="5a800-132">Implementing RemoveDrive</span></span>

<span data-ttu-id="5a800-133">O [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) método é chamado pelo mecanismo do Windows PowerShell quando um usuário chama o [Microsoft.PowerShell.Commands.Remove-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5a800-133">The [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.Remove-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) cmdlet.</span></span> <span data-ttu-id="5a800-134">O método nesse provedor fecha a conexão com o banco de dados do Access.</span><span class="sxs-lookup"><span data-stu-id="5a800-134">The method in this provider closes the connection to the Access database.</span></span>

```csharp
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
    }
```