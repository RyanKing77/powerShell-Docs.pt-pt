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
# <a name="writing-an-item-provider"></a><span data-ttu-id="81c4a-102">Writing an item provider (Escrever um fornecedor de itens)</span><span class="sxs-lookup"><span data-stu-id="81c4a-102">Writing an item provider</span></span>

<span data-ttu-id="81c4a-103">Este tópico descreve como implementar os métodos de um fornecedor de Windows PowerShell que acessar e manipulam itens no arquivo de dados.</span><span class="sxs-lookup"><span data-stu-id="81c4a-103">This topic describes how to implement the methods of a Windows PowerShell provider that access and manipulate items in the data store.</span></span> <span data-ttu-id="81c4a-104">Para poder aceder aos itens, um fornecedor deve derivar do [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="81c4a-104">To be able to access items, a provider must derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

<span data-ttu-id="81c4a-105">O fornecedor nos exemplos deste tópico utiliza uma base de dados de acesso como seu arquivo de dados.</span><span class="sxs-lookup"><span data-stu-id="81c4a-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="81c4a-106">Existem vários métodos auxiliares e classes que são utilizados para interagir com a base de dados.</span><span class="sxs-lookup"><span data-stu-id="81c4a-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="81c4a-107">Para o exemplo completo que inclui os métodos auxiliares, consulte [AccessDBProviderSample03](./accessdbprovidersample03.md)</span><span class="sxs-lookup"><span data-stu-id="81c4a-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample03](./accessdbprovidersample03.md)</span></span>

<span data-ttu-id="81c4a-108">Para obter mais informações sobre os fornecedores de Windows PowerShell, consulte [descrição geral do fornecedor do Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="81c4a-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-item-methods"></a><span data-ttu-id="81c4a-109">Implementar métodos de item</span><span class="sxs-lookup"><span data-stu-id="81c4a-109">Implementing item methods</span></span>

<span data-ttu-id="81c4a-110">O [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe expõe vários métodos que podem ser usados para acessar e manipular os itens num arquivo de dados.</span><span class="sxs-lookup"><span data-stu-id="81c4a-110">The [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class exposes several methods that can be used to access and manipulate the items in a data store.</span></span> <span data-ttu-id="81c4a-111">Para obter uma lista completa destes métodos, consulte [ItemCmdletProvider métodos](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx).</span><span class="sxs-lookup"><span data-stu-id="81c4a-111">For a complete list of these methods, see [ItemCmdletProvider Methods](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx).</span></span> <span data-ttu-id="81c4a-112">Neste exemplo, podemos implementará quatro desses métodos.</span><span class="sxs-lookup"><span data-stu-id="81c4a-112">In this example, we will implement four of these methods.</span></span> <span data-ttu-id="81c4a-113">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) obtém um item num caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="81c4a-113">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) gets an item at a specified path.</span></span> <span data-ttu-id="81c4a-114">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) define o valor do item especificado.</span><span class="sxs-lookup"><span data-stu-id="81c4a-114">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) sets the value of the specified item.</span></span> <span data-ttu-id="81c4a-115">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) verifica se existe um item no caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="81c4a-115">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) checks whether an item exists at the specified path.</span></span> <span data-ttu-id="81c4a-116">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) verifica um caminho para ver se ele mapeia para uma localização no arquivo de dados.</span><span class="sxs-lookup"><span data-stu-id="81c4a-116">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) checks a path to see if it maps to a location in the data store.</span></span>

> [!NOTE]
> <span data-ttu-id="81c4a-117">Este tópico baseia-se nas informações da [guia de introdução do Windows PowerShell fornecedor](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="81c4a-117">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="81c4a-118">Este tópico não abrange as noções básicas de como configurar um projeto de fornecedor, ou como implementar os métodos herdada a partir da [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe que criar e remover unidades.</span><span class="sxs-lookup"><span data-stu-id="81c4a-118">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="81c4a-119">Declarar a classe de fornecedor</span><span class="sxs-lookup"><span data-stu-id="81c4a-119">Declaring the provider class</span></span>

<span data-ttu-id="81c4a-120">Declarar o fornecedor de derivar a partir da [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) de classe e decorá-lo com o [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="81c4a-120">Declare the provider to derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a><span data-ttu-id="81c4a-121">Implementando GetItem</span><span class="sxs-lookup"><span data-stu-id="81c4a-121">Implementing GetItem</span></span>

<span data-ttu-id="81c4a-122">O [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) é chamado pelo mecanismo do PowerShell quando um usuário chama o [Microsoft.Powershell.Commands.Get Item](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) cmdlet no seu fornecedor.</span><span class="sxs-lookup"><span data-stu-id="81c4a-122">The [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) is called by the PowerShell engine when a user calls the [Microsoft.Powershell.Commands.Get-Item](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) cmdlet on your provider.</span></span> <span data-ttu-id="81c4a-123">O método retorna o item no caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="81c4a-123">The method returns the item at the specified path.</span></span> <span data-ttu-id="81c4a-124">O exemplo de base de dados de acesso, o método verifica se o item é a unidade em si, uma tabela na base de dados ou uma linha na base de dados.</span><span class="sxs-lookup"><span data-stu-id="81c4a-124">In the Access database example, the method checks whether the item is the drive itself, a table in the database, or a row in the database.</span></span> <span data-ttu-id="81c4a-125">O método envia o item para o motor do PowerShell ao chamar o [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) método.</span><span class="sxs-lookup"><span data-stu-id="81c4a-125">The method sends the item to the PowerShell engine by calling the [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) method.</span></span>

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

### <a name="implementing-setitem"></a><span data-ttu-id="81c4a-126">Implementando SetItem</span><span class="sxs-lookup"><span data-stu-id="81c4a-126">Implementing SetItem</span></span>

<span data-ttu-id="81c4a-127">O [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) método é chamado pelas chamadas de motor do PowerShell quando um usuário chama o [Microsoft.Powershell.Commands.Set Item](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) cmdlet .</span><span class="sxs-lookup"><span data-stu-id="81c4a-127">The [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method is called by the PowerShell engine calls when a user calls the [Microsoft.Powershell.Commands.Set-Item](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) cmdlet.</span></span> <span data-ttu-id="81c4a-128">Ele define o valor do item no caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="81c4a-128">It sets the value of the item at the specified path.</span></span>

<span data-ttu-id="81c4a-129">O exemplo de base de dados de acesso, faz sentido definir o valor de um item somente se esse item é uma linha, para que o método lançar [NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) quando o item não é uma linha.</span><span class="sxs-lookup"><span data-stu-id="81c4a-129">In the Access database example, it makes sense to set the value of an item only if that item is a row, so the method throws [NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) when the item is not a row.</span></span>

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

### <a name="implementing-itemexists"></a><span data-ttu-id="81c4a-130">Implementando ItemExists</span><span class="sxs-lookup"><span data-stu-id="81c4a-130">Implementing ItemExists</span></span>

<span data-ttu-id="81c4a-131">O [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) método é chamado pelo mecanismo do PowerShell quando um usuário chama o [Microsoft.Powershell.Commands.Test caminho](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="81c4a-131">The [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method is called by the PowerShell engine when a user calls the [Microsoft.Powershell.Commands.Test-Path](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) cmdlet.</span></span> <span data-ttu-id="81c4a-132">O método determina se existe um item no caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="81c4a-132">The method determines whether there is an item at the specified path.</span></span> <span data-ttu-id="81c4a-133">Se o item existir, o método passa-o novamente para o motor do PowerShell ao chamar [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span><span class="sxs-lookup"><span data-stu-id="81c4a-133">If the item does exist, the method passes it back to the PowerShell engine by calling [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span></span>

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

### <a name="implementing-isvalidpath"></a><span data-ttu-id="81c4a-134">Implementando IsValidPath</span><span class="sxs-lookup"><span data-stu-id="81c4a-134">Implementing IsValidPath</span></span>

<span data-ttu-id="81c4a-135">O [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) método verifica se o caminho especificado é sintaticamente válido para o fornecedor atual.</span><span class="sxs-lookup"><span data-stu-id="81c4a-135">The [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method checks whether the specified path is syntactically valid for the current provider.</span></span> <span data-ttu-id="81c4a-136">Não verifica se existe um item no caminho.</span><span class="sxs-lookup"><span data-stu-id="81c4a-136">It does not check whether an item exists at the path.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="81c4a-137">Próximos passos</span><span class="sxs-lookup"><span data-stu-id="81c4a-137">Next steps</span></span>

<span data-ttu-id="81c4a-138">Um provedor típico do mundo real é capaz de oferecer suporte a itens que contêm outros itens e de mover os itens de um caminho para outra numa unidade.</span><span class="sxs-lookup"><span data-stu-id="81c4a-138">A typical real-world provider is capable of supporting items that contain other items, and of moving items from one path to another within the drive.</span></span> <span data-ttu-id="81c4a-139">Para obter um exemplo de um fornecedor que suporte contentores, veja [escrevendo um provedor de contentor](./writing-a-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="81c4a-139">For an example of a provider that supports containers, see [Writing a container provider](./writing-a-container-provider.md).</span></span> <span data-ttu-id="81c4a-140">Para obter um exemplo de um fornecedor que suporte move itens, consulte [escrevendo um provedor de navegação](./writing-a-navigation-provider.md).</span><span class="sxs-lookup"><span data-stu-id="81c4a-140">For an example of a provider that supports moving items, see [Writing a navigation provider](./writing-a-navigation-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="81c4a-141">Veja Também</span><span class="sxs-lookup"><span data-stu-id="81c4a-141">See Also</span></span>

[<span data-ttu-id="81c4a-142">Escrever um provedor de contentor</span><span class="sxs-lookup"><span data-stu-id="81c4a-142">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="81c4a-143">Escrever um provedor de navegação</span><span class="sxs-lookup"><span data-stu-id="81c4a-143">Writing a navigation provider</span></span>](./writing-a-navigation-provider.md)

[<span data-ttu-id="81c4a-144">Descrição geral de fornecedor do PowerShell do Windows</span><span class="sxs-lookup"><span data-stu-id="81c4a-144">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)