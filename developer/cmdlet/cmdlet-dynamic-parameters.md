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
# <a name="cmdlet-dynamic-parameters"></a><span data-ttu-id="54d18-102">Cmdlet Dynamic Parameters (Parâmetros Dinâmicos de Cmdlets)</span><span class="sxs-lookup"><span data-stu-id="54d18-102">Cmdlet Dynamic Parameters</span></span>

<span data-ttu-id="54d18-103">Cmdlets pode definir os parâmetros que estão disponíveis ao usuário condições especiais, como quando o argumento de outro parâmetro é um valor específico.</span><span class="sxs-lookup"><span data-stu-id="54d18-103">Cmdlets can define parameters that are available to the user under special conditions, such as when the argument of another parameter is a specific value.</span></span> <span data-ttu-id="54d18-104">Esses parâmetros são adicionados em tempo de execução em são denominados *parâmetros dinâmicos* porque eles são adicionados apenas quando for necessário.</span><span class="sxs-lookup"><span data-stu-id="54d18-104">These parameters are added at runtime and are referred to as *dynamic parameters* because they are added only when they are needed.</span></span> <span data-ttu-id="54d18-105">Por exemplo, pode criar um cmdlet que adiciona vários parâmetros apenas quando é especificado um parâmetro específico.</span><span class="sxs-lookup"><span data-stu-id="54d18-105">For example, you can design a cmdlet that adds several parameters only when a specific switch parameter is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="54d18-106">Fornecedores e funções do Windows PowerShell também podem definir parâmetros dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="54d18-106">Providers and Windows PowerShell functions can also define dynamic parameters.</span></span>

## <a name="dynamic-parameters-in-windows-powershell-cmdlets"></a><span data-ttu-id="54d18-107">Parâmetros dinâmicos nos Cmdlets do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="54d18-107">Dynamic Parameters in Windows PowerShell Cmdlets</span></span>

<span data-ttu-id="54d18-108">Windows PowerShell utiliza parâmetros dinâmicos em vários dos seus cmdlets do fornecedor.</span><span class="sxs-lookup"><span data-stu-id="54d18-108">Windows PowerShell uses dynamic parameters in several of its provider cmdlets.</span></span> <span data-ttu-id="54d18-109">Por exemplo, o `Get-Item` e `Get-ChildItem` cmdlets adicionar um `CodeSigningCert` parâmetro no tempo de execução quando o `Path` parâmetro do cmdlet Especifica o caminho de fornecedor do certificado.</span><span class="sxs-lookup"><span data-stu-id="54d18-109">For example, the `Get-Item` and `Get-ChildItem` cmdlets add a `CodeSigningCert` parameter at runtime when the `Path` parameter of the cmdlet specifies the Certificate provider path.</span></span> <span data-ttu-id="54d18-110">Se o `Path` parâmetro do cmdlet Especifica um caminho para um fornecedor diferente, o `CodeSigningCert` parâmetro não está disponível.</span><span class="sxs-lookup"><span data-stu-id="54d18-110">If the `Path` parameter of the cmdlet specifies a path for a different provider, the `CodeSigningCert` parameter is not available.</span></span>

<span data-ttu-id="54d18-111">Os exemplos seguintes mostram como o `CodeSigningCert` adicionado o parâmetro no tempo de execução quando o `Get-Item` cmdlet é executado.</span><span class="sxs-lookup"><span data-stu-id="54d18-111">The following examples show how the `CodeSigningCert` parameter is added at runtime when the `Get-Item` cmdlet is run.</span></span>

<span data-ttu-id="54d18-112">No primeiro exemplo, o tempo de execução do Windows PowerShell adicionou o parâmetro e o cmdlet é efetuada com êxito.</span><span class="sxs-lookup"><span data-stu-id="54d18-112">In the first example, the Windows PowerShell runtime has added the parameter, and the cmdlet is successful.</span></span>

```powershell
Get-Item -Path cert:\CurrentUser -codesigningcert
```

```output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

<span data-ttu-id="54d18-113">No segundo exemplo, uma unidade de sistema de ficheiros é especificada e, é devolvido um erro.</span><span class="sxs-lookup"><span data-stu-id="54d18-113">In the second example, a FileSystem drive is specified, and an error is returned.</span></span> <span data-ttu-id="54d18-114">A mensagem de erro indica que o `CodeSigningCert` parâmetro não pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="54d18-114">The error message indicates that the `CodeSigningCert` parameter cannot be found.</span></span>

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

## <a name="support-for-dynamic-parameters"></a><span data-ttu-id="54d18-115">Suporte para parâmetros dinâmicos</span><span class="sxs-lookup"><span data-stu-id="54d18-115">Support for Dynamic Parameters</span></span>

<span data-ttu-id="54d18-116">Para oferecer suporte a parâmetros dinâmicos, o código de cmdlet tem de incluir os seguintes elementos.</span><span class="sxs-lookup"><span data-stu-id="54d18-116">To support dynamic parameters, the cmdlet code must include the following elements.</span></span>

<span data-ttu-id="54d18-117">[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) essa interface fornece o método que obtém os parâmetros dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="54d18-117">[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) This interface provides the method that retrieves the dynamic parameters.</span></span>

<span data-ttu-id="54d18-118">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="54d18-118">Example:</span></span>

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

<span data-ttu-id="54d18-119">[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) este método obtém o objeto que contém as definições de parâmetro dinâmico.</span><span class="sxs-lookup"><span data-stu-id="54d18-119">[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) This method retrieves the object that contains the dynamic parameter definitions.</span></span>

<span data-ttu-id="54d18-120">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="54d18-120">Example:</span></span>

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

<span data-ttu-id="54d18-121">Classe de parâmetro dinâmico essa classe define os parâmetros a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="54d18-121">Dynamic Parameter class This class defines the parameters to be added.</span></span> <span data-ttu-id="54d18-122">Essa classe tem de incluir um atributo de parâmetro para cada um dos parâmetros e quaisquer atributos de validação e de Alias que são necessários pelo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="54d18-122">This class must include a Parameter attribute for each parameter and any optional Alias and Validation attributes that are needed by the cmdlet.</span></span>

<span data-ttu-id="54d18-123">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="54d18-123">Example:</span></span>

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

<span data-ttu-id="54d18-124">Para obter um exemplo completo de um cmdlet que suporta parâmetros dinâmicos, consulte [como declarar parâmetros dinâmicos](./how-to-declare-dynamic-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="54d18-124">For a complete example of a cmdlet that supports dynamic parameters, see [How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="54d18-125">Veja Também</span><span class="sxs-lookup"><span data-stu-id="54d18-125">See Also</span></span>

[<span data-ttu-id="54d18-126">System.Management.Automation.Idynamicparameters</span><span class="sxs-lookup"><span data-stu-id="54d18-126">System.Management.Automation.Idynamicparameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters)

[<span data-ttu-id="54d18-127">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span><span class="sxs-lookup"><span data-stu-id="54d18-127">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="54d18-128">Como declarar parâmetros dinâmicos</span><span class="sxs-lookup"><span data-stu-id="54d18-128">How to Declare Dynamic Parameters</span></span>](./how-to-declare-dynamic-parameters.md)

[<span data-ttu-id="54d18-129">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="54d18-129">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
