---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Chamar os métodos de recursos de DSC diretamente
ms.openlocfilehash: 3ec3a3a8da615f45f3fdd28b1c1e46e312507ed5
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="calling-dsc-resource-methods-directly"></a><span data-ttu-id="6cd32-103">Chamar os métodos de recursos de DSC diretamente</span><span class="sxs-lookup"><span data-stu-id="6cd32-103">Calling DSC resource methods directly</span></span>

><span data-ttu-id="6cd32-104">Aplica-se a: O Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6cd32-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="6cd32-105">Pode utilizar o [Invoke-DscResource](https://technet.microsoft.com/library/mt517869.aspx) cmdlet para chamar diretamente as funções ou métodos de um recurso de DSC (o **Get-TargetResource**, **conjunto TargetResource**e  **Test-TargetResource** funções de um recurso com base no MOF, ou o **obter**, **definir**, e **teste** métodos de um recurso com base na classe).</span><span class="sxs-lookup"><span data-stu-id="6cd32-105">You can use the [Invoke-DscResource](https://technet.microsoft.com/library/mt517869.aspx) cmdlet to directly call the functions or methods of a DSC resource (The **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions of a MOF-based resource, or the **Get**, **Set**, and **Test** methods of a class-based resource).</span></span>
<span data-ttu-id="6cd32-106">Isto pode ser utilizado por terceiros, a que pretendem utilizar recursos de DSC ou como uma ferramenta útil enquanto programar recursos.</span><span class="sxs-lookup"><span data-stu-id="6cd32-106">This can be used by third-parties that want to use DSC resources, or as a helpful tool while developing resources.</span></span>

<span data-ttu-id="6cd32-107">Este cmdlet é normalmente utilizado em combinação com uma propriedade de configuração meta `refreshMode = 'Disabled'`, mas podem ser utilizado, independentemente da que **refreshMode** está definido como.</span><span class="sxs-lookup"><span data-stu-id="6cd32-107">This cmdlet is typically used in combination with a metaconfiguration property `refreshMode = 'Disabled'`, but it can be used no matter what **refreshMode** is set to.</span></span>

<span data-ttu-id="6cd32-108">Quando chamar o **Invoke-DscResource** cmdlet, especifique o método ou a função para chamar utilizando o **método** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6cd32-108">When calling the **Invoke-DscResource** cmdlet, you specify which method or function to call by using the **Method** parameter.</span></span> <span data-ttu-id="6cd32-109">Especificar as propriedades do recurso transferindo uma tabela hash, como o valor de **propriedade** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6cd32-109">You specify the properties of the resource by passing a hashtable as the value of the **Property** parameter.</span></span>

<span data-ttu-id="6cd32-110">Seguem-se exemplos de chamar directamente os métodos de recursos:</span><span class="sxs-lookup"><span data-stu-id="6cd32-110">The following are examples of directly calling resource methods:</span></span>

## <a name="ensure-a-file-is-present"></a><span data-ttu-id="6cd32-111">Certifique-se de que um ficheiro está presente</span><span class="sxs-lookup"><span data-stu-id="6cd32-111">Ensure a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a><span data-ttu-id="6cd32-112">Testar se um ficheiro está presente</span><span class="sxs-lookup"><span data-stu-id="6cd32-112">Test that a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a><span data-ttu-id="6cd32-113">Obter o conteúdo do ficheiro</span><span class="sxs-lookup"><span data-stu-id="6cd32-113">Get the contents of file</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

><span data-ttu-id="6cd32-114">**Nota:** diretamente chamar os métodos de composto de recurso não é suportado.</span><span class="sxs-lookup"><span data-stu-id="6cd32-114">**Note:** Directly calling composite resource methods is not supported.</span></span> <span data-ttu-id="6cd32-115">Em vez disso, chame os métodos dos recursos subjacentes que compõem o recurso composto.</span><span class="sxs-lookup"><span data-stu-id="6cd32-115">Instead, call the methods of the underlying resources that make up the composite resource.</span></span>

## <a name="see-also"></a><span data-ttu-id="6cd32-116">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="6cd32-116">See Also</span></span>
- [<span data-ttu-id="6cd32-117">Escrever um recurso personalizado de DSC com MOF</span><span class="sxs-lookup"><span data-stu-id="6cd32-117">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
- [<span data-ttu-id="6cd32-118">Escrever um recurso personalizado de DSC com classes de PowerShell</span><span class="sxs-lookup"><span data-stu-id="6cd32-118">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
- [<span data-ttu-id="6cd32-119">Depurar os recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="6cd32-119">Debugging DSC resources</span></span>](debugResource.md)