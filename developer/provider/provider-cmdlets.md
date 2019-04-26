---
title: Cmdlets do fornecedor de | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2465420-0970-4408-9ee5-260cf444cb67
caps.latest.revision: 8
ms.openlocfilehash: e6a0711cff6a550100f584fb64ae7f59f71a3cfb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080956"
---
# <a name="provider-cmdlets"></a>Provider cmdlets (Cmdlets de fornecedores)

Os cmdlets que o usuário pode executar para gerir um arquivo de dados são referidos como cmdlets do fornecedor. Para suportar estes cmdlets, terá de substituir alguns dos métodos definidos pelas interfaces e classes do provedor base.

## <a name="provider-cmdlets"></a>Cmdlets do fornecedor

Seguem-se os cmdlets de fornecedor que podem ser executados pelo utilizador:

### <a name="psdrive-cmdlets"></a>Cmdlets de PSDrive

- `Get-PSDrive`: Este cmdlet devolve que o Windows PowerShell unidades na sessão atual. Não é necessário substituir qualquer método para suportar este cmdlet.

- `New-PSDrive`: Este cmdlet permite ao utilizador criar unidades do Windows PowerShell para acessar o armazenamento de dados. Para suportar este cmdlet, substituir a [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) e [ System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) métodos.

- `Remove-PSDrive`: Este cmdlet permite ao utilizador remover unidades de Windows PowerShell que aceder ao arquivo de dados. Para suportar este cmdlet, substituir a [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) método.

### <a name="item-cmdlets"></a>Cmdlets de item

- `Clear-Item`: Este cmdlet permite ao utilizador remover o valor de um item no arquivo de dados. Para suportar este cmdlet, substituir a [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) e [ System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) métodos.

- `Copy-Item`: Este cmdlet permite ao utilizador copiar um item de uma localização para outra. Para suportar este cmdlet, substituir a [System.Management.Automation.Provider.Containercmdletprovider.Copyitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) e [ System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) métodos.

- `Get-Item`: Este cmdlet permite ao utilizador recuperar dados do arquivo de dados. Para suportar este cmdlet, substituir a [System.Management.Automation.Provider.Itemcmdletprovider.Getitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) e [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) métodos.

- `Get-ChildItem`: Este cmdlet permite que o utilizador a obter os itens subordinados de item principal. Para suportar este cmdlet, substitua os métodos seguintes:

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)

- `Invoke-Item`: Este cmdlet permite ao utilizador efetuar a ação de predefinição especificada pelo item de. Para suportar este cmdlet, substituir a [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) e [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) métodos.

- `Move-Item`: Este cmdlet permite ao utilizador mover um item de uma localização para outra localização. Para suportar este cmdlet, substituir a [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) e [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)metod.

- `New-ItemProperty`: Este cmdlet permite ao utilizador criar um novo item no arquivo de dados.

- `Remove-Item`: Este cmdlet permite ao utilizador remover itens do arquivo de dados. Para suportar este cmdlet, substituir a [System.Management.Automation.Provider.Containercmdletprovider.Removeitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) e [ System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) métodos.

- `Rename-Item`: Este cmdlet permite ao utilizador mudar o nome de itens no arquivo de dados. Para suportar este cmdlet, substituir a [System.Management.Automation.Provider.Containercmdletprovider.Renameitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) e [ System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) métodos.

- `Set-Item`: Este cmdlet permite ao utilizador atualizar os valores de itens no arquivo de dados. Para suportar este cmdlet, substituir a [System.Management.Automation.Provider.Itemcmdletprovider.Setitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) e [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) métodos.

### <a name="item-content-cmdlets"></a>Cmdlets de conteúdo do item

- `Add-Content`: Este cmdlet permite ao utilizador adicionar conteúdo a um item.

- `Clear-Content`: Este cmdlet permite ao utilizador eliminar o conteúdo de um item sem eliminar o item. Para suportar este cmdlet, substituir a [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) e [ System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) métodos.

- `Get-Content`: Este cmdlet permite ao utilizador obter o conteúdo de um item. Para suportar este cmdlet, substituir a [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) e [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) métodos. O [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) método devolve um [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) interface que define os métodos utilizados para ler o conteúdo.

- `Set-Content`: Este cmdlet permite ao utilizador atualizar o conteúdo de um item. Para suportar este cmdlet, substituir a [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) e [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) métodos. O [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) método devolve um [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) interface que define os métodos utilizados para gravar o conteúdo.

### <a name="item-property-cmdlets"></a>Cmdlets de propriedade do item

- `Clear-ItemProperty`: Este cmdlet permite ao utilizador eliminar o valor de uma propriedade. Para suportar este cmdlet, substituir a [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) e [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) métodos.

- `Copy-ItemProperty`: Este cmdlet permite ao utilizador copiar uma propriedade e o respetivo valor de uma localização para outra. Para suportar este cmdlet, substituir a [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copyproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copypropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) métodos.

- `Get-ItemProperty`: Este cmdlet obtém as propriedades de um item. Para suportar este cmdlet, substituir a [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) e [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) métodos.

- `Move-ItemProperty`: Este cmdlet permite ao utilizador mover uma propriedade e o respetivo valor de uma localização para outra. Para suportar este cmdlet, substituir a [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Moveproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Movepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) métodos.

- `New-ItemProperty`: Este cmdlet permite ao utilizador criar uma nova propriedade e defina seu valor. Para suportar este cmdlet, substituir a [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) métodos.

- `Remove-ItemProperty`: Este cmdlet permite ao utilizador eliminar uma propriedade e o respetivo valor. Para suportar este cmdlet, substituir a [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) métodos.

- `Rename-ItemProperty`: Este cmdlet permite ao utilizador alterar o nome de uma propriedade. Para suportar este cmdlet, substituir a [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) métodos.

- `Set-ItemProperty`: Este cmdlet permite ao utilizador atualizar as propriedades de um item. Para suportar este cmdlet, substituir a [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) e [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) métodos.

### <a name="location-cmdlets"></a>Cmdlets de localização

- `Get-Location`: Obtém informações sobre o local de trabalho atual. Não é necessário substituir qualquer método para suportar este cmdlet.

- `Pop-Location`: Este cmdlet altera a localização atual para a localização mais recentemente são colocada na pilha. Não é necessário substituir qualquer método para suportar este cmdlet.

- `Push-Location`: Este cmdlet adiciona a localização atual para a parte superior de uma lista de localizações (uma "pilha"). Não é necessário substituir qualquer método para suportar este cmdlet.

- `Set-Location`: Este cmdlet define o local de trabalho atual para uma localização especificada. Não é necessário substituir qualquer método para suportar este cmdlet.

### <a name="path-cmdlets"></a>Cmdlets de caminho

- `Join-Path`: Este cmdlet permite ao utilizador combinar um segmento de caminho pai e filho para criar um caminho internas do fornecedor. Para suportar este cmdlet, substituir a [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) método.

- `Convert-Path`: Este cmdlet converte um caminho de um caminho do Windows PowerShell para um caminho de fornecedor de Windows PowerShell.

- `Split-Path`: Devolve a parte especificada de um caminho.

- `Resolve-Path`: Resolve os carateres universais num caminho e exibe o conteúdo do caminho.

- `Test-Path`: Este cmdlet determina se todos os elementos de um caminho existem. Para suportar este cmdlet, substituir a [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) e [ System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) métodos.

### <a name="psprovider-cmdlets"></a>Cmdlets de PSProvider

- `Get-PSProvider`: Este cmdlet devolve informações sobre os fornecedores disponíveis na sessão. Não é necessário substituir qualquer método para suportar este cmdlet.