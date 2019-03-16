---
title: Tipos de fornecedor | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e523a8e1-42e4-4633-887f-fb74b3464561
caps.latest.revision: 12
ms.openlocfilehash: 37689571eb1650e5991af2e7002cd037ae99dd68
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057965"
---
# <a name="provider-types"></a>Provider types (Tipos de fornecedores)

Fornecedores de definem a sua funcionalidade básica, alterando a forma como os cmdlets de fornecedor (fornecidos pelo Windows PowerShell) executar suas ações. Por exemplo, os fornecedores podem utilizar a funcionalidade de padrão do `Get-Item` cmdlet ou pode alterar a forma como esse cmdlet funciona ao obter itens de arquivo de dados. A funcionalidade de fornecedor descrita neste tópico inclui a funcionalidade definida ao substituir os métodos de interfaces e classes base do provedor específico.

> [!NOTE]
> Para funcionalidades do fornecedor de previamente definidos pelo Windows PowerShell, consulte [capacidades de fornecedor](http://msdn.microsoft.com/en-us/864e4807-554a-4016-80ea-bf643a090fc6).

## <a name="drive-enabled-providers"></a>Fornecedores de unidade de capacidade

Provedores habilitados para unidade especifique as unidades de predefinidas disponíveis para o utilizador e permitir que o utilizador adicionar ou remover unidades. Na maioria dos casos, os provedores são habilitados na unidade de provedores porque elas exigem alguns unidade predefinida para acessar o armazenamento de dados. No entanto, ao escrever seu próprio provedor poderá ou não deverá permitir que o utilizador criar e remover unidades.

Para criar um fornecedor de unidade de capacidade, sua classe de provedor deve derivar do [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe ou de outra classe que deriva dessa classe. O [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe define os seguintes métodos para implementar as unidades padrão do fornecedor e oferecer suporte a `New-PSDrive` e `Remove-PSDrive` cmdlets. Na maioria dos casos, para oferecer suporte a um cmdlet de fornecedor necessário substituir o método que chama o motor do Windows PowerShell para invocar o cmdlet, tais como o `NewDrive` método para o `New-PSDrive` cmdlet e, opcionalmente, pode substituir um segundo método, como `NewDriveDynamicParameters`, para adicionar parâmetros dinâmicos para o cmdlet.

- O [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) método define as unidades padrão que estão disponíveis para o usuário sempre que o fornecedor é utilizado.

- O [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) e [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) métodos define como o fornecedor suporta a `New-PSDrive` cmdlet de fornecedor. Este cmdlet permite ao utilizador criar unidades para acessar o armazenamento de dados.

- O [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) método define como o fornecedor suporta a `Remove-PSDrive` cmdlet de fornecedor. Este cmdlet permite ao utilizador remover as unidades do arquivo de dados.

## <a name="item-enabled-providers"></a>Provedores habilitados para item

Provedores habilitados no item que o utilizador a obter, definir ou limpar os itens no arquivo de dados. Um "item" é um elemento do arquivo de dados que o utilizador pode aceder ou gerir de forma independente. Para criar um provedor habilitado para item, sua classe de provedor deve derivar do [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe ou de outra classe que deriva dessa classe.

O [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe define os seguintes métodos para a implementação de cmdlets de provedor específico. Na maioria dos casos, para oferecer suporte a um cmdlet de fornecedor necessário substituir o método que chama o motor do Windows PowerShell para invocar o cmdlet, tais como o `ClearItem` método para o `Clear-Item` cmdlet e, opcionalmente, pode substituir um segundo método, como `ClearItemDynamicParameters`, para adicionar parâmetros dinâmicos para o cmdlet.

- O [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) e [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) métodos Definir como o fornecedor suporta a `Clear-Item` cmdlet de fornecedor. Este cmdlet permite ao utilizador remover do valor de um item no arquivo de dados.

- O [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) e [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) os métodos definem como suporta o fornecedor a `Get-Item` cmdlet de fornecedor. Este cmdlet permite ao utilizador recuperar dados do arquivo de dados.

- O [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) e [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) os métodos definem como suporta o fornecedor a `Set-Item` cmdlet de fornecedor. Este cmdlet permite ao utilizador atualizar os valores de itens no arquivo de dados.

- O [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) e [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) métodos Definir como o fornecedor suporta a `Invoke-Item` cmdlet de fornecedor. Este cmdlet permite ao utilizador efetuar a ação de predefinição especificada pelo item de.

- O [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) e [System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) métodos Definir como o fornecedor suporta a `Test-Path` cmdlet de fornecedor. Este cmdlet permite ao utilizador determinar se todos os elementos de um caminho existem.

  Além dos métodos usados para implementar os cmdlets do fornecedor, o [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe também define os seguintes métodos:

- O [System.Management.Automation.Provider.Itemcmdletprovider.Expandpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ExpandPath) método permite que o utilizador utilize carateres universais ao especificar o caminho do fornecedor.

- O [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) é utilizado para determinar se um caminho é sintaticamente e semanticamente válido para o fornecedor.

## <a name="container-enabled-providers"></a>Provedores habilitados no contentor

Provedores habilitados no contentor permitem ao utilizador gerir itens que são contentores. Um contentor é um grupo de itens filho num item principal comum. Para criar um provedor habilitado para contentor, sua classe de provedor deve derivar do [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe ou de outra classe que deriva dessa classe.

> [!IMPORTANT]
> Provedores habilitados para o contentor não podem acessar arquivos de dados que contêm contêineres aninhados. Se um item subordinado de um contentor é outro contentor, tem de implementar um provedor habilitado para navegação.

O [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe define os seguintes métodos para a implementação de cmdlets de provedor específico. Na maioria dos casos, para oferecer suporte a um cmdlet de fornecedor necessário substituir o método que chama o motor do Windows PowerShell para invocar o cmdlet, tais como o `CopyItem` método para o `Copy-Item` cmdlet e, opcionalmente, pode substituir um segundo método, como `CopyItemDynamicParameters`, para adicionar parâmetros dinâmicos para o cmdlet.

- O [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) e [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) como o fornecedor suporta os métodos definem o `Copy-Item` cmdlet de fornecedor. Este cmdlet permite ao utilizador copiar um item de uma localização para outra.

- O [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) e [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) como o fornecedor suporta os métodos definem o `Get-ChildItem` cmdlet de fornecedor. Este cmdlet permite que o utilizador a obter os itens subordinados de item principal.

- O [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) e [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) como o fornecedor suporta os métodos definem os `Get-ChildItem` cmdlet de fornecedor se seu `Name` parâmetro for especificado.

- O [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) e [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) como o fornecedor suporta os métodos definem o `New-Item` cmdlet de fornecedor. Este cmdlet permite ao utilizador criar novos itens no arquivo de dados.

- O [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) e [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) como o fornecedor suporta os métodos definem o `Remove-Item` cmdlet de fornecedor. Este cmdlet permite ao utilizador remover itens do arquivo de dados.

- O [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) e [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) como o fornecedor suporta os métodos definem o `Rename-Item` cmdlet de fornecedor. Este cmdlet permite ao utilizador mudar o nome de itens no arquivo de dados.

  Além dos métodos usados para implementar os cmdlets do fornecedor, o [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe também define os seguintes métodos:

- O [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) método pode ser utilizado pela classe de fornecedor para determinar se um item tem itens subordinados.

- O [System.Management.Automation.Provider.Containercmdletprovider.Convertpath*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.ConvertPath) método pode ser utilizado pela classe de fornecedor para criar um novo caminho de específica do fornecedor a partir de um caminho especificado.

## <a name="navigation-enabled-providers"></a>Provedores habilitados para navegação

Provedores habilitados para navegação permitem ao utilizador mover os itens no arquivo de dados. Para criar um provedor habilitado para navegação, sua classe de provedor deve derivar do [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.

O [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe define os seguintes métodos para a implementação de cmdlets de provedor específico. Na maioria dos casos, para oferecer suporte a um cmdlet de fornecedor necessário substituir o método que chama o motor do Windows PowerShell para invocar o cmdlet, tais como o `MoveItem` método para o `Move-Item` cmdlet e, opcionalmente, pode substituir um segundo método, como `MoveItemDynamicParameters`, para adicionar parâmetros dinâmicos para o cmdlet.

- O [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) e [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) como o fornecedor suporta os métodos definem o `Move-Item` cmdlet de fornecedor. Este cmdlet permite ao utilizador mover um item de uma localização no armazenamento para outra localização.

- O [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) método define como o fornecedor suporta a `Join-Path` cmdlet de fornecedor. Este cmdlet permite ao utilizador combinar um segmento de caminho pai e filho para criar um caminho internas do fornecedor.

  Além dos métodos usados para implementar os cmdlets do fornecedor, o [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe também define os seguintes métodos:

- O [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) método extrai o nome do nó subordinado de um caminho.

- O [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) método extrai a parte principal de um caminho.

- O [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) método determina se o item é um item de contentor. Neste contexto, um contêiner é um grupo de itens filho num item principal comum.

- O [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) método retorna um caminho para um item que é relativo a um caminho de base especificado.

## <a name="content-enabled-providers"></a>Fornecedores de conteúdo-ativada

Fornecedores de conteúdo habilitado permitem ao utilizador limpar, obter ou definir o conteúdo dos itens num arquivo de dados. Por exemplo, o fornecedor do sistema de ficheiros permite-lhe limpar, obter e definir o conteúdo dos ficheiros no sistema de arquivos. Para criar um fornecedor de conteúdos ativado, sua classe de fornecedor tem de implementar os métodos do [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.

O [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface define os seguintes métodos para a implementação de cmdlets de provedor específico. Na maioria dos casos, para oferecer suporte a um cmdlet de fornecedor necessário substituir o método que chama o motor do Windows PowerShell para invocar o cmdlet, tais como o `ClearContent` método para o `Clear-Content` cmdlet e, opcionalmente, pode substituir um segundo método, como `ClearContentDynamicParameters`, para adicionar parâmetros dinâmicos para o cmdlet.

- O [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) e [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)como o fornecedor suporta os métodos definem o `Clear-Content` cmdlet de fornecedor. Este cmdlet permite ao utilizador eliminar o conteúdo de um item sem eliminar o item.

- O [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) e [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) como o fornecedor suporta os métodos definem o `Get-Content` cmdlet de fornecedor. Este cmdlet permite ao utilizador obter o conteúdo de um item. O [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) método devolve um [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) interface que define os métodos utilizados para ler o conteúdo.

- O [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) e [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) como o fornecedor suporta os métodos definem o `Set-Content` cmdlet de fornecedor. Este cmdlet permite ao utilizador atualizar o conteúdo de um item. O [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) método devolve um [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) interface que define os métodos utilizados para gravar o conteúdo.

## <a name="property-enabled-providers"></a>Fornecedores de propriedade ativada

A propriedade ativada fornecedores permitem ao utilizador gerir as propriedades dos itens no arquivo de dados. Para criar um fornecedor de propriedade ativada, sua classe de fornecedor tem de implementar os métodos do [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) interfaces. Na maioria dos casos, para oferecer suporte a um cmdlet de fornecedor necessário substituir o método que chama o motor do Windows PowerShell para invocar o cmdlet, tais como o `ClearProperty` método para o cmdlet de propriedade de limpar e, opcionalmente, pode substituir um segundo método, como `ClearPropertyDynamicParameters`, para adicionar parâmetros dinâmicos para o cmdlet.

O [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interface define os seguintes métodos para a implementação de cmdlets de provedor específico:

- O [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) e [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) como o fornecedor suporta os métodos definem o `Clear-ItemProperty` cmdlet de fornecedor. Este cmdlet permite ao utilizador eliminar o valor de uma propriedade.

- O [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) e [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)como o fornecedor suporta os métodos definem o `Get-ItemProperty` cmdlet de fornecedor. Este cmdlet permite que o utilizador a obter a propriedade de um item.

- O [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) e [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)como o fornecedor suporta os métodos definem o `Set-ItemProperty` cmdlet de fornecedor. Este cmdlet permite ao utilizador atualizar as propriedades de um item.

  O [System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) interface define os seguintes métodos para a implementação de cmdlets de provedor específico:

- O [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copyproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copypropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) como o fornecedor suporta os métodos definem o `Copy-ItemProperty` cmdlet de fornecedor. Este cmdlet permite ao utilizador copiar uma propriedade e o respetivo valor de uma localização para outra.

- O [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Moveproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Movepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) como o fornecedor suporta os métodos definem o `Move-ItemProperty` cmdlet de fornecedor. Este cmdlet permite ao utilizador mover uma propriedade e o respetivo valor de uma localização para outra.

- O [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) como o fornecedor suporta os métodos definem o `New-ItemProperty` cmdlet de fornecedor. Este cmdlet permite ao utilizador criar uma nova propriedade e defina seu valor.

- O [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) como o fornecedor suporta os métodos definem o `Remove-ItemProperty` cmdlet. Este cmdlet permite ao utilizador eliminar uma propriedade e o respetivo valor.

- O [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) como o fornecedor suporta os métodos definem o `Rename-ItemProperty` cmdlet. Este cmdlet permite ao utilizador alterar o nome de uma propriedade.

## <a name="see-also"></a>Veja Também

[Escrever um fornecedor do Windows PowerShell](./writing-a-windows-powershell-provider.md)