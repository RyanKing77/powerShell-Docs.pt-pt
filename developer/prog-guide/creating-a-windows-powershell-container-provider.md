---
title: Criar um fornecedor de contentor do Windows PowerShell | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], container provider
- container providers [PowerShell Programmer's Guide]
ms.assetid: a7926647-0d18-45b2-967e-b31f92004bc4
caps.latest.revision: 5
ms.openlocfilehash: 33effed9a96cf1b9ee5f1a50b60a1937526db9d1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081908"
---
# <a name="creating-a-windows-powershell-container-provider"></a>Creating a Windows PowerShell Container Provider (Criar um Fornecedor de Contentores do Windows PowerShell)

Este tópico descreve como criar um fornecedor de Windows PowerShell que pode trabalhar nos arquivos de dados de camada multi. Para este tipo de arquivo de dados, o nível superior do arquivo contém os itens de raiz e cada nível subseqüente é referido como um nó de itens subordinados. Ao permitir que o utilizador trabalhar em de nós subordinados, um usuário pode interagir hierarquicamente por meio do arquivo de dados.

Fornecedores que podem trabalhar nos arquivos de dados de múltiplos níveis são referidos como fornecedores de contentor do Windows PowerShell. No entanto, lembre-se de que um fornecedor de contentor do Windows PowerShell pode ser usado apenas quando existe um contentor (não existem contentores aninhadas) com os itens no mesmo. Se existirem contêineres aninhados, em seguida, deve implementar um fornecedor de navegação do Windows PowerShell. Para obter mais informações sobre a implementação de fornecedor de navegação do Windows PowerShell, consulte [criar um fornecedor de navegação do Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md).

> [!NOTE]
> Pode transferir o C# ficheiro de origem (AccessDBSampleProvider04.cs) para este fornecedor com o Microsoft Windows Software Development Kit para Windows Vista e o .NET Framework 3.0 Runtime Components. Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Os arquivos de fonte transferido estão disponíveis no  **\<exemplos do PowerShell >** diretório.
>
> Para obter mais informações sobre outras implementações de provedores do Windows PowerShell, consulte [conceber Windows PowerShell Fornecedor_de_e](./designing-your-windows-powershell-provider.md).

O fornecedor de contentor do Windows PowerShell descrito aqui define a base de dados como respetivo contentor único, com as tabelas e linhas de base de dados definidos como itens do contentor.

> [!CAUTION]
> Lembre-se de que esse design supõe que uma base de dados que tem um campo com o ID de nome e de que o tipo do campo é LongInteger.

Aqui está uma lista das secções seguintes deste tópico. Se não estiver familiarizado com a escrita de um fornecedor de contentor do Windows PowerShell, leia estas informações na ordem em que ele é exibido. No entanto, se estiver familiarizado com a escrita de um fornecedor de contentor do Windows PowerShell, aceda diretamente às informações de que precisa.

- [Definir uma classe de fornecedor de contentor do Windows PowerShell](#Defining-a-Windows-PowerShell-Container-Provider-Class)

- [Definir funcionalidade de Base](#defining-base-functionality)

- [A obter itens subordinados](#Retrieving-Child-Items)

- [Os parâmetros dinâmicos para a anexar o `Get-ChildItem` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-ChildItem-Cmdlet)

- [Obter os nomes de Item subordinado](#Retrieving-Child-Item-Names)

- [Os parâmetros dinâmicos para a anexar o `Get-ChildItem` Cmdlet (nome)](#Attaching-Dynamic-Parameters-to-the-Get-ChildItem-Cmdlet-(Name))

- [Mudar o nome de itens](#Renaming-Items)

- [Os parâmetros dinâmicos para a anexar o `Rename-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Rename-Item-Cmdlet)

- [Criação de novos itens](#Creating-New-Items)

- [Os parâmetros dinâmicos para a anexar o `New-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-New-Item-Cmdlet)

- [Remover um itens](#Removing-Items)

- [Os parâmetros dinâmicos para a anexar o `Remove-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Remove-Item-Cmdlet)

- [Consulta para os itens subordinados](#Querying-for-Child-Items)

- [Copiar itens](#Copying-Items)

- [Os parâmetros dinâmicos para a anexar o `Copy-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Copy-Item-Cmdlet)

- [Exemplo de código](#Code-Sample)

- [Criando o provedor do Windows PowerShell](#Building-the-Windows-PowerShell-Provider)

- [Teste o fornecedor do Windows PowerShell](#Testing-the-Windows-PowerShell-Provider)

## <a name="defining-a-windows-powershell-container-provider-class"></a>Definir uma classe de fornecedor de contentor do Windows PowerShell

Um provedor de contentor do Windows PowerShell tem de definir uma classe do .NET que deriva de [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe base. Esta é a definição de classe para o fornecedor de contentor do Windows PowerShell descrita nesta secção.

```csharp
   [CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : ContainerCmdletProvider
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L34-L35 "AccessDBProviderSample04.cs")]

Tenha em atenção que, desta definição, de classe a [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atributo inclui dois parâmetros. O primeiro parâmetro especifica um nome amigável para o fornecedor que é utilizado pelo Windows PowerShell. O segundo parâmetro especifica os recursos específicos do Windows PowerShell que o fornecedor expõe o tempo de execução do Windows PowerShell durante o processamento do comando. Para este fornecedor, não há nenhum capacidades específicas do Windows PowerShell que são adicionadas.

## <a name="defining-base-functionality"></a>Definir funcionalidade de Base

Conforme descrito em [conceber Windows PowerShell Fornecedor_de_e](./designing-your-windows-powershell-provider.md), o [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe deriva de outras classes que fornecido funcionalidade de outro fornecedor. Um provedor de contentor do Windows PowerShell, por conseguinte, tem de definir todas as funcionalidades fornecidas por essas classes.

Para implementar a funcionalidade para adicionar informações de inicialização de específico da sessão e para liberar os recursos que são utilizados pelo fornecedor, veja [criar um fornecedor de PowerShell básica do Windows](./creating-a-basic-windows-powershell-provider.md). No entanto, a maioria dos provedores de (incluindo o fornecedor descrito aqui) pode utilizar a implementação padrão dessa funcionalidade fornecida pelo Windows PowerShell.

Para obter acesso ao arquivo de dados, o fornecedor tem de implementar os métodos do [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe base. Para obter mais informações sobre a implementação desses métodos, consulte [criar um fornecedor de unidade do Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Para manipular os itens de um armazenamento de dados, como obter, configuração e itens de limpeza, o fornecedor tem de implementar os métodos fornecidos pela [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe base. Para obter mais informações sobre a implementação desses métodos, consulte [criar um fornecedor de Item do Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

## <a name="retrieving-child-items"></a>A obter itens subordinados

Para obter um item subordinado, o fornecedor de contentor do Windows PowerShell tem de substituir a [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método para oferecer suporte a chamadas a partir do `Get-ChildItem` cmdlet. Esse método obtém itens filho do arquivo de dados e escreve-as para o pipeline como objetos. Se o `recurse` parâmetro do cmdlet for especificado, o método recupera todos os filhos, independentemente de qual o nível estão em. Se o `recurse` parâmetro não for especificado, o método obtém um único nível de subordinados.

Eis a implementação do [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método para este fornecedor. Tenha em atenção que este método obtém os itens subordinados em todas as tabelas de base de dados quando o caminho indica o banco de dados do Access e obtém os itens subordinados das linhas da tabela, se o caminho indica uma tabela de dados.

```csharp
protected override void GetChildItems(string path, bool recurse)
{
    // If path represented is a drive then the children in the path are
    // tables. Hence all tables in the drive represented will have to be
    // returned
    if (PathIsDrive(path))
    {
        foreach (DatabaseTableInfo table in GetTables())
        {
            WriteItemObject(table, path, true);

            // if the specified item exists and recurse has been set then
            // all child items within it have to be obtained as well
            if (ItemExists(path) && recurse)
            {
                GetChildItems(path + pathSeparator + table.Name, recurse);
            }
        } // foreach (DatabaseTableInfo...
    } // if (PathIsDrive...
    else
    {
        // Get the table name, row number and type of path from the
        // path specified
        string tableName;
        int rowNumber;

        PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

        if (type == PathType.Table)
        {
            // Obtain all the rows within the table
            foreach (DatabaseRowInfo row in GetRows(tableName))
            {
                WriteItemObject(row, path + pathSeparator + row.RowNumber,
                        false);
            } // foreach (DatabaseRowInfo...
        }
        else if (type == PathType.Row)
        {
            // In this case the user has directly specified a row, hence
            // just give that particular row
            DatabaseRowInfo row = GetRow(tableName, rowNumber);
            WriteItemObject(row, path + pathSeparator + row.RowNumber,
                        false);
        }
        else
        {
            // In this case, the path specified is not valid
            ThrowTerminatingInvalidPathException(path);
        }
    } // else
} // GetChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L311-L362 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchilditems"></a>Coisas a serem lembrados sobre a implementação GetChildItems

As seguintes condições podem aplicar-se na implementação [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Ao definir a classe do provedor, um provedor de contentor do Windows PowerShell poderia declarar capacidades de fornecedor de ExpandWildcards, filtro, inclusão ou exclusão, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração. Nestes casos, a implementação do [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método precisa para se certificar de que o caminho transmitido ao método cumpre os requisitos do especificado capacidades. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- A implementação desse método deve levar em conta nenhuma forma de acesso para o item que pode tornar o item visível ao utilizador. Por exemplo, se um utilizador tem acesso de escrita para um ficheiro através do fornecedor do sistema de ficheiros (fornecido pelo Windows PowerShell), mas não acesso de leitura, o ficheiro ainda existe e [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) retorna `true`. A implementação pode requerer a verificação de um item de principal para ver se o filho que pode ser enumerado.

- Ao escrever a vários itens, o [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método pode demorar algum tempo. Pode projetar o seu fornecedor para escrever os itens com o [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) método um por vez. Usando essa técnica irá apresentar os itens ao usuário num fluxo.

- A implementação do [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) é responsável por impedir recursão infinita quando existem ligações circulares e assim por diante. Deve ser emitida uma exceção de terminação apropriada para refletir esse uma condição.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a>Anexar parâmetros dinâmicos para o Cmdlet Get-ChildItem

Por vezes, o `Get-ChildItem` cmdlet que chama [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) requer parâmetros adicionais que são especificados dinamicamente no tempo de execução. Para fornecer estes parâmetros dinâmicos, o fornecedor de contentor do Windows PowerShell tem de implementar o [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) método. Esse método obtém parâmetros dinâmicos para o item no caminho indicado e retorna um objeto com propriedades e campos com análise atributos semelhantes a uma classe cmdlet ou uma [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto devolvido para adicionar os parâmetros para o `Get-ChildItem` cmdlet.

Este fornecedor de contentor do Windows PowerShell não implementa esse método. No entanto, o código a seguir é a implementação do padrão desse método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a>Obter os nomes de Item subordinado

Para obter os nomes de itens subordinados, o fornecedor de contentor do Windows PowerShell tem de substituir a [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) método para oferecer suporte a chamadas a partir do `Get-ChildItem`cmdlet quando seu `Name` parâmetro for especificado. Este método obtém os nomes dos itens subordinados para os nomes de item de caminho ou subordinado especificados para todos os contentores, se o `returnAllContainers` é especificado o parâmetro do cmdlet. Um nome de subordinado é a parte de folha de um caminho. Por exemplo, o nome de subordinados para o caminho c:\windows\system32\abc.dll é "abc.dll". O nome de subordinados para o diretório c:\windows\system32 é "system32".

Eis a implementação do [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) método para este fornecedor. Tenha em atenção que o método obtém nomes de tabela, se o caminho especificado indica o banco de dados do Access (unidade) e números de linha se o caminho indica uma tabela.

```csharp
protected override void GetChildNames(string path,
                            ReturnContainers returnContainers)
{
    // If the path represented is a drive, then the child items are
    // tables. get the names of all the tables in the drive.
    if (PathIsDrive(path))
    {
        foreach (DatabaseTableInfo table in GetTables())
        {
            WriteItemObject(table.Name, path, true);
        } // foreach (DatabaseTableInfo...
    } // if (PathIsDrive...
    else
    {
        // Get type, table name and row number from path specified
        string tableName;
        int rowNumber;

        PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

        if (type == PathType.Table)
        {
            // Get all the rows in the table and then write out the
            // row numbers.
            foreach (DatabaseRowInfo row in GetRows(tableName))
            {
                WriteItemObject(row.RowNumber, path, false);
            } // foreach (DatabaseRowInfo...
        }
        else if (type == PathType.Row)
        {
            // In this case the user has directly specified a row, hence
            // just give that particular row
            DatabaseRowInfo row = GetRow(tableName, rowNumber);

            WriteItemObject(row.RowNumber, path, false);
        }
        else
        {
            ThrowTerminatingInvalidPathException(path);
        }
    } // else
} // GetChildNames
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L369-L411 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchildnames"></a>Coisas a serem lembrados sobre a implementação GetChildNames

As seguintes condições podem aplicar-se na implementação [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Ao definir a classe do provedor, um provedor de contentor do Windows PowerShell poderia declarar capacidades de fornecedor de ExpandWildcards, filtro, inclusão ou exclusão, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração. Nestes casos, a implementação do [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método precisa para se certificar de que o caminho transmitido ao método cumpre os requisitos do especificado capacidades. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

  > [!NOTE]
  > Ocorre uma exceção a esta regra quando o `returnAllContainers` é especificado o parâmetro do cmdlet. Neste caso, o método deve recuperar qualquer nome de subordinados para um contentor, mesmo que não corresponde aos valores do [System.Management.Automation.Provider.Cmdletprovider.Filter*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter), [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include), ou [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) propriedades.

- Por predefinição, substituições deste método não devem obter nomes de objetos que geralmente estão ocultos do utilizador, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) é especificada a propriedade. Se o caminho especificado indica um contentor, o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriedade não é necessária.

- A implementação do [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) é responsável por impedir recursão infinita quando existem ligações circulares e assim por diante. Deve ser emitida uma exceção de terminação apropriada para refletir esse uma condição.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a>Anexar parâmetros dinâmicos para o Cmdlet Get-ChildItem (nome)

Por vezes, o `Get-ChildItem` cmdlet (com o `Name` parâmetro) requer parâmetros adicionais que são especificados dinamicamente no tempo de execução. Para fornecer estes parâmetros dinâmicos, o fornecedor de contentor do Windows PowerShell tem de implementar o [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) método. Esse método obtém os parâmetros dinâmicos para o item no caminho indicado e retorna um objeto com propriedades e campos com análise atributos semelhantes a uma classe cmdlet ou uma [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto devolvido para adicionar os parâmetros para o `Get-ChildItem` cmdlet.

Este fornecedor não implementa esse método. No entanto, o código a seguir é a implementação do padrão desse método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a>Mudar o nome de itens

Para mudar o nome de um item, um provedor de contentor do Windows PowerShell tem de substituir a [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) método para oferecer suporte a chamadas a partir do `Rename-Item` cmdlet. Esse método altera o nome do item no caminho especificado para o novo nome fornecido. O novo nome tem de ser sempre em relação ao item principal (contentor).

Este fornecedor não substitui a [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) método. No entanto, segue-se a implementação padrão.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a>Coisas a serem lembrados sobre a implementação RenameItem

As seguintes condições podem aplicar-se na implementação [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem):

- Ao definir a classe do provedor, um provedor de contentor do Windows PowerShell poderia declarar capacidades de fornecedor de ExpandWildcards, filtro, inclusão ou exclusão, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração. Nestes casos, a implementação do [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método precisa para se certificar de que o caminho transmitido ao método cumpre os requisitos do especificado capacidades. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- O [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) método destina-se para a modificação do nome de um item apenas e não para operações de movimentação. A implementação do método deve escrever um erro se o `newName` parâmetro contém separadores de caminho ou, caso contrário, pode fazer com que o item Alterar a localização principal.

- Por predefinição, substituições desse método devem não mudar o nome de objetos, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) é especificada a propriedade. Se o caminho especificado indica um contentor, o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriedade não é necessária.

- Sua implementação do [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) deve chamar o método [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verifique o valor de retorno antes de fazer alterações ao arquivo de dados. Este método é usado para confirmar a execução de uma operação quando é efetuada uma alteração de estado do sistema, por exemplo, mudar o nome de ficheiros. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envia o nome do recurso a ser alterados ao usuário, com o tempo de execução do Windows PowerShell tendo em conta as definições de linha de comandos ou variáveis de preferência em determinar o que deverá ser apresentado.

  Após a chamada para [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) devolve `true`, o [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) método deve chamar o [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método. Este método envia uma mensagem de uma mensagem de confirmação ao utilizador para permitir que os comentários adicionais dizer se deve ser contínuo a operação. Um provedor deve chamar [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) como uma verificação adicional para as modificações de sistema potencialmente perigosas.

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a>Anexar parâmetros dinâmicos para o Cmdlet Rename-Item

Por vezes, o `Rename-Item` cmdlet requer parâmetros adicionais que são especificados dinamicamente no tempo de execução. Para fornecer estes parâmetros dinâmicos, fornecedor de contentor do Windows PowerShell tem de implementar o [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) método. Esse método obtém os parâmetros para o item no caminho indicado e retorna um objeto com propriedades e campos com análise atributos semelhantes a uma classe cmdlet ou uma [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto devolvido para adicionar os parâmetros para o `Rename-Item` cmdlet.

Este fornecedor de contentor não implementa esse método. No entanto, o código a seguir é a implementação do padrão desse método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a>Criação de novos itens

Para criar novos itens, um fornecedor de contentor tem de implementar o [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método para oferecer suporte a chamadas a partir do `New-Item` cmdlet. Este método cria um item de dados localizado no caminho especificado. O `type` parâmetro do cmdlet contém o tipo definido pelo fornecedor para o novo item. Por exemplo, o fornecedor de sistema de ficheiros utiliza um `type` parâmetro com um valor de "arquivo" ou "diretório". O `newItemValue` parâmetro do cmdlet Especifica um valor de específica do fornecedor para o novo item.

Eis a implementação do [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método para este fornecedor.

```csharp
protected override void NewItem( string path, string type,
                                 object newItemValue )
{
    // Create the new item here after
    // performing necessary validations
    //
    // WriteItemObject(newItemValue, path, false);

    // Example
    //
    // if (ShouldProcess(path, "new item"))
    // {
    //      // Create a new item and then call WriteObject
    //      WriteObject(newItemValue, path, false);
    // }

} // NewItem
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L939-L955 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-newitem"></a>Coisas a serem lembrados sobre a implementação NewItem

As seguintes condições podem aplicar-se na implementação [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- O [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método deve executar uma comparação de maiúsculas e minúsculas de cadeia transmitida a `type` parâmetro. Deve também permitir menos ambíguas correspondências. Por exemplo, para os tipos "arquivo" e "diretório", apenas a primeira letra é necessário para eliminar a ambiguidade. Se o `type` parâmetro indica um tipo não é possível criar o seu fornecedor, o [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método deve escrever uma ArgumentException com uma mensagem o fornecedor que indica os tipos pode criar.

- Para o `newItemValue` parâmetro, a implementação do [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método é recomendado para aceitar as cadeias de caracteres no mínimo. Ele também deve aceitar o tipo de objeto que é recuperado o [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) método para o mesmo caminho. O [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método pode usar o [System.Management.Automation.Languageprimitives.Convertto*](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo) tipos de método para converter a o tipo desejado.

- Sua implementação do [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) deve chamar o método [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verifique o valor de retorno antes de fazer alterações ao arquivo de dados. Após a chamada para [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retorna true, o [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método deve chamar o [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método como uma verificação adicional para as modificações de sistema potencialmente perigosas.

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a>Anexar parâmetros dinâmicos para o Cmdlet de novo Item

Por vezes, o `New-Item` cmdlet requer parâmetros adicionais que são especificados dinamicamente no tempo de execução. Para fornecer estes parâmetros dinâmicos, o fornecedor de contentor tem de implementar o [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) método. Esse método obtém os parâmetros para o item no caminho indicado e retorna um objeto com propriedades e campos com análise atributos semelhantes a uma classe cmdlet ou uma [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto devolvido para adicionar os parâmetros para o `New-Item` cmdlet.

Este fornecedor não implementa esse método. No entanto, o código a seguir é a implementação do padrão desse método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a>Remover itens

Para remover itens, o fornecedor de Windows PowerShell tem de substituir a [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) método para oferecer suporte a chamadas a partir do `Remove-Item` cmdlet. Este método elimina um item do arquivo de dados no caminho especificado. Se o `recurse` parâmetro do `Remove-Item` cmdlet está definido como `true`, o método Remove todos os itens subordinados, independentemente de seu nível. Se o parâmetro estiver definido como `false`, o método Remove apenas um único item no caminho especificado.

Este fornecedor não suporta a remoção do item. No entanto, o código a seguir é a implementação padrão da [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a>Coisas a serem lembrados sobre a implementação RemoveItem

As seguintes condições podem aplicar-se na implementação [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- Ao definir a classe do provedor, um provedor de contentor do Windows PowerShell poderia declarar capacidades de fornecedor de ExpandWildcards, filtro, inclusão ou exclusão, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração. Nestes casos, a implementação do [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método precisa para se certificar de que o caminho transmitido ao método cumpre os requisitos do especificado capacidades. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- Por predefinição, substituições deste método não deverá remover objetos, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriedade está definida como true. Se o caminho especificado indica um contentor, o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriedade não é necessária.

- A implementação do [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) é responsável por impedir recursão infinita quando existem ligações circulares e assim por diante. Deve ser emitida uma exceção de terminação apropriada para refletir esse uma condição.

- Sua implementação do [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) deve chamar o método [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verifique o valor de retorno antes de fazer alterações ao arquivo de dados. Após a chamada para [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) devolve `true`, o [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) método deve chamar o [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método como uma verificação adicional para as modificações de sistema potencialmente perigosas.

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a>Anexar parâmetros dinâmicos para o Cmdlet Remove-Item

Por vezes, o `Remove-Item` cmdlet requer parâmetros adicionais que são especificados dinamicamente no tempo de execução. Para fornecer estes parâmetros dinâmicos, o fornecedor de contentor tem de implementar o [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) método para lidar com esses parâmetros. Esse método obtém os parâmetros dinâmicos para o item no caminho indicado e retorna um objeto com propriedades e campos com análise atributos semelhantes a uma classe cmdlet ou uma [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto devolvido para adicionar os parâmetros para o `Remove-Item` cmdlet.

Este fornecedor de contentor não implementa esse método. No entanto, o código a seguir é a implementação padrão da [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a>Consulta para os itens subordinados

Para verificar se os itens filho existirem no caminho especificado, o fornecedor de contentor do Windows PowerShell tem de substituir a [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) método. Este método devolve `true` se o item tiver subordinados, e `false` caso contrário. Para um caminho nulo ou está vazio, o método considera todos os itens no arquivo de dados para ser subordinados e retorna `true`.

Eis a substituição para o [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) método. Se existirem mais de duas partes do caminho criados pelo método auxiliar ChunkPath, o método retorna `false`, uma vez que apenas um contentor de base de dados e um contentor de tabela são definidos. Para mais informações sobre esse método auxiliar, consulte o método ChunkPath é discutido [criar um fornecedor de Item do Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L1094-L1097 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-haschilditems"></a>Coisas a serem lembrados sobre a implementação HasChildItems

As seguintes condições podem aplicar-se na implementação [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems):

- Se o fornecedor de contentor expõe uma raiz que contém os pontos de montagem de interessante, a implementação do [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) método deve retornar `true`quando um valor nulo ou uma cadeia vazia é passada para o caminho.

## <a name="copying-items"></a>Copiar itens

Para copiar itens, o fornecedor de contentor tem de implementar o [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) método para oferecer suporte a chamadas a partir do `Copy-Item` cmdlet. Este método copia um item de dados de localização indicada pela `path` parâmetro do cmdlet para o local indicado pelo `copyPath` parâmetro. Se o `recurse` parâmetro for especificado, o método copia todos os sub-recipientes. Se o parâmetro não for especificado, o método copia apenas um único nível de itens.

Este fornecedor não implementa esse método. No entanto, o código a seguir é a implementação padrão da [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a>Coisas a serem lembrados sobre a implementação de CopyItem

As seguintes condições podem aplicar-se na implementação [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem):

- Ao definir a classe do provedor, um provedor de contentor do Windows PowerShell poderia declarar capacidades de fornecedor de ExpandWildcards, filtro, inclusão ou exclusão, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração. Nestes casos, a implementação do [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método precisa para se certificar de que o caminho transmitido ao método cumpre os requisitos do especificado capacidades. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- Por predefinição, substituições deste método não devem copiar objetos ao longo de objetos existentes, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Por exemplo, o fornecedor do sistema de ficheiros não copiará c:\temp\abc.txt ao longo de um ficheiro de c:\abc.txt existente, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Se o caminho especificado na `copyPath` parâmetro existe e indica um contentor, o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriedade não é necessária. Neste caso, [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) deve copiar o item indicado pela `path` parâmetro para o contentor indicado pelo `copyPath` parâmetro como um filho.

- A implementação do [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) é responsável por impedir recursão infinita quando existem ligações circulares e assim por diante. Deve ser emitida uma exceção de terminação apropriada para refletir esse uma condição.

- Sua implementação do [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) deve chamar o método [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verifique o valor de retorno antes de fazer alterações ao arquivo de dados. Após a chamada para [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retorna true, o [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) método deve chamar o [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método como uma verificação adicional para as modificações de sistema potencialmente perigosas. Para obter mais informações sobre como chamar esses métodos, consulte [mudar o nome de itens](#Renaming-Items).

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a>Anexar parâmetros dinâmicos para o Cmdlet Copy-Item

Por vezes, o `Copy-Item` cmdlet requer parâmetros adicionais que são especificados dinamicamente no tempo de execução. Para fornecer estes parâmetros dinâmicos, o fornecedor de contentor do Windows PowerShell tem de implementar o [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) método para lidar com esses parâmetros. Esse método obtém os parâmetros para o item no caminho indicado e retorna um objeto com propriedades e campos com análise atributos semelhantes a uma classe cmdlet ou uma [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto devolvido para adicionar os parâmetros para o `Copy-Item` cmdlet.

Este fornecedor não implementa esse método. No entanto, o código a seguir é a implementação padrão da [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a>Exemplo de código

Para o código de exemplo completo, consulte [exemplo de código AccessDbProviderSample04](./accessdbprovidersample04-code-sample.md).

## <a name="building-the-windows-powershell-provider"></a>Criando o provedor do Windows PowerShell

Ver [como registar os Cmdlets, fornecedores e alojar aplicações](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Teste o fornecedor do Windows PowerShell

Quando o seu fornecedor de Windows PowerShell foi registado com o Windows PowerShell, pode testá-lo ao executar os cmdlets suportados na linha de comandos. Lembre-se de que o resultado de exemplo seguinte utiliza uma base de dados do Access fictício.

1. Execute o `Get-ChildItem` cmdlet para obter a lista de itens subordinados de uma tabela de clientes da base de dados de acesso.

   ```powershell
   Get-ChildItem mydb:customers
   ```

   O resultado seguinte é apresentada.

   ```output
   PSPath        : AccessDB::customers
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : True
   Data          : System.Data.DataRow
   Name          : Customers
   RowCount      : 91
   Columns       :
   ```

2. Execute o `Get-ChildItem` cmdlet novamente para recuperar os dados de uma tabela.

   ```powershell
   (Get-ChildItem mydb:customers).data
   ```

   O resultado seguinte é apresentada.

   ```output
   TABLE_CAT   : c:\PS\northwind
   TABLE_SCHEM :
   TABLE_NAME  : Customers
   TABLE_TYPE  : TABLE
   REMARKS     :
   ```

3. Agora utilizar o `Get-Item` cmdlet para obter os itens de linha 0 na tabela de dados.

   ```powershell
   Get-Item mydb:\customers\0
   ```

   O resultado seguinte é apresentada.

   ```output
   PSPath        : AccessDB::customers\0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data          : System.Data.DataRow
   RowNumber     : 0
   ```

4. Reutilizar `Get-Item` para recuperar os dados para os itens na linha 0.

   ```powershell
   (Get-Item mydb:\customers\0).data
   ```

   O resultado seguinte é apresentada.

   ```output
   CustomerID   : 1234
   CompanyName  : Fabrikam
   ContactName  : Eric Gruber
   ContactTitle : President
   Address      : 4567 Main Street
   City         : Buffalo
   Region       : NY
   PostalCode   : 98052
   Country      : USA
   Phone        : (425) 555-0100
   Fax          : (425) 555-0101
   ```

5. Agora utilizar o `New-Item` cmdlet para adicionar uma linha para uma tabela existente. O `Path` parâmetro especifica o caminho completo para a linha e tem de indicar um número de linha que é superior ao número de linhas na tabela existente. O `Type` parâmetro indica "linha" para especificar esse tipo de item para adicionar. Por fim, o `Value` parâmetro especifica uma lista delimitada por vírgulas de valores de coluna para a linha.

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAddress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
   ```

6. Verificar a correção da operação de novo item da seguinte forma.

   ```none
   PS mydb:\> cd Customers
   PS mydb:\Customers> (Get-Item 3).data
   ```

   O resultado seguinte é apresentada.

   ```output
   ID        : 3
   FirstName : Eric
   LastName  : Gruber
   Email     : ericgruber@fabrikam.com
   Title     : President
   Company   : Fabrikam
   WorkPhone : (425) 555-0100
   Address   : 4567 Main Street
   City      : Buffalo
   State     : NY
   Zip       : 98052
   Country   : USA
   ```

## <a name="see-also"></a>Veja Também

[Criar provedores do Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Estruturar o seu fornecedor do Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Implementando um provedor de PowerShell do Windows de Item](./creating-a-windows-powershell-item-provider.md)

[Implementando um provedor de PowerShell do Windows de navegação](./creating-a-windows-powershell-navigation-provider.md)

[Como registar os Cmdlets, fornecedores e alojar aplicações](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[SDK do Windows PowerShell](../windows-powershell-reference.md)

[Guia do programador do Windows PowerShell](./windows-powershell-programmer-s-guide.md)