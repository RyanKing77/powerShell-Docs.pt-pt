---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Chamar os métodos de recursos de DSC diretamente
ms.openlocfilehash: cf237f638593706e5959e2bcc0d851b0e55baf0e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404752"
---
# <a name="calling-dsc-resource-methods-directly"></a><span data-ttu-id="f646a-103">Chamar os métodos de recursos de DSC diretamente</span><span class="sxs-lookup"><span data-stu-id="f646a-103">Calling DSC resource methods directly</span></span>

><span data-ttu-id="f646a-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f646a-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="f646a-105">Pode utilizar o [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet para chamar diretamente as funções ou métodos de um recurso de DSC (a **Get-TargetResource**, **Set-TargetResource**e  **Test-TargetResource** funções de um recurso baseado em MOF, ou o **Obtenha**, **definir**, e **teste** métodos de um recurso baseado em classes).</span><span class="sxs-lookup"><span data-stu-id="f646a-105">You can use the [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet to directly call the functions or methods of a DSC resource (The **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions of a MOF-based resource, or the **Get**, **Set**, and **Test** methods of a class-based resource).</span></span>
<span data-ttu-id="f646a-106">Isto pode ser utilizado por terceiros, a que pretende utilizar recursos de DSC, ou como uma ferramenta útil durante o desenvolvimento de recursos.</span><span class="sxs-lookup"><span data-stu-id="f646a-106">This can be used by third-parties that want to use DSC resources, or as a helpful tool while developing resources.</span></span>

<span data-ttu-id="f646a-107">Este cmdlet é normalmente utilizado em combinação com uma propriedade de metaconfiguration `refreshMode = 'Disabled'`, mas pode ser utilizado, não importa o que **refreshMode** está definido como.</span><span class="sxs-lookup"><span data-stu-id="f646a-107">This cmdlet is typically used in combination with a metaconfiguration property `refreshMode = 'Disabled'`, but it can be used no matter what **refreshMode** is set to.</span></span>

<span data-ttu-id="f646a-108">Ao chamar o **Invoke-DscResource** cmdlet, especifique qual método ou função a ser chamada utilizando o **método** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f646a-108">When calling the **Invoke-DscResource** cmdlet, you specify which method or function to call by using the **Method** parameter.</span></span> <span data-ttu-id="f646a-109">Especificar as propriedades do recurso, passando uma tabela de hash como o valor do **propriedade** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f646a-109">You specify the properties of the resource by passing a hashtable as the value of the **Property** parameter.</span></span>

<span data-ttu-id="f646a-110">Seguem-se exemplos de chamadas diretas de métodos de recursos:</span><span class="sxs-lookup"><span data-stu-id="f646a-110">The following are examples of directly calling resource methods:</span></span>

## <a name="ensure-a-file-is-present"></a><span data-ttu-id="f646a-111">Certifique-se de que um ficheiro está presente</span><span class="sxs-lookup"><span data-stu-id="f646a-111">Ensure a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a><span data-ttu-id="f646a-112">Testar a que um ficheiro está presente</span><span class="sxs-lookup"><span data-stu-id="f646a-112">Test that a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a><span data-ttu-id="f646a-113">Obter o conteúdo do ficheiro</span><span class="sxs-lookup"><span data-stu-id="f646a-113">Get the contents of file</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

><span data-ttu-id="f646a-114">**Nota:** Não é suportada a chamadas diretas de métodos de recursos compostos.</span><span class="sxs-lookup"><span data-stu-id="f646a-114">**Note:** Directly calling composite resource methods is not supported.</span></span> <span data-ttu-id="f646a-115">Em vez disso, chame os métodos dos recursos subjacentes que compõem o recurso composto.</span><span class="sxs-lookup"><span data-stu-id="f646a-115">Instead, call the methods of the underlying resources that make up the composite resource.</span></span>

## <a name="see-also"></a><span data-ttu-id="f646a-116">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="f646a-116">See Also</span></span>
- [<span data-ttu-id="f646a-117">Escrever um recurso personalizado do DSC com o MOF</span><span class="sxs-lookup"><span data-stu-id="f646a-117">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="f646a-118">Escrever um recurso personalizado do DSC com classes do PowerShell</span><span class="sxs-lookup"><span data-stu-id="f646a-118">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
- [<span data-ttu-id="f646a-119">Depurar os recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="f646a-119">Debugging DSC resources</span></span>](../troubleshooting/debugResource.md)