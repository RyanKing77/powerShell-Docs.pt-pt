---
title: Escrever um provedor de navegação | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98bcfda0-6ee2-46f5-bbc7-5fab8b780d6a
caps.latest.revision: 5
ms.openlocfilehash: f449c17e4c373c42f8a1d96fa9075940111c65bc
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056599"
---
# <a name="writing-a-navigation-provider"></a><span data-ttu-id="8a72a-102">Writing a navigation provider (Escrever um fornecedor de navegação)</span><span class="sxs-lookup"><span data-stu-id="8a72a-102">Writing a navigation provider</span></span>

<span data-ttu-id="8a72a-103">Este tópico descreve como implementar os métodos de um fornecedor de Windows PowerShell que suportam contêineres aninhados (arquivos de dados de vários níveis), mover itens e caminhos relativos.</span><span class="sxs-lookup"><span data-stu-id="8a72a-103">This topic describes how to implement the methods of a Windows PowerShell provider that support nested containers (multi-level data stores), moving items, and relative paths.</span></span> <span data-ttu-id="8a72a-104">Um provedor de navegação deve derivar do [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="8a72a-104">A navigation provider must derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="8a72a-105">O fornecedor nos exemplos deste tópico utiliza uma base de dados de acesso como seu arquivo de dados.</span><span class="sxs-lookup"><span data-stu-id="8a72a-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="8a72a-106">Existem vários métodos auxiliares e classes que são utilizados para interagir com a base de dados.</span><span class="sxs-lookup"><span data-stu-id="8a72a-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="8a72a-107">Para o exemplo completo que inclui os métodos auxiliares, consulte [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="8a72a-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>

<span data-ttu-id="8a72a-108">Para obter mais informações sobre os fornecedores de Windows PowerShell, consulte [descrição geral do fornecedor do Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8a72a-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-navigation-methods"></a><span data-ttu-id="8a72a-109">Implementar métodos de navegação</span><span class="sxs-lookup"><span data-stu-id="8a72a-109">Implementing navigation methods</span></span>

<span data-ttu-id="8a72a-110">O [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe implementa métodos que suportam contêineres aninhados, caminhos relativos e move itens.</span><span class="sxs-lookup"><span data-stu-id="8a72a-110">The [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class implements methods that support nested containers, relative paths, and moving items.</span></span> <span data-ttu-id="8a72a-111">Para obter uma lista completa destes métodos, consulte [NavigationCmdletProvider métodos](http://msdn.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider_methods\(v=vs.85\).aspx).</span><span class="sxs-lookup"><span data-stu-id="8a72a-111">For a complete list of these methods, see [NavigationCmdletProvider Methods](http://msdn.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider_methods\(v=vs.85\).aspx).</span></span>

> [!NOTE]
> <span data-ttu-id="8a72a-112">Este tópico baseia-se nas informações da [guia de introdução do Windows PowerShell fornecedor](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="8a72a-112">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="8a72a-113">Este tópico não abrange as noções básicas de como configurar um projeto de fornecedor, ou como implementar os métodos herdada a partir da [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe que criar e remover unidades.</span><span class="sxs-lookup"><span data-stu-id="8a72a-113">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span> <span data-ttu-id="8a72a-114">Este tópico também não abrange como implementar os métodos expostos pelos [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) ou [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classes.</span><span class="sxs-lookup"><span data-stu-id="8a72a-114">This topic also does not cover how to implement methods exposed by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) or [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classes.</span></span> <span data-ttu-id="8a72a-115">Para obter um exemplo que mostra como implementar o item cmdlets, consulte [escrever um fornecedor de item](./writing-an-item-provider.md).</span><span class="sxs-lookup"><span data-stu-id="8a72a-115">For an example that shows how to implement item cmdlets, see [Writing an item provider](./writing-an-item-provider.md).</span></span> <span data-ttu-id="8a72a-116">Para obter um exemplo que mostra como implementar o contentor cmdlets, consulte [escrevendo um provedor de contentor](./writing-a-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="8a72a-116">For an example that shows how to implement container cmdlets, see [Writing a container provider](./writing-a-container-provider.md).</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="8a72a-117">Declarar a classe de fornecedor</span><span class="sxs-lookup"><span data-stu-id="8a72a-117">Declaring the provider class</span></span>

<span data-ttu-id="8a72a-118">Declarar o fornecedor de derivar a partir da [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) de classe e decorá-lo com o [System.Management.Automation.Provider.Cmdletproviderattribute ](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="8a72a-118">Declare the provider to derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a><span data-ttu-id="8a72a-119">Implementando IsItemContainer</span><span class="sxs-lookup"><span data-stu-id="8a72a-119">Implementing IsItemContainer</span></span>

<span data-ttu-id="8a72a-120">O [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) método verifica se o item no caminho especificado é um contentor.</span><span class="sxs-lookup"><span data-stu-id="8a72a-120">The [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method checks whether the item at the specified path is a container.</span></span>

```csharp
protected override bool IsItemContainer(string path)
      {
         if (PathIsDrive(path))
         {
             return true;
         }

         string[] pathChunks = ChunkPath(path);
         string tableName;
         int rowNumber;

         PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

         if (type == PathType.Table)
         {
            foreach (DatabaseTableInfo ti in GetTables())
            {
                if (string.Equals(ti.Name, tableName, StringComparison.OrdinalIgnoreCase))
                {
                    return true;
                }
            } // foreach (DatabaseTableInfo...
         } // if (pathChunks...

         return false;
      }
```

### <a name="implementing-getchildname"></a><span data-ttu-id="8a72a-121">Implementando GetChildName</span><span class="sxs-lookup"><span data-stu-id="8a72a-121">Implementing GetChildName</span></span>

<span data-ttu-id="8a72a-122">O [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) método obtém a propriedade de nome do item subordinado no caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="8a72a-122">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method gets the name property of the child item at the specified path.</span></span> <span data-ttu-id="8a72a-123">Se o item no caminho especificado não é um filho de um contentor, em seguida, esse método deve retornar o caminho.</span><span class="sxs-lookup"><span data-stu-id="8a72a-123">If the item at the specified path is not a child of a container, then this method should return the path.</span></span>

```csharp
protected override string GetChildName(string path)
       {
           if (PathIsDrive(path))
           {
               return path;
           }

           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               return tableName;
           }
           else if (type == PathType.Row)
           {
               return rowNumber.ToString(CultureInfo.CurrentCulture);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

           return null;
       }
```

### <a name="implementing-getparentpath"></a><span data-ttu-id="8a72a-124">Implementando GetParentPath</span><span class="sxs-lookup"><span data-stu-id="8a72a-124">Implementing GetParentPath</span></span>

<span data-ttu-id="8a72a-125">O [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) método obtém o caminho do principal do item no caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="8a72a-125">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method gets the path of the parent of the item at the specified path.</span></span> <span data-ttu-id="8a72a-126">Se o item no caminho especificado é a raiz do arquivo de dados (para que ele não tem elemento principal), em seguida, esse método deve retornar o caminho da raiz.</span><span class="sxs-lookup"><span data-stu-id="8a72a-126">If the item at the specified path is the root of the data store (so it has no parent), then this method should return the root path.</span></span>

```csharp
protected override string GetParentPath(string path, string root)
       {
           // If root is specified then the path has to contain
           // the root. If not nothing should be returned
           if (!String.IsNullOrEmpty(root))
           {
               if (!path.Contains(root))
               {
                   return null;
               }
           }

           return path.Substring(0, path.LastIndexOf(pathSeparator, StringComparison.OrdinalIgnoreCase));
       }
```

### <a name="implementing-makepath"></a><span data-ttu-id="8a72a-127">Implementando MakePath</span><span class="sxs-lookup"><span data-stu-id="8a72a-127">Implementing MakePath</span></span>

<span data-ttu-id="8a72a-128">O [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) método é associado um caminho principal especificado e um caminho de subordinado especificado para criar um caminho de fornecedor interna (para obter informações sobre o caminho de tipos que fornecedores de pode suportar, consulte [descrição geral do fornecedor do Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8a72a-128">The [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method joins a specified parent path and a specified child path to create a provider-internal path (for information about path types that providers can support, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="8a72a-129">O motor do PowerShell chama esse método quando um usuário chama o [Microsoft.PowerShell.Commands.Join caminho](/dotnet/api/Microsoft.PowerShell.Commands.Join-Path) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8a72a-129">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.Join-Path](/dotnet/api/Microsoft.PowerShell.Commands.Join-Path) cmdlet.</span></span>

```csharp
protected override string MakePath(string parent, string child)
       {
           string result;

           string normalParent = NormalizePath(parent);
           normalParent = RemoveDriveFromPath(normalParent);
           string normalChild = NormalizePath(child);
           normalChild = RemoveDriveFromPath(normalChild);

           if (String.IsNullOrEmpty(normalParent) && String.IsNullOrEmpty(normalChild))
           {
               result = String.Empty;
           }
           else if (String.IsNullOrEmpty(normalParent) && !String.IsNullOrEmpty(normalChild))
           {
               result = normalChild;
           }
           else if (!String.IsNullOrEmpty(normalParent) && String.IsNullOrEmpty(normalChild))
           {
               if (normalParent.EndsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result = normalParent;
               }
               else
               {
                   result = normalParent + pathSeparator;
               }
           } // else if (!String...
           else
           {
               if (!normalParent.Equals(String.Empty) &&
                   !normalParent.EndsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result = normalParent + pathSeparator;
               }
               else
               {
                   result = normalParent;
               }

               if (normalChild.StartsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result += normalChild.Substring(1);
               }
               else
               {
                   result += normalChild;
               }
           } // else

           return result;
       }
```

### <a name="implementing-normalizerelativepath"></a><span data-ttu-id="8a72a-130">Implementing NormalizeRelativePath</span><span class="sxs-lookup"><span data-stu-id="8a72a-130">Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="8a72a-131">O [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) leva `path` e `basepath` parâmetros e retorna um caminho normalizado que é equivalente a `path`parâmetro e o caminho relativo a `basepath` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8a72a-131">The [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method takes `path` and `basepath` parameters, and returns a normalized path that is equivalent to the `path` parameter and relative to the `basepath` parameter.</span></span>

```csharp
protected override string NormalizeRelativePath(string path,
                                                            string basepath)
       {
           // Normalize the paths first
           string normalPath = NormalizePath(path);
           normalPath = RemoveDriveFromPath(normalPath);
           string normalBasePath = NormalizePath(basepath);
           normalBasePath = RemoveDriveFromPath(normalBasePath);

           if (String.IsNullOrEmpty(normalBasePath))
           {
               return normalPath;
           }
           else
           {
               if (!normalPath.Contains(normalBasePath))
               {
                   return null;
               }

               return normalPath.Substring(normalBasePath.Length + pathSeparator.Length);
           }
       }
```

### <a name="implementing-moveitem"></a><span data-ttu-id="8a72a-132">Implementando MoveItem</span><span class="sxs-lookup"><span data-stu-id="8a72a-132">Implementing MoveItem</span></span>

<span data-ttu-id="8a72a-133">O [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) método move um item do caminho especificado para o caminho de destino especificado.</span><span class="sxs-lookup"><span data-stu-id="8a72a-133">The [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method moves an item from the specified path to the specified destination path.</span></span> <span data-ttu-id="8a72a-134">O motor do PowerShell chama esse método quando um usuário chama o [Microsoft.PowerShell.Commands.Move Item](/dotnet/api/Microsoft.PowerShell.Commands.Move-Item) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8a72a-134">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.Move-Item](/dotnet/api/Microsoft.PowerShell.Commands.Move-Item) cmdlet.</span></span>

```csharp
protected override void MoveItem(string path, string destination)
       {
           // Get type, table name and rowNumber from the path
           string tableName, destTableName;
           int rowNumber, destRowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           PathType destType = GetNamesFromPath(destination, out destTableName,
                                    out destRowNumber);

           if (type == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(path);
           }

           if (destType == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(destination);
           }

           if (type == PathType.Table)
           {
               ArgumentException e = new ArgumentException("Move not supported for tables");

               WriteError(new ErrorRecord(e, "MoveNotSupported",
                   ErrorCategory.InvalidArgument, path));

               throw e;
           }
           else
           {
               OdbcDataAdapter da = GetAdapterForTable(tableName);
               if (da == null)
               {
                   return;
               }

               DataSet ds = GetDataSetForTable(da, tableName);
               DataTable table = GetDataTable(ds, tableName);

               OdbcDataAdapter dda = GetAdapterForTable(destTableName);
               if (dda == null)
               {
                   return;
               }

               DataSet dds = GetDataSetForTable(dda, destTableName);
               DataTable destTable = GetDataTable(dds, destTableName);
               DataRow row = table.Rows[rowNumber];

               if (destType == PathType.Table)
               {
                   DataRow destRow = destTable.NewRow();

                   destRow.ItemArray = row.ItemArray;
               }
               else
               {
                   DataRow destRow = destTable.Rows[destRowNumber];

                   destRow.ItemArray = row.ItemArray;
               }

               // Update the changes
               if (ShouldProcess(path, "MoveItem"))
               {
                   WriteItemObject(row, path, false);
                   dda.Update(dds, destTableName);
               }
           }
       }
```

## <a name="see-also"></a><span data-ttu-id="8a72a-135">Veja Também</span><span class="sxs-lookup"><span data-stu-id="8a72a-135">See Also</span></span>

[<span data-ttu-id="8a72a-136">Escrever um provedor de contentor</span><span class="sxs-lookup"><span data-stu-id="8a72a-136">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="8a72a-137">Descrição geral de fornecedor do PowerShell do Windows</span><span class="sxs-lookup"><span data-stu-id="8a72a-137">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)