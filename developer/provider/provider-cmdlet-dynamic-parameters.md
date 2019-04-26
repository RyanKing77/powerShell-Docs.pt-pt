---
title: Os parâmetros de dinâmicos de cmdlets do fornecedor | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f1069f7-8fa8-4622-9e2c-af29b0b961c2
caps.latest.revision: 6
ms.openlocfilehash: a50de014988336c473c565b506a73de1c864d7e0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080973"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>Provider cmdlet dynamic parameters (Parâmetros dinâmicos de cmdlets de fornecedores)

Fornecedores de podem definir parâmetros dinâmicos que são adicionados a um cmdlet de fornecedor quando o usuário Especifica um determinado valor para um dos parâmetros estáticos do cmdlet. Por exemplo, um provedor pode adicionar parâmetros dinâmicos diferentes com base no caminho de que o utilizador Especifica quando eles chamam o `Get-Item` ou `Set-Item` cmdlets do fornecedor.

## <a name="dynamic-parameter-methods"></a>Métodos de parâmetro dinâmico

Os parâmetros dinâmicos são definidos através da implementação de um dos métodos de parâmetro dinâmico, tal como o [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) e [ System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)metod. Esses métodos retornam um objeto com propriedades públicas que são decoradas com atributos semelhantes dos cmdlets autónomo. Eis um exemplo de uma implementação do [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) método obtido a partir do fornecedor de certificados:

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

Ao contrário dos parâmetros estáticos de cmdlets do fornecedor, pode especificar as características destes parâmetros da mesma forma que os parâmetros são definidos nos cmdlets autónomo. Eis um exemplo de uma classe de parâmetro dinâmico, retirado do fornecedor de certificados:

```csharp
internal sealed class CertificateProviderDynamicParameters
{
  /// <summary>
  /// Dynamic parameter the controls whether we only return
  /// code signing certs.
  /// </summary>
  [Parameter()]
  public SwitchParameter CodeSigningCert
  {
    get
    {
      {
        return codeSigningCert;
      }
    }

    set
    {
      {
        codeSigningCert = value;
      }
    }
  }

    private SwitchParameter codeSigningCert = new SwitchParameter();
}
```

## <a name="dynamic-parameters"></a>Parâmetros dinâmicos

Aqui está uma lista dos parâmetros estáticos que podem ser utilizados para adicionar parâmetros dinâmicos.

`Clear-Content` cmdlet pode definir parâmetros dinâmicos que são acionados pelos `Path` parâmetro do cmdlet Clear-limpar implementando o [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters* ](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) método.

`Clear-Item` cmdlet pode definir parâmetros dinâmicos que são acionados pela `Path` parâmetro do `Clear-Item` cmdlet, implementando o [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) método.

`Clear-ItemProperty` cmdlet pode definir parâmetros dinâmicos que são acionados pela `Path` parâmetro do `Clear-ItemProperty` cmdlet, implementando o [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) método.

`Copy-Item` cmdlet pode definir parâmetros dinâmicos que são acionados pelos `Path`, `Destination`, e `Recurse` parâmetros do `Copy-Item` cmdlet implementando o [ System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) método.

Cmdlet Get-ChildItems pode definir parâmetros dinâmicos que são acionados pelos `Path` e `Recurse` parâmetros do `Get-ChildItem` cmdlet implementando o [ System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) e [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) métodos.

`Get-Content` cmdlet pode definir parâmetros dinâmicos que são acionados pela `Path` parâmetro do `Get-Content` cmdlet, implementando o [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) método.

`Get-Item` cmdlet pode definir parâmetros dinâmicos que são acionados pela `Path` parâmetro do `Get-Item` cmdlet, implementando o [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) método.

`Get-ItemProperty` cmdlet pode definir parâmetros dinâmicos que são acionados pelos `Path` e `Name` parâmetros do `Get-ItemProperty` cmdlet implementando o [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) método.

`Invoke-Item` cmdlet pode definir parâmetros dinâmicos que são acionados pela `Path` parâmetro do `Invoke-Item` cmdlet, implementando o [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) método.

`Move-Item` cmdlet pode definir parâmetros dinâmicos que são acionados pelos `Path` e `Destination` parâmetros do `Move-Item` cmdlet implementando o [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) método.

`New-Item` cmdlet pode definir parâmetros dinâmicos que são acionados pelos `Path`, `ItemType`, e `Value` parâmetros do `New-Item` cmdlet implementando o [ System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) método.

`New-ItemProperty` cmdlet pode definir parâmetros dinâmicos que são acionados pelos `Path`, `Name`, `PropertyType`, e `Value` parâmetros do `New-ItemProperty` cmdlet implementando o [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) método.

`New-PSDrive` cmdlet pode definir parâmetros dinâmicos que são acionados pelos [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objeto devolvido pela `New-PSDrive` cmdlet implementando o [ System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) método.

`Remove-Item` Pode definir parâmetros dinâmicos que são acionados pela `Path` e `Recurse` parâmetros do `Remove-Item` cmdlet implementando o [ System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) método.

`Remove-ItemProperty` Pode definir parâmetros dinâmicos que são acionados pela `Path` e `Name` parâmetros do `Remove-ItemProperty` cmdlet implementando o [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) método.

`Rename-Item` cmdlet pode definir parâmetros dinâmicos que são acionados pelos `Path` e `NewName` parâmetros do `Rename-Item` cmdlet implementando o [ System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) método.

`Rename-ItemProperty` Pode definir parâmetros dinâmicos que são acionados pela `Path`, `Name`, e `NewName` parâmetros do `Rename-ItemProperty` cmdlet implementando o [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) método.

`Set-Content` cmdlet pode definir parâmetros dinâmicos que são acionados pela `Path` parâmetro do `Set-Content` cmdlet, implementando o [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) método.

`Set-Item` cmdlet pode definir parâmetros dinâmicos que são acionados pelos `Path` e `Value` parâmetros do `Set-Item` cmdlet implementando o [ System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) método.

`Set-ItemProperty` cmdlet pode definir parâmetros dinâmicos que são acionados pelos `Path` e `Value` parâmetros do `Set-Item` cmdlet implementando o [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) método.

`Test-Path` cmdlet pode definir parâmetros dinâmicos que são acionados pela `Path` parâmetro do `Test-Path` cmdlet, implementando o [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) método.

## <a name="see-also"></a>Veja Também

[Escrever um fornecedor do Windows PowerShell](./writing-a-windows-powershell-provider.md)