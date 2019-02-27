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
ms.openlocfilehash: ab78bcad301215bca9b5324bdb8de863899edec6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851115"
---
# <a name="windows-powershell-provider-quickstart"></a>Windows PowerShell Provider Quickstart (Guia de Início Rápido do Fornecedor do Windows PowerShell)

Este tópico explica como criar um fornecedor de Windows PowerShell com a funcionalidade básica de criação de uma nova unidade. Para obter informações gerais sobre fornecedores, consulte [descrição geral do fornecedor do Windows PowerShell](./windows-powershell-provider-overview.md). Para obter exemplos de fornecedores com a funcionalidade mais completa, consulte [Provider Samples](./provider-samples.md).

## <a name="writing-a-basic-provider"></a>Escrever um provedor básico

É a funcionalidade mais básica de um fornecedor de Windows PowerShell criar e remover unidades. Neste exemplo, podemos implementar o [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) e [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) métodos para o [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe. Também verá como declarar uma classe de provedor.

Quando escreve um fornecedor, pode especificar unidades-unidades padrão que são criados automaticamente quando o fornecedor está disponível. Também define um método para criar novas unidades que usar esse provedor.

Os exemplos fornecidos neste tópico baseiam-se a [AccessDBProviderSample02](./accessdbprovidersample02.md) exemplo, que faz parte de um exemplo maior que representa um banco de dados do Access como uma unidade do Windows PowerShell.

### <a name="setting-up-the-project"></a>Definindo o projeto

No Visual Studio, crie um projeto de biblioteca de classes chamado AccessDBProviderSample. Conclua os seguintes passos para configurar o seu projeto para que o Windows PowerShell será iniciada e o fornecedor será carregado para a sessão, quando cria e inicie o seu projeto.

##### <a name="configure-the-provider-project"></a>Configurar o projeto de fornecedor

1. Adicione o assembly de System.Management.Automation como uma referência ao seu projeto.

2. Clique em **projeto > AccessDBProviderSample propriedades > depurar**. Na **projeto inicial**, clique em **programa externo de início**e navegue para o executável do Windows PowerShell (normalmente c:\Windows\System32\WindowsPowerShell\v1.0\\. powershell.exe).

3. Sob **opções de inicialização**, introduza o seguinte para o **argumentos de linha de comandos** caixa: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`

### <a name="declaring-the-provider-class"></a>Declarar a classe de fornecedor

O nosso fornecedor deriva de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe. A maioria dos fornecedores que fornecem a funcionalidade real (acessar e manipular itens, navegar o arquivo de dados e obter e definir o conteúdo de itens) derivam o [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.

Para além de especificar que a classe deriva [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), deve decorá-lo com o [ System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) conforme mostrado no exemplo.

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

### <a name="implementing-newdrive"></a>Implementando NewDrive

O [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) método é chamado pelo mecanismo do Windows PowerShell quando um usuário chama o [Microsoft.Powershell.Commands.New-Psdrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive)cmdlet, especificando o nome do seu fornecedor. O parâmetro de PSDriveInfo é transmitido pelo mecanismo do Windows PowerShell e o método retorna a nova unidade para o motor do Windows PowerShell. Este método tem de ser declarado dentro da classe criada acima.

O método primeiro verifica para se certificar de que o objeto de unidade e a raiz da unidade que foram transmitidos na existem, retornando `null` se qualquer um deles não o fizer. Em seguida, utiliza um construtor da classe interna AccessDBPSDriveInfo para criar uma nova unidade e representa uma ligação à base de dados de acesso a unidade.

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

Segue-se a classe interna AccessDBPSDriveInfo que inclui o construtor usado para criar uma nova unidade e contém as informações de estado para a unidade.

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

### <a name="implementing-removedrive"></a>Implementando RemoveDrive

O [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) método é chamado pelo mecanismo do Windows PowerShell quando um usuário chama o [Microsoft.Powershell.Commands.Remove-Psdrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) cmdlet. O método nesse provedor fecha a conexão com o banco de dados do Access.

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