---
title: Tipos de provedor | Microsoft Docs
ms.custom: ''
ms.date: 08/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e523a8e1-42e4-4633-887f-fb74b3464561
caps.latest.revision: 12
ms.openlocfilehash: 0a9bfe5dd0978ffce66db1b18ef4d82be6c1a7f2
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986656"
---
# <a name="provider-types"></a>Provider types (Tipos de fornecedores)

Os provedores definem sua funcionalidade básica alterando como os cmdlets do provedor, fornecidos pelo PowerShell, executam suas ações. Por exemplo, os provedores podem usar a funcionalidade padrão do `Get-Item` cmdlet ou podem alterar a forma como esse cmdlet opera ao recuperar itens do armazenamento de dados. A funcionalidade do provedor descrita neste documento inclui a funcionalidade definida pela substituição de métodos de interfaces e classes base do provedor específico.

> [!NOTE]
> Para recursos de provedor predefinidos pelo PowerShell, consulte [recursos do provedor](/previous-versions//ee126189(v=vs.85)).

## <a name="drive-enabled-providers"></a>Provedores habilitados para unidade

Provedores habilitados para unidade especificam as unidades padrão disponíveis para o usuário e permitem que o usuário adicione ou remova unidades. Na maioria dos casos, os provedores são provedores habilitados para unidade porque exigem uma unidade padrão para acessar o armazenamento de dados. No entanto, ao escrever seu próprio provedor, você pode ou não desejar permitir que o usuário crie e remova unidades.

Para criar um provedor habilitado para unidade, sua classe de provedor deve derivar da classe [System. Management. Automation. Provider. DriveCmdletProvider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) ou de outra classe derivada dessa classe. A classe **System. Management. Automation. Provider. DriveCmdletProvider** define os métodos a seguir para implementar as unidades padrão do provedor e dar suporte `New-PSDrive` aos `Remove-PSDrive` cmdlets e. Na maioria dos casos, para dar suporte a um cmdlet de provedor, você deve substituir o método que o mecanismo do PowerShell chama para invocar o cmdlet `New-PSDrive` , como o `NewDrive` método para o cmdlet e, opcionalmente, você pode `NewDriveDynamicParameters` substituir um segundo método, como , para adicionar parâmetros dinâmicos ao cmdlet.

- O método [System. Management. Automation. Provider. DriveCmdletProvider. InitializeDefaultDrives](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) define as unidades padrão que estão disponíveis para o usuário sempre que o provedor é usado.

- Os métodos [System. Management. Automation. Provider. DriveCmdletProvider. NewDrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) e [System. Management. Automation. Provider. DriveCmdletProvider. NewDriveDynamicParameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) definem como o provedor dá suporte ao `New-PSDrive`cmdlet do provedor. Esse cmdlet permite que o usuário crie unidades para acessar o armazenamento de dados.

- O método [System. Management. Automation. Provider. DriveCmdletProvider. RemoveDrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) define como seu provedor oferece suporte `Remove-PSDrive` ao cmdlet do provedor. Esse cmdlet permite que o usuário remova unidades do armazenamento de dados.

## <a name="item-enabled-providers"></a>Provedores habilitados para item

Provedores habilitados para item permitem que o usuário obtenha, defina ou limpe os itens no repositório de dados. Um "item" é um elemento do armazenamento de dados que o usuário pode acessar ou gerenciar de forma independente. Para criar um provedor habilitado para item, sua classe de provedor deve derivar da classe [System. Management. Automation. Provider.](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) @ cmdletprovider ou de outra classe que deriva dessa classe.

A classe **System. Management. Automation. Provider.** mycmdletprovider define os métodos a seguir para implementar cmdlets de provedor específicos. Na maioria dos casos, para dar suporte a um cmdlet de provedor, você deve substituir o método que o mecanismo do PowerShell chama para invocar o cmdlet `Clear-Item` , como o `ClearItem` método para o cmdlet e, opcionalmente, você pode `ClearItemDynamicParameters` substituir um segundo método, como , para adicionar parâmetros dinâmicos ao cmdlet.

- Os métodos [System. Management. Automation. Provider. Docmdletprovider. ClearItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) e [System. Management. Automation. Provider. @ cmdletprovider. ClearItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) definem como seu provedor dá suporte ao `Clear-Item`cmdlet do provedor. Esse cmdlet permite que o usuário remova o valor de um item no repositório de dados.

- Os métodos [System. Management. Automation. Provider. Docmdletprovider. GetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) e [System. Management. Automation. Provider. @ cmdletprovider. GetItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) definem como seu provedor dá `Get-Item` suporte ao cmdlet do provedor. Esse cmdlet permite que o usuário recupere dados do armazenamento de dados.

- Os métodos [System. Management. Automation. Provider. Docmdletprovider. SetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) e [System. Management. Automation. Provider. @ cmdletprovider. SetItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) definem como seu provedor dá `Set-Item` suporte ao cmdlet do provedor. Esse cmdlet permite que o usuário atualize os valores de itens no armazenamento de dados.

- Os métodos [System. Management. Automation. Provider. createcmdletprovider. InvokeDefaultAction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) e [System. Management. Automation. Provider. docmdletprovider. InvokeDefaultActionDynamicParameters](/dotnet/api/system.management.automation.provider.itemcmdletprovider.invokedefaultactiondynamicparameters) definem como seu provedor dá suporte `Invoke-Item` ao cmdlet do provedor. Esse cmdlet permite que o usuário execute a ação padrão especificada pelo item.

- Os métodos [System. Management. Automation. Provider. Createcmdletprovider.](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) [ItemExistsDynamicParameters e System. Management. Automation. Provider. @ cmdletprovider.](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) testdefinem como seu provedor dá suporte ao `Test-Path`cmdlet do provedor. Esse cmdlet permite que o usuário determine se todos os elementos de um caminho existem.

Além dos métodos usados para implementar cmdlets do provedor, a classe **System. Management. Automation. Provider.** createcmdletprovider também define os seguintes métodos:

- O método [System. Management. Automation. Provider. Docmdletprovider. ExpandPath](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ExpandPath) permite que o usuário use curingas ao especificar o caminho do provedor.

- O [System. Management. Automation. Provider. @ cmdletprovider. IsValidPath](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) é usado para determinar se um caminho é sintaticamente e semanticamente válido para o provedor.

## <a name="container-enabled-providers"></a>Provedores habilitados para contêiner

Provedores habilitados para contêiner permitem que o usuário gerencie itens que são contêineres. Um contêiner é um grupo de itens filho em um item pai comum. Para criar um provedor habilitado para contêiner, sua classe de provedor deve derivar da classe [System. Management. Automation. Provider. ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) ou de outra classe derivada dessa classe.

> [!IMPORTANT]
> Provedores habilitados para contêiner não podem acessar armazenamentos de dados que contêm Contêineres aninhados. Se um item filho de um contêiner for outro contêiner, você deverá implementar um provedor habilitado para navegação.

A classe **System. Management. Automation. Provider. ContainerCmdletProvider** define os métodos a seguir para implementar cmdlets de provedor específicos. Na maioria dos casos, para dar suporte a um cmdlet de provedor, você deve substituir o método que o mecanismo do PowerShell chama para invocar o cmdlet `Copy-Item` , como o `CopyItem` método para o cmdlet e, opcionalmente, você pode `CopyItemDynamicParameters` substituir um segundo método, como , para adicionar parâmetros dinâmicos ao cmdlet.

- Os métodos [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) e [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) definem como o provedor dá suporte ao `Copy-Item` cmdlet do provedor. Esse cmdlet permite que o usuário Copie um item de um local para outro.

- Os métodos [System. Management. Automation. Provider. ContainerCmdletProvider.](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) GetChildItems e [System. Management. Automation. Provider. ContainerCmdletProvider. GetChildItemsDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) definem como seu provedor dá suporte `Get-ChildItem` ao cmdlet do provedor. Esse cmdlet permite que o usuário recupere os itens filho do item pai.

- Os métodos [System. Management. Automation. Provider. ContainerCmdletProvider.](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) getchildnames e [System. Management. Automation. Provider. ContainerCmdletProvider. GetChildNamesDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) definem como seu provedor oferece suporte `Get-ChildItem` ao cmdlet do provedor `Name` se seu parâmetro for especificado.

- Os métodos [System. Management. Automation. Provider. ContainerCmdletProvider. NewItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) e [System. Management. Automation. Provider. ContainerCmdletProvider. NewItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) definem como o provedor dá suporte ao `New-Item` cmdlet do provedor. Esse cmdlet permite que o usuário crie novos itens no armazenamento de dados.

- Os métodos [System. Management. Automation. Provider. ContainerCmdletProvider. RemoveItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) e [System. Management. Automation. Provider. ContainerCmdletProvider. RemoveItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) definem como o provedor dá suporte ao `Remove-Item` cmdlet do provedor. Esse cmdlet permite que o usuário remova itens do armazenamento de dados.

- Os métodos [System. Management. Automation. Provider. ContainerCmdletProvider. RenameItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) e [System. Management. Automation. Provider. ContainerCmdletProvider. RenameItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) definem como o provedor dá suporte ao `Rename-Item` cmdlet do provedor. Esse cmdlet permite que o usuário renomeie itens no armazenamento de dados.

Além dos métodos usados para implementar cmdlets do provedor, a classe **System. Management. Automation. Provider. ContainerCmdletProvider** também define os seguintes métodos:

- O método [System. Management. Automation. Provider. ContainerCmdletProvider. HasChildItems](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) pode ser usado pela classe Provider para determinar se um item tem itens filho.

- O método [System. Management. Automation. Provider. ContainerCmdletProvider. ConvertPath](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.ConvertPath) pode ser usado pela classe Provider para criar um novo caminho específico do provedor a partir de um caminho especificado.

## <a name="navigation-enabled-providers"></a>Provedores habilitados para navegação

Os provedores habilitados para navegação permitem que o usuário mova itens no armazenamento de dados. Para criar um provedor habilitado para navegação, sua classe de provedor deve derivar da classe [System. Management. Automation. Provider. NavigationCmdletProvider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .

A classe **System. Management. Automation. Provider. NavigationCmdletProvider** define os métodos a seguir para implementar cmdlets de provedor específicos. Na maioria dos casos, para dar suporte a um cmdlet de provedor, você deve substituir o método que o mecanismo do PowerShell chama para invocar o cmdlet `Move-Item` , como o `MoveItem` método para o cmdlet e, opcionalmente, você pode `MoveItemDynamicParameters` substituir um segundo método, como , para adicionar parâmetros dinâmicos ao cmdlet.

- Os métodos [System. Management. Automation. Provider. NavigationCmdletProvider. MoveItem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) e [System. Management. Automation. Provider. NavigationCmdletProvider. MoveItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) definem como o provedor dá suporte ao `Move-Item` cmdlet do provedor. Esse cmdlet permite que o usuário mova um item de um local na loja para outro local.

- O método [System. Management. Automation. Provider. NavigationCmdletProvider. MakePath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) define como seu provedor oferece suporte `Join-Path` ao cmdlet do provedor. Esse cmdlet permite que o usuário combine um segmento de caminho pai e filho para criar um caminho interno de provedor.

Além dos métodos usados para implementar cmdlets do provedor, a classe **System. Management. Automation. Provider. NavigationCmdletProvider** também define os seguintes métodos:

- O método [System. Management. Automation. Provider. NavigationCmdletProvider.](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) getchildname extrai o nome do nó filho de um caminho.

- O método [System. Management. Automation. Provider. NavigationCmdletProvider. GetParentPath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) extrai a parte pai de um caminho.

- O método [System. Management. Automation. Provider. NavigationCmdletProvider. IsItemContainer](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) determina se o item é um item de contêiner. Nesse contexto, um contêiner é um grupo de itens filho em um item pai comum.

- O método [System. Management. Automation. Provider. NavigationCmdletProvider. NormalizeRelativePath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) retorna um caminho para um item que é relativo a um caminho base especificado.

## <a name="content-enabled-providers"></a>Provedores habilitados para conteúdo

Os provedores habilitados para conteúdo permitem que o usuário Limpe, obtenha ou defina o conteúdo de itens em um armazenamento de dados.
Por exemplo, o provedor FileSystem permite que você limpe, obtenha e defina o conteúdo dos arquivos no sistema de arquivos. Para criar um provedor de conteúdo habilitado, sua classe de provedor deve implementar os métodos da interface [System. Management. Automation. Provider. IContentCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) .

A interface **System. Management. Automation. Provider. IContentCmdletProvider** define os métodos a seguir para implementar cmdlets de provedor específicos. Na maioria dos casos, para dar suporte a um cmdlet de provedor, você deve substituir o método que o mecanismo do PowerShell chama para invocar o cmdlet `Clear-Content` , como o `ClearContent` método para o cmdlet e, opcionalmente, você pode `ClearContentDynamicParameters` substituir um segundo método, como , para adicionar parâmetros dinâmicos ao cmdlet.

- Os métodos [System. Management. Automation. Provider. IContentCmdletProvider. ClearContent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) e [System. Management. Automation. Provider. IContentCmdletProvider. ClearContentDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) definem como o provedor dá suporte o `Clear-Content` cmdlet do provedor. Esse cmdlet permite que o usuário exclua o conteúdo de um item sem excluir o item.

- Os métodos [System. Management. Automation. Provider. IContentCmdletProvider. GetContentReader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) e [System. Management. Automation. Provider. IContentCmdletProvider. GetContentReaderDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) definem como seu provedor dá suporte `Get-Content` ao cmdlet do provedor. Esse cmdlet permite que o usuário recupere o conteúdo de um item. O `System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader` método retorna uma interface [System. Management. Automation. Provider. IContentReader](/dotnet/api/System.Management.Automation.Provider.IContentReader) que define os métodos usados para ler o conteúdo.

- Os métodos [System. Management. Automation. Provider. IContentCmdletProvider. GetContentWriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) e [System. Management. Automation. Provider. IContentCmdletProvider. GetContentWriterDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) definem como seu provedor dá suporte `Set-Content` ao cmdlet do provedor. Esse cmdlet permite que o usuário atualize o conteúdo de um item. O `System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter` método retorna uma interface [System. Management. Automation. Provider. IContentWriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) que define os métodos usados para gravar o conteúdo.

## <a name="property-enabled-providers"></a>Provedores habilitados para propriedades

Provedores habilitados para propriedades permitem que o usuário gerencie as propriedades dos itens no armazenamento de dados.
Para criar um provedor habilitado para propriedade, sua classe de provedor deve implementar os métodos de [System. Management. Automation. Provider. IPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) e [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider ](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider)interfaces. Na maioria dos casos, para dar suporte a um cmdlet de provedor, você deve substituir o método que o mecanismo do PowerShell chama para invocar o cmdlet, como o `ClearProperty` método para o cmdlet Clear-Property e, opcionalmente, você pode substituir um segundo método, como `ClearPropertyDynamicParameters` , para adicionar parâmetros dinâmicos ao cmdlet.

A interface **System. Management. Automation. Provider. IPropertyCmdletProvider** define os seguintes métodos para implementar cmdlets de provedor específicos:

- Os métodos [System. Management. Automation. Provider. IPropertyCmdletProvider. clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) e [System. Management. Automation. Provider. IPropertyCmdletProvider. ClearPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) definem como seu provedor dá suporte `Clear-ItemProperty` ao cmdlet do provedor. Esse cmdlet permite que o usuário exclua o valor de uma propriedade.

- Os métodos [System. Management. Automation. Provider. IPropertyCmdletProvider. GetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) e [System. Management. Automation. Provider. IPropertyCmdletProvider. GetPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) definem como o provedor dá suporte o `Get-ItemProperty` cmdlet do provedor. Esse cmdlet permite que o usuário recupere a propriedade de um item.

- Os métodos [System. Management. Automation. Provider. IPropertyCmdletProvider. SetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) e [System. Management. Automation. Provider. IPropertyCmdletProvider. SetPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) definem como o provedor dá suporte o `Set-ItemProperty` cmdlet do provedor. Esse cmdlet permite que o usuário atualize as propriedades de um item.

  A interface **System. Management. Automation. Provider. IDynamicPropertyCmdletProvider** define os seguintes métodos para implementar cmdlets de provedor específicos:

- Os métodos [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. copieproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) e [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. CopyPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) definem como seu o provedor oferece `Copy-ItemProperty` suporte ao cmdlet do provedor. Esse cmdlet permite que o usuário Copie uma propriedade e seu valor de um local para outro.

- Os métodos [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. moveproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) e [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. MovePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) definem como seu o provedor oferece `Move-ItemProperty` suporte ao cmdlet do provedor. Esse cmdlet permite que o usuário mova uma propriedade e seu valor de um local para outro.

- Os métodos [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. NewProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) e [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. NewPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) definem como seu o provedor oferece `New-ItemProperty` suporte ao cmdlet do provedor. Esse cmdlet permite que o usuário crie uma nova propriedade e defina seu valor.

- Os métodos [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. RemoveProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) e [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. RemovePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) definem como seu provedor oferece suporte `Remove-ItemProperty` ao cmdlet. Esse cmdlet permite que o usuário exclua uma propriedade e seu valor.

- Os métodos [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider.](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) renameproperty e [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. RenamePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) definem como seu provedor oferece suporte `Rename-ItemProperty` ao cmdlet. Esse cmdlet permite que o usuário altere o nome de uma propriedade.

## <a name="see-also"></a>Consulte também

[about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)

[Escrevendo um provedor do Windows PowerShell](./writing-a-windows-powershell-provider.md)
