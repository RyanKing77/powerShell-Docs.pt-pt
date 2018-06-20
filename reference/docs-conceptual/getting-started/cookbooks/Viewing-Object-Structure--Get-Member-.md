---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Membro de Get de estrutura de objeto de visualização
ms.assetid: a1819ed2-2ef3-453a-b2b0-f3589c550481
ms.openlocfilehash: cc93e45e4306b3d623c1d3d1096dd20c1afc59c8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950748"
---
# <a name="viewing-object-structure-get-member"></a><span data-ttu-id="55b46-103">Visualizar a estrutura de objeto (Get-membro)</span><span class="sxs-lookup"><span data-stu-id="55b46-103">Viewing Object Structure (Get-Member)</span></span>

<span data-ttu-id="55b46-104">Porque os objetos reproduzir essa uma função central no Windows PowerShell, existem vários comandos nativos concebidos para trabalhar com os tipos de objeto arbitrários.</span><span class="sxs-lookup"><span data-stu-id="55b46-104">Because objects play such a central role in Windows PowerShell, there are several native commands designed to work with arbitrary object types.</span></span> <span data-ttu-id="55b46-105">O mais importante é o **Get-membro** comando.</span><span class="sxs-lookup"><span data-stu-id="55b46-105">The most important one is the **Get-Member** command.</span></span>

<span data-ttu-id="55b46-106">A técnica mais simples para analisar os objetos que um comando devolve é para encaminhar a saída desse comando para o **Get-membro** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="55b46-106">The simplest technique for analyzing the objects that a command returns is to pipe the output of that command to the **Get-Member** cmdlet.</span></span> <span data-ttu-id="55b46-107">O **Get-membro** cmdlet mostra-lhe o nome do tipo de objeto formal e uma lista completa dos seus membros.</span><span class="sxs-lookup"><span data-stu-id="55b46-107">The **Get-Member** cmdlet shows you the formal name of the object type and a complete listing of its members.</span></span> <span data-ttu-id="55b46-108">O número de elementos que são devolvidos por vezes, pode ser muito confuso.</span><span class="sxs-lookup"><span data-stu-id="55b46-108">The number of elements that are returned can sometimes be overwhelming.</span></span> <span data-ttu-id="55b46-109">Por exemplo, um objeto de processo pode ter mais de 100 membros.</span><span class="sxs-lookup"><span data-stu-id="55b46-109">For example, a process object can have over 100 members.</span></span>

<span data-ttu-id="55b46-110">Para ver todos os membros de um objeto de processo e a saída de página, para que possa visualizar todos, escreva:</span><span class="sxs-lookup"><span data-stu-id="55b46-110">To see all the members of a Process object and page the output so you can view all of it, type:</span></span>

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

<span data-ttu-id="55b46-111">O resultado deste comando será algo semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="55b46-111">The output from this command will look something like this:</span></span>

```output
TypeName: System.Diagnostics.Process

Name                           MemberType     Definition
----                           ----------     ----------
Handles                        AliasProperty  Handles = Handlecount
Name                           AliasProperty  Name = ProcessName
NPM                            AliasProperty  NPM = NonpagedSystemMemorySize
PM                             AliasProperty  PM = PagedMemorySize
VM                             AliasProperty  VM = VirtualMemorySize
WS                             AliasProperty  WS = WorkingSet
add_Disposed                   Method         System.Void add_Disposed(Event...
...
```

<span data-ttu-id="55b46-112">Iremos pode tornar esta longa lista de informações mais utilizável através de filtragem para elementos que queremos ver.</span><span class="sxs-lookup"><span data-stu-id="55b46-112">We can make this long list of information more usable by filtering for elements we want to see.</span></span> <span data-ttu-id="55b46-113">O **Get-membro** comando permite-lhe listar apenas os membros que são propriedades.</span><span class="sxs-lookup"><span data-stu-id="55b46-113">The **Get-Member** command lets you list only members that are properties.</span></span> <span data-ttu-id="55b46-114">Existem várias formas de propriedades.</span><span class="sxs-lookup"><span data-stu-id="55b46-114">There are several forms of properties.</span></span> <span data-ttu-id="55b46-115">O cmdlet apresenta as propriedades de qualquer tipo, se definimos os **Get-membro MemberType** parâmetro para o valor **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="55b46-115">The cmdlet displays properties of any type if we set the **Get-Member MemberType** parameter to the value **Properties**.</span></span> <span data-ttu-id="55b46-116">A lista resultante ainda está a ser muito longas, mas um pouco mais fácil gerir:</span><span class="sxs-lookup"><span data-stu-id="55b46-116">The resulting list is still very long, but a bit more manageable:</span></span>

```
PS> Get-Process | Get-Member -MemberType Properties

   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
...
ExitCode                   Property       System.Int32 ExitCode {get;}
...
Handle                     Property       System.IntPtr Handle {get;}
...
CPU                        ScriptProperty System.Object CPU {get=$this.Total...
...
Path                       ScriptProperty System.Object Path {get=$this.Main...
...
```

> [!NOTE]
> <span data-ttu-id="55b46-117">Os valores permitidos de MemberType são AliasProperty, CodeProperty, propriedade, NoteProperty, ScriptProperty, propriedades, PropertySet, método, CodeMethod, ScriptMethod, métodos, ParameterizedProperty, MemberSet e todos os.</span><span class="sxs-lookup"><span data-stu-id="55b46-117">The allowed values of MemberType are AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, and All.</span></span>

<span data-ttu-id="55b46-118">Existem mais de 60 propriedades para um processo.</span><span class="sxs-lookup"><span data-stu-id="55b46-118">There are over 60 properties for a process.</span></span> <span data-ttu-id="55b46-119">O motivo que do Windows PowerShell, muitas vezes, mostra que apenas alguns a propriedades de qualquer objecto bem conhecido é o facto de que todos eles mostra produziria uma unmanageable quantidade de informações.</span><span class="sxs-lookup"><span data-stu-id="55b46-119">The reason Windows PowerShell often shows only a handful of properties for any well-known object is that showing all of them would produce an unmanageable amount of information.</span></span>

> [!NOTE]
> <span data-ttu-id="55b46-120">Windows PowerShell determina como apresentar um tipo de objeto através da utilização de informações armazenadas em ficheiros XML com nomes terminados em. format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="55b46-120">Windows PowerShell determines how to display an object type by using information stored in XML files that have names ending in .format.ps1xml.</span></span> <span data-ttu-id="55b46-121">Os dados de formatação de objetos do processo, que são objetos System .NET, são armazenados no DotNetTypes.format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="55b46-121">The formatting data for process objects, which are .NET System.Diagnostics.Process objects, is stored in DotNetTypes.format.ps1xml.</span></span>

<span data-ttu-id="55b46-122">Se precisar de ver as propriedades além das que do Windows PowerShell apresenta por predefinição, terá de formatar os dados de saída por si.</span><span class="sxs-lookup"><span data-stu-id="55b46-122">If you need to look at properties other than those that Windows PowerShell displays by default, you will need to format the output data yourself.</span></span> <span data-ttu-id="55b46-123">Isto pode ser feito utilizando os cmdlets de formato.</span><span class="sxs-lookup"><span data-stu-id="55b46-123">This can be done by using the format cmdlets.</span></span>