---
title: Escrever um fornecedor de item | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 606c880c-6cf1-4ea6-8730-dbf137bfabff
caps.latest.revision: 5
ms.openlocfilehash: e3289e9336b863b5e0998a2beb29353c82a31f79
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847307"
---
# <a name="writing-an-item-provider"></a>Writing an item provider (Escrever um fornecedor de itens)

Este tópico descreve como implementar os métodos de um fornecedor de Windows PowerShell que acessar e manipulam itens no arquivo de dados. Para poder aceder aos itens, um fornecedor deve derivar do [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.

O fornecedor nos exemplos deste tópico utiliza uma base de dados de acesso como seu arquivo de dados. Existem vários métodos auxiliares e classes que são utilizados para interagir com a base de dados. Para o exemplo completo que inclui os métodos auxiliares, consulte [AccessDBProviderSample03](./accessdbprovidersample03.md)

Para obter mais informações sobre os fornecedores de Windows PowerShell, consulte [descrição geral do fornecedor do Windows PowerShell](./windows-powershell-provider-overview.md).

## <a name="implementing-item-methods"></a>Implementar métodos de item

O [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe expõe vários métodos que podem ser usados para acessar e manipular os itens num arquivo de dados. Para obter uma lista completa destes métodos, consulte [ItemCmdletProvider métodos](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx). Neste exemplo, podemos implementará quatro desses métodos. [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) obtém um item num caminho especificado. [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) define o valor do item especificado. [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) verifica se existe um item no caminho especificado. [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) verifica um caminho para ver se ele mapeia para uma localização no arquivo de dados.

> [!NOTE]
> Este tópico baseia-se nas informações da [guia de introdução do Windows PowerShell fornecedor](./windows-powershell-provider-quickstart.md). Este tópico não abrange as noções básicas de como configurar um projeto de fornecedor, ou como implementar os métodos herdada a partir da [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe que criar e remover unidades.

### <a name="declaring-the-provider-class"></a>Declarar a classe de fornecedor

Declarar o fornecedor de derivar a partir da [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) de classe e decorá-lo com o [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a>Implementando GetItem

O [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) é chamado pelo mecanismo do PowerShell quando um usuário chama o [Microsoft.Powershell.Commands.Get Item](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) cmdlet no seu fornecedor. O método retorna o item no caminho especificado. O exemplo de base de dados de acesso, o método verifica se o item é a unidade em si, uma tabela na base de dados ou uma linha na base de dados. O método envia o item para o motor do PowerShell ao chamar o [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) método.

```csharp
protected override void GetItem(string path)
      {
          // check if the path represented is a drive
          if (PathIsDrive(path))
          {
              WriteItemObject(this.PSDriveInfo, path, true);
              return;
          }// if (PathIsDrive...

           // Get table name and row information from the path and do
           // necessary actions
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               DatabaseTableInfo table = GetTable(tableName);
               WriteItemObject(table, path, true);
           }
           else if (type == PathType.Row)
           {
               DatabaseRowInfo row = GetRow(tableName, rowNumber);
               WriteItemObject(row, path, false);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

       }
```

### <a name="implementing-setitem"></a>Implementando SetItem

O [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) método é chamado pelas chamadas de motor do PowerShell quando um usuário chama o [Microsoft.Powershell.Commands.Set Item](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) cmdlet . Ele define o valor do item no caminho especificado.

O exemplo de base de dados de acesso, faz sentido definir o valor de um item somente se esse item é uma linha, para que o método lançar [NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) quando o item não é uma linha.

```csharp
protected override void SetItem(string path, object values)
       {
           // Get type, table name and row number from the path specified
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type != PathType.Row)
           {
               WriteError(new ErrorRecord(new NotSupportedException(
                     "SetNotSupported"), "",
                  ErrorCategory.InvalidOperation, path));

               return;
           }

           // Get in-memory representation of table
           OdbcDataAdapter da = GetAdapterForTable(tableName);

           if (da == null)
           {
               return;
           }
           DataSet ds = GetDataSetForTable(da, tableName);
           DataTable table = GetDataTable(ds, tableName);

           if (rowNumber >= table.Rows.Count)
           {
               // The specified row number has to be available. If not
               // NewItem has to be used to add a new row
               throw new ArgumentException("Row specified is not available");
           } // if (rowNum...

           string[] colValues = (values as string).Split(',');

           // set the specified row
           DataRow row = table.Rows[rowNumber];

           for (int i = 0; i < colValues.Length; i++)
           {
               row[i] = colValues[i];
           }

           // Update the table
           if (ShouldProcess(path, "SetItem"))
           {
               da.Update(ds, tableName);
           }

       }
```

### <a name="implementing-itemexists"></a>Implementando ItemExists

O [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) método é chamado pelo mecanismo do PowerShell quando um usuário chama o [Microsoft.Powershell.Commands.Test caminho](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) cmdlet. O método determina se existe um item no caminho especificado. Se o item existir, o método passa-o novamente para o motor do PowerShell ao chamar [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).

```csharp
protected override bool ItemExists(string path)
       {
           // check if the path represented is a drive
           if (PathIsDrive(path))
           {
               return true;
           }

           // Obtain type, table name and row number from path
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           DatabaseTableInfo table = GetTable(tableName);

           if (type == PathType.Table)
           {
               // if specified path represents a table then DatabaseTableInfo
               // object for the same should exist
               if (table != null)
               {
                   return true;
               }
           }
           else if (type == PathType.Row)
           {
               // if specified path represents a row then DatabaseTableInfo should
               // exist for the table and then specified row number must be within
               // the maximum row count in the table
               if (table != null && rowNumber < table.RowCount)
               {
                   return true;
               }
           }

           return false;

       }
```

### <a name="implementing-isvalidpath"></a>Implementando IsValidPath

O [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) método verifica se o caminho especificado é sintaticamente válido para o fornecedor atual. Não verifica se existe um item no caminho.

```csharp
protected override bool IsValidPath(string path)
       {
           bool result = true;

           // check if the path is null or empty
           if (String.IsNullOrEmpty(path))
           {
               result = false;
           }

           // convert all separators in the path to a uniform one
           path = NormalizePath(path);

           // split the path into individual chunks
           string[] pathChunks = path.Split(pathSeparator.ToCharArray());

           foreach (string pathChunk in pathChunks)
           {
               if (pathChunk.Length == 0)
               {
                   result = false;
               }
           }
           return result;
       }
```

## <a name="next-steps"></a>Próximos passos

Um provedor típico do mundo real é capaz de oferecer suporte a itens que contêm outros itens e de mover os itens de um caminho para outra numa unidade. Para obter um exemplo de um fornecedor que suporte contentores, veja [escrevendo um provedor de contentor](./writing-a-container-provider.md). Para obter um exemplo de um fornecedor que suporte move itens, consulte [escrevendo um provedor de navegação](./writing-a-navigation-provider.md).

## <a name="see-also"></a>Veja Também

[Escrever um provedor de contentor](./writing-a-container-provider.md)

[Escrever um provedor de navegação](./writing-a-navigation-provider.md)

[Descrição geral de fornecedor do PowerShell do Windows](./windows-powershell-provider-overview.md)