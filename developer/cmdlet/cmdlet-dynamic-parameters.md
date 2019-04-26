---
title: Parâmetros de cmdlet dinâmico | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 2fc73b6ef5a862fafb7a3c8fe3da19ac71bafc05
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068543"
---
# <a name="cmdlet-dynamic-parameters"></a>Cmdlet Dynamic Parameters (Parâmetros Dinâmicos de Cmdlets)

Cmdlets pode definir os parâmetros que estão disponíveis ao usuário condições especiais, como quando o argumento de outro parâmetro é um valor específico. Esses parâmetros são adicionados em tempo de execução em são denominados *parâmetros dinâmicos* porque eles são adicionados apenas quando for necessário. Por exemplo, pode criar um cmdlet que adiciona vários parâmetros apenas quando é especificado um parâmetro específico.

> [!NOTE]
> Fornecedores e funções do Windows PowerShell também podem definir parâmetros dinâmicos.

## <a name="dynamic-parameters-in-windows-powershell-cmdlets"></a>Parâmetros dinâmicos nos Cmdlets do Windows PowerShell

Windows PowerShell utiliza parâmetros dinâmicos em vários dos seus cmdlets do fornecedor. Por exemplo, o `Get-Item` e `Get-ChildItem` cmdlets adicionar um `CodeSigningCert` parâmetro no tempo de execução quando o `Path` parâmetro do cmdlet Especifica o caminho de fornecedor do certificado. Se o `Path` parâmetro do cmdlet Especifica um caminho para um fornecedor diferente, o `CodeSigningCert` parâmetro não está disponível.

Os exemplos seguintes mostram como o `CodeSigningCert` adicionado o parâmetro no tempo de execução quando o `Get-Item` cmdlet é executado.

No primeiro exemplo, o tempo de execução do Windows PowerShell adicionou o parâmetro e o cmdlet é efetuada com êxito.

```powershell
Get-Item -Path cert:\CurrentUser -codesigningcert
```

```output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

No segundo exemplo, uma unidade de sistema de ficheiros é especificada e, é devolvido um erro. A mensagem de erro indica que o `CodeSigningCert` parâmetro não pode ser encontrado.

```powershell
Get-Item -Path C:\ -codesigningcert
```

```output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a>Suporte para parâmetros dinâmicos

Para oferecer suporte a parâmetros dinâmicos, o código de cmdlet tem de incluir os seguintes elementos.

[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) essa interface fornece o método que obtém os parâmetros dinâmicos.

Exemplo:

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) este método obtém o objeto que contém as definições de parâmetro dinâmico.

Exemplo:

```csharp
 public object GetDynamicParameters()
 {
   if (employee)
   {
     context= new SendGreetingCommandDynamicParameters();
     return context;
   }
   return null;
}
private SendGreetingCommandDynamicParameters context;
```

Classe de parâmetro dinâmico essa classe define os parâmetros a ser adicionado. Essa classe tem de incluir um atributo de parâmetro para cada um dos parâmetros e quaisquer atributos de validação e de Alias que são necessários pelo cmdlet.

Exemplo:

```csharp
public class SendGreetingCommandDynamicParameters
{
  [Parameter]
  [ValidateSet ("Marketing", "Sales", "Development")]
  public string Department
  {
    get { return department; }
    set { department = value; }
  }
  private string department;
}
```

Para obter um exemplo completo de um cmdlet que suporta parâmetros dinâmicos, consulte [como declarar parâmetros dinâmicos](./how-to-declare-dynamic-parameters.md).

## <a name="see-also"></a>Veja Também

[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters)

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Como declarar parâmetros dinâmicos](./how-to-declare-dynamic-parameters.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
